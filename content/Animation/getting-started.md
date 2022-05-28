---
title: "Getting Started"
date: 2022-05-28T15:22:44-04:00
draft: true
weight: 2
---

The following guide will assume you're using Blender 3.1, although the .fbx file on the previous page can be used in pretty much any software of your choice.

First, download the .blend file from the [Files]({{< ref "/content/Animation/files.md" >}} "Files") page.

Open it up in blender. You'll see a male character mesh and matching armature. From this you can start animating! If you're completely new to animating, there are tons of guides out there for Blender on youtube. Any of the ones for v2.8+ will translate very easily to the latest version of Blender. I'd suggest you check out these 2 in particular:

- [Animation Part 1](https://youtu.be/zp6kCe5Kmf4)
- [Animation Part 4](https://youtu.be/nlT9rYcIRzU)

The first link gives some basic explanation on creating keyframes. The second one goes a little more in depth on bones/rigs and shows creating a simple walk cycle.

Just follow the normal process for creating an animation in Blender, and spend as much time as you need here refining the animation so it looks exactly how you want before placing it into Zomobid.

## Tips
- Keep your movements to ONLY rotations (with the exception of some translation of the spine to move the entire body). Don't scale or translate bones around or you'll get wonky results.
- You can set the length of the animation in frames in the timeline editor, then hit Space and loop your animation to see how it looks.
- Crtl + Tab with the armature selected to switch beteween Object/Pose modes quickly
- Hit the "record" button on the timeline editor before switching back over to the action editor. This will turn on auto-keyframe mode so any time you move bones it will automatically create a new keyframe at your current position on the animation timeline. If you don't want auto-keyframe mode, you'll have to hit I -> Location & Rotation every time to create the frame.