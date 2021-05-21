# MobileForce in SugarCRM Instance Integration Guide

## Step 1: Setup OAuth2 Keys
- Login to SugarCRM instance as an admin user
- Go to *User Icon (top right) > Admin > System > OAuth Keys*
- Click *OAuth Keys* tab on the Main Menu Navbar and in the drop down sub-menu, click on *Create OAuth Key*
- Add a new consumer key with secret and save it safely
- Make sure the OAuth type is set to OAuth2
- Send the chosen *Consumer Key* and *Consumer Secret* to MobileForce team

![Create OAuth Key in SugarCRM](/images/sugar_oauth_key_create.png)

## Step 2: Disable Client IP Change Check
- Login to SugarCRM instance as an admin user
- Go to *User Icon (top right) > Admin > System Settings* screen
- Make sure you uncheck (clear) the setting *Validate user IP Address* under *Advanced* section

## Step 3: Add a API Platform
- Login to SugarCRM instance as an admin user
- Go to *User Icon (top right) > Admin > Configure API Platforms* screen
- Add a new platform with the name *api* and *Save*

## Step 4: Only if you are on Sugar 11 or Later: Configure the Content Security Policy Settings
- Login to SugarCRM instance as an admin user
- Find out if you are on Sugar 11 as follows: Go to *User Icon (top right) > Admin > About*
- If it says sugar version:  "11.x.x" then you need to perform the next two steps.
- Go to *User Icon (top right) > Admin > Content Security Policy Settings* screen
- Set the Trusted Domain ('default-src') to take the value  '*.mobileforcesoftware.com' and *Save*

## Step 5: Install MobileForce Modules
- Download one or more of the MobileForce Module ZIP Files below to your computer
  - [*MobileForce_CPQ* - Configure, Price, Quote Module](/assets/MobileForce_CPQ.zip)
  - [*MobileForce_FSM* - Field Service Management Module](/assets/MobileForce_FSM.zip)
  - [*MobileForce_DSR* - Dynamic Scheduling & Route Optimization Module](/assets/MobileForce_DSR.zip)
- Login to SugarCRM instance as an admin user
- Go to *User Icon > Admin > Module Loader*
- Upload each of the Module ZIP File you downloaded, one by one
- Click *Install* and *Commit* to install each of the uploaded Modules

![Module Loader in SugarCRM](/images/sugar_module_loader.png)

## Step 5: Install Custom Buttons UI Module
- Download [*wRecordButtons* Module ZIP File](/assets/wRecordButtons_v5.22.zip) to your computer
- Login to SugarCRM instance as an admin user
- Go to *User Icon > Admin > Module Loader*
- Upload the Module ZIP File you downloaded to install the Module

![Module Loader in SugarCRM](/images/sugar_module_loader.png)

## Step 6: Add Custom Buttons to Opportunity and Case Record Views: Deep Links to MobileForce Modules
- Login to SugarCRM instance as an admin user
- Go to *User Icon > Admin > Studio > Opportunities Module > Fields*
- Add a Custom Field of type wRecord Buttons
![Custom Button Field in Opportunities Module in SugarCRM](/images/sugar_custom_button_field.png)

- Configure the wRecord Custom Button as shown in the screenshot below
![Custom Button Field Configuration in SugarCRM](/images/sugar_configure_custom_button.png)
- For the Base URL textbox field in the custom button configuration, please copy and paste the following URL

```
https://<instance_name>/#mfcpq_MobileForce_CPQ/{id}/{name}/{account_id}/{account_name}
```

- Replace <instance_name> in the above URL with your full instance domain name (ex: sg-mobileforce.demo.sugarcrm.com)
- Click *Save* on the Configuration screen. Then click on *Save* in the Edit Field screen
- Next, Go to *User Icon > Admin > Studio > Cases Module > Fields*
- Add a Custom Field of type wRecord Buttons
- Configure the wRecord Custom Button as shown in the screenshot above, except name the button as *+ Service Task*
- For the Base URL textbox field in the custom button configuration, please copy and paste the following URL

```
https://<instance_name>/#mffsm_MobileForce_FSM/{id}/{name}/{account_id}/{account_name}
```

- Replace <instance_name> in the above URL with your full instance domain name (ex: sg-mobileforce.demo.sugarcrm.com)
- Click *Save* on the Configuration screen. Then click on *Save* in the Edit Field screen
- Finally, Go back to *User Icon > Admin > Studio > Cases Module > Fields*
- Add a Custom Field of type wRecord Buttons
- Configure the wRecord Custom Button as shown in the screenshot above, except name the button as *+ Sales Task*
- For the Base URL textbox field in the custom button configuration, please copy and paste the following URL

```
https://<instance_name>/#mfdsr_MobileForce_DSR/{id}/{name}/{account_id}/{account_name}
```

- Replace <instance_name> in the above URL with your full instance domain name (ex: sg-mobileforce.demo.sugarcrm.com)
- Click *Save* on the Configuration screen. Then click on *Save* in the Edit Field screen

## Step 7: Rebuild and Update Your SugarCRM Instance
- Login to SugarCRM instance as an admin user
- Go to *User Icon > Admin > Repair > Quick Repair and Rebuild*
- Please wait. This will take 15-30 seconds to rebuild the system and will print out the log.
- This will deploy the changes we made in the instance

![Quick Build and Repair in SugarCRM](/images/sugar_quick_repair_rebuild.png)

## Step 8: Login and Use Your SugarCRM Instance
- Login to SugarCRM instance as a regular user
- **CPQ**, **Field Service** and **Scheduler** Module names with no sub-menus will be shown in Mega Menu Navigation Bar 
- When user clicks on the **CPQ** or **Field Service** or **Scheduler** in Navigation Bar it will load the iframe to MobileForce
- **CPQ** list of existing prosposals/quotes screen is shown. It may be empty on first login.
- Click *Add* button on the bottom toolbar to create a new Quote/Proposal
- Alternatively, go to any open *Opportunity* record in SugarCRM
- Click on **+ CPQ** custom button at the top to create a new Quote/Proposal for that *Opportunity*

![Create New Quote/Proposal in SugarCRM](/images/sugar_cpq_launch_points.png)

## Step 9: Move Up the MobileForce Module Tabs on the Main Menu for the Logged-in User
- Login to SugarCRM instance as any test user
- Go to *User Icon > Profile*
- Click on *Edit* button
- Go to **Advanced** tab
- Under **Layout Options**, move the **CPQ**, **Field Service** and/or **Scheduler** modules Up in the list of Display Modules
- Click *Save* button to save preferences

![Display Modules in User Preferences in SugarCRM](/images/sugar_display_modules_user.png)

