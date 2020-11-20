# MobileForce in SugarCRM Instance Integration Guide

## Step 1: Setup OAuth2 Keys
- Login to SugarCRM instance as an admin user
- Go to *User Icon (top right) > Admin > System > OAuth Keys*
- Click *OAuth Keys* tab on the Main Menu Navbar and in the drop down sub-menu, click on *Create OAuth Key*
- Add a new consumer key with secret and save it safely
- Make sure the OAuth type is set to OAuth2
- Send the chosen *Consumer Key* and *Consumer Secret* to MobileForce team

![Create OAuth Key in SugarCRM](/images/sugar_oauth_key_create.png)

### Step 2: Disable Client IP Change Check
- Login to SugarCRM instance as an admin user
- Go to *User Icon (top right) > Admin > System Settings* screen
- Make sure you uncheck (clear) the setting *Validate user IP Address* under *Advanced* section

### Step 3: Add a API Platform
- Login to SugarCRM instance as an admin user
- Go to *User Icon (top right) > Admin > Configure API Platforms* screen
- Add a new platform with the name *api* and *Save*

## Step 4: Install MobileForce FSM Module
- Download [*MobileForce_FSM* Module ZIP File](/assets/MobileForce_FSM.zip) to your computer
- Login to SugarCRM instance as an admin user
- Go to *User Icon > Admin > Module Loader*
- Upload the Module ZIP File you downloaded
- Click *Install* and *Commit* to install the Module

![Module Loader in SugarCRM](/images/sugar_module_loader.png)

## Step 5: Install MobileForce CPQ Module
- Download [*MobileForce_CPQ* Module ZIP File](/assets/MobileForce_CPQ.zip) to your computer
- Login to SugarCRM instance as an admin user
- Go to *User Icon > Admin > Module Loader*
- Upload the Module ZIP File you downloaded
- Click *Install* and *Commit* to install the Module

![Module Loader in SugarCRM](/images/sugar_module_loader.png)

## Step 6: Install Custom Buttons UI Module
- Download [*wRecordButtons* Module ZIP File](/assets/wRecordButtons_v5.22.zip) to your computer
- Login to SugarCRM instance as an admin user
- Go to *User Icon > Admin > Module Loader*
- Upload the Module ZIP File you downloaded to install the Module

![Module Loader in SugarCRM](/images/sugar_module_loader.png)

## Step 7: Add Custom Button to Opportunity Record View: A Deep Link to MobileForce CPQ
- Login to SugarCRM instance as an admin user
- Go to *User Icon > Admin > Studio > Opportunities Module > Fields*
- Add a Custom Field of type wRecord Buttons
![Custom Button Field in Opportunities Module in SugarCRM](/images/sugar_custom_button_field.png)

- Configure the wRecord Custom Button as shown in the screenshot below
![Custom Button Field Configuration in SugarCRM](/images/sugar_configure_custom_button.png)
- For the Base URL textbox field in the custom button configuration, please copy and paste the following URL

```
https://apps.mobileforcesoftware.com/adlwebui/login.php?account=sugarmf&target=native%3A%2F%2Fnav%3Fto%3DHome%253BNewSugarQuote%26params%3D%257B%2522form%2522%253A%257B%2522account%2522%253A%2522%257B%255C%2522key%255C%2522%253A%255C%2522{account_id}%255C%2522%252C%255C%2522value%255C%2522%253A%255C%2522{account_name}%255C%2522%257D%2522%252C%2522opportunity%2522%253A%2522%257B%255C%2522key%255C%2522%253A%255C%2522{id}%255C%2522%252C%255C%2522value%255C%2522%253A%255C%2522{name}%255C%2522%257D%2522%257D%257D
```

- Click *Save* on the Configuration screen. Then click on *Save* in the Edit Field screen.

## Step 8: Rebuild and Update Your SugarCRM Instance
- Login to SugarCRM instance as an admin user
- Go to *User Icon > Admin > Repair > Quick Repair and Rebuild*
- Please wait. This will take 15-30 seconds to rebuild the system and will print out the log.
- This will deploy the changes we made in the instance

![Quick Build and Repair in SugarCRM](/images/sugar_quick_repair_rebuild.png)

## Step 9: Login and Use Your SugarCRM Instance
- Login to SugarCRM instance as a regular user
- **CPQ** and **Field Service** Module names with no sub-menus will be shown in Mega Menu Navigation Bar 
- When user clicks on the **CPQ** or **Field Service** in Navigation Bar it will load the iframe to MobileForce
- MobileForce will display the Sugar OAuth2 login page
- Please login with the same credentials as the logged-in user
- **CPQ** list of existing prosposals/quotes screen is shown. It may be empty on first login.
- Click *Add* button on the bottom toolbar to create a new Quote/Proposal
- Alternatively, go to any open *Opportunity* record in SugarCRM
- Click on **+ CPQ** custom button at the top to create a new Quote/Proposal for that *Opportunity*

![Create New Quote/Proposal in SugarCRM](/images/sugar_cpq_launch_points.png)

## Step 10: Move Up the CPQ and Field Service Tabs on the Main Menu for the Logged-in User
- Login to SugarCRM instance as any test user
- Go to *User Icon > Profile*
- Click on *Edit* button
- Go to **Advanced** tab
- Under **Layout Options**, move the **CPQ** and **Field Service** modules Up in the list of Display Modules
- Click *Save* button to save preferences

![Display Modules in User Preferences in SugarCRM](/images/sugar_display_modules_user.png)

