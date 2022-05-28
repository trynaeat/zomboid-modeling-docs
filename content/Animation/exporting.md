---
title: "Exporting"
date: 2022-05-28T15:22:44-04:00
draft: true
weight: 3
---

Zomboid supports the .fbx and .x formats for models/animations. Since .fbx is a much newer and more flexible format supported by many tools, I suggest using .fbx at all times.

To export your animation, first select everything in the scene (that means the armature AND Body mesh). Now, there are a couple of options for how you want your action exported...

## Export NLA
You can push the actions you want to NLA strips, then in the export settings choose to export NLA. This is a bit more complicated but it means you can have several actions in a single file and easily choose which ones to export.

## Export Every Action
This is a simple method, but it's important to make sure you only have the single action you want in your .blend file before you export so you don't bloat the file with a bunch of extra actions

Let's go with this method. Say you have an action called BobHC_Sample_Anim:

![sample_anim_1](/images/sample_anim_1.PNG?width=800px)

Make your export settings look like this (remember to select everything first). Note All Actions is checked.

![sample_anim_2](/images/sample_anim_2.PNG)

**TIP**: Hit the + at the top and give this preset a name/save it for later use.

When naming the .fbx file, I also give it a name that exactly matches the name of my action strip, so in this case it would be called BobHC_Sample_Anim.fbx. This isn't strictly necessary, but it will save you from errors and typos in the future.

Hit Export. The final .fbx file should be at least a few hundred kb in size. That's a good indicator that your action actually got exported.