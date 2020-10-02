---
id: iframe-quick-start
title: API Quick Start
---

This quick start guide enables you to quickly set up and use the Jitsi API. 

For comprehensive Jitsi 8x8 API usage information refer to the ***Jitsi API Guide***. 

# Overview

Embedding the Jitsi 8x8 API into your site or app enables you to host and provide secure video meetings with your colleagues or stakeholders. The full compliment of comprehensive meeting features in the Jitsi implementation leads to successful meeting engagement and future positive interactions.

Your Jitsi 8x8 meetings can be hosted and attended using any device while keeping your  data and privacy protected. You can reach your colleagues and stakeholders anywhere in the world eliminating the need for any travel or inconvenience.

# Create 8x8 Account


# Installation

To enable Jitsi 8x8 meetings in your site or app you must use embed the Jitsi 8x8 API into your site or app’s HTML page using the following script:

```
<script src='https://meet.jit.si/external_api.js'></script>
...
const domain = 'meet.jit.si';
const options = {
    roomName: 'PickAnAppropriateMeetingNameHere',
    width: 700,
    height: 700,
    parentNode: document.querySelector('#meet')
};
const api = new JitsiMeetExternalAPI(domain, options);
```
In the script you can change or update the following parameters to accommodate and further personalize your Jitsi 8x8 implementation :

*   roomName -
*   Width -
*   Height -
*   parentNode -

**Note:** The **<code>meet.jit.si</code></strong> API is free for your use. As a courtesy we request that you not remove the Jitsi 8x8 logo or the pages that appear after hanging up a call. If you require further assistance regarding your brand logo, the removal of pop-up ads, or any other details regarding implementation of the Jitsi 8x8 API contact the [Jitsi 8x8 team](mailto:vpaas@8x8.com).

# Creating the meeting name

You can create your own unique and identifiable meeting names when using the **<code>meet.jit.si</code></strong> implementation.

For example:


```
meet.jit.si/new-product-launch
meet.jit.si/web-analytics-discusssion
meet.jit.si/4th-qtr-results
```


You can also put it behind a tenant name. For example:


```
meet.jit.si/my_company/your_unique_meeting_id
```


For example:


```
8×8.vc/my_company/your_unique_meeting_id
```



# Displaying dial-in information

Here’s how you construct showing dial-in information statelessly for the meeting example above:

**`your_unique_meeting_id`**

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



# Adding a one-tap number

You can add a one-tap number to perform API calls without any authentication or authorization requirement.

For example, consider the scenario in which you want to add a one tap dial-in number for every event (e.g., +1 209-844-4600,,1366520583#)

In order to enable this feature you need to run the following Jitsi 8x8 API call first:


```
https://api.jitsi.net/phoneNumberList?conference=SuccessivePortsCompeteMeanwhile@conference.meet.jit.si
```


This call returns all the phone numbers that can be used to join the subject meeting. The first number displayed in the call return is the one detected as closest to the endpoint that performed the call. We run this on in the browser so that we can get a number that matches the location of the user.

The second call you run generates your pin code for the meeting:


```
https://api.jitsi.net/conferenceMapper?conference=some-id-you-like@conference.mycompany.meet.jit.si
```


If you are interested in our professional video API offering, please contact the 8x8 Jitsi team at vpaas@8×8.com

