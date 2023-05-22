In the Hierarchy window select the 'Main Camera' object. 

Over in the Inspector click **Add Component** and add the `CameraRotate` script component. 

--- collapse ---

---
title: I dont have a CameraRotate script
---

In the AddComponent box hit <kbd>Enter</kbd> twice to create a new script called `CameraRotate`. 

The new script will appear in your Assets folder. Move it into the 'Scripts' folder to organise your files. 

Open the `CameraRotate` script in your script editor and type or copy and paste the following code. 

--- code ---
---
language: cs
filename: CameraRotate.cs
line_numbers: true
line_number_start: 1
line_highlights: 7, 20-27
---

using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class CameraRotate : MonoBehaviour
{
  public GameObject ball;
  public float sensitivity = 5f;

  void Start()
  {
      // Focus the camera on the Ball
      transform.LookAt(ball.transform);
  }

  void Update()
  {
      //If the left mouse button held down, rotate the camera using mouse position
      if (Input.GetKey("mouse 0"))
      {
          float mouse = Input.GetAxis("Mouse Y");
          transform.Rotate(new Vector3(mouse * sensitivity * -1, 0, 0));
          float look = Input.GetAxis("Mouse X") * sensitivity;
          transform.RotateAround(ball.transform.position, Vector3.up, look);
      } 
  }
}

--- /code ---

Save your script and switch back to the Unity editor.

--- /collapse ---

In the Inspector set the 'Ball' variable of the `CameraRotate` script by dragging the sphere from the Hierarchy window onto the box. 

![The CameraRotate component with the Ball object set correctly.](images/camera-rotate-component.png)
