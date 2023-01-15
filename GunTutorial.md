# Simple Gun Tutorial
https://www.youtube.com/watch?v=kXbQMhwj5Uc

This will allow you to set up a simple gun system in unity.

## 1 Project Setup

Start by creating a 3D unity project in that project import the Unity First Person Controller assets 

https://assetstore.unity.com/packages/essentials/starter-assets-first-person-character-controller-196525

Create a scene and pull in the first person prefab, and make sure you can control it, if not, make sure you fix that before you start.

## 2 Game object

Create an empty game object under your camera and call it whatever you like, we're going to use the simple name "Weapon Holder"

Create a child of this game object and import an asset to be your weapon, giving it an appropriate name. (Unpack the prefab)
Create a parent of the object and call it "Gun" this is how we will control if you were to hace multiple guns.
If you need to reorient your gun so that it is facing the correct direction to your camera.

Open up your game display separately and align your gun where you want it to be, usually the gun is somewhere around the bottom right as though it is being held by the player controller.

##3 Scriptable Objects

Create a folder for your scriptable objects and in that folder create a new C# script called GunData.
Your code should look like this
![image](https://user-images.githubusercontent.com/114996410/212564495-996e5450-9a4d-4eb4-add5-7eae82171c79.png)

You will now be able to right click and create a Weapon GameObject, create one and call it whatever you wish, we'll go with the video calling it "AR"
you can now change the information in the weapon in the inspector, we are going to copy the video and go with this.
![image](https://user-images.githubusercontent.com/114996410/212564568-e6f798f9-e427-4e3f-b66b-b537e842dc3a.png)

##4 Making a gun work

Create a script and simply call it "Gun"
Write in the following code:


using System;
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Gun : MonoBehaviour {

   
    [SerializeField] private GunData gunData;
    [SerializeField] private Transform cam;
    
    float timeSinceLastShot;

    private void Start() {
        PlayerShoot.shootInput += Shoot;
        PlayerShoot.reloadInput += StartReload;
    }

    private void OnDisable() => gunData.reloading = false;

    public void StartReload() {
        if (!gunData.reloading && this.gameObject.activeSelf)
            StartCoroutine(Reload());
    }

    private IEnumerator Reload() {
        gunData.reloading = true;

        yield return new WaitForSeconds(gunData.reloadTime);

        gunData.currentAmmo = gunData.magSize;

        gunData.reloading = false;
    }

    private bool CanShoot() => !gunData.reloading && timeSinceLastShot > 1f / (gunData.fireRate / 60f);

    private void Shoot() {
        if (gunData.currentAmmo > 0) {
            if (CanShoot()) {
                if (Physics.Raycast(cam.position, cam.forward, out RaycastHit hitInfo, gunData.maxDistance)){
                    IDamageable damageable = hitInfo.transform.GetComponent<IDamageable>();
                    damageable?.TakeDamage(gunData.damage);
                }

                gunData.currentAmmo--;
                timeSinceLastShot = 0;
                OnGunShot();
            }
        }
    }

    private void Update() {
        timeSinceLastShot += Time.deltaTime;

        Debug.DrawRay(cam.position, cam.forward * gunData.maxDistance);
    }

    private void OnGunShot() {  }
}
Go into the inspector on your "Gun" object attach this script and drag in the AR scriptable Object.
Also go into the "Gun" game object and attach a new empty game object, calling it "Muzzle" position it where you would expect the bullet to come from on the weapon.
Also drag in the muzzle into the muzzle field.

Create a new script called "PlayerShoot"

Within this script this is your code.
using System;
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class PlayerShoot : MonoBehaviour {

    public static Action shootInput;
    public static Action reloadInput;

    [SerializeField] private KeyCode reloadKey = KeyCode.R;

    private void Update()
    {
        if (Input.GetMouseButton(0))
            shootInput?.Invoke();

        if (Input.GetKeyDown(reloadKey))
            reloadInput?.Invoke();
    }
}

You should now have a gun that both shoots and reloads, this tutorial won't cover the damage portion or how to create an enemy object with health.















