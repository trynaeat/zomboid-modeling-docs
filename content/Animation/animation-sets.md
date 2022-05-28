---
title: "Animation Sets"
date: 2022-05-28T15:22:44-04:00
draft: true
weight: 5
---
The next thing you need to do is create your animation sets. These essentially tell the game when/how to play your animation based on certain conditions. They are simply .xml files you can edit with the text-editor of your choice.

This part can involve a bit of trial and error and I suggest searching the vanilla games files to find an action *similar* to the one you're making which you can adapt. Look in `/media/AnimSets/player` or `/media/AnimSets/player-vehicle`. Lets look at an action from the vanilla game, `LoadDblBarrel.xml`

```xml
<?xml version="1.0" encoding="utf-8"?>
<animNode>
	<m_Name>LoadDblBarrel</m_Name>
	<m_AnimName>Bob_Reload_DBShotgun_Load</m_AnimName>
	<m_deferredBoneAxis>Y</m_deferredBoneAxis>
	<m_Looped>false</m_Looped>
	<m_SyncTrackingEnabled>false</m_SyncTrackingEnabled>
	<m_SpeedScale>ReloadSpeed</m_SpeedScale>
	<m_BlendTime>0.40</m_BlendTime>
	<m_Conditions>
		<m_Name>PerformingAction</m_Name>
		<m_Type>STRING</m_Type>
		<m_StringValue>Reload</m_StringValue>
	</m_Conditions>
	<m_Conditions>
		<m_Name>WeaponReloadType</m_Name>
		<m_Type>STRING</m_Type>
		<m_StringValue>doublebarrelshotgun</m_StringValue>
	</m_Conditions>
	<m_Conditions>
		<m_Name>isLoading</m_Name>
		<m_Type>BOOL</m_Type>
		<m_BoolValue>true</m_BoolValue>
	</m_Conditions>
	<m_Events>
		<m_EventName>loadFinished</m_EventName>
		<m_Time>End</m_Time>
		<m_ParameterValue></m_ParameterValue>
	</m_Events>
	<m_Events>
		<m_EventName>playReloadSound</m_EventName>
		<m_TimePc>0.4</m_TimePc>
		<m_ParameterValue>load</m_ParameterValue>
	</m_Events>
	<m_Events>
		<m_EventName>changeWeaponSprite</m_EventName>
		<m_TimePc>0.14</m_TimePc>
		<m_ParameterValue>ShotgunDoubleBarrel_OPEN</m_ParameterValue>
	</m_Events>
</animNode>
```

As the name suggests, this plays the animation for loading a double barrel shotgun. The m_Name prop can be whatever you want it to be called. m_AnimName is the name of your action, again having your filename match your action name can remember what the correct name is for this step.

The m_Conditions nodes let you specify certain animation variable values that trigger your animation. In this case, we check the WeaponReloadType is "doublebarrelshotgun". In this case, the weapon's item script specifies this variable, and it's automatically set anytime the user equips a shotgun. If you're making a custom weapon you could give it its own reloadType value and check for that in your own animation set. It also checks that the user isLoading and is in the middle of a reload action. These are all set by various Lua scripts in the game. For more complicated use-cases you can write Lua scripts to set whatever animation variables you want, then design your AnimationSet to react to them.

You'll also notice the m_Events nodes. These do the opposite, they *trigger* game events when certain points are reached in your animation. In this case it's used to play a sound and also switch the weapon to the opened-up version before the player starts moving their hand to insert shells inside.

You can copy/paste a vanilla animation and tweak it to your needs. Another nice thing you can do is extend an existing animation set and only tweak the nodes that you need to be different. Let's look at an example I created for the Crossbow reload:

```
<?xml version="1.0" encoding="utf-8"?>
<animNode x_extends="LoadDblBarrel.xml">
	<m_Name>LoadCrossbow</m_Name>
	<m_Conditions />
	<m_Conditions>
		<m_StringValue>Crossbow</m_StringValue>
	</m_Conditions>
	<m_Conditions />
	<m_Events />
	<m_Events />
	<m_Events>
		<m_ParameterValue>Hydrocraft.Crossbow</m_ParameterValue>
	</m_Events>
</animNode>
```

You'll see I've overridden the second condition, to instead check that the Crossbow reload is happening rather than a typical dblbarrel reload. I also overrode the last event, so the weapon sprite gets set to an empty crossbow rather than an open shotgun. Otherwise I completely reused the existing dblbarrel animation set (and indeed the animation itself).

When you've created your Animation Set, you want to place it in your mods `media/AnimSets/player` or `media/AnimSets/player-vehice` folder.

![sample_anim_6](/images/sample_anim_6.PNG)

Note that if you tweak your sets while the game is running, it will reload the xml file so you don't need to reboot the game every time. If you add a new one though, you'll need to reboot the game.