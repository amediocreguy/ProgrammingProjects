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

`[SerializeField] private LightingPreset Preset;`

`//Variables`

`[SerializeField, Range (0, 24)] private float TimeOfDay;`

Also add the attribute above the public class `[ExecuteInEditMode]` or `[ExecuteAlways]` depending on your version of Unity.

This will allow us to manage the time of day whilst not playing the game and in edit mode in Unity.

Add the following  `OnValidate` Function:

![alt text](https://i.imgur.com/5LjwGn6.png)

This will make it so any time you change anything in the editor it will check for and change what light is set to the sun and if no light is set to the sun it will set the first directional light found to the sun.

Now we will add in a script on a UpdateLighting function that will take a variable from 0 to 1 and depending on our preset it will change the gradients.

![alt text](https://i.imgur.com/LfpyTKs.png)
