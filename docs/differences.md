
## RICOH THETA Development Community Tip Sheet

early access outline

Last updated: December 6, 2021

This is a community document based on contributions of informal test results from the theta360.guide independent community. This is not an official RICOH document. For official information, please contact RICOH. You should confirm these community tips with your own tests prior to deployment in a business setting. As these are unofficial tips, the official RICOH THETA API may change unexpectedly and these techniques could stop working.


## Limited Functionality on SC2 and SC2B


<table>
  <tr>
   <td><strong>Limited API</strong>
   </td>
   <td><strong>Explanation</strong>
   </td>
  </tr>
  <tr>
   <td>commands/status
   </td>
   <td>Only works with SC2 for takePicture.  Cannot be used with startCapture.  To see when the interval or bracket shooting is finished when using startCapture, use osc/state and look for _captureState of the SC2
   </td>
  </tr>
  <tr>
   <td>camera.startCapture
   </td>
   <td>SC2 does not support interval composite shooting. Additionally, only the SC2B supports time shift shooting.   You will not be able to use time shift on the standard SC2
   </td>
  </tr>
  <tr>
   <td>camera.stopCapture
   </td>
   <td>when interval shooting captureNumber is set to 0 (unlimited shots in interval shooting), the SC2 will not return the list of files when stopCapture is finished
   </td>
  </tr>
  <tr>
   <td>camera.listFiles
   </td>
   <td>SC2 will not show multiple thumbnails when maxThumbSize is set to 640.  It will only return a single thumbnail.  To get multiple thumbnails, get each thumbnail individually in a loop. You can also use GET to grab the thumbnail of each file as binary data by adding ?type=thumb to the URL  
   </td>
  </tr>
  <tr>
   <td>camera.delete
   </td>
   <td>Prior to firmware 1.42, the SC2 could not delete more than one image or video file when specified as a list.  It also didn’t support the“all” parameter to delete all files. 
   </td>
  </tr>
  <tr>
   <td>camera._getMetadata
   </td>
   <td>does not return correct information.  Workaround is to download the file to your mobile device and then extract the metadata locally after download.
   </td>
  </tr>
  <tr>
   <td>camera._getMySetting
   </td>
   <td>May not be returning correct results on the SC2. Note that the SC2 reverts to MySetting when the Wi-Fi connection is dropped or the camera is restarted or resumed from sleep. See the article below for more information.
<p>
<a href="https://docs.google.com/document/d/e/2PACX-1vTPLBqVabuiic4uuSAy-h9PSCZOgtqY7mweDJnS5bXvpJuYwToVxlqpOtbGXfR279tN6nQRN7cqs2xX/pub">https://docs.google.com/document/d/e/2PACX-1vTPLBqVabuiic4uuSAy-h9PSCZOgtqY7mweDJnS5bXvpJuYwToVxlqpOtbGXfR279tN6nQRN7cqs2xX/pub</a>
   </td>
  </tr>
</table>



## Unsupported by SC2 and SC2B


