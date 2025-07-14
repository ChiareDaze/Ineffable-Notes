These are my notes on how to use Adobe After Effects where i'm going to explain how it works and what effects i use to edit.

>[!warning]
>I'm self-taught and not a professional, so i'll keep my explanations simple and i'll just share my basic knowledge of what i use to edit

![[pinterestdownloader.com-1752367969.969781.gif]]

>"Three two one, let's jam"

---
# Index

>[!info] Index
>- [[#Shortcuts cheat sheet (windows)]]
>- [[#Interface]] 
>- [[#How to create a project and import a file]]
>- [[#Keyframes and graphs]]

---

## Shortcuts cheat sheet (windows)

>[!info] File Operrations
>- New Project `Ctrl+Alt+N`
>- Open Project `Ctrl+O`
>- Save Project `Ctr+S`
>- Close Project `Ctrl+Shift+W`

>[!info] Importing
>- Import File `Ctrl+I`
>- Import Multiple Files `Ctrl+Shift+I`

>[!info] Composition
>- New Composition `Ctrl+N`
>- Composition Settings `Ctrl+K`
>- Add to Render Queue `Ctrl+M`

>[!info] Layer Operations
>- New Solid `Ctrl+Y`
>- New Text `Ctrl+Alt+Shift+T`
>- Duplicate Layer `Ctrl+D`
>- Split Layer `Ctrl+Shift+D`
>- Pre-compose `Ctrl+Shift+C`

>[!info] Viewing
>- Fit to View `Shift+/`
>- Zoom In `Ctrl+ +`
>- Zoom Out `Ctrl + -`
>- Toggle Transparency Grid `Alt+Shift+Ctrl+T`

>[!info] Transform Project
>- Anchor Point `A`
>- Position `P`
>- Scale `S`
>- Rotation `R`
>- Opacity `T`

>[!info] Keyframes
>- Toggle Keyframes `Alt+Shift+P`
>- Go to Next Keyframe `J`
>- Got to Previous Keyframe `K`
>- Show the Keyframes `U`
>- Convert to Easy Ease (select the keyframes) `F9`

---
### Interface

![[Pasted image 20250714230317.png|600]]

The After Effects interface consists of several panels that enable you to work with projects, effects, and animations.

**Project**
This panel shows all the important elements of the project such as files or compositions.
![[Screenshot 2025-07-14 230802.png|200]]

**Timeline**
This is the panel where you create and manage the animation timeline, including keyframes and duration.
![[Screenshot 2025-07-14 230852.png|1000]]

**Composition**
It is a window that displays a composition, allowing you to preview, arrange, and edit the visual elements, layers and settings of a project in a *WYSIWYG* (What You See Is What You Get) environment.
![[Screenshot 2025-07-14 230845.png|500]]


>[!info] Secondary panels
>![[Screenshot 2025-07-14 230945.png|150]]
>- *Preview*: allows you to visualize the preview of the animation
>>![[Screenshot 2025-07-14 231022.png|150]]
>- *Effects and Presets*: offers a wide range of effects that can be applied to the layers
>>![[Screenshot 2025-07-14 231013.png|150]]
>- *Alignment*: helps position and align elements within the compositions
>>![[Screenshot 2025-07-14 231002.png|150]]
>- *Properties*: shows details about the selected layer
>>![[Screenshot 2025-07-14 230957.png|150]]

---
### How to create a project and import a file

When creating a new file, the first time you open After Effects, a window will appear asking whether you want to create a new project or open an existing one.

![[Pasted image 20250714233143.png|400]]

To create a new project, click on *New Project*. Otherwise, select *Open Project* and and select the file based on its location in the directories.

Once the project is open, the main interface of After Effects will be displayed (as previously explained). So, the next step is to create a composition and import the files you want to use and then edit them as needed.

In the *Composition panel*, click on the *New Composition* option, which will open a window where you need to specify the composition's properties (height, width, frame rate, etc.).

![[Screenshot 2025-07-14 234230.png|450]]

After creating the composition, to import files, navigate to the top left corner of the screen and click on the *File* menu. A dropdown menu will appear, from which you should select *Import*. Then, choose the files you wish to import into your project.

![[Screenshot 2025-07-14 234908.png|350]]

Now, all your files will be listed in the *Project panel*. The last step is to select the individual files and drag them onto the *Timeline panel*.

![[ezgif.com-video-to-gif-converter.gif|1000]]

---
### Keyframes and graphs

When working in After Effects, **keyframes** and **graphs** are important tools for creating smooth, professional-looking animations. Here's a breakdown of how they work and how you can control your animations more precisely by using them.

#### Keyframe
It is a marker that defines a specific value for a property (like position, scale, rotation, opacity, etc.) at a certain point in time. 
Think of keyframes as "checkpoints" in your animation. When you set two keyframes with different values, After Effects automatically calculates all the in-between frames (this process is called *interpolation*).

*Example*
Set a keyframe at frame $0$ with an object on the middle of the screen, and another keyframe after a few frames with the object on the right side, After Effects will animate the object moving from left to right between those two points.

![[2025-07-1500-17-14-ezgif.com-video-to-gif-converter.gif|1000]]

>[!info] Types of keyframes
>Not all keyframes behave the same way. There are different types of interpolation, which affects how the values change between keyframes.
>- **Linear keyframes**: these create a constant rate of changing between two points. The animations move at a stead and "mechanical" pace (no acceleration or decelerations). These keyframes appear as diamond shapes (such as the keyframes in the earlier example).
>- **Eased keyframes**: These allow the animation to gradually speed up or slow down, creating a more natural and realistic movement. When you apply easy ease, the keyframes becomes curves and appear as hourglass icons.

*Easy ease example*
![[2025-07-1500-29-57-ezgif.com-video-to-gif-converter.gif|2000]]

#### Graphs
It is where you can fine-tune how your animations behave between keyframes.
It visually represents either:

**The value graph**
This shows how the actual value of a property changes over time. For instance, if you're animating position, it will display $X$ and $Y$ coordinates changing as curves. The vertical axis represents the *value* (like pixels) and the horizontal axis represents *time*.
A steeper slope means a faster change, while a flatter slope means slower change.

**The speed graph**
Instead of showing values, the speed graph shows how fast those values are changing. The $Y$ axis here represents *speed*, and the $X$ axis is still *time*. Tall peaks mean high speed and dips or flat areas mean slower or no movement. This graph is particularly useful when you're trying to adjust how quickly an object accelerates or decelerates.

>[!info] Modify graphs and animation curves
>Once you've applied keyframes, you can jump into the graph editor and tweak the motion curves to get more nuanced results.
>- The keyframes appear curved and allow you to shape the animation path. You can drag these handles to make the motion and end faster (or the other way round)
>- You can manually adjust the speed and influence of keyframes by manipulating these handles, allowing you to create effects like:
>	- Smooth acceleration and deceleration
>	- Sudden burst of speed
>	- Bounces, anticipations or overshoot

>[!warning]
>My tip is to not just read about it, but to actually try it out. Experiment with different settings, play around with the graphs and see what works best for you. That's the best way to learn and develop your own style.

I'll add all the gifs and images tomorrow (maybe). I'm too tired (it's 1am help)