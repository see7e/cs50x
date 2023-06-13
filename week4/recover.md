---
title: Problem Set 4 - Recover
tags: programação, cs50
use: Exercise
languages: C
dependences: CS50
---

<details> <summary>Table of Contents</summary>

- [Recover](#recover)
	- [Background](#background)
	- [Getting Started](#getting-started)
	- [Specification](#specification)
	- [Usage](#usage)
	- [Hints](#hints)
	- [Testing](#testing)
	- [How to Submit](#how-to-submit)
- [Walkthrough](#walkthrough)
	- [Main Processing](#main-processing)
	- [Cleanup and Termination](#cleanup-and-termination)
	- [Trace Log](#trace-log)
	- [Style](#style)
	- [Submitted](#submitted)

</details>

---

# Recover

Implement a program that recovers JPEGs from a forensic image, per the below.

```bash
$ ./recover card.raw
```

## Background

In anticipation of this problem, we spent the past several days taking photos around campus, all of which were saved on a digital camera as JPEGs on a memory card. Unfortunately, we somehow deleted them all! Thankfully, in the computer world, “deleted” tends not to mean “deleted” so much as “forgotten.” Even though the camera insists that the card is now blank, we’re pretty sure that’s not quite true. Indeed, we’re hoping (er, expecting!) you can write a program that recovers the photos for us!

Even though JPEGs are more complicated than BMPs, JPEGs have “signatures,” patterns of bytes that can distinguish them from other file formats. Specifically, the first three bytes of JPEGs are

```
0xff 0xd8 0xff
```
> or `255 216 255` in decimal 

from first byte to third byte, left to right. The fourth byte, meanwhile, is either `0xe0`, `0xe1`, `0xe2`, `0xe3`, `0xe4`, `0xe5`, `0xe6`, `0xe7`, `0xe8`, `0xe9`, `0xea`, `0xeb`, `0xec`, `0xed`, `0xee`, or `0xef`. Put another way, the fourth byte’s first four bits are `1110`.

Odds are, if you find this pattern of four bytes on media known to store photos (e.g., my memory card), they demarcate the start of a JPEG. To be fair, you might encounter these patterns on some disk purely by chance, so data recovery isn’t an exact science.

Fortunately, digital cameras tend to store photographs contiguously on memory cards, whereby each photo is stored immediately after the previously taken photo. Accordingly, the start of a JPEG usually demarks the end of another. However, digital cameras often initialize cards with a [FAT file system](https://en.wikipedia.org/wiki/File_Allocation_Table) whose “block size” is 512 bytes (B). The implication is that these cameras only write to those cards in units of $512 B$. A photo that’s 1 MB (i.e., $1,048,576 B$) thus takes up $1,048,576 ÷ 512 = 2,048$ “blocks” on a memory card. But so does a photo that’s, say, one byte smaller (i.e., $1,048,575 B$)! The wasted space on disk is called “slack space.” Forensic investigators often look at slack space for remnants of suspicious data.

The implication of all these details is that you, the investigator, can probably write a program that iterates over a copy of my memory card, looking for JPEGs’ signatures. Each time you find a signature, you can open a new file for writing and start filling that file with bytes from my memory card, closing that file only once you encounter another signature. Moreover, rather than read my memory card’s bytes one at a time, you can read 512 of them at a time into a buffer for efficiency’s sake. Thanks to FAT, you can trust that JPEGs’ signatures will be “block-aligned.” That is, you need only look for those signatures in a block’s first four bytes.

Realize, of course, that JPEGs can span contiguous blocks. Otherwise, no JPEG could be larger than 512 B. But the last byte of a JPEG might not fall at the very end of a block. Recall the possibility of slack space. But not to worry. Because this memory card was brand-new when I started snapping photos, odds are it’d been “zeroed” (i.e., filled with 0s) by the manufacturer, in which case any slack space will be filled with 0s. It’s okay if those trailing 0s end up in the JPEGs you recover; they should still be viewable.

Now, I only have one memory card, but there are a lot of you! And so I’ve gone ahead and created a “forensic image” of the card, storing its contents, byte after byte, in a file called `card.raw`. So that you don’t waste time iterating over millions of 0s unnecessarily, I’ve only imaged the first few megabytes of the memory card. But you should ultimately find that the image contains 50 JPEGs.

## Getting Started

Log into [code.cs50.io](https://code.cs50.io/), click on your terminal window, and execute `cd` by itself. You should find that your terminal window’s prompt resembles the below:

```bash
$
```

Next execute

```bash
wget https://cdn.cs50.net/2022/fall/psets/4/recover.zip
```

in order to download a ZIP called `recover.zip` into your codespace.

Then execute

```bash
unzip recover.zip
```

to create a folder called `recover`. You no longer need the ZIP file, so you can execute

```bash
rm recover.zip
```

and respond with “y” followed by Enter at the prompt to remove the ZIP file you downloaded.

Now type

```bash
cd recover
```

followed by Enter to move yourself into (i.e., open) that directory. Your prompt should now resemble the below.

```bash
recover/ $
```

Execute `ls` by itself, and you should see two files: `recover.c` and ‘card.raw\`.

## Specification

Implement a program called `recover` that recovers JPEGs from a forensic image.

-   Implement your program in a file called `recover.c` in a directory called `recover`.
-   Your program should accept exactly one command-line argument, the name of a forensic image from which to recover JPEGs.
-   If your program is not executed with exactly one command-line argument, it should remind the user of correct usage, and `main` should return `1`.
-   If the forensic image cannot be opened for reading, your program should inform the user as much, and `main` should return `1`.
-   The files you generate should each be named `###.jpg`, where `###` is a three-digit decimal number, starting with `000` for the first image and counting up.
-   Your program, if it uses `malloc`, must not leak any memory.

## Usage

Your program should behave per the examples below.

```bash
$ ./recover
Usage: ./recover IMAGE
```

where `IMAGE` is the name of the forensic image. For example:

```bash
$ ./recover card.raw
```

## Hints

Keep in mind that you can open `card.raw` programmatically with `fopen`, as with the below, provided `argv[1]` exists.

```c
FILE *file = fopen(argv[1], "r");
```

When executed, your program should recover every one of the JPEGs from `card.raw`, storing each as a separate file in your current working directory. Your program should number the files it outputs by naming each `###.jpg`, where `###` is three-digit decimal number from `000` on up. Befriend [`sprintf`](https://man.cs50.io/3/sprintf) and note that `sprintf` stores a formatted string at a location in memory. Given the prescribed `###.jpg` format for a JPEG’s filename, how many bytes should you allocate for that string? (Don’t forget the `NUL` character!)

You need not try to recover the JPEGs’ original names. To check whether the JPEGs your program spit out are correct, simply double-click and take a look! If each photo appears intact, your operation was likely a success!

Odds are, though, the JPEGs that the first draft of your code spits out won’t be correct. (If you open them up and don’t see anything, they’re probably not correct!) Execute the command below to delete all JPEGs in your current working directory.

```bash
$ rm *.jpg
```

If you’d rather not be prompted to confirm each deletion, execute the command below instead.

```bash
$ rm -f *.jpg
```

Just be careful with that `-f` switch, as it “forces” deletion without prompting you.

If you’d like to create a new type to store a byte of data, you can do so via the below, which defines a new type called `BYTE` to be a `uint8_t` (a type defined in `stdint.h`, representing an 8-bit unsigned integer).

```c
typedef uint8_t BYTE;
```

Keep in mind, too, that you can read data from a file using [`fread`](https://man.cs50.io/3/fread), which will read data from a file into a location in memory. Per its [manual page](https://man.cs50.io/3/fread), `fread` returns the number of bytes that it has read, in which case it should either return `512` or `0`, given that `card.raw` contains some number of 512-byte blocks. In order to read every block from `card.raw`, after opening it with `fopen`, it should suffice to use a loop like:

```c
while (fread(buffer, 1, BLOCK_SIZE, raw_file) == BLOCK_SIZE)
{


}
```

That way, as soon as `fread` returns `0` (which is effectively `false`), your loop will end.

## Testing

Execute the below to evaluate the correctness of your code using `check50`. But be sure to compile and test it yourself as well!

```bash
check50 cs50/problems/2023/x/recover
```

Execute the below to evaluate the style of your code using `style50`.

```bash
style50 recover.c
```

## How to Submit

In your terminal, execute the below to submit your work.

```bash
submit50 cs50/problems/2023/x/recover
```

---

# Walkthrough
> Full code in [here](./src/recover/recover.c)

Following the guidelines of the exercise, as each image occupies a constant space in the memory, and other const value is the name of the output files so:
- `BLOCK_SIZE`: Represents the size of the chunks to be read from the forensic image. It is set to $512$ bytes.
- `FILENAME_SIZE`: Determines the size of the character array used to store the filenames of the recovered JPEG files. It is set to $8$.

If there's any doubt about the headers:
- `stdio.h`: Provides standard input/output functions.
- `stdlib.h`: Provides memory allocation functions.
- `stdint.h`: Provides fixed-width integer types.

The program has to be executed with one file at time, as it receives the information using CLI, the number of argument must be controlled with:

```c
if (argc != 2)
{
	printf("Usage: ./recover IMAGE\n");
	return 1;
}
```

It checks if the correct number of command-line arguments is provided (1 argument). If the count is incorrect, an error message is displayed, and the program returns with an exit code of 1 as asked.

Other erro handling is when the program tries to open the file with `fopen(...)`, if the file pointer can't be assigned (due to permits or nonexistence) the process is breaked and returned 1 as exit code as follows.

```c
FILE *raw_file = fopen(argv[1], "r");
if (raw_file == NULL)
{
	printf("Could not open %s as reading file.\n", argv[1]);
	return 1;
}
```

## Main Processing

The program uses a buffer of size (512 B) `BLOCK_SIZE` to read the forensic image file in chunks. It initializes `file_count` to keep track of the number of recovered JPEG files and `filename` to store the current filename being processed. The `outfile` variable is used as a pointer to `FILE` to represent the currently open JPEG file.

```c
int file_count = 0;
FILE *outfile = NULL;
uint8_t buffer[BLOCK_SIZE];
char filename[FILENAME_SIZE];
```

The main processing loop, which is given as a Hint, reads the forensic image file in chunks using `fread`. If the number of bytes read is less than `BLOCK_SIZE`, it means the end of the file has been reached, and the loop terminates.

```c
while (fread(buffer, sizeof(uint8_t), BLOCK_SIZE, raw_file) == BLOCK_SIZE)
{...}
```

Inside the loop, the program checks if the current buffer chunk contains a JPEG header by comparing the first four bytes with the JPEG header pattern: `0xff` `0xd8` `0xff`.

If a JPEG header is found, the program performs the following actions:

```c
if (buffer[0] == 0xff && buffer[1] == 0xd8 && buffer[2] == 0xff && (buffer[3] & 0xf0) == 0xe0)
{...}
```

1. Closes the previously open JPEG file (if any) using `fclose`.
	
  ```c
	if (outfile != NULL)
	{
		fclose(outfile);
		outfile = NULL;
	}
	```

2. Generates the filename for the new JPEG file by formatting the `file_count` as a three-digit decimal number and appending the ".jpg" extension.
	
	```c
	snprintf(filename, FILENAME_SIZE, "%03i.jpg", file_count);
	```

3. Attempts to open the new JPEG file in write mode using `fopen`. If the file cannot be opened, an error message is displayed, the input file is closed, and the program returns with an exit code of 1.
	
	```c
	if (outfile == NULL)
	{
		printf("Could not create %s.\n", filename);
		fclose(raw_file);
		return 1;
	}
	```

4. Increments the `file_count` for the next JPEG file.
	
  ```c
  file_count++;
  ```

If the current buffer chunk is part of a JPEG file (i.e., an open JPEG file exists), the program writes the buffer data to the file using `fwrite`.

## Cleanup and Termination

Once the main processing loop ends, the program checks if an open JPEG file exists and closes it using `fclose`.

```c
// Close files
if (outfile != NULL)
{
	fclose(outfile);
}
fclose(raw_file);
return 0;
```

Finally, both the input file and the program terminate successfully, returning 0 to indicate no errors if none occurred.

## Trace Log

```bash
recover/ $ check50 cs50/problems/2023/x/recover
Connecting......
Authenticating...
Verifying.......
Preparing.....
Uploading...............
Waiting for results..........................
Results for cs50/problems/2023/x/recover generated by check50 v3.3.7'
:) recover.c exists.
:) recover.c compiles.
:) handles lack of forensic image
:) recovers 000.jpg correctly
:) recovers middle images correctly
:) recovers 049.jpg correctly
:) program is free of memory errors
'To see the results in your browser go to https://submit.cs50.io/check50/######################################
```

## Style

```bash
recover/ $ style50 recover.c
Results generated by style50 v2.7.5
'Looks good!'
```

## Submitted

```bash
recover/ $ submit50 cs50/problems/2023/x/recover
Connecting......
Authenticating...
Verifying......
Preparing.....
Files that will be submitted:
'./recover.c'
Files that won\'t be submitted:
./014.jpg
./003.jpg
./033.jpg
./018.jpg
./029.jpg
./031.jpg
./048.jpg
./015.jpg
./010.jpg
./001.jpg
./recover
./023.jpg
./040.jpg
./041.jpg
./045.jpg
./027.jpg
./030.jpg
./025.jpg
./021.jpg
./012.jpg
./011.jpg
./024.jpg
./028.jpg
./049.jpg
./037.jpg
./013.jpg
./047.jpg
./034.jpg
./006.jpg
./007.jpg
./044.jpg
./022.jpg
./000.jpg
./019.jpg
./032.jpg
./036.jpg
./016.jpg
./042.jpg
./002.jpg
./035.jpg
./038.jpg
./020.jpg
./039.jpg
./card.raw
./026.jpg
./004.jpg
./009.jpg
./043.jpg
./005.jpg
./008.jpg
./046.jpg
./017.jpg
Keeping in mind the course\'s policy on academic honesty, are you sure you want to submit these files (yes/no)? yes
Uploading......
Go to https://submit.cs50.io/users/see7e/cs50/problems/2023/x/recover to see your results.
```
