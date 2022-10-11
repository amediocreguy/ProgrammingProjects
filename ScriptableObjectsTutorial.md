# Scriptable Objects Tutorial

This will show how to make Scriptable Objects that can be used in future projects and tutorials.

This is done from the Brackeys video, so we will be following along with his steps of creating a card for Hearthstone.
https://www.youtube.com/watch?v=aPXvoWVabPY

## 1. Creating our Card Blank

Firstly you will need to create a card blank to act as our scriptable object I used the hearthstone card blank from 
https://www.deviantart.com/demaretc/art/Neutral-Epic-Monster-Empty-Card-507712903

![alt text](https://images-wixmp-ed30a86b8c4ca887773594c2.wixmp.com/f/82021352-fa8f-4e22-96a1-630256cab82e/d8ea1s7-bed07082-3953-480f-85d9-b5a3c37e9c1b.png?token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ1cm46YXBwOjdlMGQxODg5ODIyNjQzNzNhNWYwZDQxNWVhMGQyNmUwIiwiaXNzIjoidXJuOmFwcDo3ZTBkMTg4OTgyMjY0MzczYTVmMGQ0MTVlYTBkMjZlMCIsIm9iaiI6W1t7InBhdGgiOiJcL2ZcLzgyMDIxMzUyLWZhOGYtNGUyMi05NmExLTYzMDI1NmNhYjgyZVwvZDhlYTFzNy1iZWQwNzA4Mi0zOTUzLTQ4MGYtODVkOS1iNWEzYzM3ZTljMWIucG5nIn1dXSwiYXVkIjpbInVybjpzZXJ2aWNlOmZpbGUuZG93bmxvYWQiXX0.a0KDGVm_dwfxMdFwGJXh9DvkjndPDGSbzEBFE2m0vQ4)

Make sure you get an image that does not have the values for Mana, Attack or Health, as we will add these in Unity.

In your main scene in Unity create a UI Canvas, and as a child to that canvas create a UI Image and add your card as the sprite, making sure to click Preserve Aspect.

Now create five seperate UI Text Objects as a child to the canvas called, Name, Descrption, Mana, Attack and Health.

Here if you want, you can change your text to be the same as the Hearthstone card text, I didn't to make it more clear to see where the text it.

Finally, create a UI Image that is above the Card Template in the Hierarchy so that your card looks like the below.
![alt text](https://i.imgur.com/9zk8kA4.png)

