# RICOH THETA SC2 API

Build Android iOS mobile apps for the SC2 and connect 
your mobile app to the camera with Wi-Fi using this API.

![header](images/overview/header.png)

## Overview

The RICOH THETA SC2 is a great, lightweight camera that takes good-looking 360° pictures. Many people in the developer community have asked about building applications for the SC2. Although the SC2 camera appears to conform to the RICOH THETA Wi-Fi API, it is not listed on 
[the official RICOH API site](https://api.ricoh/docs/theta-web-api-v2.1/) which we all use as our reference. Some developers have [reported problems](https://community.theta360.guide/t/question-about-getlivepreview-by-thetasc2-on-android/5117) with the SC2 and the 
[RICOH THETA SDK](https://www2.theta360.guide/doc/article/3) for features such as live preview. Other people have 
[reported problems using the SC2 with the Google Streetview mobile app](https://community.theta360.guide/t/theta-sc2-crash-street-view-app/5288?u=craig).

Camera support note: All models except m15 work with the API.  However, there are minor differences between each model.  This test is for the SC2. One important point about the SC2 is that it is using a slower MCU compared to the RICOH THETA V and Z1.  The slower speed of the SC2 results in longer processing times for all API commands.  This can cause problems if you run multiple API commands in sequence and do not check for completion of each command.  There are extensive examples in this document and sample code that show how to use 
[POST /osc/commands/status](https://api.ricoh/docs/theta-web-api-v2.1/protocols/commands_status/) to verify that your previous API command is finished processing.

This article organizes usage of the SC2 Wi-Fi API based on community testing.  It is not an official RICOH 
document. Please contact RICOH for official information.

## Tools and Setup

