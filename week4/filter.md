---
title: Problem Set 4 - Filter
tags: programming, cs50
use: Exercise
languages: C
dependences: CS50
---

<details> <summary>Table of Contents</summary>

- [Filter Less](#filter-less)
  - [Background](#background)
    - [Bitmaps](#bitmaps)
    - [A Bit(map) More Technical](#a-bitmap-more-technical)
    - [Image Filtering](#image-filtering)
      - [Grayscale](#grayscale)
      - [Sepia](#sepia)
      - [Reflection](#reflection)
      - [Blur](#blur)
  - [Getting Started](#getting-started)
  - [Understanding](#understanding)
    - [`bmp.h`](#bmph)
    - [`filter.c`](#filterc)
    - [`helpers.h`](#helpersh)
    - [`helpers.c`](#helpersc)
    - [`Makefile`](#makefile)
  - [Specification](#specification)
  - [Usage](#usage)
  - [Hints](#hints)
  - [Testing](#testing)
  - [How to Submit](#how-to-submit)
- [Filter More](#filter-more)
  - [Background](#background-1)
    - [Image Filtering](#image-filtering-1)
      - [Edges](#edges)
  - [Getting Started](#getting-started-1)
  - [Specification](#specification-1)
  - [Hints](#hints-1)
  - [Testing](#testing-1)
  - [How to Submit](#how-to-submit-1)
- [Walkthrough](#walkthrough)
  - [**Grayscale function (`grayscale`):**](#grayscale-function-grayscale)
  - [**Sepia function (`sepia`):**](#sepia-function-sepia)
  - [**Reflect function (`reflect`):**](#reflect-function-reflect)
  - [**Blur function (`blur`):**](#blur-function-blur)
  - [Trace Log](#trace-log)
  - [Style](#style)
  - [Submitted](#submitted)

</details>

---

# Filter Less

Implement a program that applies filters to BMPs, per the below.

```bash
$ ./filter -r IMAGE.bmp REFLECTED.bmp
```

where `IMAGE.bmp` is the name of an image file and `REFLECTED.bmp` is the name given to an output image file, now reflected.

## Background

### Bitmaps

Perhaps the simplest way to represent an image is with a grid of pixels (i.e., dots), each of which can be of a different color. For black-and-white images, we thus need 1 bit per pixel, as 0 could represent black and 1 could represent white, as in the below.

![a simple bitmap](https://cs50.harvard.edu/x/2023/psets/4/filter/less//bitmap.png)

In this sense, then, is an image just a bitmap (i.e., a map of bits). For more colorful images, you simply need more bits per pixel. A file format (like [BMP](https://en.wikipedia.org/wiki/BMP_file_format), [JPEG](https://en.wikipedia.org/wiki/JPEG), or [PNG](https://en.wikipedia.org/wiki/Portable_Network_Graphics)) that supports “24-bit color” uses 24 bits per pixel. (BMP actually supports 1-, 4-, 8-, 16-, 24-, and 32-bit color.)

A 24-bit BMP uses 8 bits to signify the amount of red in a pixel’s color, 8 bits to signify the amount of green in a pixel’s color, and 8 bits to signify the amount of blue in a pixel’s color. If you’ve ever heard of RGB color, well, there you have it: red, green, blue.

If the R, G, and B values of some pixel in a BMP are, say, `0xff`, `0x00`, and `0x00` in hexadecimal, that pixel is purely red, as `0xff` (otherwise known as `255` in decimal) implies “a lot of red,” while `0x00` and `0x00` imply “no green” and “no blue,” respectively.

### A Bit(map) More Technical

Recall that a file is just a sequence of bits, arranged in some fashion. A 24-bit BMP file, then, is essentially just a sequence of bits, (almost) every 24 of which happen to represent some pixel’s color. But a BMP file also contains some “metadata,” information like an image’s height and width. That metadata is stored at the beginning of the file in the form of two data structures generally referred to as “headers,” not to be confused with C’s header files. (Incidentally, these headers have evolved over time. This problem uses the latest version of Microsoft’s BMP format, 4.0, which debuted with Windows 95.)

The first of these headers, called `BITMAPFILEHEADER`, is 14 bytes long. (*Recall that 1 byte equals 8 bits*) The second of these headers, called `BITMAPINFOHEADER`, is 40 bytes long. Immediately following these headers is the actual bitmap: an array of bytes, triples of which represent a pixel’s color. However, BMP stores these triples backwards (i.e., as BGR), with 8 bits for blue, followed by 8 bits for green, followed by 8 bits for red. (Some BMPs also store the entire bitmap backwards, with an image’s top row at the end of the BMP file. But we’ve stored this problem set’s BMPs as described herein, with each bitmap’s top row first and bottom row last.) In other words, were we to convert the 1-bit smiley above to a 24-bit smiley, substituting red for black, a 24-bit BMP would store this bitmap as follows, where `0000ff` signifies red and `ffffff` signifies white; we’ve highlighted in red all instances of `0000ff`.

![red smile](https://cs50.harvard.edu/x/2023/psets/4/filter/less//red_smile.png)

> Because we’ve presented these bits from left to right, top to bottom, in 8 columns, you can actually see the red smiley if you take a step back.

To be clear, recall that a hexadecimal digit represents 4 bits. Accordingly, `ffffff` in hexadecimal actually signifies `111111111111111111111111` in binary.

Notice that you could represent a bitmap as a 2-dimensional array of pixels: where the image is an array of rows, each row is an array of pixels. Indeed, that’s how we’ve chosen to represent bitmap images in this problem.

### Image Filtering

What does it even mean to filter an image? You can think of filtering an image as taking the pixels of some original image, and modifying each pixel in such a way that a particular effect is apparent in the resulting image.

#### Grayscale

One common filter is the “grayscale” filter, where we take an image and want to convert it to black-and-white. How does that work?

Recall that if the red, green, and blue values are all set to `0x00` (hexadecimal for `0`), then the pixel is black. And if all values are set to `0xff` (hexadecimal for `255`), then the pixel is white. So long as the red, green, and blue values are all equal, the result will be varying shades of gray along the black-white spectrum, with higher values meaning lighter shades (closer to white) and lower values meaning darker shades (closer to black).

So to convert a pixel to grayscale, we just need to make sure the red, green, and blue values are all the same value. But how do we know what value to make them? Well, it’s probably reasonable to expect that if the original red, green, and blue values were all pretty high, then the new value should also be pretty high. And if the original values were all low, then the new value should also be low.

In fact, to ensure each pixel of the new image still has the same general brightness or darkness as the old image, we can take the average of the red, green, and blue values to determine what shade of grey to make the new pixel.

If you apply that to each pixel in the image, the result will be an image converted to grayscale.

#### Sepia

Most image editing programs support a “sepia” filter, which gives images an old-timey feel by making the whole image look a bit reddish-brown.

An image can be converted to sepia by taking each pixel, and computing new red, green, and blue values based on the original values of the three.

There are a number of algorithms for converting an image to sepia, but for this problem, we’ll ask you to use the following algorithm. For each pixel, the sepia color values should be calculated based on the original color values per the below.

```c
  sepiaRed = .393 * originalRed + .769 * originalGreen + .189 * originalBlue
  sepiaGreen = .349 * originalRed + .686 * originalGreen + .168 * originalBlue
  sepiaBlue = .272 * originalRed + .534 * originalGreen + .131 * originalBlue
```

Of course, the result of each of these formulas may not be an integer, but each value could be rounded to the nearest integer. It’s also possible that the result of the formula is a number greater than 255, the maximum value for an 8-bit color value. In that case, the red, green, and blue values should be capped at 255. As a result, we can guarantee that the resulting red, green, and blue values will be whole numbers between 0 and 255, inclusive.

#### Reflection

Some filters might also move pixels around. Reflecting an image, for example, is a filter where the resulting image is what you would get by placing the original image in front of a mirror. So any pixels on the left side of the image should end up on the right, and vice versa.

Note that all of the original pixels of the original image will still be present in the reflected image, it’s just that those pixels may have rearranged to be in a different place in the image.

#### Blur

There are a number of ways to create the effect of blurring or softening an image. For this problem, we’ll use the “box blur,” which works by taking each pixel and, for each color value, giving it a new value by averaging the color values of neighboring pixels.

Consider the following grid of pixels, where we’ve numbered each pixel.

![a grid of pixels](https://cs50.harvard.edu/x/2023/psets/4/filter/less//grid.png)

The new value of each pixel would be the average of the values of all of the pixels that are within 1 row and column of the original pixel (forming a 3x3 box). For example, each of the color values for pixel 6 would be obtained by averaging the original color values of pixels 1, 2, 3, 5, 6, 7, 9, 10, and 11 (note that pixel 6 itself is included in the average). Likewise, the color values for pixel 11 would be be obtained by averaging the color values of pixels 6, 7, 8, 10, 11, 12, 14, 15 and 16.

For a pixel along the edge or corner, like pixel 15, we would still look for all pixels within 1 row and column: in this case, pixels 10, 11, 12, 14, 15, and 16.

## Getting Started

Log into [code.cs50.io](https://code.cs50.io/), click on your terminal window, and execute `cd` by itself. You should find that your terminal window’s prompt resembles the below:

```bash
$
```

Next execute

```bash
wget https://cdn.cs50.net/2022/fall/psets/4/filter-less.zip
```

in order to download a ZIP called `filter-less.zip` into your codespace.

Then execute

```bash
unzip filter-less.zip
```

to create a folder called `filter-less`. You no longer need the ZIP file, so you can execute

```bash
rm filter-less.zip
```

and respond with “y” followed by Enter at the prompt to remove the ZIP file you downloaded.

Now type

```bash
cd filter-less
```

followed by Enter to move yourself into (i.e., open) that directory. Your prompt should now resemble the below.

```bash
filter-less/ $
```

Execute `ls` by itself, and you should see a few files: `bmp.h`, `filter.c`, `helpers.h`, `helpers.c`, and `Makefile`. You should also see a folder called `images` with four BMP files. If you run into any trouble, follow these same steps again and see if you can determine where you went wrong!

## Understanding

Let’s now take a look at some of the files provided to you as distribution code to get an understanding for what’s inside of them.

### `bmp.h`

Open up `bmp.h` (as by double-clicking on it in the file browser) and have a look.

You’ll see definitions of the headers we’ve mentioned (`BITMAPINFOHEADER` and `BITMAPFILEHEADER`). In addition, that file defines `BYTE`, `DWORD`, `LONG`, and `WORD`, data types normally found in the world of Windows programming. Notice how they’re just aliases for primitives with which you are (hopefully) already familiar. It appears that `BITMAPFILEHEADER` and `BITMAPINFOHEADER` make use of these types.

Perhaps most importantly for you, this file also defines a `struct` called `RGBTRIPLE` that, quite simply, “encapsulates” three bytes: one blue, one green, and one red (the order, recall, in which we expect to find RGB triples actually on disk).

Why are these `struct`s useful? Well, recall that a file is just a sequence of bytes (or, ultimately, bits) on disk. But those bytes are generally ordered in such a way that the first few represent something, the next few represent something else, and so on. “File formats” exist because the world has standardized what bytes mean what. Now, we could just read a file from disk into RAM as one big array of bytes. And we could just remember that the byte at `array[i]` represents one thing, while the byte at `array[j]` represents another. But why not give some of those bytes names so that we can retrieve them from memory more easily? That’s precisely what the structs in `bmp.h` allow us to do. Rather than think of some file as one long sequence of bytes, we can instead think of it as a sequence of `struct`s.

### `filter.c`

Now, let’s open up `filter.c`. This file has been written already for you, but there are a couple important points worth noting here.

First, notice the definition of `filters` on line 10. That string tells the program what the allowable command-line arguments to the program are: `b`, `g`, `r`, and `s`. Each of them specifies a different filter that we might apply to our images: blur, grayscale, reflection, and sepia.

The next several lines open up an image file, make sure it’s indeed a BMP file, and read all of the pixel information into a 2D array called `image`.

Scroll down to the `switch` statement that begins on line 101. Notice that, depending on what `filter` we’ve chosen, a different function is called: if the user chooses filter `b`, the program calls the `blur` function; if `g`, then `grayscale` is called; if `r`, then `reflect` is called; and if `s`, then `sepia` is called. Notice, too, that each of these functions take as arguments the height of the image, the width of the image, and the 2D array of pixels.

These are the functions you’ll (soon!) implement. As you might imagine, the goal is for each of these functions to edit the 2D array of pixels in such a way that the desired filter is applied to the image.

The remaining lines of the program take the resulting `image` and write them out to a new image file.

### `helpers.h`

Next, take a look at `helpers.h`. This file is quite short, and just provides the function prototypes for the functions you saw earlier.

Here, take note of the fact that each function takes a 2D array called `image` as an argument, where `image` is an array of `height` many rows, and each row is itself another array of `width` many `RGBTRIPLE`s. So if `image` represents the whole picture, then `image[0]` represents the first row, and `image[0][0]` represents the pixel in the upper-left corner of the image.

### `helpers.c`

Now, open up `helpers.c`. Here’s where the implementation of the functions declared in `helpers.h` belong. But note that, right now, the implementations are missing! This part is up to you.

### `Makefile`

Finally, let’s look at `Makefile`. This file specifies what should happen when we run a terminal command like `make filter`. Whereas programs you may have written before were confined to just one file, `filter` seems to use multiple files: `filter.c` and `helpers.c`. So we’ll need to tell `make` how to compile this file.

Try compiling `filter` for yourself by going to your terminal and running

```bash
$ make filter
```

Then, you can run the program by running:

```bash
$ ./filter -g images/yard.bmp out.bmp
```

which takes the image at `images/yard.bmp`, and generates a new image called `out.bmp` after running the pixels through the `grayscale` function. `grayscale` doesn’t do anything just yet, though, so the output image should look the same as the original yard.

## Specification

Implement the functions in `helpers.c` such that a user can apply grayscale, sepia, reflection, or blur filters to their images.

-   The function `grayscale` should take an image and turn it into a black-and-white version of the same image.
-   The function `sepia` should take an image and turn it into a sepia version of the same image.
-   The `reflect` function should take an image and reflect it horizontally.
-   Finally, the `blur` function should take an image and turn it into a box-blurred version of the same image.

You should not modify any of the function signatures, nor should you modify any other files other than `helpers.c`.

## Usage

Your program should behave per the examples below. `INFILE.bmp` is the name of the input image and `OUTFILE.bmp` is the name of the resulting image after a filter has been applied.

```bash
$ ./filter -g INFILE.bmp OUTFILE.bmp
```

```bash
$ ./filter -s INFILE.bmp OUTFILE.bmp
```

```bash
$ ./filter -r INFILE.bmp OUTFILE.bmp
```

```bash
$ ./filter -b INFILE.bmp OUTFILE.bmp
```

## Hints

-   The values of a pixel’s `rgbtRed`, `rgbtGreen`, and `rgbtBlue` components are all integers, so be sure to round any floating-point numbers to the nearest integer when assigning them to a pixel value!
-   When implementing the `grayscale` function, you’ll need to average the values of 3 integers. Why might you want to divide the sum of these integers by 3.0 and not 3?
-   In the `reflect` function, you’ll need to swap the values of pixels on opposite sides of a row. Recall from lecture how we implemented swapping two values with a temporary variable. No need to use a separate function for swapping unless you would like to!
-   How might a function that returns the lesser of two integers come in handy while implementing `sepia`, particularly when you need to make sure a color’s value is no higher than 255?
-   When implementing the `blur` function, you might find that blurring one pixel ends up affecting the blur of another pixel. Perhaps create a copy of `image` (the function’s third argument) by declaring a new (two-dimensional) array with code like `RGBTRIPLE copy[height][width];` and copying `image` into `copy`, pixel by pixel, with nested `for` loops? And then read pixels’ colors from `copy` but write (i.e., change) pixels’ colors in `image`?

## Testing

Be sure to test all of your filters on the sample bitmap files provided!

Execute the below to evaluate the correctness of your code using `check50`. But be sure to compile and test it yourself as well!

```bash
check50 cs50/problems/2023/x/filter/less
```

Execute the below to evaluate the style of your code using `style50`.

```bash
style50 helpers.c
```

## How to Submit

In your terminal, execute the below to submit your work.

```bash
submit50 cs50/problems/2023/x/filter/less
```

---

# Filter More

## Background
> *[...]*

### Image Filtering
> *[...]*

#### Edges

In artificial intelligence algorithms for image processing, it is often useful to detect edges in an image: lines in the image that create a boundary between one object and another. One way to achieve this effect is by applying the [Sobel operator](https://en.wikipedia.org/wiki/Sobel_operator) to the image.

Like image blurring, edge detection also works by taking each pixel, and modifying it based on the 3x3 grid of pixels that surrounds that pixel. But instead of just taking the average of the nine pixels, the Sobel operator computes the new value of each pixel by taking a weighted sum of the values for the surrounding pixels. And since edges between objects could take place in both a vertical and a horizontal direction, you’ll actually compute two weighted sums: one for detecting edges in the x direction, and one for detecting edges in the y direction. In particular, you’ll use the following two “kernels”:

![Sobel kernels](https://cs50.harvard.edu/x/2023/psets/4/filter/more/sobel.png)

How to interpret these kernels? In short, for each of the three color values for each pixel, we’ll compute two values `Gx` and `Gy`. To compute `Gx` for the red channel value of a pixel, for instance, we’ll take the original red values for the nine pixels that form a 3x3 box around the pixel, multiply them each by the corresponding value in the `Gx` kernel, and take the sum of the resulting values.

Why these particular values for the kernel? In the `Gx` direction, for instance, we’re multiplying the pixels to the right of the target pixel by a positive number, and multiplying the pixels to the left of the target pixel by a negative number. When we take the sum, if the pixels on the right are a similar color to the pixels on the left, the result will be close to 0 (the numbers cancel out). But if the pixels on the right are very different from the pixels on the left, then the resulting value will be very positive or very negative, indicating a change in color that likely is the result of a boundary between objects. And a similar argument holds true for calculating edges in the `y` direction.

Using these kernels, we can generate a `Gx` and `Gy` value for each of the red, green, and blue channels for a pixel. But each channel can only take on one value, not two: so we need some way to combine `Gx` and `Gy` into a single value. The Sobel filter algorithm combines `Gx` and `Gy` into a final value by calculating the square root of `Gx^2 + Gy^2`. And since channel values can only take on integer values from 0 to 255, be sure the resulting value is rounded to the nearest integer and capped at 255!

And what about handling pixels at the edge, or in the corner of the image? There are many ways to handle pixels at the edge, but for the purposes of this problem, we’ll ask you to treat the image as if there was a 1 pixel solid black border around the edge of the image: therefore, trying to access a pixel past the edge of the image should be treated as a solid black pixel (values of 0 for each of red, green, and blue). This will effectively ignore those pixels from our calculations of `Gx` and `Gy`.

## Getting Started

Log into [code.cs50.io](https://code.cs50.io/), click on your terminal window, and execute `cd` by itself. You should find that your terminal window’s prompt resembles the below:

```bash
$
```

Next execute

```bash
wget https://cdn.cs50.net/2022/fall/psets/4/filter-more.zip
```

in order to download a ZIP called `filter-more.zip` into your codespace.

Then execute

```bash
unzip filter-more.zip
```

to create a folder called `filter-more`. You no longer need the ZIP file, so you can execute

```bash
rm filter-more.zip
```

and respond with “y” followed by Enter at the prompt to remove the ZIP file you downloaded.

Now type

```bash
cd filter-more
```

followed by Enter to move yourself into (i.e., open) that directory. Your prompt should now resemble the below.

```bash
filter-more/ $
```

Execute `ls` by itself, and you should see a few files: `bmp.h`, `filter.c`, `helpers.h`, `helpers.c`, and `Makefile`. You should also see a folder called `images` with four BMP files. If you run into any trouble, follow these same steps again and see if you can determine where you went wrong!

## Specification

Implement the functions in `helpers.c` such that a user can apply grayscale, reflection, blur, or edge detection filters to their images.

>-   The function `grayscale` should take an image and turn it into a black-and-white version of the same image.
>-   The `reflect` function should take an image and reflect it horizontally.
>-   The `blur` function should take an image and turn it into a box-blurred version of the same image.
-   The `edges` function should take an image and highlight the edges between objects, according to the Sobel operator.

## Hints

-   The values of a pixel’s `rgbtRed`, `rgbtGreen`, and `rgbtBlue` components are all integers, so be sure to round any floating-point numbers to the nearest integer when assigning them to a pixel value!

## Testing

Be sure to test all of your filters on the sample bitmap files provided!

Execute the below to evaluate the correctness of your code using `check50`. But be sure to compile and test it yourself as well!

```bash
check50 cs50/problems/2023/x/filter/more
```

Execute the below to evaluate the style of your code using `style50`.

```bash
style50 helpers.c
```

## How to Submit

In your terminal, execute the below to submit your work.

```bash
submit50 cs50/problems/2023/x/filter/more
```

---

# Walkthrough
> Full code [here](./src/filter-less/helpers.c)

Firstly we need to add some headers (why not in some `.h` file)
The process to loop through the array elements is the same as in Smile

```c
for (int i = 0; i < height; i++)
{
	for (int j = 0; j < width; j++) {...}
}
```

## **Grayscale function (`grayscale`):**

For each pixel, it calculates the average value of the red, green, and blue components by summing them up and dividing by 3.

```c
RGBTRIPLE pixel = image[i][j];

// Calculate average of RGB values
BYTE average = (pixel.rgbtRed + pixel.rgbtGreen + pixel.rgbtBlue) / 3;

// Assign the average value to each RGB component
image[i][j].rgbtRed = average;
image[i][j].rgbtGreen = average;
image[i][j].rgbtBlue = average;
```

The calculated average value is then assigned to each RGB component of the pixel, effectively converting it to grayscale.

## **Sepia function (`sepia`):**

For each pixel, it applies the sepia transformation by using the [formulas](#sepia) to calculate new values for the red, green, and blue components, slightly changed to fulfill the requirements.

```c
RGBTRIPLE pixel = image[i][j];

// Apply sepia formula to each RGB component
int sepiaRed = round(0.393 * pixel.rgbtRed + 0.769 * pixel.rgbtGreen + 0.189 * pixel.rgbtBlue);
int sepiaGreen = round(0.349 * pixel.rgbtRed + 0.686 * pixel.rgbtGreen + 0.168 * pixel.rgbtBlue);
int sepiaBlue = round(0.272 * pixel.rgbtRed + 0.534 * pixel.rgbtGreen + 0.131 * pixel.rgbtBlue);

// Cap the values at 255 if they exceed by ternary operator
image[i][j].rgbtRed = (sepiaRed > 255) ? 255 : sepiaRed;
image[i][j].rgbtGreen = (sepiaGreen > 255) ? 255 : sepiaGreen;
image[i][j].rgbtBlue = (sepiaBlue > 255) ? 255 : sepiaBlue;
```

The calculated values are then assigned to the corresponding RGB components of the pixel.

## **Reflect function (`reflect`):**

For each row of pixels, it swaps (using the traditional `temp`) the pixels from the left and right sides of the image, and that’s it.

```c
// Swap pixels from left and right sides
RGBTRIPLE temp = image[i][j];
image[i][j] = image[i][width - 1 - j];
image[i][width - 1 - j] = temp;
```

`temp` holds the value of the pixel on the left side, then assigning the value of the pixel on the right side to the left side, and finally assigning the temporary value to the right side, and so, inverting the image horizontally.


## **Blur function (`blur`):**

This was a bit more complex. It starts by creating a temporary copy of the image, stored in the `tempImage` array, using `calloc` as dynamic memory allocation.
> **Why?** 
> *Short answer*:
> Using `calloc` eliminates the need to manually initialize the memory block to zero after using `malloc`. It provides a convenient (*or laziness*) way to allocate and initialize memory in a single step.
> 
> *Long answer*:
> Because the initialization (*just a convenience*). `malloc` allocates uninitialized memory, which means the contents of the allocated memory block are undefined. On the other hand, `calloc` allocates memory and initializes all its bytes to zero.
> 
> Since `tempImage` represents an image, initializing it with zeroes is desirable because it ensures that all the pixels in the temporary image are initialized to black (RGB values of 0). This is important because the `blur` function calculates the average RGB values by summing the RGB values of neighbouring pixels. If the memory were uninitialized, these calculations would be incorrect.

```c
// Create a temporary copy of the image
RGBTRIPLE(*tempImage)[width] = calloc(height, width * sizeof(RGBTRIPLE));
if (tempImage == NULL)
{
	printf("Not enough memory to store temporary image.\n");
	return;
}
```
> Personal suggestion: as the error return values in `filter.c` are all numbers different of `0`, it would make sense if `buffer()` is changed to an `int` function type.

For each pixel, it calculates the sum of the RGB values of the pixel itself and its neighbouring pixels (including diagonals) within a `3x3` grid.

```c
for (int k = -1; k <= 1; k++)
{
	for (int l = -1; l <= 1; l++) {...}
}
```

And
- first verify is the grid box is still in the image boundaries (`if` condition)
- keeps track of the count of neighbouring pixels included in the sum (using the `count` variable)
- calculates the average RGB values by dividing the sum of the RGB values by the `count`

```c
for (int l = -1; l <= 1; l++) 
{
	int row = i + k;
	int col = j + l;
	
	// Check if the neighboring pixel is within the image bounds
	if (row >= 0 && row < height && col >= 0 && col < width)
	{
		// Accumulate the RGB values of neighboring pixels
		redSum += image[row][col].rgbtRed;
		greenSum += image[row][col].rgbtGreen;
		blueSum += image[row][col].rgbtBlue;
		count++;
	}
}
```

The calculated average values are assigned to the corresponding pixel in the `tempImage` array.

```c
// Calculate the average RGB values and assign them to the current pixel in the temporary image
tempImage[i][j].rgbtRed = round((float)redSum / count);
tempImage[i][j].rgbtGreen = round((float)greenSum / count);
tempImage[i][j].rgbtBlue = round((float)blueSum / count);
```

Once the entire image is processed (*and that's a **lot** of loops*), the pixels from the `tempImage` array are copied back to the original `image` array (*in another loop!*),  applying the blur effect to the original image. Finally, the memory allocated for the `tempImage` array is freed.

## Trace Log

```log
### :( grayscale correctly filters single pixel without whole number average
**Cause**  
expected "28 28 28\\n", not "27 27 27\\n"  

**Log**  
testing with pixel (27, 28, 28)  
running ./testing 0 1...  
checking for output "28 28 28\\n"... 

**Expected Output:**  
28 28 28  

**Actual Output:**  
27 27 27

### :( grayscale correctly filters more complex 3x3 image
**Cause**  
expected "20 20 20\\n50 5...", not "20 20 20\\n50 5..."  

**Log**  
testing with sample 3x3 image  
first row: (10, 20, 30), (40, 50, 60), (70, 80, 90)  
second row: (110, 130, 140), (120, 140, 150), (130, 150, 160)  
third row: (200, 210, 220), (220, 230, 240), (240, 250, 255)  
running ./testing 0 4...  
checking for output "20 20 20\\n50 50 50\\n80 80 80\\n127 127 127\\n137 137 137\\n147 147 147\\n210 210 210\\n230 230 230\\n248 248 248\\n"...  

**Expected Output:**  
20 20 20  
50 50 50  
80 80 80  
127 127 127  
137 137 137  
147 147 147  
210 210 210  
230 230 230  
248 248 248  

**Actual Output:**  
20 20 20  
50 50 50  
80 80 80  
127 127 127  
137 137 137  
147 147 147  
210 210 210  
230 230 230  
249 249 249
```

Have to use `round()` then on `BYTE average`.

```bash
filter-less/ $ check50 cs50/problems/2023/x/filter/less
Connecting.......
Authenticating...
Verifying......
Preparing.....
Uploading......
Waiting for results.......................
Results for cs50/problems/2023/x/filter/less generated by check50 v3.3.7'
:) helpers.c exists
:) filter compiles
:) grayscale correctly filters single pixel with whole number average
:) grayscale correctly filters single pixel without whole number average
:) grayscale leaves alone pixels that are already gray
:) grayscale correctly filters simple 3x3 image
:) grayscale correctly filters more complex 3x3 image
:) grayscale correctly filters 4x4 image
:) sepia correctly filters single pixel
:) sepia correctly filters simple 3x3 image
:) sepia correctly filters more complex 3x3 image
:) sepia correctly filters 4x4 image
:) reflect correctly filters 1x2 image
:) reflect correctly filters 1x3 image
:) reflect correctly filters image that is its own mirror image
:) reflect correctly filters 3x3 image
:) reflect correctly filters 4x4 image
:) blur correctly filters middle pixel
:) blur correctly filters pixel on edge
:) blur correctly filters pixel in corner
:) blur correctly filters 3x3 image
:) blur correctly filters 4x4 image'
To see the results in your browser go to https://submit.cs50.io/check50/######################################
```

## Style

```bash
filter-less/ $ style50 helpers.c
Results generated by style50 v2.7.5
'Looks good!'
```

## Submitted

```bash
filter-less/ $ submit50 cs50/problems/2023/x/filter/less
Connecting......
Authenticating...
Verifying......
Preparing.....
Files that will be submitted:
'./helpers.c'
Files that won\'t be submitted:
./bmp.h
./filter.c
./images/tower.bmp
./images/yard.bmp
./filter
./helpers.h
./Makefile
./images/courtyard.bmp
./images/stadium.bmp
Keeping in mind the course\'s policy on academic honesty, are you sure you want to submit these files (yes/no)? yes
Uploading......
Go to https://submit.cs50.io/users/see7e/cs50/problems/2023/x/filter/less to see your results.
```