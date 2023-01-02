---
permalink: /
---

If you’ve got a question regarding Flat Kit, **please read through the Frequently Asked Questions**, and try searching for the answers here in this documentation. Also, many questions have been already covered in the [issues page](https://github.com/Dustyroom/flat-kit-doc/issues). If the question is not covered, please [report an issue](https://github.com/Dustyroom/flat-kit-doc/issues), go to our [Discord](https://discord.gg/GBAeuWC9qS) or shoot an email to *info@dustyroom.com*.

If you find a bug, it really helps us if you include steps to reproduce it. Please mind that we get lots of messages daily, be patient - we’re getting to it. Also, if you've got a feature you’d like to see implemented, let us know — some of the great ones came from the suggestions. Flat Kit is a vast field of stylistic possibilities, so please make sure you skim trough this manual, it may help you understand all the features better and give you a few ideas.

# Frequently Asked Questions (FAQs)

#### Q. I have purchased Quibli. How do I get the discount for Flat Kit?

> **A.** Once you log into the account you have purchased Quibli from, and load the Flat Kit Asset Store page, you should see the automatic 50% off discount for Flat Kit.

#### Q. After importing/updating Flat Kit the shaders failed to compile. 'X' shader is missing from the list. Why?

> **A.** Because of the recent Unity's error, there is a mess going on with the packages in the Package Manager. You see one version of the package but in reality it may be another, unsupported one. Also, this bug won't let you install and change the versions of the assets in the Package Manager (which you need to do in this case — **you need to update the version of Universal RP**). Unity is working on it, here's the [issue tracker](https://issuetracker.unity3d.com/issues/package-manager-doesnt-show-available-updates).  
If you updated to the latest version of Unity, and still haven't resolved it, please restart Unity. If after restart the errors won’t go away, clean the cache of the Package Manager and re-import Flat Kit, as it is another one symptom of this Unity's problem. You can find the cache here  
*Mac OS:* ~/Library/Unity/Asset Store-5.x (press Shift+Cmd+G in any Finder Window or press Go -> Go to Folder on the top bar and paste this path)  
*Windows:* %APPDATA%\Unity\Asset Store-5.x (hidden folder, press Win+R to open 'Run' window and paste this path)  
*Linux:* ~/.local/share/unity3d/Asset Store-5.x  

#### Q. What is the difference between Flat Kit and Quibli?

> **A.**Flat Kit is a set of tools for bread-and-butter toon shading end effects. Quibli was designed to be more open in regards to non-photorealistic stylization, while including the tools for the anime style works. The detailed comparison can be found [here](https://quibli.dustyroom.com/quibli-flat-kit/).

#### Q. Is it easy to use Flat Kit for a beginner?  

> **A.** Yes, there's nothing complicated about it from the user perspective. Even though there are lots of parameters, they all have good default values and well-structured interface. Additionally, there are mouse-over tooltips with little hints on all parameters.

#### Q. Is it possible to apply the Flat Kit look while using my own shaders?  

> **A.** The cel shading (`Flat Kit\Stylized Surface`) is implemented as object shaders, which means that they are used on regular materials. However, the *Outline* and *Fog* are *image effects* applied globally (as camera components in the Built-In RP and as Render Features in URP).

#### Q. What platforms can I build for? What about VR?  

> **A.** Flat Kit shaders work in builds for all platforms listed in Unity Build settings, including VR, WebGL and mobile.

#### Q. There are missing scripts in some demo scenes on the main camera

> **A.** Unity has some camera scripts that are available only in a particular RP. Because we use the same scenes for the URP and Built-In RP demos in Flat Kit, it may appear that a script is missing from the camera in our demos. This warning is harmless and can be safely ignored, or you may remove the missing script from the camera.

#### Q. Does Flat Kit support URP? Why is the feature X is available in Universal RP but not in Built-In RP?  

> **A.** Flat Kit supports URP as well as Built-In RP, although Built-In RP is not being developed after Flat Kit v.2.0. There are a few known limitations in URP, please see [FlatKit in URP chapter](index.md#8-flat-kit-in-urp). As Built-In RP is being deprecated by Unity an it has its drawbacks, we continue to support it but we develop new great features only for URP, instead of supporting an obsolete technology. Please note, there is no HDRP version of Flat Kit yet.

#### Q. Does Flat Kit support PBR (Physically-Based Rendering)?  

> **A.** In Flat Kit indirect sources of light influence the colors of the scene by default, which can be turned off. The shaders do not support parameters required for the photorealistic look such as glossiness, metallic or subsurface scattering.

#### Q. Does Flat Kit support normal maps?  

> **A.** Yes, it does. It is in Normal map section of the interface.

#### Q. Does Flat Kit support emission maps?  

> **A.** Yes, the URP version. There is no support for emission maps in Built-In RP version of Flat Kit.

#### Q. I’ve got errors just after importing Flat Kit. Why?  

> **A.** First thing to try would be to restart Unity and check again. Secondly, try re-importing the asset. If none of these helped, shoot a mail to `info@dustyroom.com`.

#### Q. What is the Shader Compilation Target Level of Flat Kit shaders?  

> **A.** The object shaders target 3.5 (or es 3.0 and WebGL 2.0).

#### Q. It takes very long to import Flat Kit into Unity in Built-in RP  

> **A.** FlatKit Built-in RP uses shader variants to achieve high flexibility and best performance. This comes at a cost of increased time to import the asset and build the game binary. In URP importing is much shorter, so we encourage you to use the URP version of Flat Kit if possible. If you have to use Built-In RP, though, to speed things up, uncheck unneeded elements when importing the asset.

#### Q. Does Flat Kit work with Post-processing stack v.2?  

> **A.** Yes, it does. The fog and outline image effects can be added on the same camera as the Post-processing component (Built-in Rendering Pipeline). Post-processing in URP is known as ‘Renderer Features’, so you don't have to install Post-Processing v.2. See FlatKit in URP for the details.

# 1. Quick Overview

Flat Kit has everything you need to achieve a slick minimalist look in your project. We’ve spent hundreds of hours to research, design and implement the right set of assets needed to allow lots of customisation without sacrificing performance. We hope it works for your project out of the box, but if you have questions after reading this guide, let us know at `info@dustyroom.com`.

To name Flat Kit a set of flat shaders, cel shaders or toon ones, would be a serious underestimation. Yes, these all can be easily done. As well as countless other (maybe unseen before) styles. It can be sharp flat, it can have one, two, nine steps of hard shadow, or soft-shaded, or gradient-shaded — with pale or acid colors, it can have three gradient effects (when you start thinking out of the box, the parameter like ‘Specular’, usual for, well, a specularity or glare, here can act as your fourth shadow, or a gradient etc).

In case you already use any other flat-looking shaders, you will still find a variety of useful tools for quick image processing. Particularly, later in the manual we’ll overview the Height Gradient mode of the Stylized Surface Shader, the Fog Image Effect camera component, LightPlane shader effect etc. They have quite little related to toon or cell shading, but in conjunction with a stylish flat or cel look, they add a whole new life to your scene. Plus, they can be used out of context of non-photorealistic aesthetics. It is a spice that can dramatically make your dish sweeter (tastier).

Flat Kit was made with optimised and fast workflow in mind, so that one could fulfil the picture popped up in the mind — as quickly as possible, in various ways. This means:

* One task could be done in different ways. It is a multi-purpose set of shaders;
* Some outstanding graphical results can be achieved in minutes (given that you have your models ready, there are lots in FlatKit);
* There is always an element of you-didn’t-think-it-can-be-done-this-way surprise thanks to FlatKit deep yet streamlined interface.  
For example, let’s take fog. Fog is usually a big part of any 3D environment, isn’t it? There are lots of methods to implement fog into the scene, often complex and complicated. With Flat Kit, we decided to make it as convenient as possible for the user end. So, the fog can be done in two ways: using **Fog Image Effect** post-effect/camera component/renderer feature or/and using **LightPlane** shader (see *Wanderer* demo scene). One more way would be to use **Water** shader. Although the latter is not necessarily an obvious choice, it still is capable of doing this.

We are going to explain how these work and what they are down in the manual. Both ways suit different needs, but they really do compliment each other.

Another example of the multi-purpose nature of our shaders is cel shading itself. Now, it would take a whole chapter of this manual to elaborate on cel shading. For now it’s only worth mentioning that the same or similar results can be made using different parameters of the shader’s interface.
It’s important, because apart from the expected ‘Cel Shade parameter’, Flat Kit also has a bunch of additional settings to explore. Each additional parameter of the shader adds an extra dimension of possibilities. All the tools designed for cel shading can do bread and butter stuff, as well as add lots of juice. But what's important is that when these cel shading tools are combined, they are much more than the sum of the components — they synergise. We’ll talk about the importance of such a potential later in the manual.

One of the big advantages of using these shaders is the fact that you don’t have to guess how the colors will look on your scene. If you want precision and accuracy — you have it. Moreover, if you want something unpredictable and you are trying to make your scene look different to spark your inspiration and imagination, but not sure how, you can do this, too! Sometimes you'll find yourself saving lots of temporary 'cool stuff' in 'later' folder while working on something specific, because pleasant surprises will keep popping. Remember, this is a set of shaders selected to complement each other.

![Flat Kit structural view chart](FlatKit_Manual_Images/FlatKit-Structure-Chart.png)
> Flat Kit structural view chart.

# 2. Quick start. Beginning to work with Flat Kit

Flat Kit is fully self-contained and does not depend on any external assets.  
If you do not need demo scenes, example materials and models you may skip importing the Demos directory in the asset.  
The easiest way to get started with the asset is to dig into the demo scenes.  
For Built-In RP it may take a while for Unity to import the asset — this is normal. Under the hood, Unity needs to generate all shader variants that are used in the demo scenes. For URP it is virtually immediate.  
For URP, it is important that you created the project in URP initially, as opposed to creating a Built-in RP project and 'upgrading' it to URP one.  
On the 3D models side, it’s important that you decide whether you would like making normals ‘smooth’ or 'sharp' for your meshes in a 3D editor, as the result will be different in either case. If you import someone else's models and can’t edit the object in 3D editor, at least try to calculate normals in Unity — in the import settings of the model. The shaders should work regardless, but sometimes the difference can be obvious, especially on objects with rounded corners.  

> **Note.** Our demos were created in **Linear color space** (a setting found in Project Settings). We recommend switching to it if your project is in **Gamma color space**, although this is entirely optional.  

**Here's a video showing how to import a Universal RP (URP) version of Flat Kit in a Universal RP project.**

<iframe width="560" height="315" src="https://www.youtube.com/embed/EuDdSFXnibc" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>  

Below are the written instructions on how to import Flat Kit. You can watch the video above of follow the guide below.

* **Step 1.** It's advised that you imported Flat Kit from Unity Package Manager. Please make sure you have Unity v. 2020.3 LTS or later running. Go to Window ▶︎ Package Manager. On the top left find the My Assets drop down menu. You'll find Flat Kit among your assets. Choose the version you'd like to import. Click Download, then Import.  
![Flat Kit import instructions - Step 1](FlatKit_Manual_Images/manual_import_instructions_2.png)

* **Step 2.** Choose which version of Flat Kit to import. If your project is in URP - select [Render Pipeline] Universal (URP).unitypackage. If your project is in Built-In RP, choose [Render Pipeline] Built-In.unitypackage. Click Import. You can re-import any of the versions anytime. The latest imported version overwrites the previously installed one. If you don't see this step, see the note below.  
![Flat Kit import instructions - Step 2](FlatKit_Manual_Images/manual_import_instructions_3.png)

* **Step 3.** Once imported, go to Project tab ▶︎ Assets ▶︎ Flat Kit. You'll find the Flat Kit unitypackage file of your preferred RP. Double-click it.  
![Flat Kit import instructions - Step 3](FlatKit_Manual_Images/manual_import_instructions_4.png)

* **Step 4.** Pick what contents of Flat Kit would you like to get unpacked. Click Import. You can import anything at any time while working on your project.  
![Flat Kit import instructions - Step 4](FlatKit_Manual_Images/manual_import_instructions_5.png)

> **NOTE.** If you don't see *step 2* while importing, or URP unitypackage is missing, try cleanig the Unity Package Manager cache and import / update Flat Kit after that. The cache files can be found here:  
*Mac OS:* ~/Library/Unity/Asset Store-5.x (press Shift+Cmd+G in any Finder Window and paste this path)  
*Windows:* %APPDATA%\Unity\Asset Store-5.x (hidden folder)  
*Linux:* ~/.local/share/unity3d/Asset Store-5.x  
More info about the Unity cache can be found in the Unity community answers page [here](https://answers.unity.com/questions/45050/where-unity-store-saves-the-packages.html).  

> **NOTE.** If you are going to use the URP version of Flat Kit, it is highly advised that you created an originally URP project, **NOT** a URP project 'upgraded' from a Built-in RP one.  

We included a **Readme** tool, which is a useful debugging helper. It does the following:

* Shows the stats like Unity, Universal RP and Flat Kit's versions;
* Detects what RP the project belongs to (Universal RP or Built-In RP);
* Checks for available updates;
* Configures Flat Kit for the pipeline of the project;
* Clears Flat Kit's Package Manager cache, which can be useful in re-importing Flat Kit during troubleshooting;
* Opens this documentation as well as redirects to Git where you can open a support ticket;
* Copies debug info which is useful for in-depth troubleshooting.  

The *[Readme]* file can be found in *Project* panel ▶︎ *Assets* folder ▶︎ *Flat Kit* folder ▶︎ *[Readme]*.  

![Flat Kit import instructions - Step 5](FlatKit_Manual_Images/flat-kit-readme-file.png)

# 3. Shaders. In-Depth Overview

When you create a material, you’ll choose a shader. By default, Unity has the standard shader picked up. Once installed, all Flat Kit material shaders are located under the Flat Kit sub-menu of the Shader drop-down menu. Please choose the one that would work for your current task. Below is the description of all the shaders.

Our shaders expose shading properties as material features. If a feature toggle is not activated on any materials in the build scenes, the portion of shader code for that feature is not included in the build.
Because of the fact that these shaders are designed for a stylized look as opposed to photorealistic, metallicness and translucency features are not supported. The support for PBR (Physically-Based Rendering) in Flat Kit means that indirect sources of light (e.g. skybox) influence the colors of the material, unless you turn this feature off.

At the moment, there are the following shaders included into Flat Kit: *Stylized Surface*, *Stylized Surface Cutout*, *Stylized Surface with Outline*, *Gradient Skybox*, *Water*, *Terrain*, *LightPlane*.

![Collection of shaders in Flat Kit. From a Shader drop-down, hover the FlatKit sub-menu and choose a shader](FlatKit_Manual_Images/all_shaders.png)
> Collection of shaders in Flat Kit. From a Shader drop-down, hover the FlatKit sub-menu and choose a shader.

## 3.1. ‘Stylized Surface’ Shader

This is a versatile lit shader to be used on rigid object materials. To use it on a material select the shader “FlatKit/Stylized Surface” or “FlatKit/Stylized Surface Cutout” (Built-In RP only). This is your main go-to shader. It works for the vast majority of cases.  
Stylized Surface shader consists of the following **main** building blocks:

* Color,
* Cel Shading mode (None, Single [Cel], Steps, Gradient),
* Extra Cel layer,
* Specular,
* Rim,
* Height Gradient,
* Outline.

The **additional** parameters are:

* Advanced Lighting,
* Unity Built-in Shadows,
* Textures (Albedo, Normal, Emission).

> **NOTE:** Each combination of the features above, used in your project results in generating a **shader variant** during the build process. To limit the build time and the resulting binary size be careful not to add un-useful feature combinations. On the other hand, this mechanism makes sure that only the used features are included in the build. More information on shader variants: <https://docs.unity3d.com/Manual/SL-MultipleProgramVariants.html>

![‘Stylized Surface’ shader in Single mode. Simple use case](FlatKit_Manual_Images/stylized-surface-1.png)
> ‘Stylized Surface’ shader in Single mode. Simple use case.  

![‘Stylized Surface’ shader in Single mode. More complex use case](FlatKit_Manual_Images/stylized-surface-2.png)
> ‘Stylized Surface’ shader in Single mode. More complex use case with more options engaged, but still, uses only Single mode.  

### 3.1.1. The Main Parameters of the Shader

#### Color

This would be the color of your mesh (applicable to most cases, though you can make the shader's other parameters override or mask this main color, if you wish).

#### Cel Shading Mode

This is where you choose the style (mode) of your shading, the color of the shading, and other respective parameters of the modes. Depending on the mode you choose the parameters will look differently. So, let’s talk about modes.

* **None.** Use this to achieve a simple flat look or to get any other creative picture not involving cel shading, however, the following parameters of Stylized Surface shader will still let you do this, if you choose so.  
Note, the flatness and actual representation of colors on the scene depend on the lighting of the scene. In our demos we use Skybox as the source of lighting. Conveniently, there is a Dependency slider on the Lighting panel of Unity, which tells how much of the influence the Skybox provides. At minimum, there won’t be any shadows, as well as the colors will be identical to those you would choose in the *Color* block of the shader. At maximum, the Skybox heavily dictates what the colors will look like. For more natural (not necessarily realistic — but natural, organic look of the scene, it’s healthy to let Skybox influence the coloring of the scene).

* **Single.** This mode provides you with one shadow of chosen *Color*. *Self Shading Size* is the size of the cel. Larger values mean larger size of the shadow. *Shadow Edge Size* controls the sharpness of the cel. The lower the value — the sharper the cel. The higher the value — the more blurry is the shadow. *Localized Shading* is basically how condensed the shadow is. Higher values represent sharper cel.

* **Steps.** Basically, you choose the shading color and number of steps to blend from main *Color* into the color you pick up in *Steps* mode.

* **Curve.** The gradient, interpolated transition from one color to another.  
In order to get Steps and Curve modes to work — as soon as you have a number of steps (*Steps* mode) or curve shape (*Curve* mode) chosen — the shader will ask you to save its utility ramp texture somewhere on the disk. It will write the transition onto it. The texture will appear red in the editor. This is because internally we use the R8 texture format for efficiency.

![Curve shading mode of Stylized Surface shader](FlatKit_Manual_Images/FK-StylizedSurface-Steps-Curves.png)
> *Steps* and *Curve* shading mode of Stylized Surface shader  

#### Extra Cel Layer

This is like another instance of *Single* mode of *Cel Shading Mode*. Works independently from the *main Cel Shading Mode*. It means, you can make main Cel shading as *None* (flat), and add an *Extra Cel Layer*. The result will be the same as if you would have used the *Single mode*. Or, make the *main Cel layer* and *Extra Cel Layer* almost identical, giving an *Extra Cel Layer* a darker color, and making it smaller. This would result in stepping, similar to Steps mode with 1 step. Classic toon.

#### Specular

You can make a, well, specular with this parameter. Also it can be used as another layer of shadow.

* **Specular Color** picks up the color of your glare, the parameter works in HDR.  
* **Specular Size** determines how big the specular is. Higher values mean bigger specular.  
* **Specular Edge Smoothness** — moving slider to the left decreases blurriness and makes specular sharper.

![Specular. Inspector interface](FlatKit_Manual_Images/specular_parameters.png)
> *Specular*. Inspector interface

#### Rim

Rim was designed as one of the ways to make a specific effect of a color 'wrapping' from behind the object. In some cases it can remind an outline effect.  

* **Rim Color** selects the color of the parameter. It works in HDR.  
* **Light Align** parameter rotates the rim.  
* **Rim Size** controls how big the Rim is. Very high values can serve you as an unlit effect.  
* **Rim Edge Smoothness** — moving slider to the left sharpens the Rim, to the right — makes Rim blurry.

![Rim. Inspector interface](FlatKit_Manual_Images/rim_parameters.png)
> *Rim*. Inspector interface

You can think of Rim as some kind of inner shadow and/or as inner glow, if used on smoothened curvy models. In one of the *Fruit Vase* demo scenes, there is an example of extensive use of Rim as an outline. On *Blueprint Grid* demo scene *Rim* is used as a smooth inner glow. This parameter can be used creatively, for example, to substitute *Curve mode* or *Extra Cel parameter*. **Just reminding you that the name like 'Rim', 'Specular' etc should not be perceived literally, they can do more than that.** In the screenshot below, with the help of Suzanne the Blender Monkey, we tried to show a few instances of *Stylized Surface* shader with *None* mode selected (meaning no straightforward shadows are applied), using orange color, and only *Rim* parameter enabled. The results are variations of Rim section only. As you see, the *Rim* alone is quite a creative tool. Imagine adding some creative *Specular* and *Height Gradient*...

![Rim only, usage examples](FlatKit_Manual_Images/rim_examples_suzanne.png)
> Variety of uses of *Rim* parameter alone on Suzanne the Blender Monkey. Interface of *Stylized Surface* shader with *‘None’* cel shading mode

Although *Rim* option is creatively useful and sometimes can remind an outline effect, there are two more obvious ways to add an outline using Flat Kit: to use [Stylized Surface with Outline](index.md#33-stylized-surface-with-outline-shader) shader and/or to use [Outline Image Effect](index.md#42-outline-image-effect) camera component in Built-In RP/Forward Renderer's Renderer Feature in URP. We’ll talk about both of them later in this manual.

> **TIP.** Animate Cel layer size, Specular size or Rim size — to get a neat transition effect.

#### Height Gradient

This effect overlays a gradient from opaque selected color to transparent color onto everything you’ve set before. Height Gradient is global (absolute) per material, it doesn't depend on object's boundaries. If you would like to make a relative gradient (for instance, each object holding one material to contain an entire gradient within itself), duplicate the material and adjust the height gradient. Alternatively, you can use a *Curve* mode of *Stylized Surface*.

![Height Gradient. Inspector interface](FlatKit_Manual_Images/gradient_height_parameters.png)
> *Height Gradient.* Inspector interface

* **Gradient Color** picks the parameter’s own color to fade into from transparency.  
* **Center X** and **Y** are initial points from where the effect takes effect. Adjust these to move the gradient across the scene. Center X is useful if you engage - *Gradient Angle*, which means the rotation of the Gradient.  
* **Size** determines how steep the transition of Gradient is. The further the value is from 0 (zero) — the more gradual the effect is. Negative values flip the Gradient.  
* **Gradient Angle** rotates the gradient.

A bit more about the nature and use of *Height Gradient* is covered in the [*‘Terrain’ Shader*](index.md#36-terrain-shader) section of this manual.  

#### Enable Vertex Colors

If enabled, the final shading of the object is multiplied by the mesh’s vertex color values. It is a debug parameter, usually this is not used for changing the look.  

#### Outline

![Outline part of Stylized Surface shader. Inspector interface](FlatKit_Manual_Images/stylized-surface-outline-interface.png)
> *Outline* part of Stylized Surface shader. Inspector interface

The *Outline* part of the *Stylized Surface* shader allows you to add pseudo-outlines to your models.

* **Color** picks up the color of the outline.  
* **Width** determines how thick the outline is.  
* **Scale** adjust this parameter when you have gaps on the vertices (please note, this is not an ultimate solution, the gaps need a complex approach — in modelling, adjusting the normals, adjusting camera distance etc).  
* **Depth Offset** moves the outline inwards or outwards an object.  
* **Camera Distance Impact** **(this parameter is available in Universal RP only)** makes outlines that are further from camera appear thinner than outlines closer to the camera.

Please remember that in addition to this shader Flat Kit has also a global *Outline Image Effect* applied per Forward Renderer (in URP) and per camera (in Built-In RP).  
In the [Outline Image Effect](index.md#42-outline-image-effect) chapter in this manual you can find some useful specific and general info.

Sometimes it is useful to manipulate the normals of your model in order to force the shader to render outlines where it wouldn't do so otherwise.
More on this is covered in [Outline Image Effect](index.md#42-outline-image-effect) chapter. But here's one thing you can try without using 3d editor software. Among the other parameters of the import settings of the model, there is a section where is it possible to change the angle detection threshold for normals. It may come handy in adding or removing some of the outlines where they wouldn't appear normally. Also, slight adjustments to these parameters may resolve some of the visual issues. If you have gaps in the outline, for instance, try tweaking these controls (but remember to backup the project first, it's always a good idea to backup things. In fact, if you are working on something, do it now).

![Import settings of the model](FlatKit_Manual_Images/mesh-import-settings.png)
> Import settings of the model has a section for manipulating the normals, which is useful for the *Stylized Surface with Outline* shader as well as for *Outline* global effect.

Please note that this way of doing the outlines is made to be super fast, but unlike in Photoshop it can't produce an ideal outline. There are fundamental limitations to this fast approach of making the outline. For example, the outline itself in not a hollow contour as such but rather a modified (roughly said, 'expanded') copy of a model layered on the back of the original model. In most cases it can produce very good results with fast performance, but the transparency on this model won't work, as reducing the model's opacity will reveal the filled pseudo-outline layer in the background.

### 3.1.2. The Additional Parameters of the Shader

#### Advanced Lighting

**Light Color Contribution.** Light Color Contribution defines how much the color of the light source of the scene impacts the color of the object. The value of 0.0 results in completely ignoring scene lights, the value of 1.0 results in full multiplication between scene light color and the object color. As an example, imagine the winter morning light. Usually it is blue-tinted, thus all the snow around can’t be white but rather blueish.

Please note that the effect is visible only if the color of the light is anything but white.

Light Color Contribution works only with directional light. The point and spot lights are contributing to colors and shading of the material regardless of the Light Color Contribution value.

![Light Color Contribution parameter on Flat Kit shaders Inspector panel](FlatKit_Manual_Images/light_color_contribution.png)
> *Light Color Contribution* parameter on Flat Kit shaders Inspector panel

Let’s view it in example.  
Three pictures below describe how we change Light Color Contribution values on all (two) used materials: on a sphere and on a plane. Within a picture we change the intensity value of Directional Light as our main source of light.  
Additionally, there is a point light on each picture. This way it’s visible how local lights work together with the main Directional Light.  
Take the first image (below). At first, we turn down the *Intensity* to the very low value. White sun now has no impact on the scene brightness, resulting in a darker scene.  
Then we change the color of Directional Light from white to red. It has no effect because Directional Light is too “weak” to fill the scene.  
After raising *Intensity* value back to “1” the scene is now lighter and has a red tint.  

![Light Color Contribution at value 0.5. Changing intensity value and color of Directional Light](FlatKit_Manual_Images/lighting_2_color_contrib_0.5.png)
> *Light Color Contribution* at value 0.5. Changing *Intensity* value and color of Directional Light

Once we change *Color Light Contribution* parameter to “0” (pic below), Directional light has no effect light-wise and color-wise. Changing *Intensity* parameter of Directional Light on the Inspector panel has no effect. Both sides of the picture are identical.  
This way you can achieve a flat look, in other words, the colors on the scene are exactly the same as you choose in the shader parameters.

![Light Color Contribution at value 0. Directional Light intensity at max and min values](FlatKit_Manual_Images/lighting_1_color_contrib_0.png)
> *Light Color Contribution* at value 0. Directional Light *Intensity* at max and min values

Now, (on the pic below) we raise *Light Color Contribution* to the max value of “1”. If we set Directional Light *Intensity* parameter low, the scene theoretically has no source of direct light. Local lights now act as the only light sources. If the *Intensity* of Directional Light is at its maximum, it’s too hot now.

![Light Color Contribution at value 1. Changing intensity value of Directional Light](FlatKit_Manual_Images/lighting_8.png)
> *Light Color Contribution* at value 1. Changing *Intensity* value of Directional Light

If you use a Particle System and choose your particles to emit light, Flat Kit shaders respect that!

![Particles emitting light on Flat Kit shaders](FlatKit_Manual_Images/lighting_particles_lights.png)
> Particles emitting light on Flat Kit shaders.

**Override light direction** It is a way to make the material have an independent direction of the light from the Directional Light. This can be useful in cases when you need to align the position of the cels or Rim or Specular. Normally, to adjust these parameters globally, you should rotate the Directional light. Once *Override light direction* parameter is enabled, the material no longer obeys the Directional Light, it now has independent mapping vectors for the light-dependent parameters (e.g. mentioned earlier cels, Rim, Specular) that you can adjust with *Pitch* and *Yaw* parameters. Simply put, you can rotate the the cels, Rim and Specular.  

#### Unity Built-in Shadows

If the object has the ‘Receive Shadows’ option turned on in Mesh Renderer, you have an ability to use Unity-processed shadows on it, as you would do in Unity Standard Material shader, with a few extra-options.

![Unity Built-in Shadows mode menu. Inspector interface](FlatKit_Manual_Images/unity_built_in_shadows_modes.png)
> Unity Built-in Shadows mode menu. Inspector interface

* **Mode** lets you choose the coloring and blending parameters for the built-in shadows. **None** mode turns the built-in shadow parameter off.
**Multiply** mode lets you cast the shadows as in default material. You don’t have direct control over the color. You can change intensity and sharpness. The blending mode is 'Multiply'. **Color** mode lets you choose the color of the cast shadow. The blending mode is 'Normal'.
* **Power** sets how visible the Unity built-in shadow is.
* **Sharpness** defines how blurred or crisp the shadow edge is.
* **Shadow Occlusion** masks received Unity shadows in areas where normals face away from the light. **Useful to remove shadows that 'go through' objects.**

> **NOTE.** *Shadow Occludion* parameter is available in the URP version of Flat Kit only.

![Unity Built-in Shadows in Color mode. Inspector interface](FlatKit_Manual_Images/unity_built_in_shadows_mode_color_parameters.png)
> *Unity Built-in Shadows* in *Color* mode. Inspector interface

#### Texture Maps

If you’ve got a UV-unwrapped mesh, you can add a diffuse texture to it. If you work with transparency in textures in Built-In RP, please use *Stylized Shader Cutout* shader. It can see alpha on the texture as transparency. URP supports alpha by default.

**Albedo** Allows to use the albedo, or diffuse texture. In URP this slot supports transparent textures by default. Can be used together with *Alpha Clipping* parameter (explained below).

* **Texture selection slot** lets you pick a texture;  
* **Tiling** repeats the texture along X and Y axis;  
* **Offset** shifts the texture along X and Y axis within the UV map of the mesh;  
* **Blending Mode** lets you choose between 'Multiply' or 'Add' blending modes. 'Multiply' Blending Mode multiplies the luminosity of the base color by the blend color. Multiplication by white produces no change, while the black pixels remain, making the material darker. 'Add' Blending Mode is a little bit different from 'Multiply' — blending with black color produces no change, while generally it brightens the bright colors.  
* **Texture Impact** controls how visible the texture is. Values to the left decrease visibility of the texture up until it is invisible.  

> **TIP.** If you would like to have a material with a texture with a cel shading on top of this texture, you can set the *Stylized Surface* to *Single* **Cel Shading Mode**, set the base **Color** to white or light grey, set the  **Color Shaded** parameter to a bit darker one, set the Albedo texture (if your texture is not mostly white) to *Multiply* **Blending mode**, Texture Impact to the maximum value. You should get the model filled with a texture and with cel shadows combined.

**Normal Map** To make an impression of a relatively low-poly mesh having many details of a high-poly one, you can use normal maps. Add one to *Bump Map* slot in the Inspector panel.

![‘Stylized Surface’ shader — normal map applied](FlatKit_Manual_Images/normalmap-interface.png)
> ‘Stylized Surface’ shader — normal map applied

* **Texture selection slot** lets you pick a texture;  
* **Tiling** repeats the texture along X and Y axis;  
* **Offset** shifts the texture along X and Y axis within the UV map of the mesh;  

![‘Normal Map Tree’ demo scene, a tree without and with a normal map](FlatKit_Manual_Images/normalmap-trees.png)
> ‘Normal Map Tree’ demo scene, a tree without and with a normal map

**Emission** Enables Emission map part of the shader.  
> **NOTE.** Emission map support is available in Universal RP version of Flat Kit only, there is no Emission map parameter in Built-In version of Flat Kit.  

**Emission Map** Allows to use custom emission maps to designate the parts of the meshes to have a 'glow' effect.  

* **Texture selection slot** lets you pick a texture;  
* **Tiling** repeats the texture along X and Y axis;  
* **Offset** shifts the texture along X and Y axis within the UV map of the mesh;  
* **Emission Color** chooses the color of the 'glowing' effect.  

![Emission map part of the Stylized Surface interface](FlatKit_Manual_Images/stylized-surface-emission-interface.png)
> Emission map part of the Stylized Surface interface  

### 3.1.3. Setting material values from scripts

The following are the color field names for manipulation via the code for tweening, randomization etc:

* `_BaseColor` (in URP), `_Color` (in Built-in RP): the primary color, “Color” in the inspector. The alpha value controls transparency of the object if `Surface Type` is set to `Transparent`
* `_ColorDim` (and `_ColorDimSteps`, `_ColorDimCurve` in the corresponding cel shading modes): Color Shaded in the Inspector
* `_ColorDimExtra`: the shaded color of the *“Extra Cel Layer”* feature
* `_FlatRimColor`: rim color, requires *“Enable Rim Color”*
* `_FlatSpecularColor`: specular color, requires *“Enable Specular Color”*
* `_ColorGradient`: the gradient color used along with the `_BaseColor` parameter when *“Enable Height Color”* feature is active
* The full list of parameters is at the top of the file `Assets/FlatKit/Shaders/StylizedSurface/StylizedSurface.shader`.

> **NOTE.** The outline toggle is implemented as a [shader keyword](https://docs.unity3d.com/Manual/shader-keywords.html), so unfortunately it can't be toggled at runtime. However, you can enable the outline in the material inspector and toggle its visibility in code by setting the outline width (0 will visually disable the outline). Or, you can create two identical materials with the only difference being the outline toggle, and switch between these materials at runtime with `renderer.material = myMaterial`.

## 3.2. ‘Stylized Surface Cutout’ Shader

> **NOTE:** '*Stylized Surface Cutout*' shader has been deprecated in Flat Kit 2.1.2 for Universal RP version. Because URP supports transparency by default, there's no need for this separate shader in URP. The *Stylized Surface* and *Stylized Surface with Outline* shaders can do everything *Stylized Surface Cutout* could — using *Rendering options* part of the shaders in the bottom of the interface. There you can find an option to set the shading in transparency mode (*Surface Type* drop down menu ▶︎ *Transparent*. The default type is *Opaque*) '*Stylized Surface Cutout*' is still available in Built-In RP version.
{: .notice--warning}

This is a version of *Stylized Surface* shader with an option to treat alpha as transparency on a texture. The rest of the shader is the same.

The *Base Alpha cutout* parameter determines how much of the alpha portion of the texture is going to be transparent.

![‘Stylized Surface Cutout’ shader — Valley demo scene, tree branches material. Inspector interface](FlatKit_Manual_Images/stylized_surface_cutout_screenshot.png)
> ‘Stylized Surface Cutout’ shader — Valley demo scene, tree branches material. Inspector interface

Use this shader if you work with transparency in Built-In RP. In URP you are good to go with the *Stylized Surface* shader instead of this one. It will spare a few cycles from your CPU.

## 3.3. ‘Stylized Surface with Outline’ Shader

> **NOTE:** *Stylized Surface with Outline* shader has been deprecated in Universal RP version of Flat Kit: the outline functionality has been moved to the *Stylized Surface* shader. *Stylized Surface with Outline* remains available and working for the sake of compatibility with existing projects, but it is advised to use *Stylized Surface* for the new projects instead. *Stylized Surface with Outline* has not been deprecated in Built-In LTS version of Flat Kit.
{: .notice--warning}

*Stylized Surface with Outline* shader, being the same as the regular *Stylized Surface* shader in a nutshell, has an additional option of... outlines. [*Stylized Surface* info is here](index.md#31-stylized-surface-shader).

![‘Stylized Surface with Outline’ shader](FlatKit_Manual_Images/stylized_surface_with_outline_interface.png)
> ‘Stylized Surface with Outline’ shader

* **Color** picks up the color of the outline.  
* **Width** determines how thick the outline is.  
* **Scale** adjust this parameter when you have gaps on the vertices (please note, this is not an ultimate solution, the gaps need a complex approach — in modelling, adjusting the normals, adjusting camera distance etc).  
* **Depth Offset** moves the outline inwards or outwards an object.  
* **Camera Distance Impact** **(this parameter is available in Universal RP only)** makes outlines that are further from camera appear thinner than outlines closer to the camera.

## 3.4. ‘Gradient Skybox’ Shader

This is a simple method to fill the sky of your scene.

* **Top Color** and **Bottom Color** define two colors to be blended.  
* **Intensity** is a darkness/brightness controller of the skybox.  
* **Exponent** accentuates the effect in favour of either *Top Color* or *Bottom Color*.  
* **Direction X angle** and **Direction Y angle** rotate the effect along the corresponding axis.  

> **TIP.** Make *Top Color* and *Bottom Color* identical colors or move the *Exponent* parameter to one of the extremes if you want a flat background.

![Gradient Skybox. Inspector panel interface](FlatKit_Manual_Images/gradient-skybox-interface.png)
> Gradient Skybox. Inspector panel interface

## 3.5. 'Water' Shader

Water shader works in URP only. There is no Built-In version of a Water shader in Flat Kit.

Water shader lets you create a stylized water surface. That's is primary function. If you feel adventurous, you can make many other wobbling, glittering, weird things with it. It has a lot of parameters to fine-tune the look you want. Although this shader may look a bit complicated at first, it is intuitive and has helping tooltips on the parameters.

![Water shader interface](FlatKit_Manual_Images/water-shader-interface.png)
> *Water* shader interface

First of all, you'll need a surface to place a material with *Water* shader on. A plane with vertex grid will do fine. The more high resolution the water mesh is the smoother and well-defined the waves will be. For extra interest you can slightly displace the vertices while editing the mesh. With Flat Kit you get a few such models.

The controls are grouped into the logical sections. Let's float through the parameters of the shader.

----------------------------

### Colors

**Source** There are two modes of the color input — *Linear* and *Gradient Texture*.

![Water color source dropdown](FlatKit_Manual_Images/water-color-source-dropdown.png)
> Water color source dropdown

* **Linear.** This one allows to use just colors for *Shallow* and *Deep* parts of water. This effect is simple one — just two colors.

![Water color source dropdown](FlatKit_Manual_Images/water-color-source-linear.png)
> Water color source - linear

If *Linear* color source is chosen, two exclusive to this mode parameters appear to select colors:

**Shallow.** Color at the top of the water.

**Deep.** Color below the surface.  

* **Gradient Texture.** Use this one if you are looking for something fancy. You can create a depth gradient consisting of several colors. Using a Gradient Editor ramp, you can add up to 8 color stops onto the ramp. Now you have a *Shallow* color, *Deep* color and anything you want in between (see *Pool* demo scene).

![Water color source — gradient](FlatKit_Manual_Images/water-color-source-gradient.png)
> Water color source - gradient. Clicking on the color window opens the Gradient Editor.

When you click on the white color field, the Gradient Editor will show up.

![Gradient Editor](FlatKit_Manual_Images/water-gradient-editor.png)
> Gradient Editor. Edit the gradient and close the window, then save the texture.

After you finished editing the color gradient, click the 'Export' button to save the texture somewhere on the disk. We recommend to name the textures with the names beginning on something like 'water...' or 'awesome_gradient...' because later you'll have these textures stacked up one below another in the texture selection window, and it will be much quicker to scroll through them.  
When you have your texture saved, the material will be instantly filled with this gradient.

![Export Button](FlatKit_Manual_Images/water-gradient-export-button.png)
> Export Button. Click it and save the texture to the disk.

**Shallow Depth.** This is a lowest point of *Shallow* part. It is a point where *Shallow* part merges with the top of the gradient.

**Gradient Size.** This is the lowest (deepest) point of the gradient. It is a point where it merges with the *Deep* part.

Below is a little chart, which may came handy for understanding the parameters for the coloring part of the *Water* shader.
![Water Gradient Chart](FlatKit_Manual_Images/water-gradient-chart.png)
> Water Gradient chart

**Transparency.** How clear (transparent) the color of the water is. The transparency doesn't affect other parameters like foam or refractions. This allows you to achieve awesome weird optical effects.

**Shadow Strength.** How visible the shadow is.

----------------------

### Crest

Crest parameter colors the tips of the waves.

**Color.** The color of the wave. It helps accentuate individual waves.

**Size.** How big of a part of a wave is colored (accentuated).

**Sharp transition.** How smoothly the accentuated wave blends into overall color of the water.

----------------------

### Wave geometry

This section determines the overall shape of the waves. All the controls for the mesh displacement can be found here.

**Shape.** The formula that determine how the displacement of the waves is shaped and distributed across the mesh.

* **None** turns displacement waves off. As no waves are visible, the surface becomes flat.
* **Round** is linear (comb-looking) shape with rounded tips;
![Shape parameter — 'Round'](FlatKit_Manual_Images/wave_shape_round.png)

> Shape parameter — 'Round'

* **Grid** is grid-like (checkerboard-looking) shape;
![Shape parameter — 'Grid'](FlatKit_Manual_Images/wave_shape_grid.png)

> Shape parameter — 'Grid'

* **Pointy** is more linear (comb-looking) movement with sharp tips.
![Shape parameter — 'Pointy'](FlatKit_Manual_Images/wave_shape_pointy.png)

> Shape parameter — 'Pointy'

**Speed.** How fast it moves along the Direction parameter.  

**Amplitude.** Sets deviation amount, or, how high it is. Use this parameter to set the height of the waves. Positive values 'raise' the waves effect above the base point, negative values make the waves lower than the initial base point.

**Frequency.** Density of the effect.  

**Direction.** Direction of the motion. This parameter works tightly with *Speed*. Using these two you can make ponds, pools, seas etc (static water) and rivers, waterfalls etc (streaming water). Please note, there's an independent set of parameters *Speed* and *Direction* for foam as well, described a bit further.

**Noise.** Adds nonlinearity to the *Shape*. Use it to make *Grid*, for example, more chaotic.  

----------------------

### Foam

**NOTE:** In order to see the foam, the model must be UV-unwrapped.

**Source.** How the foam is being made — from texture or generated from noise. Please select one of the following parameters:

* **None.** Turns off the foam.
* **GradientNoise.** The foam shape comes from generative noise.
* **Texture.** If you choose *Texture* source, you'll have an option to import your own, preferably seamlessly tiling, texture, or use one of the included ones — we shortlisted the best from dozens of originally pre-generated .png textures to come with Flat Kit. If you are planning to use your own textures, we suggest you to put them into a single (red) color in the import settings to save memory.

**Color.** Color value of the foam. Can be opaque or transparent.  

**Shore Depth.** The maximum point where the water is detecting the edges to create a foam 'outline'.  

**Amount.** How often 'grains' occur.  

**Scale.** How big the foam 'chunks' are.  

**Sharpness.** How smooth or sharp the foam is.  

**Stretch X.** How stretched the foam is along X axis.

**Stretch Y.** How stretched the foam is along Y axis.

> **TIP.** Sometimes we find it useful to generously stretch the foam along one of the axis, so that the foam becomes a set of straight lines. This effect definitely can have its use.

**Speed.** How fast it moves along the Direction parameter.  

**Direction.** Direction of the motion. This parameter works tightly with *Speed*. Using these two you can make ponds, pools, seas etc (static water) and rivers, waterfalls etc (streaming water)

----------------------

### Refraction

Use these parameters to control the optical distortion of the water.

**Frequency.** The frequency of noise that creates the refraction.

**Amplitude.** The deviation from the initial point.

**Speed.** How fast the refraction moves on the water.

**Scale.** How big is the noise that creates the refraction.

----------------------
We included a component called *Buoyancy*. The *Water* shader deforms the water mesh, which in its turn moves the objects that have *Buoyancy* component on them. More info can be found in the [Buoyancy](index.md#53-buoyancy) part of Additional Scripts section of this manual.

> **TIP.** Place the plane somewhere behind or in front of your scene objects. Place the *Water* shader on it. Set *Clearness* to max, set foam *scale* to very high, lower the *frequency*, as well as opacity. With fine-tuning, it is possible to achieve something like a film grain effect.

## 3.6. ‘Terrain’ Shader

Terrains are great in Unity. But it’s not so trivial to work with terrain materials, that is why we added a separate shader that deals with the Unity Terrain system.

If you are not familiar with Unity Terrains, please refer to their documentation. In two words, terrain uses Terrain Layers, something like containers of all textures — diffuse, normal, bump etc. FlatKit *Terrain* shader sees those textures and applies its own colors onto the layers. Since we are talking about the flat look, no normal or bump maps are required. In order to have full control over colors of the terrain, you can load a plain white texture as your terrain layer (on *Valley demo* scene we did so). All the colors will be available from the shader interface, they will be multiplied with your white texture, resulting in the pure color you choose. If you are already familiar with *Stylized Surface* shader, *Terrain* shader interface won’t be news to you. [*Stylized Surface* info is here](index.md#31-stylized-surface-shader).

This is an appropriate time to talk about Height Gradient parameter Flat Kit offers. You can use it as a part of Stylized Surface, Stylized Surface Cutout and Terrain shaders. Height Gradient works wonders on terrain in context of flat shading.

Usually flat shaded landscape objects lack organic embellishment the real world has. All extra-shadows, small scale details, big and tiny grunge spots etc make the picture nonlinear to our eyes, thus, interesting, engaging. With flat aesthetics — there is a color, there may be a shadow or shadows, maybe a few models for the more natural look. The result — quite a boring scene. If you want a more polished look, you’ll want to fight linearity, with *Height Gradient* coming handy. It stretches the interpolation between transparency and its own color along the vertical axis (by default) and multiplies the gradient over the colors you already have. You can rotate the direction, so that it is no longer vertical but diagonal, horizontal and all in-between.
This effect changes the scene dramatically. Now, the terrain has its shadow work that you set on the interface, and on top of that there is a gradient, subtle or obvious. Immediately, it adds depth and a more professional look to the scene.
If you work on some kind of an environmental landscape object but do not use Unity Terrain, please use the *Stylized Surface* shader instead of *Terrain*. *Height Gradient* is available there, too.

![Height Gradient on Unity Terrain (without on upper image, with — on lower one). Valley Demo Scene](FlatKit_Manual_Images/height-gradient-example-01.png)
> Height Gradient on Unity Terrain (without on upper image, with — on lower one). Valley Demo Scene

## 3.7. ‘LightPlane’ Shader

This shader is what we are particularly proud of. It looks like a small tool. But it has immeasurable possibilities. Fog, mist, delicate scene boundaries, light beams, glow of magic swords, laser beams. These things are what *LightPlane* is for.

The *Wanderer* demo scene includes *LightPlane* shader implemented not only as fog areas, but also as light beams of so-called pick-up objects and even as planets. The *Valley* demo scene has got the *LightPlane* shader used as floating air particles thanks to the Unity particle system.

![LightPlane Shader. Inspector panel interface](FlatKit_Manual_Images/light_plane_interface.png)
> LightPlane Shader. Inspector panel interface

The parameters of the *LightPlane* shader are:

* *Depth Fade Distance* controls how quickly the **objects behind light plane** become hidden. Imagine you are looking at a frosted glass window. Any objects that are very close to the window on the other side are clearly visible, but anything that's far behind the window is completely blurred out. *Depth Fade Distance* defines how far the objects need to be from the window to become completely invisible.

* *Camera Distance Fade Close* / *Camera Distance Fade Far* control distance range from the camera at which **the light plane object** transitions from transparent to opaque (see pic below).

![LightPlane — Camera Distance parameters](FlatKit_Manual_Images/lightplane-camera-dist.png)
> *LightPlane* — *Camera Distance X and Y* parameters

* *UV Fade X* controls transparency on the sides along X axis of the plane/mesh (see pic below);  

![LightPlane — UV Fade X parameter](FlatKit_Manual_Images/lightplane-uv-fade-dist-x.png)
> *LightPlane* — *UV Fade X* parameter

* *UV Fade Y* controls transparency on the sides along Y axis of the plane/mesh (see pic below);

![LightPlane — UV Fade Y parameter](FlatKit_Manual_Images/lightplane-uv-fade-dist-y.png)
> *LightPlane* — *UV Fade Y* parameter

When combined, *UV Fade X* and *UV Fade Y* can make a fluffy blob.

![LightPlane — UV Fade X and UV Fade Y parameters combined](FlatKit_Manual_Images/lightplane-uv-fade-dist-x-y.png)
> *LightPlane* — *UV Fade X* and *UV Fade Y* parameters combined

* *Allow Alpha Overflow* makes alpha more than '1', used for HDR, looks nice with some bloom.

## 3.8. GPU Instancing

When the `Enable Instancing` option is enabled on a material, the shaders can perform [GPU Instancing](https://docs.unity3d.com/Manual/GPUInstancing.html) of the following fields that are common across all Flat Kit shaders:

1. *Color* value (property name `_Color`),  
1. Parameters of the cel shading mode *“Single”*  
    * *Shaded Color* value (property name `_ColorDim`),  
1. Specular parameters, active when *“Enable Specular”* is checked  
    * *Specular Color* value (property name `_FlatSpecularColor`),  
    * *Specular Size* value (property name `_FlatSpecularSize`),  
    * *Edge Smoothness* value (property name `_FlatSpecularEdgeSmoothness`),  
1. Rim light parameters, active when *“Enable Rim”* is checked  
    * *Rim color* value (property name `_FlatRimColor`),  
    * *Rim size* value (property name `_FlatRimSize`),  
    * *Edge Smoothness* value (property name `_FlatRimEdgeSmoothness`),  
    * *Light Align* value (property name `_FlatRimLightAlign`),
1. Unity shadow parameters, located in the *“Unity Built-in Shadows”* section  
    * *Color* value (property name `_UnityShadowColor`).

# 4. Image Effects

Both *Fog* and *Outline* image effects rely on image-based anti-aliasing, like the one in Unity's Post-processing stack.

* In Universal RP (URP) — post-processing effects are called ‘Renderer Features’ of the Forward Renderer.
* In Built-In RP: Post-processing is made of Camera effects placed onto the camera in the scene as Components.
  
## 4.1. Fog Image Effect

Fog Image Effect camera component can be reviewed as a post-processing effect. It can be subtle, like a mist in the lower part of the valley, or a dominant effect, as in a completely hazed environment. Simply put, it works in the following way. You decide whether you need only length fog or height fog or both. Then you determine the bounds where it would take effect. Then you choose colors along each dimension. And after that, blend between distance and height. This effect starts from camera position up to the Near/Far, Low/High bounds, meaning, your camera is the zero coordinate from where the fog spreads. Each camera on the scene can have a separate independent instance of an effect.

Because Unity’s MSAA (multi-sample anti-aliasing, which is an option in the Quality Settings of your project) does not apply to depth texture, there may be inconsistencies between the anti-aliased color image and the unprocessed depth image. This may look as aliasing if fog intensity is set to a high value. *Such artefacts may only occur if using MSAA*, so we recommend using screen-space anti-aliasing, such as in Unity’s post-processing stack that you can import by going to Window ▶︎ Package Manager in Unity 2018+.

When you click on any of the color ramps (Distance or Height Gradient), the Gradient Editor pops up.

Fog Image Effect is being used in the *Wanderer* demo scene (more subtly) and *Valley* Demo scene (more accentuated).

![Fog Image Effect. Inspector panel interface](FlatKit_Manual_Images/fog_image_effect.png)
> Fog Image Effect. Inspector panel interface

Gradient editor controls the colors of the gradient. To open it, click on Distance Gradient or Height Gradient. The bottom row of breakpoints (pointing up) is the selection of the colors. The above row (pointing down) controls the opacity of the area it points at; the opacity value of one breakpoint fades into the opacity value of the adjacent one. Same for colors.

> **TIP.** If you want the area close to you to be without fog, apart from increasing Near parameter, you can open up the color ramp(s), add a breakpoint next to the leftmost one on the ramp, select leftmost one, make it transparent (see screenshot of Gradient Editor below). The breakpoint you created (opaque, next to the transparent one) becomes your distance or height control.

![Fog Image Effect. Gradient Editor interface.](FlatKit_Manual_Images/fog_image_effect_gradient_editor.png)
> Fog Image Effect. Gradient Editor interface.

## 4.2. Outline Image Effect

Outline Image effect is, essentially, a contour on the objects on the scene. It can draw outer outlines, inner ones or both outer and inner outlines of the objects.

![Outline Forward Renderer in URP. Inspector interface.](FlatKit_Manual_Images/outline-image-effect-interface.png)
> Outline Forward Renderer in URP. Inspector interface.

### Setting up Flat Kit Outline (URP)

If you are working in a Universal Rendering Pipeline (URP) project, the post processing components you used to put on the camera in the old Built-In RP ('Standard', '3D' project) — they are called 'Renderer Features' in URP and can be found in the settings of the Forward Renderer.  

Please make sure that you installed Flat Kit properly as described [in this manual above](https://flatkit.dustyroom.com/#2-quick-start-beginning-to-work-with-flat-kit).  

Particularly, to make Universal RP generate post-effects (aka Renderer Features), please pay attention to the steps 5 and 6 in [the guide in the manual](https://flatkit.dustyroom.com/#2-quick-start-beginning-to-work-with-flat-kit).
In short, you'll need to set **[Flat Kit] Example Settings URP file** in **Graphics panel** (Edit ▶︎ Project Settings ▶︎ Graphics panel) and in **Quality panel** (Edit ▶︎ Project Settings ▶︎ Quality panel).  

After that you'll be able to load, for example, *Wanderer* demo scene that comes with Flat Kit, launch the scene (press Play) and see the outlines displayed.  

To be able to use Flat Kit's Outline in your own scene, you can either go from scratch:  

1. Create a new **Forward Renderer**. To avoid further confusion, name it, for example, *MyNewAwesomeForwardRenderer*. (Go to Assets menu on top ▶︎ Create ▶︎ Rendering Universal Rendering Pipeline ▶︎ Forward Renderer).
2. Add it to the **Renderer List** of the **[Flat Kit] Example Settings URP** file in the Inspector panel. To do this, go to **Project panel ▶︎ Flat Kit ▶︎ ExampleSettings ▶︎ [FlatKit] Example Settings URP**. Select it, look at the Inspector panel, see the **Renderer List** section, press **'+'** button and drag *MyNewAwesomeForwardRenderer* Forward Renderer you created in step 1 — into the created line of the **Renderer List**.  
3. Select that newly created *MyNewAwesomeForwardRenderer* Forward Renderer, press **'Add Renderer Feature'** and Select **Flat Kit Outline**. This will add the Outline Renderer feature. But to be able to adjust parameters, like width, color of the outlines, you'll need to create the Outline Settings file.  
4. Go **Assets menu on top ▶︎ Create ▶︎ FlatKit ▶︎ Outline Settings**. This creates an Outline settings file. Name it *MyNewOutlinesSettings*.  
5. Add this *'MyNewOutlinesSettings'* settings file to **Flat Kit Outline** Renderer Feature you created in step 3 — into the **Settings** field.  
6. In your scene select the camera (Main Camera) in Hierarchy panel, look at Inspector panel, find **Rendering** section and in the **Renderer** drop down menu select *MyNewAwesomeForwardRenderer* Forward Renderer you created in step 1.  
7. You may need to launch the scene by pressing Play.  

Or, you can do it the easy way.  

1. In your scene select the camera (Main Camera) in Hierarchy panel, look at Inspector panel, find **Rendering** section and in the **Renderer** drop down menu select *[FlatKit] Wanderer-ForwardRenderer* or *[FlatKit] FruitVaseScene-Var-ForwardRenderer*. They both have outlines already engaged.  
2. You may need to press Play.  

To change the parameters of the outlines then, please:

* Press *Ctrl + F (Windows)* or *Cmd + F (macOS)* and type *[FlatKit] Wanderer-Var-OutlineSettings* in the search field that becomes active in Project Panel. Select the found file and change the parameters in the Inspector panel.

### Parameters of Flat Kit Outline

**Main settings** are the following.

* *Edge Color* lets you choose the color of the outline.  
* *Thickness* makes the outline thicker or thinner. It controls how wide or narrow the line of the outline is.
* *Resolution Invariant* if enabled, the line width will stay constant regardless of the rendering resolution. However, some of the lines may appear blurry.  
* *Use Depth* enables or disables taking the scene's depth data into calculating the outlines. This parameter outlines the outer contour of the objects with depth threshold control.  
* *Use Normals* creates outlines for “inner” parts of the objects, meaning, for those that are inside the boundaries of the object, for every given camera perspective. The effect depends on the geometry of an object. So, having proper normals here is important. There is a Normals Threshold control. It's discussed a bit more a little further down.  
* *Use Color* enables or disables taking all color difference data on the scene when calculating the outlines. This feature is URP only.

**NOTE:** If you see that *Use Depth* and *Use Normals* have no effect in your project, please navigate to Project Settings -> Graphics and insert **[FlatKit] Example Settings URP** file into *Scriptable Rendering Pipeline Setting* field. If you are using your own settings file instead, please make sure to have *Opaque texture* and *Depth texture* checkboxes on, which can be found on Inspector tab when you select that URP settings file.

**Advanced settings** section hosts the parameters to adjust the tools above as well as a few more controls. The thresholds parameters are basically the limits that determine the ranges in which the effects take places. For example, the higher Min Depth value is, the further away from camera the outline will be generated. The lower Max Depth value is, the sooner outlines stop occurring.  

* *Min Depth Threshold* and *Max Depth Threshold* determine the range of depth differences where outline should be applied. Lower values draw lines “inside” the scene resulting in a more beveled image. Higher values have more flat effect.  
* *Min Normals Threshold* and *Max Normals Threshold* determine the range of normals edges to be outlined. Lower values increase the amount of affected normals, leading to more stroked effect. Higher values decrease the amount of affected normals, leading to flatter look. Basically, it determines min and max angles of the normals for the outlines to occur.  
* *Min* and *Max Color Thresholds* let you set the least and the strongest differences in color of the mesh to make the outline appear. This feature is URP only.  
* *Outline Only* renders the outlines without meshes themselves, making it a kind of wireframe renderer. This feature is URP only.
* *Render Event* This is one quite powerful feature available on the interface. It lets you choose a stage at which the outlines are applied. It allows to apply outlines over the transparent objects. If you want to exclude transparent objects like Water or UI elements, set this to 'Before Transparent'. Also, it allows you to stack the *Outline Image Effect* with other post effects. This feature is URP only.

You'll need to *press 'Play'* to see the effect of *Render Event*.

![Outline Image Effect Render Event list](FlatKit_Manual_Images/outline-image-effect-render-events.png)
> Outline Image Effect Render Event list

Here is an example of choosing when to render the outlines. We took *Wanderer* demo scene and applied an example *Outline* Image Effect. After that we tried a few different items from the *Render Event* list.

!['After Rendering Skybox' chosen in Render Event list](FlatKit_Manual_Images/after_rendering_skybox.png)
> *'After Rendering Skybox'* chosen in Render Event list. *Wanderer* demo scene

!['Before Rendering Post Processing' chosen in Render Event list, 'Outlines Only' parameter ticked](FlatKit_Manual_Images/before_rendering_post_processing_outlines_only.png)
> *'Before Rendering Post Processing'* chosen in *Render Event* list, *'Outlines Only'* parameter ticked

Also, in URP you have an ability to chain and change the orders of Image effects, but it's a general Unity information. More info in the chapter [Flat Kit Image Effects in URP](index.md#83-flat-kit-image-effects-in-urp)

Please note that *Outline Image Effect* is a global effect, as it is used as the camera component in Built-In RP and as a scene's Renderer Feature in URP, which is suitable for a consistent look of your project. If you would like to outline a particular object on your scene, you can engage the shader instead — [Stylized Surface with Outline](index.md#33-stylized-surface-with-outline-shader) shader.

If you would like to exclude an object from an outline pass, considering that you are using one of the Stylized Surface shaders, and you are in a URP project, please go to the interface of the shader and switch rendering to 'Transparent'. It won't change the look of the shader but will exclude it from the outline pass. You can control this too as described a few paragraphs above in Render Event list part.

![Flat Kit Depth Normals renderer feature](FlatKit_Manual_Images/flat-kit-depth-normals.png)
> Flat Kit Depth Normals Renderer Feature

> **NOTE:** The *Flat Kit Depth Normals* is no longer needed starting Unity 2021.1 and will soon be removed.

Some general info. Manipulating the normals of the mesh can be a very efficient way to control the behavior of the outlines. It can be done in a 3d editor. For example, here's how to do it in Blender.

![Rotating normals in Blender](FlatKit_Manual_Images/normals-rotation1.png)
> Rotating normals in Blender. Manipulating the normals angle is one of the ways to make Flat Kit generate outlines where you want them

> **TIP:** Combinations of the settings in Outline Image Effect let you control the behavior of the outlines quite widely already. You can get even more control on the outlines using *‘Stylized Surface with Outline’* shader in addition to the global Outline effect. Also, *Rim* parameter of *Stylized Surface* and *Stylized Surface with Outline* shaders can accentuate object's edges, often it looks like a partial outline, which can be helpful.

> **TIP:** One of the commonly asked questions is if some of the objects can be rendered without the Outline Renderer Feature applied. Outline image effect is global and is not designed to be selective to objects — it is applied per Renderer (in URP). However, moving object to be rendered in the transparent pass can solve this problem. In Flat Kit Stylized Surface there is such an option. If you are using non-Flat Kit shaders, please refer to their documentation to see whether it is possible — to enable transparency without affecting the look. In Flat Kit there is an option of Render Event. It lets you choose when to render the lines. Take a look at [this chapter](#42-outline-image-effect) in our manual.  
Another way of excluding something from rendering outlines on — is to render it with a separate camera in a camera stack: one camera is for non-outlined objects and another one is for everything else (outlined). Please refer to Unity documentation on camera stacking to get to know more about this general Unity technique.

# 5. Additional scripts

## 5.1. UV Scroller

Used in the *Wanderer* demo scene. It scrolls waterfall texture along the Y axis. Also used in *Ocean Water* scene under the waterfall.

## 5.2. Linear Motion

Linear Motion is a simple script that translates (moves) and rotates any object. We used it heavily on cameras to prepare promo video footage. There is an option to translate or rotate along the X, Y, Z axis.

![Linear motion script. Inspector interface](FlatKit_Manual_Images/ConstantMotion.png)
> *Linear motion* script. Inspector interface

> **TIP.** Use a couple of instances of this component if you want to translate and rotate along more than one axis and make more complex automations.

## 5.3. Buoyancy

This script is used with *Water* shader specifically when there is an object on the water surface, and you want it to physically flow on this surface. The object will replicate the water's shape, while water is being deformed. This scripts is added on the object as a component. You'll need to point to the water object mesh this object is interacting with (in *Water* field of the script interface).

![Buoyancy script interface](FlatKit_Manual_Images/buoyancy_interface.png)
> *Buoyancy* script interface

* *Water* field is where you choose the mesh of the water surface. The object holding this script will be afloat on this mesh.
* *Size* parameter sets the definition of the movement, meaning, how many of the *Water* object's vertices it takes into account.
* *Amplitude* is how far the object travels from its initial point on the water while floating.

# 6. Demo Scenes

We tried to depict the big spectrum of possibilities using various scenes. They are one of ten million examples of possible Flat Kit use cases. Consider viewing them as starting points or macro-preset objects for your own project.

* *Valley*, *Wanderer* scenes are environmental. There we tried to show the work of both fog systems of Flat Kit. Also it is one of the perspectives of displaying the shaders — how these would look in a large scene.

Valley uses Terrain shader and transparent textures inside a Stylized Surface Cutout shader. Valley demo scene is also an example of obvious, rather than subtle, use of *Fog* Image Effect. Once the scene is loaded, you can scan through the *Fog* Image Effect presets to find which one you like more. There is a Presets chapter later in this manual with explanation of how to use them.
In a *Valley* scene, please note that although the ground is made with Unity native terrain, the trees on it are populated manually, not using the terrain system.

* *Blueprint Grid (Mugs)* and *Fruit Vase* scenes are an exhibition of most sought use cases of cel / toon shading.

However, you can find more experimental stuff there, too. It has been a temptation to overpopulate the scenes with content, because while making these included materials — literally dozens of interesting by-product or work-in-progress materials showed up, but we had to discard them to keep the scenes clean.
Blueprint Grid is a descriptive one, there is a text telling what we used to get the displayed materials.
Fruit Vase is actually a collection of 7 scenes. There is one vase with fruits across all scenes and each scene is dedicated to some specific look, thus uses a different set of materials.

* *Tree Island* scene is a showcase of a more cartoony use case. Imagine a 3d-platform game with such a look. Or Any other arcade game.

* *Room*. We just had to include a room.

* *Retro Cars*. Retro cars are curvy. A great opportunity to show how shiny (or rough) shaders can be.

* *Normal Map Tree*. An example of normal maps application.

* *Ocean Water*. This is a demo scene showcasing the *Water* shader in a way the game would look like. A non-toon-shading application for *Stylized Surface* is showed in this scene, too. You can choose various water looks in the Hierarchy tab by switching different Water objects on.  
**NOTE:** This scene will work in Universal RP only.

* *Pool* scene shows more various versions of the *Water* shader. In the Hierarchy tab you can choose between different water objects. Each of these objects has its own *Water* material.  
**NOTE:** This scene will work in Universal RP only.

* *Water Vessels* is an attempt to show a few basic and more non-obvious *Water* shader parameters, all at once. Having these materials, you can use them as starting points in you own projects.  
**NOTE:** This scene will work in Universal RP only.

# 7. Presets

Unity has its own Preset management system. The preset is the saved current state of the shader, in our case, the Flat Kit material. The presets are available across scenes and can be saved whenever you want inside the current project. For convenience, we saved the most useful presets inside a shared presets folder (Assets/FlatKit/PresetsShared).

In Flat Kit you can find presets as .mat Material instances (that you can drag and drop on the objects) and .preset Unity Presets (saved states of shaders that you can recall from interface of already applied materials). The sets are identical. Unity presets (.preset) are great when you have a material (.mat) applied to lots of objects and you want to swap it with a preset you already have.

To save the preset, select the material or an object with this material you want to save, click on the ‘mixer’ icon on the top right of the shader interface on the Inspector panel. Then, the menu will pop up. Click ‘Save Current to…’. Then you choose the destination. Once created, you can move the actual file wherever you would like. All presets within a project will show up in the ‘Select Preset’ menu.

![Preset menu. How to load.](FlatKit_Manual_Images/preset-button.png)
> Preset menu. How to load.

Save, recall, experiment, discard bad results, save great results, all by using Unity’s preset system. You cat A/B this way and share the shader’s parameters across multiple separate materials. Scan through them and once you stumble upon something close to what you are looking for, adjust the one.

> **TIP.** Naming the preset files as descriptive as possible is a gratifying practice. It would save your time later when you gather lots of them. It would be easier to navigate through them and distinguish between them, and also the proper names would remind you what you had in mind at the moment of saving the preset. Just look at the screenshot below.

# 8. Flat Kit in URP

Although many of the features in Flat Kit look identically in URP and in Built-In RP versions, the differences are becoming inevitable for a couple of reasons. Built-in RP is being deprecated by Unity, URP is faster and it is a way to go, URP offers the tools Built-In RP is lacking. One of the differences is in post-processing. Flat Kit Built-In RP uses Post-Processing Stack v.2. Flat Kit URP uses URP's native Volume toolkit. Both of these offer similar post-processing tools but they behave differently. Even when using the same values for Color grading section in Built-In RP and URP, the outcome is slightly different.

Please note, Flat Kit had been initially created for the Built-in Rendering Pipeline. To keep the visual results as close to the original as possible, the URP version of Flat Kit is using HLSL code rather than shader graph. It means you can switch a Flat Kit project between URP and Built-in RP at any point without extra work. However if you’d like to edit the shaders, you'll need some programming skills. Although you can switch between the Rendering Pipelines, we cannot guarantee that all Unity versions will let you do it flawlessly. That is why, to make Flat Kit work out of the box, we highly recommended that you created a Universal RP project to begin with.

## 8.2. URP Installation

In order to have a working Flat Kit in Universal RP (we've included the URP version alongside the Built-in pipeline version, in a single package), you'll need to have Unity's Universal RP package installed in your project.

After that, you will need to use a Universal RP Asset file. You can either use the one that comes with Flat Kit, called ***[Flat Kit] Example Settings URP***, or you can create your own URP asset file to work with.

* Right click on Assets (in Project tab) ▶︎ Create ▶︎ Rendering ▶︎ URP ▶︎ Pipeline Asset.

Once you do it, the Asset and Forward Renderer are created.

Please refer to the chapter ['Quick start. Beginning to work with Flat Kit'](index.md#2-quick-start-beginning-to-work-with-flat-kit) in the beginning of this manual for more important information about setting up Flat Kit and using URP Pipeline Asset files.  

The last step of the installation shown in the video in a chapter ['Quick start. Beginning to work with Flat Kit'](index.md#2-quick-start-beginning-to-work-with-flat-kit) was pressing *Configure for URP* button in a *[Readme]* file that came with Flat Kit. This automatic step replaces two manual steps of setting up Flat Kit in Universal RP:
* **Manual Step 1.** Navigate to *Project Settings* -> *Graphics* and insert **[FlatKit] Example Settings URP** file into *Scriptable Rendering Pipeline Setting* field.
If you are using your settings file instead, please make sure to have *Opaque texture* and *Depth texture* checkboxes on, which can be found on Inspector tab when you select that URP settings file.  
![Flat Kit import instructions - Step 5](FlatKit_Manual_Images/manual_import_instructions_6.png)

* **Manual Step 2.** Please do this in *Quality* tab's *Rendering* field as well. This Example Settings file comes with Flat Kit — select **[FlatKit] Example Settings URP** file. Do it for all Quality levels.  
![Flat Kit import instructions - Step 6](FlatKit_Manual_Images/manual_import_instructions_7.png)

Here's a video showing setting it up.  

<iframe width="560" height="315" src="https://www.youtube.com/embed/8yiihlFPmGg?start=108" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>  

## 8.3. Flat Kit Image Effects in URP

In URP, 'Fog' and 'Outline' image effects, included in Flat Kit, are no longer image effects, they have been adapted to become Render Features. Unlike the conventional image effects that are added to the camera game object, Render Features are added as stages to the Forward Renderer.

To use Flat Kit effects, please first update the Universal RP to the version higher than 8.2.0.

Go to Window ▶︎ Package Manager ▶︎ Universal RP ▶︎ Select the version to upgrade to ▶︎ click Upgrade

Our example scenes already include configurations of the Forward Renderer with outline and fog image effects (look for the URP Config folders in the demo directory).

To enable outline and fog, select the ForwardRendererConfig and add the 'outline' or 'fog' stage. In the case of 'outline' effect, you also need to add the DepthNormalsPass stage.

The order of the effects can be managed like this.

![Managing the order of renderer layers in URP](FlatKit_Manual_Images/URP-renderer-layers-01.png)
> Managing the order of renderer layers in URP

It's a default URP thing. What is worth noting is that for Outlines we made an option to choose the order of Renderer Events within Outline Image Effect interface. Please refer to the corresponding chapter of this manual, [Outline Image Effect](index.md#42-outline-image-effect).

## 8.4. Post-processing V2 in URP (General Info)

We use PPv2 in our demo scenes for additional image effects. To enable these additional effects you need to:

Go to Assets (in Project tab) ▶︎ Universal Rendering Pipeline asset ▶︎ go to Inspector tab ▶︎ Post-processing Feature Set ▶︎ select Post Processing V2 from the drop-down.

Enable the Post Processing flat on the camera inspector:

![Camera properties. How to enable Post-processing v.2](FlatKit_Manual_Images/enable-post-processing-camera.png)
> Camera properties. How to enable Post-processing v.2

# 9. Contact information and links

[Flat Kit at the Asset Store](https://assetstore.unity.com/packages/vfx/shaders/flat-kit-cel-toon-shading-143368)

[Discord](https://discord.gg/GBAeuWC9qS)  

Email  
info@dustyroom.com

[Dustyroom website](http://dustyroom.com)

[Twitter](https://twitter.com/_dstrm)

![]()
>