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
- Set the Trusted Domain ('default-src') to take the value ```*.mobileforcesoftware.com``` and *Save*

## Step 5: Install MobileForce Modules
- Download one or more of the MobileForce Module ZIP Files below to your computer
  - [*MobileForce_CPQ* - Configure, Price, Quote Module](https://apps.mobileforcesoftware.com/sugarcrm/modules/1.0.10/MobileForce_CPQ.zip)
  - [*MobileForce_FSM* - Field Service Management Module](https://apps.mobileforcesoftware.com/sugarcrm/modules/1.0.10/MobileForce_FSM.zip)
- Login to SugarCRM instance as an admin user
- Go to *User Icon > Admin > Module Loader*
- Upload each of the Module ZIP File you downloaded, one by one
- Click *Install* and *Commit* to install each of the uploaded Modules

![Module Loader in SugarCRM](/images/sugar_module_loader.png)

## Step 6: Rebuild and Update Your SugarCRM Instance
- Login to SugarCRM instance as an admin user
- Go to *User Icon > Admin > Repair > Quick Repair and Rebuild*
- Please wait. This will take 15-30 seconds to rebuild the system and will print out the log.
- This will deploy the changes we made in the instance

![Quick Build and Repair in SugarCRM](/images/sugar_quick_repair_rebuild.png)

## Step 7: Login and Use Your SugarCRM Instance
- Login to SugarCRM instance as a regular user
- **CPQ**, **Field Service** and **Scheduler** Module names with no sub-menus will be shown in Mega Menu Navigation Bar 
- When user clicks on the **CPQ** or **Field Service** in Navigation Bar it will load the iframe to MobileForce
- **CPQ** list of existing prosposals/quotes screen is shown. It may be empty on first login.
- Click *Add* button on the bottom toolbar to create a new Quote/Proposal

![Create New Quote/Proposal in SugarCRM](/images/sugar_cpq_launch_points.png)

## Step 8: Move Up the MobileForce Module Tabs on the Main Menu for the Logged-in User
- Login to SugarCRM instance as any test user
- Go to *User Icon > Profile*
- Click on *Edit* button
- Go to **Advanced** tab
- Under **Layout Options**, move the **CPQ**, **Field Service** and/or **Scheduler** modules Up in the list of Display Modules
- Click *Save* button to save preferences

![Display Modules in User Preferences in SugarCRM](/images/sugar_display_modules_user.png)

