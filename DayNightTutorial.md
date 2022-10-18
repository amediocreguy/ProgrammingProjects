# Day Night Cycle Tutorial
https://www.youtube.com/watch?v=m9hj9PdO328
This will help you create a day night cycle in Unity

## 1. Create your scene

Once you have created your project in unity, I am using the 3D project base.
Open unity and create a scene with whatever name you wish.
I named my scene DayNight.

## 2. Create your scripts

Create two Scripts one called 'LightingPreset' this will hold the preset we create for lighting conditions.

The other script will be called 'LightingManager' This will control the lighting conditions in the scene allowing for control as the time of day changes.

## 3. Lighting Preset

In the `LightingPreset` script add the following code:

`using System.Collections;`

`using System.Collections.Generic;`

`using UnityEngine;`

`//this will allow you to create an instance of the class in the unity editor when you right click.`

`[System.Serializable]`

`[CreateAssetMenu(fileName ="lighting Preset", menuName = "Scriptables/Lighting Preset", order =1)]`

`//Changing from monobehaviour to ScriptableObject will let us share a preset between scenes on a single file`

Add the following variables to the script:

`public Gradient AmbientColor;`

`public Gradient DirectionalColor;`

`public Gradient FogColor;`

Now, go back into unity, right click go into scriptables and create a lighting preset, I have called mine `DefaultLighing`

Play around with the gradients in the default lighting preset to fit what you want it to look like.

This is my gradients:

![alt text](https://i.imgur.com/A107jCa.png)


## 4. Lighting Manager

Open your `LightingManager` script.

In this script we want to add two SerializeFields as References and one as a Variable, like follows

`//References`

`[SerializeField] private Light DirectionalLight;`

`[SerializeField] Private LightingPreset Preset;`

`//Variables`

`[SerializeField, Range (0, 24)] private float TimeOfDay;`














