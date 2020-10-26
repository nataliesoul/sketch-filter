# "Ink Sketch" Filter using Shaders in Spark AR
*Beginner*

In this guide you'll learn to create a simple camera effect that resembles ink sketch done on white paper.

We're going to use a built-in shaders patches - easiestway to achive variety of atistic styles for Instagram camera.

### Setting up

Create new **Blank Project** and follow along.

1. Click on **Add Object** and select **Rectangle**. Set the **Size** and **Width** of the rectangle to **Fill Height**, and **Fill Width** - rectangle will fill the screen of the device.

![Test Animated Gif](/tutorial-img/fill-width.gif)

2. Create a **Material** for the Rectangle. Set the **Shader Type** to **Flat**.
3. To create a patch for the material:
   1. Select the material
   2. Click the arrow next to Diffuse in the Inspector

### Using Spark AR Library

![Test Animated Gif](/tutorial-img/libruary.png)

1. Click on **Library** and select **Patch Assets**. 
2. In Collections select **Shaders**.
3. Scroll to the bottom, and select **Sobel Filter**.

![Test Animated Gif](/tutorial-img/AR-Library-Sobel-filter3.gif)

Discription of the Sobel Filter already have a hint of how to use it. We will do exactly that.

![Test Animated Gif](/tutorial-img/sobel-screen.png)

Now we need to open Patch Editor.

![Test Animated Gif](/tutorial-img/view-patch-editor.png)

Select **View** - **Show/Hide PAtch Editor**.
