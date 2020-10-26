# Sketch Filter in Spark AR
*Beginner*

In this guide, you'll learn to create a simple camera effect that resembles an ink sketch done on white paper using Shaders.

We're going to use built-in shaders patches - the easiest way to achieve a variety of artistic styles for the Instagram camera.

### Setting up

Create a new **Blank Project** and follow along.

1. Click on **Add Object** and select **Rectangle**. Set the **Size** and **Width** of the rectangle to **Fill Height**, and **Fill Width** - rectangle will fill the screen of the device.

![Test Animated Gif](/tutorial-img/fill-width.gif)

2. Create a **Material** for the Rectangle. Set the **Shader Type** to **Flat**.
3. To create a patch for the material:
   1. Select the material
   2. Click the arrow next to Diffuse in the Inspector

### Using Spark AR Library

![Test Animated Gif](/tutorial-img/library.png)

1. Click on **Library** and select **Patch Assets**. 
2. In Collections select **Shaders**.
3. Scroll to the bottom, and select **Sobel Filter**.
4. Press on **Import Free*

![Test Animated Gif](/tutorial-img/AR-Library-Sobel-filter3.gif)

The description of the Sobel Filter already has a hint of how to use it. We will do exactly that.

![Test Animated Gif](/tutorial-img/sobel-screen.png)

Now we need to open Patch Editor.

![Test Animated Gif](/tutorial-img/view-patch-editor.png)

Select **View** - **Show/Hide Patch Editor**.

Now when we have Patch Editor open we will start building our effect.

1. Click on **Camera**, and select ""+"" button against **Texture Extraction**
2. Drag extracted texture to the Patch Editor.

![Drag Camara Texture to the Patch Editor](/tutorial-img/camera-texture-drag.gif)

3. Click on **Device**, and also drag it to the Patch Editor.
4. Mouse-click on Pacth Editor, and in the **Search** area type **"Divide"** - **Add Patch**
5. Connect Device **Screen Size** output to the **First Value** of Divide patch, and **Screen Scale** to the  **Second Value**

![Divide patch](/tutorial-img/divide-conect.gif)

6. Connect **Divide** output to the **Texture Size** input of the Sobel Filter patch. 

7. Drag **Sobel Filter** to the Patch Editor, and connect **RGBA** output from **cameraTexture** to the **Sobel Filter**.
8. Mouse-click on Patch Editor, and in the **Search** area type **"Swizzle"** - **Add Patch**
9. Connect **Sobel Filter** to the input **Value** of the **Swizzle** patch.
10. In **Swizzle** patch change Swizzle value from "x" to "**rgb1**"
11. Connect **Swizzle** output to the input of a **Diffuse Texture**.

![Sobel Filter](/tutorial-img/sobel-filter-preview.png)

Now we can see in see our first Shader at work.
To give our filter a cleaner look, we will add another Shader - **Adjust Color** Shader. So we going to repeat the steps to access the Shaders library.

1. Click on **Library** and select **Patch Assets**. 
2. In Collections select **Shaders**.
3. Scroll to the middle, and select **Adjust Colors**.
4. Press on **Import Free*
5. Drag **Adjust Colors** Shader to the patch editor.
6. Now we need to add our Shader betwen Swizzle and Diffuse Texture, so break the connection between them. 
7. Connect **Swizzle** output to the **Texture** input of Adjust Colors Shader patch, and connect output to the **Diffuse Texture**.

![Adjust Colors Shader](/tutorial-img/adjust-color-shader.png)

If you ever used photo-editing software you will be probably familiar with at least with concepts of Brightness and Contrast.
Our goal is to adjust the value to the point where we have a minimum of color noise and have maximum contrast on the edges.

The last Shader we going ro add is DuoTone Shader. And again we going to repeat steps to access the Shaders library.

1. Click on **Library** and select **Patch Assets**. 
2. In Collections select **Shaders**.
3. Select **Duotone Color**.
4. Press on **Import Free**
5. Drag DuoTone Shader to the patch editor.
6. Again brake connection between Adjust Colors Shader and Diffuse Texture.
7. Connect Adjust Colors Shader's output to the **Texture** input of DuoTone Shader patch, and connect output to the Diffuse Texture.

And the last step is to change Color A to white and color B to black. You can tweak the value of Adjust Colors Shader to your satisfaction.

![DuoTone Shader](/tutorial-img/duotone-shader.png)

Following the same steps, you can play with different Shaders to  achieve different camera effects.




