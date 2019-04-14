<p align="center">
   <img src="https://user-images.githubusercontent.com/2917613/28090232-861702b0-6683-11e7-8379-1347e01c9411.png" height="300">
<p>

# Module: MMM-Alexa

MMM-Alexa module allows MagicMirror to connect Amazon Alexa Voice Synthesis (AVS) service without requiring anything else. 

> This module do not contain it's own **hotword**.
> You will need an external module for this like **[MMM-VoiceCommander]**(https://github.com/thestigh/MMM-VoiceCommander) to activate Alexa. Have a look at **[MMM-VoiceCommander]**(https://github.com/thestigh/MMM-VoiceCommander) as it more than a **hotword** module.

## Installation and requirements

Start by doing the commands below to make the initial installation: 

> Perform the commands from ***~/MagicMirror/modules*** directory

```
git clone https://github.com/thestigh/MMM-Alexa
cd MMM-Alexa
npm install
```

After installation you need to check your **audio setup**, as this module also relies on *arecord/aplay*.
From your home directory, run command: ***sudo nano ~/.asoundrc***

If it is empty, copy following code to the editor (values might need to be changed):

```
pcm.!default{
  type asym
  playback.pcm{
     type plug
     slave.pcm "hw:0,0"
  }

  capture.pcm{
    type plug
    slave.pcm "hw:0, 0"
  }
}

ctl.!default{
  type hw
  card 0
}
```

> Do you want help to confiure or just deeper understanding *arecord*, [click here](https://github.com/TheStigh/MMM-VoiceCommander/tree/master/docsarecordHelp.md)

Then make sure you set the **hw:** and the  **card** vales according to your own hardware configuration (you get the output at the end of installerscript you just ran) where hw:0,0 represent output and hw:1,0 represent input source.

> ***Save and close*** nano editor


## Config.js entries and options

### 1. Adding MagicMirror to Amazon AVS Service

To use this module, you have to be registered to Amazon AVS service and add you MagicMirror as device/product with using your account in order to use Amazon Alexa service.

Follow [this help page](https://github.com/TheStigh/MMM-Alexa/tree/master/docs/helpAVS.md) to get up and running with Amazon. ***TODO: add instructions***

> Remember that each initial code can be used only once, then it's being converted to token by the module. So if you run your mirror at your computer for testing, you should gather another code.

### 2. config.js
Add it to the modules array in the config/config.js file:

```
{
       module: 'MMM-alexa',
       position: 'top_right', // The status indicator position
           config: {
		    avsDeviceId: 'my_device/product',
		    avsClientId: 'amzn1.application-oa2-client.***abcdefgh***',
		    avsClientSecret: '***abcdefgh***',
		    avsInitialCode: '***ANVabcdefgh***',
		    enableRaspberryButton: true
		    }
},
```
> Replace the ***abcdefgh*** with values from **step 3** 

### 3. Configuration options

The following properties can be configured:

| Argument | Default | Description |
|---|---|---|
| **`avcDeviceId`** | `""` | The device/product id  that you've created at Amazon |
| **`avsClientId`** | `""` | The client id which is generated at Amazon |
| **`avsClientSecret`** | `""` | The client secret which is generated at Amazon |
| **`avsInitialCode`** | `""` | The initial code for authentication |
| **`hideStatusIndicator`** | `false` | Hide status indicator on the MM |
| **`debug`** | `false` | Add `alexaStart()` and `alexaStop()` commands to the MM console |
| **`disableVoiceActivityDetection`** | `false` | Disable voice activity detection(VAD), it's used to understand when the user stops speaking |
| **`enableRaspberryButton`** | `false` | Enable starting to record with pressing button which is connected to GPIO |


### 4. Installing microphone dependencies

After installation you need to check your **audio setup**, as this module also relies on *arecord/aplay*.
From your home directory, run command:

> ***sudo nano ~/.asoundrc***

If it is empty, copy following code to the editor (values might need to be changed):

```
pcm.!default {
  type asym
   playback.pcm {
     type plug
     slave.pcm "hw:0,0"
   }
   capture.pcm {
     type plug
     slave.pcm "hw:1,0"
   }
}
```

> Do you want help to configure or just deeper understanding *arecord*, [click here](https://github.com/TheStigh/MMM-VoiceCommander/tree/master/docsarecordHelp.md)

> ***Save and close*** nano editor

Then run this command :

`amixer cset numid=3 1`

### 5. OPTIONAL: Raspberry Pi Button to start recording

Button should be connected to GPIO pin 4. The button is used only to start recording.
Do not forget to enable Raspberry Pi button in config. 


## Tested on

| Hardware Platform    |   Operating System   | Notes                                                                                                                                                                                                                                                                                             |
| -------------------- | -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| HP Elite 8300        | ✔  Ubuntu 18.04 LTS  | -                                                                                                                                                                                                                                                                                                 |
| HP Elite HPEu        | ✔  Ubuntu 16.04 LTS  | -                                                                                                                                                                                                                                                                                                 |
| HP G60 Laptop        | ✔  Ubuntu 18.04 LTS  | -                                                                                                                                                                                                                                                                                                 |
| Huawei Matebook Pro  | ✔  Ubuntu 16.04 LTS  | -                                                                                                                                                                                                                                                                                                 |
| Intel NUC Celeron    | ✔  Ubuntu 16.04 LTS  | -                                                                                                                                                                                                                                                                                                 |
| Tinker Board S       | ✔  TinkerOS 2.0.8    | -                                                                                                                                                                                                                                                                                                 |
| Raspberry Pi 3b+     | ✔  Debian Stretch    | -                                                                                                                                                                                                                                                                                                 |
| Odroid               | ✘                    | Need somebody to test on Odroid!                                                            |
| Windows              | ✘                    | Need somebody to test on Windows!                                                            |



## Development

Feel free to create Pull Requests, or issues as new ideas. Current plan for development is listed below.
  
  * Improve voice activity detection


## Special thanks

> I can't thank ***sdetweil*** enough for his great help with attach/release control of microphone ++

## Licence

MIT