<table>
  <tr>
   <td><strong>Unsupported API</strong>
   </td>
   <td><strong>Explanation</strong>
   </td>
  </tr>
  <tr>
   <td>GET /plugin
   </td>
   <td>SC2 does not support plug-ins
   </td>
  </tr>
  <tr>
   <td>camera._convertVideoFormats
   </td>
   <td>SC2 has fixed parameters for video.  Also, it appears that topBottomCorrection may be applied after the file is downloaded versus applying topBottomCorrection inside the camera.
   </td>
  </tr>
  <tr>
   <td>camera._cancelVideoConvert
   </td>
   <td>SC2 cannot perform video conversions
   </td>
  </tr>
  <tr>
   <td>camera._listAccessPoints
   </td>
   <td>SC2 does not support client mode connections and thus cannot connect to external Wi-Fi access points
   </td>
  </tr>
  <tr>
   <td>camera._setAccessPoint
   </td>
   <td>Set access point in client mode.  SC2 only supports access point mode.
   </td>
  </tr>
  <tr>
   <td>camera._deleteAccessPoint
   </td>
   <td>SC2 does not support client mode Wi-Fi and thus cannot save external Wi-Fi access point information inside the camera.
   </td>
  </tr>
  <tr>
   <td>camera._listPlugins
   </td>
   <td>SC2 does not support plug-ins
   </td>
  </tr>
  <tr>
   <td>camera._setPlugins
   </td>
   <td>SC2 does not support plug-ins
   </td>
  </tr>
  <tr>
   <td>camera._pluginControl
   </td>
   <td>SC2 does not support plug-ins
   </td>
  </tr>
  <tr>
   <td>camera._getPluginLicense
   </td>
   <td>SC2 does not support plug-ins
   </td>
  </tr>
  <tr>
   <td>camera._getPluginOrders
   </td>
   <td>SC2 does not support plug-ins
   </td>
  </tr>
  <tr>
   <td>camera._setPluginOrders
   </td>
   <td>SC2 does not support plug-ins
   </td>
  </tr>
  <tr>
   <td>camera._deleteMySetting
   </td>
   <td>does not appear to delete all the settings on the SC2.  Suggest you overwrite the settings in MySetting.  Also, it appears that camera.reset may not reset all the SC2 settings in MySetting.  See the article link in the camera._getMySetting section.
   </td>
  </tr>
  <tr>
   <td>aperture
   </td>
   <td>Only Z1 has an adjustable aperture
   </td>
  </tr>
  <tr>
   <td>_authentication
   </td>
   <td>SC2 does not support client mode and thus cannot disable digest authentication for client mode.
   </td>
  </tr>
  <tr>
   <td>_bluetoothPower
   </td>
   <td>Does not appear to work on the SC2, but you can turn on bluetooth manually with the button on the side of the camera.
   </td>
  </tr>
  <tr>
   <td>_compositeShootingOutputInterval
   </td>
   <td>Only Z1 support interval composite shooting
   </td>
  </tr>
  <tr>
   <td>_compositeShootingTime
   </td>
   <td>Only Z1 support interval composite shooting
   </td>
  </tr>
  <tr>
   <td>_HDMIreso
   </td>
   <td>No HDMI output on Z1.  
   </td>
  </tr>
  <tr>
   <td>_imageStitching
   </td>
   <td>SC2 cannot control image stitching
   </td>
  </tr>
  <tr>
   <td>_language
   </td>
   <td>not supported on SC2.  even on the Z1, it’s not clear what impact this setting has.
   </td>
  </tr>
  <tr>
   <td>_microphone
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>_microphoneChannel
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>_networkType
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>_password
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>previewFormat
   </td>
   <td>width and height not working.  SC2 only has one preview format and one fps.
   </td>
  </tr>
  <tr>
   <td>_shootingMethod
   </td>
   <td>for MySetting
   </td>
  </tr>
  <tr>
   <td>_topBottomCorrection
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>videoStitching
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>_visibilityReduction
   </td>
   <td>reduce size of tripod at bottom of image
   </td>
  </tr>
  <tr>
   <td>_username
   </td>
   <td>name for client mode digest authentication.  SC2 does not support client mode Wi-Fi connections
   </td>
  </tr>
  <tr>
   <td>_wlanFrequency
   </td>
   <td>SC2 only supported 2.4GHz.  Z1 supports 2.4GHz and 5GHz
   </td>
  </tr>
</table>



## Unique SC2 APIs


<table>
  <tr>
   <td><strong>API</strong>
   </td>
   <td><strong>Explanation</strong>
   </td>
  </tr>
  <tr>
   <td>cameraMode presets
   </td>
   <td>SC2 has unique presets for face mode, night view mode, lens-by-lens exposure.  SC2B also has room mode
   </td>
  </tr>
</table>



## Z1 Surprising Behavior


<table>
  <tr>
   <td><strong>API</strong>
   </td>
   <td><strong>Explanation</strong>
   </td>
  </tr>
  <tr>
   <td>camera.reset
   </td>
   <td>offDelay is set to 64800 (18 hours) on reset.  For the SC2, the offDelay is reset to 600 (10 minutes).
   </td>
  </tr>
</table>



## Other Interesting API Findings


### Interval shooting



* SC2, minimum value is 8
* V, minimum value is 4
* Z1, minimum value is 6 for JPEG
* 10 for RAW+


### mySetting

THETA Z1 and SC2 can save shooting conditions set with a smartphone or the API. Shooting conditions registered in My Settings can be enabled by the end user by pressing and holding the Function (Fn) button on the THETA. The advantage is that you can save your shooting conditions and use them even while not connected to a smartphone.



* Both Z1 and SC2 mySetting settings survive reboot and sleep
* There is no My Settings icon on the SC2 (in fact, no OLED at all). Therefore, there is no way for the end user to change the settings without the mobile app.
* If you run camera.reset, the Z1 will give an error for the getMySetting command. This is expected behavior, since mySetting has no settings. However, using camera.reset with an SC2 will not reset the settings.


### Time For Camera to Be Ready

The SC2 has a slower processor than the Z1.  The Sc2 takes approximately 8,181 milliseconds to be ready for the next picture versus 2,922 milliseconds for the Z1.  This is based on polling the camera status every 100ms.  So, if you poll it more frequently, you will get more accurate results.

The amount of time taken for the picture also varies with light conditions.  If the image is darker, it will leave the shutter open longer.


## Testing the API with the Oppkey THETA ATK

A free tester is available to help you test the RICOH THETA API.

**[Get Oppkey THETA ATK Now](https://oppkey.github.io/oppkey_theta_atk/)**

