## How to get up and running with Amazon Voice Synthesis (AVS) services

> **For easier steps, please keep the browser open at each step, and copy/paste the links from step 2**

***

## 1. Register an account
You will need to register an account at Amazon Developer, [click here to get started](https://www.amazon.com/ap/register?openid.pape.max_auth_age=1&openid.return_to=https%3A%2F%2Fdeveloper.amazon.com%2Fap_login.html&prevRID=58N9KKJN1AEBPGJDP3K1&openid.identity=http%3A%2F%2Fspecs.openid.net%2Fauth%2F2.0%2Fidentifier_select&openid.assoc_handle=mas_dev_portal&openid.mode=checkid_setup&prepopulatedLoginId=&failedSignInCount=0&language=en_US&openid.claimed_id=http%3A%2F%2Fspecs.openid.net%2Fauth%2F2.0%2Fidentifier_select&pageId=amzn_developer_portal&openid.ns=http%3A%2F%2Fspecs.openid.net%2Fauth%2F2.0).

*Register Account*
<p align="left">
   <img src="https://github.com/TheStigh/MMM-Alexa/blob/master/imgs/1_amazon_create_account.png" height="300">
<p>

*Click 'Login with Amazon'*
<p align="left">
   <img src="https://github.com/TheStigh/MMM-Alexa/blob/master/imgs/2_amazon_logged_in.png" height="300">
<p>

*Click 'Create a New Login Profile'*
<p align="left">
   <img src="https://github.com/TheStigh/MMM-Alexa/blob/master/imgs/3_amazon_create_security_profile.png" height="300">
<p>

*Fill in the required information for your Security Profile*
<p align="left">
   <img src="https://github.com/TheStigh/MMM-Alexa/blob/master/imgs/4_amazon_creating_profile.png" height="300">
<p>

*Here you are finished creating the Security Profile*
<p align="left">
   <img src="https://github.com/TheStigh/MMM-Alexa/blob/master/imgs/5_amazon_profile_created.png" height="300">
<p>

***

## 2. Time to create your Alexa product
Now, you will need to copy and paste this link into your browser:

https://developer.amazon.com/alexa/console/avs/products

On this page, click **CREATE PRODUCT**

On following page; fill inn following information:

> Please note more fields than you initially see will pop up as you fill in your answers.

***During this process, make a note of following as you will need some in step 3, and all in config.js***
```
avsDeviceId = Product ID
avsClientId = Client ID
avsClientSecret = Client Secret
avsInitialCode= Initial Code
```

| Argument |  | Description |
|---|---|---|
| Product name |  | Fill in a name for your device/product, like *My MagicMirror Project* |
| Product ID |  | Fill in your unique product ID, like *MagicMirror* |
| Please select your product type |  | Select **Application with Alexa built-in** |
| Product category |  | Select what ever you want, like *Smart Home* |
| Brief product description |  | Give it a description, like *This is my project* |
| How will end users interact with your product? |  | Select **Hands-Free** |
| Do you intend to distribute this product commercially? |  | Select **No** |
| Is this a children’s product or is it otherwise directed to children younger than 13 years old? |  | Select **No** |

On next page, use the dropdown list and select the Security Profile you created earlier
Then the page is extended, and you will need to add two more lines to it to get finished:

```
Allowed origins - Type in **https://localhost:9745** and click ADD
Allowed return URLs - Type in **https://thestigh.github.io/MMM-Alexa/** and click ADD
```

Tick the checkbox for accepting the ***Agreement***, click **FINISH** and you have successfully set up your product!

***

## 3. Create your 'avsInitialCode'

Go to **[following page](https://thestigh.github.io/MMM-Alexa/)** and copy/paste **Client ID & Product ID** recorded during step 2.

*Fill in your details according to this example and click 'Request Code'*
<p align="left">
   <img src="https://github.com/TheStigh/MMM-Alexa/blob/master/imgs/7_amazon_create_avs.png" height="300">
<p>

you will most likely get prompted to login in.
After this step, you should be asked to ALLOW access, which you obviously accept:
<p align="left">
   <img src="https://github.com/TheStigh/MMM-Alexa/blob/master/imgs/8_amazon_avs_grant.png" height="300">
<p>
 

At the end, you will return to the original page and have received the ***avsInitialCode***
<p align="left">
   <img src="https://github.com/TheStigh/MMM-Alexa/blob/master/imgs/9_amazon_avs_received.png" height="300">
<p>

***

# YOU ARE GOOD TO GO!
