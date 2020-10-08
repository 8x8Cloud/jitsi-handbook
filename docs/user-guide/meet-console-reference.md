# 1 Overview

Jitsi as a Service (JaaS) enables you to develop and integrate Jitsi Meetings functionality into your web applications. The JaaS integration incorporates the extensive functionality of the 8x8 Jitsi Platform. By using JaaS your enterprise can host meetings that leverage the distributed Jitsi meetings infrastructure from datacenters around the world.

As shown in the following diagram, the JaaS Meet Console enables you to configure and incorporate the powerful [iFrame](https://jitsi.github.io/handbook/docs/dev-guide/dev-guide-iframe) and [Mobile SDK](https://jitsi.github.io/handbook/docs/dev-guide/dev-guide-mobile) Jitsi components to further facilitate and enhance your business operations:


![alt_text](images/image1.png "image_tooltip")


Your JaaS account provides an isolated context referred to as a tenant.  A tenant is a group of users who share a common access with specific privileges. This is where your meetings will take place and where you will create your meeting room. The tenant defines the root level for the meeting room namespaces you can create and use. All JaaS Meeting rooms are prefixed with the tenant ID (

<p id="gdcalert2" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: undefined internal link (link text: "Section 3.2, “Integrate JaaS using the Jitsi iFrame API"). Did you generate a TOC? </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert3">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>

[Section 3.2, “Integrate JaaS using the Jitsi iFrame API](#heading=h.1i434wla4wfh)”).

Contact your 8x8 representative at [vpaas@8x8.com](mailto:vpaas@8x8.com) to obtain a JaaS account.


# 2 The Meet Console

The Meet Console facilitates management of your JaaS account. It  provides the tools that enable you to manage and configure key details associated with your JaaS integrations. It consists of the following JaaS management pages:



*   [API keys](#api-keys)
*   [Webhooks](#webhooks)
*   [Branding]()
*   [Iframe Integration]()
*   [Analytics]()
*   [Team management]()


## 2.1 API keys

The Meet Console API Keys page enables you to define and manage the authentication keys for your meeting participants. You add the API keys used to authenticate the Jitsi [JSON Web Tokens](https://tools.ietf.org/html/rfc7519) (JWTs) created by your integration for each individual user endpoint.

To allow participation in your tenant meetings, you must generate a JWT for each participant and sign it with the Private Key.


![alt_text](images/image2.png "image_tooltip")


### 2.1.2 Generating the JaaS API key

A JaaS API key is a Public Key consisting of a 4096 bits RSA SSH Key Pair in PEM format. You can generate the Key Pair using the Web**<code> ssh-keygen</code></strong> and specify <strong><code>rsa</code></strong> as algorithm <strong><code>4096</code></strong> as size and <strong><code>PEM</code></strong> as format. 

For example:

```
> ssh-keygen -t rsa -b 4096 -m PEM -f <filename>

```

The following shows an example output after running the keygen command:

```

dev$ssh-keygen -t rsa -b 4096 -m PEM -f jaasauth.key
Generating public/private rsa key pair.
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in jaasauth.key.
Your public key has been saved in jaasauth.key.pub.
The key fingerprint is:
SHA256:aHkvV50wzp6hJ7DB/BTiuzGbh73x3JAnSLhGuxRsyxw dev@dev-machine
The key's randomart image is:
+---[RSA 4096]----+
|                 |
|                 |
|        . . o    |
|       B o + + . |
|      + E o = o  |
|     . * / = +   |
|        #oO B .  |
|       o.Xo* =   |
|        =...o .  |
+----[SHA256]-----+

```

You can save the generated Key Pair using the **<code>openssl </code></strong>command. 

For example: 


```
> openssl rsa -in <filename> -pubout -outform PEM -out <filename>.pub
```


Another example of the **`openssl`** command is as follows::


```
dev$openssl rsa -in jaasauth.key -pubout -outform PEM -out jaasauth.key.pub
writing RSA key
```


The following is an example of a saved JaaS API (Public) key file:


```
dev$cat jaasauth.key.pub
-----BEGIN PUBLIC KEY-----
MIICIjANBgkqhkiG9w0BAQEFAAOCAg8AMIICCgKCAgEA1DJxsTKt2lBSl0n4WaqO
xA/lZ+5PeaLMnSPBLku8ZlVjDaU5fUH8oTkoEZovhJGBcR+uWUp8XMfE3l0LWat2
2UfdM4WMm2F8wLKAay/NGrLNQFfcJCn6dEimASVPKKe7wRX1/mcDeb5mAXvRF4u2
iZ3BYw7lLPT6lxtdAwWP+s7sQfsK/7ADoz46o0MZiRlzRDnYtclt2pU4Y6z+fXyF
tMs4bIIWzLxe81rucXLFXi2FVZu4fngTEV91NS4Y+PiQ4sSLPnEJh5TDZLbq6tLS
7qOrnp5tbUS1bPfmRIL38viC+m9wOzPM2Kt8+NEj/HtKg4UlJ4cMS2OB+jGYv//H
zZXfPbzSzn6IEs6C6AH+EEqj0tUTX6wlhi5x6wyaEok20DHq/BgvD4vOwa9eBlBn
I+kw0NT4mjDmv9I2Rc7QbXsrOkPkCNGKsgXdGeJKO2UNNpetEBV5LTYiTjO3sQH7
7WH92ujOg0TouTYvjeuTjkEn8GqWUH6l6UrYw0kbno/WBQGcBFpe4ygmSgznLhGq
3yAuDXoXu7hBHNXTOdyis0aKp+2KOGvoV21gYrU4Z8Uy4JjZNZ1oSwn0Z6RO69tZ
4ni9b++cjjTx0Py0I/U0XvNSneJyXpdjHpOnVQPsLQOVbfBHdSHgNbVaT+18vSeM
9VI7LlqQd0SpRw0S0D9/qgcCAwEAAQ==
    -----END PUBLIC KEY-----
```


The Private Key is used in generating the Jitsi JWT.


### 2.1.3 Uploading an API Key

Once an RSA key is generated and in the correct format, your JaaS API key can be dragged and dropped into the **Add API key** field and then added by clicking the **Add API Key** button. 


![alt_text](images/image3.png "image_tooltip")


The API Key ID (**kid**) is composed of the tenant’s unique identifier and is used in the JWT header. The tenant unique identifier is prefixed as **`vpaas-magic-cookie-`** and is used as the value of the sub field in the JWT. 

The following screenshot shows a kid example:


![alt_text](images/image4.png "image_tooltip")


Refer to to [section 3.1, "The Jitsi JWT"]() for more details.


## 2.2 Webhooks

The Meet Console Webhooks page enables you to define **<code>POST HTTP</code></strong> JaaS platform requests. These requests can be triggered by selected and defined in-meeting or post-meeting events that are generated by your tenant.


### 2.2.1 Defining a Webhook endpoint

You can define an endpoint by clicking **Add endpoint** and specifying a target URL. After you have added the webhook, you can select one or more events that will trigger requests to the defined endpoint. The added endpoints are listed by URL and list of events. 

The following screen shot shows a **PARTICIPANT_JOINED** action event configuration with an endpoint URL of **`https://postb.in/b/1600147371176-9105843019206:`**


![alt_text](images/image5.png "image_tooltip")


You can later edit the current endpoint by selecting it from the list, or add more endpoints for other significant meeting events.

The following screen shot shows the completed webhook configuration:


![alt_text](images/image6.png "image_tooltip")


## Branding

The Meet Console Branding page enables you to brand the meetings run on your tenant with your own:

*   Custom meeting URL
*   Enterprise Logo or symbol
*   Company website link
*   UI background image

Using this functionality enables you to share the URL meeting location with select participants.You can also uniquely identify your tenant so that meetings display your enterprise’s brand identification and selected background. Using a clickable link on your logo that leads to your company website also further facilitates and enhances your brand identity. 

The branding can be viewed by all meeting participants and is visible in recordings and live streaming sessions from your tenant.


![alt_text](images/image7.png "image_tooltip")


## 2.4 Iframe Integration (In Progress)

This section is continuously evolving to describe JaaS and to document its integration.>

The Meet Console IFrame integration page enables you to ……..


![alt_text](images/image8.png "image_tooltip")


## 2.5 Analytics (beta)

**Note**: The Analytics page is in beta stage.

Analytics provides a helpful tool that analyzes the quality of meetings that have taken place in your tenant. You use the Analytics tool to develop insights and determine the quality of your meetings.

You can get a dashboard view of:

*   **Total conferences** - either ongoing or terminated
*   **All participants joined** - either successful or dropped conferences
*   **Participants unable to joi**n - either partially failed or totally failed conferences

The view includes the tenant ID and the unique Conference ID (Conf ID).

For more information on Analytics refer to:  

*   [Access analytics for meetings as an administrator](https://docs.8x8.com/8x8WebHelp/video-meetings/Content/meeting-analytics.htm) in the [8x8 Meet User Help](https://docs.8x8.com/8x8WebHelp/video-meetings/Content/workd/about-meetings.htm)
*   [Metric definitions](https://callstats-io.zendesk.com/hc/en-us/sections/202141229-Metric-definitions) on the [FAQ-callstats.io](https://callstats-io.zendesk.com/hc/en-us/categories/200708101-FAQ) page


![alt_text](images/image9.png "image_tooltip")


![alt_text](images/image10.png "image_tooltip")


## 2.6 Team management

Access to and use of the Meet Console can be shared across your JaaS team via the Team management page.

![alt_text](images/image11.png "image_tooltip")


![alt_text](images/image12.png "image_tooltip")



# 3 Integration

The following sections describe how to integrate JaaS into your enterprise.


## 3.1 The Jitsi JWT

The header of the JWT contains 3 claims:



*   **<code>alg</code></strong>: The algorithm used for signing the JWT
*   <strong><code>kid</code></strong>: The <strong>kid</strong> listed for the uploaded API Key (

<p id="gdcalert22" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: undefined internal link (link text: "see Section 2.1.2, "Generating the API key""). Did you generate a TOC? </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert23">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>

[see Section 2.1.2, "Generating the API key"](#heading=h.wvqutnvxtxta))
*   <strong><code>typ</code></strong>: The type which equals the JWT

For example: 


```
    {
      "alg": "RS256",
      "kid": "vpaas-magic-cookie-1fc542a3e4414a44b2611668195e2bfe/4f4910",
      "typ": "JWT"
    }
```


The following claims are expected in the JWT body:



*   **<code>aud: "jitsi"</code></strong> - This value is hardcoded in the body
*   <strong><code>context</code></strong>: 
*   <strong><code>user</code></strong>:
*   <strong><code>id:</code></strong> The unique identifier for the user
*   <strong><code>name</code></strong>: The user name
*   <strong><code>*avatar</code></strong>: The publicly available URL that points to the user avatar picture 
*   <strong><code>*email</code></strong>: The user email
*   <strong><code>*moderator</code></strong>: 
    *   If the user is the moderator set to <strong><code>"true"</code></strong>
    *   If this value is missing or is set to <strong><code>"false"</code></strong> the user will not have moderator permissions.
*   <strong><code>features</code></strong>: The key value map for the features that are available to the user; key represents the feature name and the value should be true / false 
*   Supported keys: “livestreaming”, “recording”
*   <strong><code>exp:</code></strong> The time after which the JWT expires
*   <strong><code>iss: "chat"</code></strong> - This is a hardcoded value 
*   <strong><code>nbf</code></strong>: The time before which the JWT must not be accepted for processing
*   <strong><code>room:</code></strong> The meeting room value for which the token is issued; this field supports also wildcard (“*”) if the token is issued for all rooms
*   <strong><code>sub:</code></strong> The tenant unique identifier (see section 2.2.2)

For example:


```
    {
      "aud": "jitsi",
      "context": {
        "user": {
          "id": "0f8b7760-c17f-4a12-b134-c6ac37167144",
          "name": "John Doe",
          "avatar": "https://link.to/user/avatar/picture",
          "email": "john.doe@company.com",
          "moderator": "true"
        },
        "features": {
          "livestreaming": "true",
          "recording": "true"
        }
      },
      "exp": 1696284052,
      "iss": "chat",
      "nbf": 1596197652,
      "room": "*",
      "sub": "vpaas-magic-cookie-1fc542a3e4414a44b2611668195e2bfe"
    }
```


For the above examples, a JWT example can be found on the **<code>[jwt.io](https://jwt.io/)</code></strong> Auth0 JWT site and accessing the [debugger](https://jwt.io/#debugger-io?token=eyJhbGciOiJSUzI1NiIsImtpZCI6InZwYWFzLW1hZ2ljLWNvb2tpZS0xZmM1NDJhM2U0NDE0YTQ0YjI2MTE2NjgxOTVlMmJmZS80ZjQ5MTAiLCJ0eXAiOiJKV1QifQ.eyJhdWQiOiJqaXRzaSIsImNvbnRleHQiOnsidXNlciI6eyJpZCI6IjBmOGI3NzYwLWMxN2YtNGExMi1iMTM0LWM2YWMzNzE2NzE0NCIsIm5hbWUiOiJKb2huIERvZSIsImF2YXRhciI6Imh0dHBzOi8vbGluay50by91c2VyL2F2YXRhci9waWN0dXJlIiwiZW1haWwiOiJqb2huLmRvZUBjb21wYW55LmNvbSIsIm1vZGVyYXRvciI6InRydWUifSwiZmVhdHVyZXMiOnsibGl2ZXN0cmVhbWluZyI6InRydWUiLCJyZWNvcmRpbmciOiJ0cnVlIn19LCJleHAiOjE2OTYyODQwNTIsImlzcyI6ImNoYXQiLCJuYmYiOjE1OTYxOTc2NTIsInJvb20iOiIqIiwic3ViIjoidnBhYXMtbWFnaWMtY29va2llLTFmYzU0MmEzZTQ0MTRhNDRiMjYxMTY2ODE5NWUyYmZlIn0.R2Xl8vGijJ2ZIzJCSTnsneXWbx5SpN2NxFQjOdD-uhtlsZFcZCkSuHUFdY9wgsx-Qgsdvqbwlz2sm67GVlF4rSdCHfuGtlCQlSsQbNDO8u-4X9ZPGTmQdomFEb_F-z4C1SI6Rg6kDyC5aLdmRlImJvMp4HF2njq8ionYnKIjSRKu9VP2WiWgTtLReit8CA2DFUyR44e_iZmZd-_aldw_fV1b7OZFX-PLydfpwpyqfLwpAijKGRZC7G4ru0r7EjBgSPdGPtFXS-rzh1oio4LMqUOTQ-cuEPTNpcjVb_DkJWIvIYDT2vee_SZd2RWAz1FbRXGnobPhbvET9-Nj_yQC9k3yH2qytiSe0WtK0g0VPyxvtxpKElx7sOtGKtb6v6AKDtHmJ5EyCvyRVkSNK67N3l5MOn9--DIuTPhjDTnvN-GfhLf8CNpAlLbygNt_RK4p3eQtFsTZNRORs3xgu1_DrZ65TKi-bqWh3wXgZhl8xWNGjQSFU0cXEthWhjHtr19uFGy0AqcM31hRa5P21cZj6Spd6qZ8yk7FvVqOeOhEygO-X7d52xItmRLtH7KpVTnCnWN0klYdRHlCCeM_rsyj-VWMGPBrJCsJ4tfUYnwlm8re0QQMvB6-auGK9pvvJlmz3lnlvfvzdUyIwDH9JIPdtZAjygO0zu1ydUk17ZgYJuk&publicKey=-----BEGIN%20PUBLIC%20KEY-----%0AMIICIjANBgkqhkiG9w0BAQEFAAOCAg8AMIICCgKCAgEA1DJxsTKt2lBSl0n4WaqO%0AxA%2FlZ%2B5PeaLMnSPBLku8ZlVjDaU5fUH8oTkoEZovhJGBcR%2BuWUp8XMfE3l0LWat2%0A2UfdM4WMm2F8wLKAay%2FNGrLNQFfcJCn6dEimASVPKKe7wRX1%2FmcDeb5mAXvRF4u2%0AiZ3BYw7lLPT6lxtdAwWP%2Bs7sQfsK%2F7ADoz46o0MZiRlzRDnYtclt2pU4Y6z%2BfXyF%0AtMs4bIIWzLxe81rucXLFXi2FVZu4fngTEV91NS4Y%2BPiQ4sSLPnEJh5TDZLbq6tLS%0A7qOrnp5tbUS1bPfmRIL38viC%2Bm9wOzPM2Kt8%2BNEj%2FHtKg4UlJ4cMS2OB%2BjGYv%2F%2FH%0AzZXfPbzSzn6IEs6C6AH%2BEEqj0tUTX6wlhi5x6wyaEok20DHq%2FBgvD4vOwa9eBlBn%0AI%2Bkw0NT4mjDmv9I2Rc7QbXsrOkPkCNGKsgXdGeJKO2UNNpetEBV5LTYiTjO3sQH7%0A7WH92ujOg0TouTYvjeuTjkEn8GqWUH6l6UrYw0kbno%2FWBQGcBFpe4ygmSgznLhGq%0A3yAuDXoXu7hBHNXTOdyis0aKp%2B2KOGvoV21gYrU4Z8Uy4JjZNZ1oSwn0Z6RO69tZ%0A4ni9b%2B%2BcjjTx0Py0I%2FU0XvNSneJyXpdjHpOnVQPsLQOVbfBHdSHgNbVaT%2B18vSeM%0A9VI7LlqQd0SpRw0S0D9%2FqgcCAwEAAQ%3D%3D%0A-----END%20PUBLIC%20KEY-----) as shown in the following screen shot:



<p id="gdcalert23" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image13.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert24">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image13.png "image_tooltip")



## 3.2 Integrate JaaS using the Jitsi iFrame API

To integrate JaaS using the IFrame API, refer to the [IFrame API · Jitsi Meet Handbook](https://jitsi.github.io/handbook/docs/dev-guide/dev-guide-iframe) for the complete procedure.

You can adapt the script source to **<code>8x8.vc</code></strong> by updating the script domain as follows:


```
<script src="https://8x8.vc/libs/external_api.min.js"></script>
```


The rooms must be defined in the namespace of your tenant in the form of <code>&lt;<strong>tenant</strong>>/&lt;<strong>roomname</strong>>.</code>

The **roomname** should be a single-level (no slash) string composed of legitimate, safe URL characters.

An example valid room value for the tenant 

**`vpaas-magic-cookie-1fc542a3e4414a44b2611668195e2bfe`**` 

is:


```
 roomName: "vpaas-magic-cookie-1fc542a3e4414a44b2611668195e2bfe/adevmeeting"
```


The following is an IFrame example of successfully joining a meeting:



<p id="gdcalert24" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image14.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert25">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image14.png "image_tooltip")



# 4 Mobile SDKs

JaaS features the following Mobile SDKs that you can integrate into enterprise or app:

&lt;In Progress>


# 5 Whitelisting JaaS IP ranges and domains

Customers that integrate JaaS should whitelist the IP ranges and domains listed in the following documents:



*   [Dropbox - Static IP Ranges for Jitsi Meetings.pdf](https://go.8x8.vc/ranges)
*   [X Series Technical Requirements](https://support.8x8.com/cloud-phone-service/voice/network-setup-voice/x-series-technical-requirements)  - the IPs and Domains marked for Meetings

