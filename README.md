    

# Veeso Marlin DRM Plugin Reference

## About

* * *

The Veeso Marlin DRM Plugin allows rendering of Marlin DRM secured video content in the Veeso Player

## Eclipse Project Integration

Step 1: Add the VeesoMarlinPlugin project to your workspace

- In Package Explorer, right-click and select New -> Project

- Select Android Project from existing code

- Select the folder "VeesoMarlinPlugin" from the downloaded archive

Step 2: Add the library as a dependency for your Android Application

- In Package Explorer, right click your Android Application Project

- Click Properties

- On the Android tab, click Add.. in the library section

- Select VeesoMarlinPlugin and click OK

- Click on Apply and then OK

Step 3: Add the Veeso Player as a dependency to the VeesoMarlinPlugin project 

- In Package Explorer, right click your VeesoMarlinPlugin project 

- Click Properties

- On the Android tab, click Add.. in the library section

- Select AppscendVastPlayer and click OK

- Click on Apply and then OK

Step 4: Add the ExpressPlay SDK as a referenced library for the VeesoMarlinPlugin project 

- In Package Explorer, right click your VeesoMarlinPlugin project 

- Click Properties

- Click on Java Build Path. Then navigate to Libraries and click on Add External JARs. 

- Go to your downloaded copy of the ExpressPlay Test SDK, decompress the *.zip file, and open the newly created folder. Find the subfolder called Library and open it. Inside the folder there is a file called wasabi.jar. Click and open the wasabi.jar file. The file should now appear in the build path. Next expand the wasabi.jar file and click Native library location and then click Edit. 

- Select External Folder. Go to back to your ExpressPlay Test SDK and open the Library folder. Ensure that you see both the wasabi.jar and the libWasabiJni.so files in that folder and apply the changes. The external libraries should now appear in the package explorer under Referenced Libraries.

### Simple Usage Example

Import the MarlinManager class:
<pre>
    
<span style="color:purple">import</span> co.veeso.drm.marlin.MarlinManager;
    
</pre>
Initialize the Marlin Library and register the singleton instance with the Veeso player
<pre>
   
		MarlinManager.getInstance().init(this);
		APSMediaPlayer.getInstance().registerAdapterInGroup(MarlinManager.getInstance(), APSMediaPlayer.kAPSMediaPlayerDRMPluginsGroup);
    
</pre>

Finally, add the correct metadata keys, either through JSON or programatically.

JSON example:
<pre>
    
		{
			"content": [{
					"url": "MARLIN ENCODED HLS STREAM URL",
					"controls" : {
						"components" : ["playback", "backButton", "forwardButton", "totalTime", "slider", "currentTime", "fullscreen"],
						"liveText" : "LIVE"
					},
					"metadata": {
						"drm_encoding_type" : "marlin",
						"drm_encoding_url" : "ActionToken URL"
					},
					"autoplay": true
				}]
		}
    
</pre>