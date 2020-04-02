# sfm
Steven Bao and Bo Zhao.

## Tutorial

[Here](https://github.com/potree/PotreeConverter) is the GitHub page of PotreeConverter, which contains the full usage for PotreeConverter.



#### Change Default View in Potree Page

1. Open the **.html** file in the root directory of the potree folder with a **text editor**.
2. Scroll down to the bottom and locate the code: `viewer.fitToScreen();`
3. Replace the code with
```
viewer.scene.view.position.set(x, y, z);
viewer.scene.view.lookAt(x, y, z);
```
*The first line changes the view angle.</br>The second line changes the center of the viewer.*

Tips for finding the appropriate coordinates:
1. Open your potree page with a web browser

2. Play with your point cloud and find your favorite view

3. Scroll down to the bottom part of the control bar (on the left)

4. Under "Scene" - "Objects" - "Other", you can find "Camera"

5. Click on "Camera", then "Properties" will show up.

6. The coordinate under **"position"** is the one for `viewer.scene.view.position.set(x, y, z)`</br>

   The coordinate under **"target"** is for `viewer.scene.view.lookAt(x, y, z)`

#### Add Map Projection Information
If your point cloud data contain map projection information, you can also add it to your Potree page!

PotreeConverter has an option for us to keep the projection of our data so that the location could be shown in the generated Potree page

2. An example of the basic codes that convert *data.las* and generate a Potree page is:

   `./PotreeConverter.exe C:/data.las -o C:/potree_converted -p pageName`

2. In order to add the projection information to the conversion process, we can use the option `--projection`

   `--projection                           Specify projection in proj4 format.`

3. For example, if the projection of our point cloud data is WGS 84, we can use [this](https://spatialreference.org) website to find the projection in proj4 format:

   ![how to find proj4 format](/tutorial_gifs/how-to-find-proj4-format.gif)

   So we know that the the proj4 format for WGS84 is

   `+proj=longlat +ellps=WGS84 +datum=WGS84 +no_defs`

4. Therefore, we add the `--projection` option at the end of the original codes.

  Original:
  `./PotreeConverter.exe C:/data.las -o C:/potree_converted -p pageName`

  New:
   `./PotreeConverter.exe C:/data.las -o C:/potree_converted -p pageName --projection "+proj=longlat +ellps=WGS84 +datum=WGS84 +no_defs"`

5. After you run the new codes, you will find that the projection has been added and you can see the location in the generated Potree page!

*The data used for our example is from [senseFly](https://www.sensefly.com/education/datasets/?dataset=4944).*
