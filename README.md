# AR Robot

![Result](https://github.com/tiago-peres/ar-robot/blob/master/imgs/result.png)

In this project work, we will:
+ Install the Vuforia SDK for building AR applications
+ Set up marker detection with an image target
+ Create a simple AR app that will show a 3D robot model through your smartphone camera when you point it at a special "target" that you'll print out.

For this project, we will need an Android device running 4.4 or above, or an iOS device running 9 or above.

## Instructions
### Step 1 - Install the Vuforia SDK
Let's get the Vuforia SDK working in a new Unity project. If you already downloaded the Vuforia SDK as part of Unity installation, you may be able to skip some or all of these steps.

1. In Unity, create a new 3D Unity project.
2. Select Edit > Project Settings > Player
3. In the XR Settings, check the "Vuforia Augmented Reality Supported" box.

![Vuforia Augmented Reality Supported](https://github.com/tiago-peres/ar-robot/blob/master/imgs/1.PNG)

### Step 2 - Add a Vuforia AR Camera to the Scene
1. In Unity, select GameObject > Vuforia > AR Camera. You will be prompted to install some additional assets, this will happen once per project.

![Vuforia AR Camera](https://github.com/tiago-peres/ar-robot/blob/master/imgs/2.png)

2. Delete the MainCamera object.

### Step 3 - Create an Image Target
Next, you'll add an image of the robot to a Vuforia database. This image will be the marker that the application is looking for to make the robot appear.

1. You will need to create a free Vuforia developer account on the Vuforia developer portal: https://developer.vuforia.com/vui/auth/register
2. Once registered, create a new developer key on their website by going to Develop > License Manager > Get Development Key. Name it “ARLesson”.
3. Download the zip file **[VuforiaAssets](https://github.com/tiago-peres/ar-robot/blob/master/VuforiaAssets.zip)**, which contains the assets you will need. After you unzip it, import it as a custom package to your Unity project.
4. Back on the Vuforia website, go to Develop > Target Manager > Add Database. Name it “arRobot_ImageTargets”.
5. Once the database is created, click on it and add a new target. Choose Single Image, browse for the ImageTargetRobot.jpg file, and set a width of 0.07. Name it “Robot”.
6. Click on Download Database, then Download for Unity Editor. Import the resulting unitypackage file to your Unity project.

_Here’s a tip!_ Vuforia benefits from having lots of trackable features which means zones of contrast in the target image. After the upload, each image will get a rating, like below.

7. Go back to the Vuforia website and navigate to the License Manager page. Click on "ARLesson" and copy the license key.

8. In Unity, click the button "Open Vuforia Engine Configuration" and paste the license key into the "App License Key" field.

![Open Vuforia Engine Configuration](https://github.com/tiago-peres/ar-robot/blob/master/imgs/3.PNG)
![App License Key](https://github.com/tiago-peres/ar-robot/blob/master/imgs/4.PNG)

### Step 4 - Add the Targets to the Scene
Finally, you'll connect the image target to the Unity prefab that you want the app to show in augmented reality space, in this case a 3d robot model prefab.

1. In your Unity project, create an image target object by selecting: GameObject > Vuforia > Image
2. Configure the target to use the "arRobot_ImageTargets" database and then the "Robot" Image Target.

![Configure the target](https://github.com/tiago-peres/ar-robot/blob/master/imgs/5.PNG)

3. Add the RobotAnimated prefab as a child of the image target. Make sure its local scale is 1.

4. Add the scene to the build in Build Settings and build to your device.

5. Print out a physical copy of the ImageTargetRobot.jpg or, if you use a smartphone, point to a screen with the ImageTargetRobot.jpg opened. When you run your application, the 3D robot should appear when you point your smartphone camera at the image.
