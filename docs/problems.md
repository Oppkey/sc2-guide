# SC2 Problem Quick Summary

## LivePreview Randomly Stops in SDK

__Problem Description__: livePreview screen goes black in SC2.
With the Android SDK,
you get an
EOFException in readMJpegFrame() in MJpegInputStream.

__Workaround__: [Submitted by tamy](https://community.theta360.guide/t/question-about-getlivepreview-by-thetasc2-on-android/5117/15?u=craig).
Call camera.getLivePreview again after the error occurs.

## LivePreview Stops After Running a Command

__Problem Description__: livePreview stops after certain commands.

__Workaround__: Certain API commands appear to stop the live preview.  If the screen is 
stopping, run camera.getLivePreview again.

## startCapture always shows inProgress

Problem and solution [reported by timbit123](https://community.theta360.guide/t/solved-check-for-sc2-auto-bracket-completion/5651/2?u=craig).

__Problem Description__: When using /osc/command/status with the id from
`startCapture`, the state is always inProgress.

__Workaround__: Use `/osc/state` and wait for `_captureStatus` to go back to `idle`.

## listFiles does not show thumbnails and freezes SC2

[Problem reported by timbit123](https://community.theta360.guide/t/sc2-listfiles-command-with-thumbnails-not-working/5748?u=craig).

__Problem Description__: `maxThumbSize: 640` does not show the thumbnails.
The SC2 will freeze. There is no way to get the thumbnails. The
listFiles command on the SC2 works differently than it does on the V and Z1.

__Workaround__: As of August 11, 2020, we have thumbnails 
working with the SC2.  You can get a base64 encoded 
thumbnail of approximately 7.3kB in size. 

![thumbnail screenshot](images/thumbnail/thumbnail-screenshot.png)


Grab the URL of the file you want to get the thumbnail for and 
then specify it in `_startFileUrl`.

Example in Dart map.

```dart
  Map data = {
    'name': 'camera.listFiles',
    'parameters': {
      'fileType': 'image',
      'entryCount': 5,
      'maxThumbSize': 640,
      '_detail': true,
      '_startFileUrl':
          'http://192.168.1.1/files/thetasc26c21a247d9055838792badc5/100RICOH/R0010129.JPG'
    }
```

This is the response from a THETA SC2. 

```json
200
{
  "name": "camera.listFiles",
  "results": {
    "entries": [
      {
        "name": "R0010129.JPG",
        "fileUrl": "http://192.168.1.1/files/thetasc26c21a247d9055838792badc5/100RICOH/R0010129.JPG",
        "size": 3943866,
        "isProcessed": true,
        "previewUrl": "",
        "dateTimeZone": "2020:08:01 15:07:50-07:00",
        "width": 5376,
        "height": 2688,
        "_thumbSize": 7349,
        "thumbnail": "/9j/2wCEAAsICAoIBwsKCQoNDAsNERwSEQ8PESIZGhQcKSQrKigkJyctMkA3LTA9MCcnOEw5PUNFSElIKzZPVU5GVEBHSEUBDA0NEQ8RIRISIUUuJy5FRUVFRUVFRUVFRUVFRUVFRUVFRUVFRUVFRUVFRUVFRUVFRUVFRUVFRUVFRUVFRUVFRf/EAaIAAAEFAQEBAQEBAAAAAAAAAAABAgMEBQYHCAkKCxAAAgEDAwIEAwUFBAQAAAF9AQIDAAQRBRIhMUEGE1FhByJxFDKBkaEII0KxwRVS0fAkM2JyggkKFhcYGRolJicoKSo0NTY3ODk6Q0RFRkdISUpTVFVWV1hZWmNkZWZnaGlqc3R1dnd4eXqDhIWGh4iJipKTlJWWl5iZmqKjpKWmp6ipqrKztLW2t7i5usLDxMXGx8jJytLT1NXW19jZ2uHi4+Tl5ufo
        ...
```


Code sample is available that saves thumbnails to local storage to help with
testing.

## camera._getMetadata not working as expected

__Problem Description__: Properties such as ExposureBiasValue
are incorrect.  

__Workaround__: The correct metadata appears to be in the image file.
Pull the actual image to your mobile phone and then use a library
to extract the metadata in the image on your mobile phone.  Do not
use camera._getMetadata to pull the information if you suspect 
it is not providing you with the correct values.

## previewFormat width and height not working

__Problem Description__: with getOptions, the `previewFormat` does 
not show correct values.  `width` and `height` return 0.

__Workaround__: There is no known workaround to set the width and 
height, but getLivePreview does appear to work. The preview format
of the SC2 is fixed at 1024x512 at 30fps.  Unlike the V and the Z1, the 
preview format cannot be changed to different fps and frame size. 
Examples of how to extract the JPEG frames from the MotionJPEG
stream are available.  If your mobile app checks the camera model, you can
figure out what the size of the frames are on the SC2 without 
needing to use previewFormat.  For SC2, the size is always 1024x512.

## camera.delete does not delete multiple images from camera

__Problem Description__: [camera.delete](https://api.ricoh/docs/theta-web-api-v2.1/commands/camera.delete/) only deletes one image. The 
array of URLs and special parameters such as "all" and "image" do 
not work.

__Workaround__: Use listFiles to get the list of images and then 
delete each file individually in a loop or map. 



