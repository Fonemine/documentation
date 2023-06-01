# MobileForce in SugarCRM Instance Integration Guide

This document is updated (Summer 2023) to describe three distinct actions that need to be performed in order to make Mobileforce work within your Sugar Instance. 

A**ssumptions:** This document assumes that you have a Sugar Instance with Sugar Sell (in order to use Mobileforce CPQ) and Sugar Serve (in order to use Mobileforce FSM). It also assumes you have Admin credentials for your Sugar Instance in order to complete **Action 1** below, and Admin credentials to Mobileforce in order to complete **Action 3** below.


1. **Action 1**: Install Mobileforce within your Sugar Instance: You need to be a Sugar Admin to complete the steps in this action

2. **Action 2**:  Create a Mobileforce cloud Instance for Mobileforce FSM and Mobileforce CPQ:  You will need to run a (new) Mobileforce script to create a Mobileforce cloud Instance for FSM and CPQ. This instance is different from your  Sugar Instance. Anyone can run this script, but you need to know some details (specifically admin email) about your Mobileforce Admin user/roles in order to complete this action.

3. **Action 3**: Finally  you need to make changes to your Mobileforce Instance to tie together your sugar instance with your Mobileforce Instance. You need to be a Mobileforce Solutions consultant to complete this step.


# Action 1: Install Mobileforce within your Sugar Instance (Sugar Admin Role)

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
  - [*MobileForce_CPQ* - Configure, Price, Quote Module](https://apps.mobileforcesoftware.com/sugarcrm/modules/1.0.13/MobileForce_CPQ.zip)
  - [*MobileForce_FSM* - Field Service Management Module](https://apps.mobileforcesoftware.com/sugarcrm/modules/1.0.13/MobileForce_FSM.zip)
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

# Action 2:  Create a Mobileforce Cloud Instance for Mobileforce FSM and Mobileforce CPQ (Mobileforce Business User: with Mobileforce Admin email)

Run the script https://apps.mobileforcesoftware.com/website/provision.php
This script specifically uses the information you provide for **Account Name, Work email , and  CRM**, to automatically create a Mobileforce Cloud Instance that is specifically customized for you and your CRM.


# Action 3:  Configure your Mobileforce Cloud Instance to integrate with your Sugar Instance (Mobileforce Solution Consultant).

Specify the following Prop keys in your Mobileforce Cloud Instance ADL by using your Sugar Instance URL

Assuming your sugar instance URL is abstracted as **sugar-instance-url**
Assuming your sugar instance has an admin user **sguser** whose password is **sgpwd**
Assuming your OAuth client id key in **Action 1, Step 1** is **ConsumerKey**
Assuming your OAuth client id secret in **Action 1, Step 1** is **ConsumeSecret**

```
1. <prop key="sugarcrm-sugarurl">sugar-instance-url</prop>
2. <prop kev="sugarcrm-oauth-accesstokenurl">sugar-instance-url/rest/v10/oauth2/token</prop>
3. <prop key="sugarcrm-sugarurl">sugar-instance-url</prop>
4. <prop key="sugarcrm-oauth-service-username">sguser</prop>
5. <prop key="sugarcrm-oauth-service-password">sgpwd</prop>
6. <prop key="sugarcrm-oauth-clientid">ConsumerKey</prop>
7  <prop key="sugarcrm-oauth-clientsecret">ConsumerSecret</prop>
```
