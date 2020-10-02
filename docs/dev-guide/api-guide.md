# Overview

Embedding the Jitsi 8x8 API into your site or app enables you to host and provide secure video meetings with your colleagues or stakeholders. The full compliment of comprehensive meeting features in the Jitsi 8x8 implementation leads to successful meeting engagement and future positive interactions.

Your Jitsi 8x8 meeting can be hosted and attended using any device while keeping your  data and privacy protected. You can reach your colleagues and stakeholders anywhere in the world eliminating the need for any travel or inconvenience.

# Setup

The following sections describe how to setup your Jitsi 8x8 Meet:


## Create 8x8 Account


## Installation

To embed Jitsi 8x8 Meet in your application you need to add the Jitsi 8x8 Meet API library. To add the library use one of the following script options:

**??**
**Self-hosted**:

```
<script src='https://<your-domain>/external_api.js'></script>
```

**meet.jit.si:**


```
<script src='https://meet.jit.si/external_api.js'></script>
```

## Creating the meeting name

## Displaying dial-in information

## Adding a one-tap number


## Displaying dial-in information

Here’s how you construct showing dial-in information statelessly for the meeting example above:

your_unique_meeting_id

To join your meeting, dial one of these numbers and then enter the pin.

PIN: 3105 9337 88


<table>
  <tr>
   <td><strong>Country</strong>
   </td>
   <td><strong>Dial-in Numbers</strong>
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td><strong>US</strong>
   </td>
   <td>
<ul>

<li>+1.512.647.1431
</li>
</ul>
   </td>
   <td>
<ul>

<li>
</li>
</ul>
   </td>
  </tr>
  <tr>
   <td><strong>UK</strong>
   </td>
   <td>
<ul>

<li>+44.203.885.2179
</li>
</ul>
   </td>
   <td>
<ul>

<li>
</li>
</ul>
   </td>
  </tr>
  <tr>
   <td><strong>France</strong>
   </td>
   <td>
<ul>

<li>+33.1.87.21.0005
</li>
</ul>
   </td>
   <td>
<ul>

<li>
</li>
</ul>
   </td>
  </tr>
  <tr>
   <td><strong>Germany</strong>
   </td>
   <td>
<ul>

<li>+49.89.380.38719
</li>
</ul>
   </td>
   <td>
<ul>

<li>
</li>
</ul>
   </td>
  </tr>
  <tr>
   <td><strong>Netherlands</strong>
   </td>
   <td>
<ul>

<li>+31.85.208.1541
</li>
</ul>
   </td>
   <td>
<ul>

<li>
</li>
</ul>
   </td>
  </tr>
  <tr>
   <td><strong>Spain</strong>
   </td>
   <td>
<ul>

<li>+34.932.205.409
</li>
</ul>
   </td>
   <td>
<ul>

<li>
</li>
</ul>
   </td>
  </tr>
  <tr>
   <td><strong>Canada</strong>
   </td>
   <td>
<ul>

<li>+1.437.538.3987
</li>
</ul>
   </td>
   <td>
<ul>

<li>
</li>
</ul>
   </td>
  </tr>
  <tr>
   <td><strong>Australia</strong>
   </td>
   <td>
<ul>

<li>+61.8.7150.1136
</li>
</ul>
   </td>
   <td>
<ul>

<li>
</li>
</ul>
   </td>
  </tr>
  <tr>
   <td><strong>Brazil</strong>
   </td>
   <td>
<ul>

<li>+55.21.3500.0112
</li>
</ul>
   </td>
   <td>
<ul>

<li>
</li>
</ul>
   </td>
  </tr>
  <tr>
   <td><strong>Japan</strong>
   </td>
   <td>
<ul>

<li>+81.3.4510.2372
</li>
</ul>
   </td>
   <td>
<ul>

<li>
</li>
</ul>
   </td>
  </tr>
  <tr>
   <td><strong>Switzerland</strong>
   </td>
   <td>
<ul>

<li>+41.61.588.0496
</li>
</ul>
   </td>
   <td>
   </td>
  </tr>
</table>



## Adding a one-tap number

