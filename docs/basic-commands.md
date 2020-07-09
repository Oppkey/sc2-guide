## Basic Commands

Use standard HTTP requests to communicate with the SC2.  Most of the commands are
POST requests and require a script or an API testing tool. A few of the 
commands are GET requests and can be tested with a browser.

### info

Check API Access with "info"
Use the simplest possible API command first to make sure your workstation can talk to the camera with HTTP. Send a GET command to http://192.168.1.1/osc/info

You can also run the GET command in your browser.

![info](images/basic-commands/info.png)

You will see the response below.

![info response](images/basic-commands/info-response.png)

This is a test using Google Chrome.

![info Chrome](images/basic-commands/info-chrome.png)

Chrome displays colored highlighting in my browser because I am using the free extension 
[JSON Awesome](https://chrome.google.com/webstore/detail/json-viewer-awesome/iemadiahhbebdklepanmkjenfdebfpfe?hl=en).

The rest of this tutorial will focus on POST commands.  You will need to use an API testing tool.

