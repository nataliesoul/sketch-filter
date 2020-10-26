# "Ink Sketch" Filter using Shaders in Spark AR
*Beginner*

In this guide you'll learn to create a simple camera effect that resembles ink sketch done on white paper.

We're going to use a built-in shaders patches - easiest way to achive variety of atistic styles for Instagram camera.

### Setting up

Create new **Blank Project** and follow along.

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

Discription of the Sobel Filter already have a hint of how to use it. We will do exactly that.

![Test Animated Gif](/tutorial-img/sobel-screen.png)

Now we need to open Patch Editor.

![Test Animated Gif](/tutorial-img/view-patch-editor.png)

Select **View** - **Show/Hide Patch Editor**.

Now when we have Patch Editor open we will start building our effect.

1. Click on **Camera**, and select ""+"" button against **Texture Extraction**
2. Drag extracted texture to the Patch Editor.
3. Cick on **Device**, and also drag it to the Patch Editor.
4. Connect Device **Screen Size** outbut to the **First Value** of Divide patch, ans **Screen Scale** to the  **Second Value**
5. Connect **Divide** output to the **Texture Size** input of Sobel Filter patch. 
4. Mouse-click on Pacth Editor, and in the **Search** area type **"Divide"** - **Add Pacth**
5. Drag **Sobel Filter** to the Patch Editor, and conect **RGBA** output from **cameraTexture** to the **Sobel Filter**.
6. Mouse-click on Pacth Editor, and in the **Search** area type **"Sweezle"** - **Add Pacth**
7. Connect **Sobel Filter** to the input **Value** of **Swizzle** patch.
8. In **Swizzle** patch change Swizzle value from "x" to "**rgb1**"
8. Connect **Swizzle** output to the input of a **Diffuse Texture**.

Now we can see in see our furst Shader in work.
To give our filter cleaner look we will add another Shader - **Adjust Color** Shader. So we going to repetat speps to acess librury of Shaders.

1. Click on **Library** and select **Patch Assets**. 
2. In Collections select **Shaders**.
3. Scroll to the middle, and select **Adjust Colors**.
4. Press on **Import Free*
5. Drag **Adjust Colors** Shader to the patch editor.
5. Now we need to add our Shader betwen Swizzle and Diffuse Texture, so brake the connection between them. 
6. Connect Swizzle output to the **Texture** input of Adjust Colors Shader patch, and output connect to the Diffuse Texture.

If you ever used photo-editing software you will be probably familiar with at least with concepts of Brightness and Contrast.
Our goal is to adjust value to the point where we have minimum of color noise and have maximum contrast on the edges.

Last Shader we going ro add is DuoTone Shader. And again we going to repetat steps to acess librury of Shaders.

1. Click on **Library** and select **Patch Assets**. 
2. In Collections select **Shaders**.
3. Select **Duotone Color**.
4. Press on **Import Free*
5. Drag DuoTone Shader to the patch editor.
6. Again brake conection between Adjust Colors Shader and Diffuse Texture.
7. Connect Adjust Colors Shader's output to the **Texture** input of DuoTone Shader patch, and output connect to the Diffuse Texture.

And the last step is to change Color A to white and color B to black. You can tweak value of Adjust Colors Shader to your satisfaction.


Following the same steps you can play with different Shaders to achive different camera effects.