Adding a one-tap number performs API calls without any the need for authentication or authorization. 

For example, consider the scenario in which you want to add a one tap dial-in number for every event (e.g., +1 209-844-4600,,1366520583#)

In order to enable this feature you need to run the following Jitsi 8x8 API call first:


```
https://api.jitsi.net/phoneNumberList?conference=SuccessivePortsCompeteMeanwhile@conference.meet.jit.si
```


This will return all the phone numbers that can be used to join the subject meeting. The first number returned will always be the one that was detected as closest to the endpoint that performed the call. We run this on in the browser so that we can get a number that matches the location of the user.

The second call you make generates your pin code for the meeting:


```
https://api.jitsi.net/conferenceMapper?conference=some-id-you-like@conference.mycompany.meet.jit.si
```


If you are interested in our professional video API offering, contact the Jitsi 8x8 team at vpaas@8×8.com


## **2.**6** Creating the Jitsi Meet API object**


```
api = new JitsiMeetExternalAPI(domain, options)
```


After you have installed the Jitsi 8x8 Meet API library, you need to create the Jitsi 8x8 Meet API object. The object consists of ______.

The API object constructor can use the following options:



*   **domain**: The domain used to build the conference URL (e.g., **<code>meet.jit.si</code></strong>).
*   <strong>options</strong>: The object with properties.  

    <strong><span style="text-decoration:underline;">Optional</span></strong> arguments include:

    *   **roomName**:  The name of the room to join
    *   **width**:  The width for the created Iframe. If a number is specified it is treated as pixel units. If a string is specified the format is number followed by 'px', 'em', 'pt' or '%'.
    *   **height**: The height for the created Iframe. If a number is specified it is treated as pixel units. If a string is specified the format is number followed by 'px', 'em', 'pt' or '%'.
    *   **parentNode**:  The HTML DOM Element where the Iframe will be added as a child.
    *   **configOverwrite**:  The JavaScript (JS) object with overrides for options defined in the **<code>config.js</code></strong> file.
    *   <strong>interfaceConfigOverwrit</strong>e:  The JS object with overrides for options defined in the <strong><code>interface_config.js</code></strong> file.
    *   <strong>noSSL</strong>: (optional, defaults to false) Boolean indicating if the server should be contacted using HTTP or HTTPS.
    *   <strong>jwt</strong>:  JWT token.
    *   <strong>onload</strong>:  handler for the iframe onload event.
    *   invitees:  Array of objects containing information about new participants that will be invited in the call.
    *   <strong>devices</strong>:  A map containing information about the initial devices that will be used in the call.
    *   <strong>userInfo</strong>:  JS object containing information about the participant opening the meeting, such as email.

The following example represents _________:


```
const domain = 'meet.jit.si';
const options = {
    roomName: 'JitsiMeetAPIExample',
    width: 700,
    height: 700,
    parentNode: document.querySelector('#meet')
};
const api = new JitsiMeetExternalAPI(domain, options);
```


You can set the initial media devices for the call using the following:


```
const domain = 'meet.jit.si';
const options = {
    ...
    devices: {
        audioInput: '<deviceLabel>',
        audioOutput: '<deviceLabel>',
        videoInput: '<deviceLabel>'
    },
    ...
};
const api = new JitsiMeetExternalAPI(domain, options);
```


You can override options set in the **<code>config.js</code></strong> and<strong><code> interface_config.js</code></strong> files using <strong><code>configOverwrite</code></strong> and<strong><code> interfaceConfigOverwrite</code></strong>, respectively. 

For example, to enable the filmstrip-only interface mode, you can use the following:


```
const options = {
    ...
    configOverwrite: { startWithAudioMuted: true },
    interfaceConfigOverwrite: { filmStripOnly: true },
    ...
};
const api = new JitsiMeetExternalAPI(domain, options);
```


You can also pass a JWT token to Jitsi 8x8 Meet in order to ______:


```
const options = {
   ...
   jwt: '<jwt_token>',
   ...
};
const api = new JitsiMeetExternalAPI(domain, options);
```


You can set the userInfo (email, display name) for the call:


```
var domain = "meet.jit.si";
var options = {
    ...
    userInfo: {
        email: 'email@jitsiexamplemail.com',
        displayName: 'John Doe'
    }
}
var api = new JitsiMeetExternalAPI(domain, options);
```



## **2.**7** Configuring the tile view**

You can configure the maximum number of columns in the tile view by overriding the **<code>TILE_VIEW_MAX_COLUMNS</code></strong> property from the <strong><code>interface_config.js</code></strong> via  <strong><code>interfaceConfigOverwrite</code></strong>:


```
const options = {
    ...
    interfaceConfigOverwrite: { TILE_VIEW_MAX_COLUMNS: 2 },
    ...
};
const api = new JitsiMeetExternalAPI(domain, options);
```


**Note:** **<code>TILE_VIEW_MAX_COLUMNS</code></strong> uses values from 1 to 5. The default value is 5.


# 
    **3 Controlling conferences**

The **<code>JitsiMeetExternalAPI</code></strong> provides a number of features that facilitate control of your conferences. All of these controls are invoked by using _____. 

The complete list of conference control features include the following:



*   

<p id="gdcalert4" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: undefined internal link (link text: "getAvailableDevices"). Did you generate a TOC? </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert5">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>

[getAvailableDevices](#heading=h.kicbrkulajlu)
*   

<p id="gdcalert5" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: undefined internal link (link text: "getCurrentDevices"). Did you generate a TOC? </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert6">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>

[getCurrentDevices](#heading=h.majvwsqixiga)
*   

<p id="gdcalert6" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: undefined internal link (link text: "getVideoQuality"). Did you generate a TOC? </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert7">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>

[getVideoQuality](#heading=h.hfso6d8sw8kz)
*   

<p id="gdcalert7" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: undefined internal link (link text: "isDeviceChangeAvailable"). Did you generate a TOC? </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert8">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>

[isDeviceChangeAvailable](#heading=h.hgn1g05luimg)
*   

<p id="gdcalert8" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: undefined internal link (link text: "isDeviceListAvailable"). Did you generate a TOC? </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert9">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>

[isDeviceListAvailable](#heading=h.snbemb55eblb)
*   

<p id="gdcalert9" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: undefined internal link (link text: "isMultipleAudioInputSupported"). Did you generate a TOC? </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert10">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>

[isMultipleAudioInputSupported](#heading=h.h4y4ssmjkyip)
*   

<p id="gdcalert10" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: undefined internal link (link text: "setAudioInputDevice"). Did you generate a TOC? </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert11">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>

[setAudioInputDevice](#heading=h.2fd1q72lovmi)
*   

<p id="gdcalert11" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: undefined internal link (link text: "setAudioOutputDevice"). Did you generate a TOC? </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert12">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>

[setAudioOutputDevice](#heading=h.v6patocyynim)
*   

<p id="gdcalert12" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: undefined internal link (link text: "setVideoInputDevice"). Did you generate a TOC? </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert13">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>

[setVideoInputDevice](#heading=h.f7fwkgji62y7)


## 3.1 getAvailableDevices

This meeting control retrieves the list of available devices in your __________ . Using this information you can ______.


```
api.getAvailableDevices().then(devices => {
    // devices = {
    //     audioInput: [{
    //         deviceId: 'ID'
    //         groupId: 'grpID'
    //         kind: 'audioinput'
    //         label: 'label'
    //     },....],
    //     audioOutput: [{
```


 **<code>   //         deviceId: 'ID'</code></strong>


```
    //         groupId: 'grpID'
    //         kind: 'audioOutput'
    //         label: 'label'
    //     },....],
    //     videoInput: [{
    //         deviceId: 'ID'
    //         groupId: 'grpID'
    //         kind: 'videoInput'
    //         label: 'label'
    //     },....]
    // }
    ...
});
```



## 3.2 getCurrentDevices

This control retrieves a list with the devices that are being used for th. You can use this information to _____ ________.


```
api.getCurrentDevices().then(devices => {
    // devices = {
    //     audioInput: {
    //         deviceId: 'ID'
    //         groupId: 'grpID'
    //         kind: 'videoInput'
    //         label: 'label'
    //     },
    //     audioOutput: {
    //         deviceId: 'ID'
    //         groupId: 'grpID'
    //         kind: 'videoInput'
    //         label: 'label'
    //     },
    //     videoInput: {
    //         deviceId: 'ID'
    //         groupId: 'grpID'
    //         kind: 'videoInput'
    //         label: 'label'
    //     }
    // }
    ...
});
```

## getVideoQuality

This control provides information about the current meeting video quality setting.


```
api.getCurrentDevices();
```



## isDeviceChangeAvailable

This conference control resolves to true if the device change is available and to false if not.


```
// The accepted deviceType values are - 'output', 'input' or undefined.
api.isDeviceChangeAvailable(deviceType).then(isDeviceChangeAvailable => {
    ...
});
```



## isDeviceListAvailable

The**<code> isDeviceListAvailable</code></strong> method resolves to true if the device list is available; resolves to false if the device list is not available:


```
api.isDeviceListAvailable().then(isDeviceListAvailable => {
    ...
});
```



## 3.6 isMultipleAudioInputSupported

This method resolves to true if multiple audio inputs are supported and to false if not.


```
api.isMultipleAudioInputSupported().then(isMultipleAudioInputSupported => {
    ...
});
```



## 3.7 setAudioInputDevice

This method sets the audio input device to the one with the label or id that is passed.


```
api.setAudioInputDevice(deviceLabel, deviceId);
```



## 3.8 setAudioOutputDevice

This method sets the audio output device to the one with the label or id that is passed.


```
api.setAudioOutputDevice(deviceLabel, deviceId);
```



## 3.9 setVideoInputDevice

This method sets the video input device to the one with the label or id that is passed.


```
api.setVideoInputDevice(deviceLabel, deviceId);
```


You can control the embedded Jitsi 8x8 Meet conference by calling **<code>executeCommand</code></strong> on the <strong><code>JitsiMeetExternalAPI</code></strong> object:


```
api.executeCommand(command, ...arguments);
```



# 
    4 executeCommand Parameters

The Jitsi API **<code>command</code></strong> parameter is a string containing the name of the command. The following commands are currently supported:



*   

<p id="gdcalert13" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: undefined internal link (link text: "displayName"). Did you generate a TOC? </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert14">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>

[displayName](#heading=h.to6ioicm81na)
*   

<p id="gdcalert14" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: undefined internal link (link text: "password"). Did you generate a TOC? </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert15">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>

[password](#heading=h.m5ajua5cfwpv)
*   

<p id="gdcalert15" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: undefined internal link (link text: "toggleLobby"). Did you generate a TOC? </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert16">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>

[toggleLobby](#heading=h.yq6xgfs6i6o)
*   

<p id="gdcalert16" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: undefined internal link (link text: "sendTones"). Did you generate a TOC? </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert17">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>

[sendTones](#heading=h.no31mr9pe458)
*   

<p id="gdcalert17" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: undefined internal link (link text: "subject"). Did you generate a TOC? </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert18">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>

[subject](#heading=h.3jij56a8tx35)
*   

<p id="gdcalert18" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: undefined internal link (link text: "toggleAudio"). Did you generate a TOC? </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert19">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>

[toggleAudio](#heading=h.j9o4eeijxm3o)
*   

<p id="gdcalert19" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: undefined internal link (link text: "toggleVideo"). Did you generate a TOC? </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert20">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>

[toggleVideo](#heading=h.bxgvn6pevtjc)
*   

<p id="gdcalert20" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: undefined internal link (link text: "toggleFilmStrip"). Did you generate a TOC? </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert21">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>

[toggleFilmStrip](#heading=h.x11jm8rf9eoh)
*   

<p id="gdcalert21" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: undefined internal link (link text: "toggleChat"). Did you generate a TOC? </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert22">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>

[toggleChat](#heading=h.j73i9piiyq47)
*   

<p id="gdcalert22" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: undefined internal link (link text: "toggleShareScreen"). Did you generate a TOC? </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert23">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>

[toggleShareScreen](#heading=h.hn33scizhda8)
*   

<p id="gdcalert23" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: undefined internal link (link text: "toggleTileView"). Did you generate a TOC? </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert24">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>

[toggleTileView](#heading=h.px6yjhwvf6s8)
*   

<p id="gdcalert24" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: undefined internal link (link text: "Hangup"). Did you generate a TOC? </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert25">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>

[Hangup](#heading=h.ndti76mbzbsh)
*   

<p id="gdcalert25" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: undefined internal link (link text: "Email"). Did you generate a TOC? </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert26">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>

[Email](#heading=h.9imt5djedwmd)
*   

<p id="gdcalert26" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: undefined internal link (link text: "avatarUrl"). Did you generate a TOC? </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert27">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>

[avatarUrl](#heading=h.ghllidq56obx)
*   

<p id="gdcalert27" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: undefined internal link (link text: "sendEndpointTextMessage"). Did you generate a TOC? </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert28">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>

[sendEndpointTextMessage](#heading=h.4lydv1fyhti4)
*   

<p id="gdcalert28" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: undefined internal link (link text: "setLargeVideoParticipant"). Did you generate a TOC? </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert29">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>

[setLargeVideoParticipant](#heading=h.w11uzr4o1i8o)
*   

<p id="gdcalert29" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: undefined internal link (link text: "setVideoQuality"). Did you generate a TOC? </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert30">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>

[setVideoQuality](#heading=h.1cs7hvq9w42x)
*   

<p id="gdcalert30" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: undefined internal link (link text: "muteEveryone"). Did you generate a TOC? </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert31">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>

[muteEveryone](#heading=h.ma0ou8u5s6f)
*   

<p id="gdcalert31" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: undefined internal link (link text: "startRecording"). Did you generate a TOC? </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert32">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>

[startRecording](#heading=h.euopfw1whstk)
*   

<p id="gdcalert32" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: undefined internal link (link text: "stopRecording"). Did you generate a TOC? </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert33">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>

[stopRecording](#heading=h.7cyv29pp2wap)
*   

<p id="gdcalert33" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: undefined internal link (link text: "Multiple Command Execution"). Did you generate a TOC? </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert34">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>

[Multiple Command Execution](#heading=h.rtr1nf9bidiy)


## 4.1 displayName

The **<code>displayName</code></strong> command sets the display name for the local participant. It requires the new display name to be set.


```
api.executeCommand('displayName', 'New Nickname');
```



## 4.2 password

The **<code>password</code></strong> command sets the password for the video meeting room.


```
// set new password for channel
api.addEventListener('participantRoleChanged', function(event) {
    if (event.role === "moderator") {
        api.executeCommand('password', 'The Password');
    }
});
// join a protected channel
api.on('passwordRequired', function ()
{
    api.executeCommand('password', 'The Password');
});
```



## 4.3 toggleLobby

The **<code>toggleLobby</code></strong> command toggles the lobby mode either on or off. It requires the desired state of lobby mode as the argument.


```
api.addEventListener('participantRoleChanged', function (event) {
    if(event.role === 'moderator') {
        api.executeCommand('toggleLobby', true);
    }
});
```



## 4.4 sendTones

The **<code>sendTones</code></strong> command enables you to play touch tones during a meeting.


```
api.executeCommand('sendTones', {
    tones: string, // The dial pad touch tones to play. For example, '12345#'.
    duration: number, // Optional. The number of milliseconds each tone should play. The default is 200.
    pause: number // Optional. The number of milliseconds between each tone. The default is 200.
});
```



## 4.5 subject

The **<code>subject</code></strong> command sets the conference subject. You use the subject as the command argument.


```
api.executeCommand('subject', 'New Conference Subject');
```



## 4.6 toggleAudio

The **<code>toggleAudio</code></strong> command mutes and unmutes the audio for local participants. No arguments are required.


```
api.executeCommand('toggleAudio');
```



## 4.7 toggleVideo

The **<code>toggleVideo</code></strong> command mutes or unmutes the video for the local participant. No arguments are required.


```
api.executeCommand('toggleVideo');
```



## 4.8 toggleFilmStrip

The **<code>toggleFilmStrip</code></strong> command either hides or shows your filmstrip. No arguments are required.


```
api.executeCommand('toggleFilmStrip');
```



## 4.9 toggleChat

The **<code>toggleChat</code></strong> command either hides or shows the chat. No arguments are required.


```
api.executeCommand('toggleChat');
```



## 4.10 toggleShareScreen

The **<code>toggleShareScreen</code></strong> command starts and stops screen sharing. No arguments are required.


```
api.executeCommand('toggleShareScreen');
```



## 4.11 toggleTileView

The **<code>toggleTileView</code></strong> command enables you to enter or exit the tile view layout mode. No arguments are required.


```
api.executeCommand('toggleTileView');
```



## 4.12 hangup

The **<code>hangup</code></strong> command disconnects and hang ups the call. No arguments are required.


```
api.executeCommand('hangup');
```



## 4.13 email

The **<code>email</code></strong> command changes the local email address. This command requires the new email address to be set as the argument.


```
api.executeCommand('email', 'example@example.com');
```



## 4.14 avatarUrl

The **<code>avatarUrl</code></strong> command changes the local avatar URL. This command requires the new avatar URL to be set as the argument.


```
api.executeCommand('avatarUrl', 'https://avatars0.githubusercontent.com/u/3671647');
```



## 4.15 sendEndpointTextMessage

The **<code>sendEndpointTextMessage</code></strong> sends a text message to another participant through your data channels.


```
api.executeCommand('sendEndpointTextMessage', 'receiverParticipantId', 'text');
```



## 4.16 setLargeVideoParticipant

The **<code>setLargeVideoParticipant</code></strong> displays the given participant on the large video. The participant with the participant id (Jid) if specified will be displayed on the large video. If no argument is passed, the participant to be displayed is selected based on the dominant/pinned speaker settings.


```
api.executeCommand('setLargeVideoParticipant', 'abcd1234');
```



## 4.17 setVideoQuality

The **<code>setVideoQuality</code></strong> command sets send and receive video resolution. This command requires the resolution height as the argument.


```
api.executeCommand('setVideoQuality', 720);
```



## 4.18 muteEveryone

The **<code>muteEveryone</code></strong> command enables the moderator to mute all the meeting participants.


```
api.executeCommand('muteEveryone');
```



## 4.19 startRecording 

The **<code>startRecording</code></strong> command starts a file recording or streaming depending on the passed parameters. For example:



*   **YouTube** streams - recording mode should be stream and **<code>youtubeStreamKey </code></strong>must be provided. The <strong><code>youtubeBroadcastID</code></strong> is optional.
*   Dropbox recordings, recording mode should be file and a dropbox oauth2 token must be provided. Also dropbox saving should be enabled on the used Jitsi 8x8 meet deploy config.
*   File recording, recording mode should be file and optionally shouldShare could be passed on. No other params should be passed.


```
api.executeCommand('startRecording', {
    mode: string //recording mode, either `file` or `stream`.
    dropboxToken: string, //dropbox oauth2 token.
    shouldShare: boolean, //whether the recording should be shared with the participants or not. Only applies to certain Jitsi 8x8 meet deploys.
    youtubeStreamKey: string, //the youtube stream key.
    youtubeBroadcastID: string //the youtube broacast ID.
});
```



## 4.20 stopRecording

The **<code>stopRecording</code></strong> command stops an ongoing recording, stream or file.


```
api.executeCommand('stopRecording', 
    mode: string //recording mode to stop, `stream` or `file`
);
```



## 4.21 Multiple Command Execution

You can also execute multiple commands using the **<code>executeCommands</code></strong> method:


```
api.executeCommands(commands);
```


The **<code>commands</code></strong> parameter is an object with the names of the commands as keys and the arguments for the commands as values:


```
api.executeCommands({
    displayName: [ 'nickname' ],
    toggleAudio: []
});

