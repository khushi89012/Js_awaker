# Js_awaker

# Screen Wake Lock Example

This repository demonstrates how to utilize the Screen Wake Lock API to prevent a device's screen from dimming or locking during a video call. 

## Overview

The Screen Wake Lock API provides a way to prevent devices from dimming or locking the screen automatically, ensuring that important activities such as video calls remain uninterrupted.

## Getting Started

To use the Screen Wake Lock API, follow these steps:

1. Include the code provided in your project.

2. Call the `startVideoCall()` function when initiating a video call.

3. The `requestWakeLock()` function requests a wake lock to prevent the screen from dimming or locking during the video call.

4. The `releseWakeLock()` function releases the wake lock after a specified duration (default: 10 minutes).

## Code Example

```javascript
async function requestWakeLock(){
  try{
    wakeLock = await navigator.wakeLock.request('screen')
    console.log("Screen wake lock is activated")
  }
  catch(err){
    console.error("Error requesting : ",err.message)
  }
}

const releseWakeLock = ()=> wakeLock && wakeLock.release()

const startVideoCall = ()=>{
  requestWakeLock()
  setTimeout(releseWakeLock,600000)
}
