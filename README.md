# sfm
Steven Bao and Bo Zhao.


## Tutorial
#### Change Default View in Potree Page
1. Open the **.html** file in the root directory of the potree folder with a **text editor**.
2. Scroll down to the bottom and locate the code: `viewer.fitToScreen();`
3. Replace the code with
```
viewer.scene.view.position.set(x, y, z);
viewer.scene.view.lookAt(x, y, z);
```
The first line changes the view angle.</br>The second line changes the center of the viewer.

Tips for finding the appropriate coordinates:
1. Open your potree page with a web browser
2. Play with your point cloud and find your favorite view
3. Scroll down to the bottom part of the control bar (on the left)
4. Under "Scene" - "Objects" - "Other", you can find "Camera"
5. Click on "Camera", then "Properties" will show up.
6. The coordinate under **"position"** is the one for `viewer.scene.view.position.set(x, y, z)`</br>The coordinate under **"target"** is for `viewer.scene.view.lookAt(x, y, z)`




*The data used for our example is from [senseFly](https://www.sensefly.com/education/datasets/?dataset=4944).*
