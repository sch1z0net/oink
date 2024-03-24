
Introducing Oink FFT: A Quick and Dirty JavaScript FFT Implementation ![A funny pig is displayed, the Icon of OINK FFT](https://github.com/sch1z0net/sch1z0net.github.io/blob/main/oink_fft/favicon/favicon-32x32.png)
=====================================================================

Are you looking to dive into Fourier analysis without getting lost in complex algorithms and mathematical intricacies?  
Meet *Oink FFT* - your quick and dirty solution for Fast Fourier Transform in JavaScript.  
Whether you're exploring signal processing concepts, building audio visualizations, 
or experimenting with frequency analysis, *Oink FFT* provides a simple and effective solution 
to get you started quickly. Dive into the world of Fourier analysis with *Oink FFT* 
and unlock the dirty secrets hidden within your data.

> [!TIP]
> For a better visual presentation and even a **LIVE BENCHMARK**, please visit
> [The Official OINK Site](https://sch1z0net.github.io/oink_fft/) 

What is FFT?
------------

FFT, or Fast Fourier Transform, is a powerful algorithm used in digital signal processing 
to efficiently compute the Discrete Fourier Transform (DFT) of a sequence. 
It transforms a signal from its time-domain representation to its frequency-domain representation, 
revealing the underlying frequencies present in the signal.

Why Oink FFT?
-------------

Oink FFT is designed for simplicity and ease of use. 
It provides a pretty quick FFT algorithm in JavaScript, 
allowing you to perform frequency analysis on your data with minimal effort.

### Key Features:

1.  **Simplicity:** Oink FFT is designed to be easy to understand and use, making it perfect for beginners and casual users.
2.  **Quick and Dirty:** This FFT implementation prioritizes simplicity and speed, making it suitable for rapid prototyping and experimentation.
3.  **JavaScript-Based:** Oink FFT is written in JavaScript, making it accessible to web developers and compatible with modern web applications.
4.  **Speed-Optimized:** Leveraging WebAssembly (WASM) and harnessing specific mathematical Fourier Intrinsics, this implementation is finely tuned for exceptional speed.
5.  **Competitive Performance:** With its optimized speed, Oink FFT can effectively compete with other available FFT implementations.

Getting Started:
----------------

To start using Oink FFT, simply import the library into your JavaScript project and follow the intuitive API to perform FFT operations on your data.

> [!NOTE]
> This is an Alpha Version, providing only Forward FFTs for several sizes. Code might still contain bugs, and more features will be added in the future.

### 1. Easy Import

```javascript
// To use this library, you first need to include it in your project.
import * as OINK from 'https://cdn.jsdelivr.net/gh/sch1z0net/oink@v0.1.5-alpha/oink_fft.js';
```

### 2\. Usage Example

```javascript
// Here's how you can use the Forward FFT of size 1024
// It returns the spectrum, a Float32Array of length = 2048
// with real and imaginary values in alternating order
// [re, im, re, im, re, im ...]
let realInput = new Float32Array([/* Fill with 1024 Float Values */]);
let spectrum  = OINK.fftReal1024(realInput);
console.log("FFT Result:", spectrum);
```

### 3\. Use different available FFT sizes

```javascript
// 128 input -> 256 spectrum
let spectrum  = OINK.fftReal128(realInput);
// 256 input -> 512 spectrum
let spectrum  = OINK.fftReal256(realInput);
// 512 input -> 1024 spectrum
let spectrum  = OINK.fftReal512(realInput);
// 1024 input -> 2048 spectrum
let spectrum  = OINK.fftReal1024(realInput);
// 2048 input -> 4096 spectrum
let spectrum  = OINK.fftReal2048(realInput);
```

### Just try out some Examples

[Simple FFT Table](https://sch1z0net.github.io/oink_fft/examples/simple/) 

[FFT Plotter using Chart.js](https://sch1z0net.github.io/oink_fft/examples/plot/)

About this Project
==================

When working on a music project, I needed a quick and dirty solution to process FFT as fast as possible. 
I didn't want to rely on third party tools, so I started to study FFT on my own. 
I figured out how to exploit the symmetry properties that are intrinsic to the FFT, 
which could save a lot of execution time already. To make it a little bit dirty (but even faster) 
I used Float32 Arrays instead of the full double precision. 
The quality of the resulting sound after FFT processing is pretty acceptable, 
and if your requirements are even lower than that (like for example just displaying a rough frequency spectrum), 
then you shouldn't worry about the little 'dirt' that's introduced. 
Finally I digged even deeper to optimize the execution speed. 
So I ended up changing my initial JS code to C and used Web Assembly (WASM) to get the full potential out of modern Web Development.
