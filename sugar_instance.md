# MobileForce in SugarCRM Instance Integration Guide

## Step 1: Setup OAuth2 Keys
- Login to SugarCRM instance as an admin user
- Go to *User Icon (top right) > Admin > System > OAuth Keys*
- Click *OAuth Keys* tab on the Main Menu Navbar and in the drop down sub-menu, click on *Create OAuth Key*
- Add a new consumer key with secret and save it safely
- Make sure the OAuth type is set to OAuth2
- Send the chosen *Consumer Key* and *Consumer Secret* to MobileForce team

![Create OAuth Key in SugarCRM](/images/sugar_oauth_key_create.png)

### Step 1a: Disable Client IP Change Check
- Login to SugarCRM instance as an admin user
- Go to *User Icon (top right) > Admin > System Settings* screen
- Make sure you uncheck (clear) the setting *Validate user IP Address* under *Advanced* section

## Step 2: Create a MobileForce Custom Package and Module in SugarCRM
- Login to SugarCRM instance as an admin user
- Go to *User Icon > Admin > Module Builder*
- Click on *+ New Package* button
- Create a package with 
  * Name: MobileForce_CPQ
  * Key: mfcpq
- After creating the package, you will be taken back to list of packages screen
- Select **MobileForce_CPQ** package
- Click on *+ New Module* button
- Create a new module with
  * Name: MobileForce_CPQ
  * Plural Label: CPQ
  * Singular Label: CPQ
  * Check both Team Security and Navigation Tab
  * Select Type: basic
- After creating the module, you will be taken back to **MobileForce_CPQ** package screen
- On the MobileForce_CPQ package screen, click on *Deploy* button to deploy the package

## Step 3: Add MobileForce_CPQ Custom Module to Displayable Modules List
- Login to SugarCRM instance as an admin user
- Go to *User Icon > Admin > Display Modules and Subpanels*
- Move **CPQ** from **Hidden Modules** list to **Displayed Modules** list
- Move it up the list to just after **Leads** module

![Display Modules and Subpanels in SugarCRM](/images/sugar_display_modules_admin.png)

## Step 4: Enable the CPQ on the Main Menu for the Logged-in User
- Login to SugarCRM instance as any test user
- Go to *User Icon > Profile*
- Click on *Edit* button
- Go to **Advanced** tab
- Under **Layout Options**, move the **CPQ** from Hide Modules to Display Modules
- Move it up the list to just after **Leads** module

![Display Modules in User Preferences in SugarCRM](/images/sugar_display_modules_user.png)

## Step 5: Customize the Module Menu and Module Layout/View in Navigation Bar (Mega Menu) 

- Login to SugarCRM Demo Builder
- Go to *Demo Builder > Instance > Preview > Open File Manager*
- If you are not on Demo Builder, and instead in a test or production instance, go directly to the File System or File Manager
- In the file system, go to **/custom/modules**
- Create a new folder named **mfcpq_MobileForce_CPQ**
- Go to **/custom/Extension/modules**
- Create a new folder named **mfcpq_MobileForce_CPQ**
- Underneath that folder, successively create subfolders under **mfcpq_MobileForce_CPQ** as follows: **Ext/clients/base/menus/header**
- After everything is created the following path should be accessible: **/custom/Extension/modules/mfcpq_MobileForce_CPQ/Ext/clients/base/menus/header**
- Go to **/custom/Extension/modules/mfcpq_MobileForce_CPQ/Ext/clients/base/menus/header**
- On your PC or Mac, open a Text Editor and create a local file called **removeModuleLinks.php** with the following content and upload it to the **header** folder

```php
<?php
$module_name='mfcpq_MobileForce_CPQ';
$viewdefs[$module_name]['base']['menu']['header'] = array();
```

- Next, Go to **/custom/modules/mfcpq_MobileForce_CPQ**
- Underneath that folder, successively create subfolders as follows: **clients/base/layouts/records**
- After everything is created the following path should be accessible: **/custom/modules/mfcpq_MobileForce_CPQ/clients/base/layouts/records**
- Go to **/custom/modules/mfcpq_MobileForce_CPQ/clients/base/layouts/records**
- On your PC or Mac, open a Text Editor and create a local file called **records.php** with the following content and upload it to the **records** folder

```php
<?php
$module_name = 'mfcpq_MobileForce_CPQ';
$viewdefs[$module_name]['base']['layout']['records'] = array(
    'components' => array(
        array(
            'layout' => array(
                'type' => 'base',
                'name' => 'mfcpq',
                'css_class' => 'mfcpq',
                'components' => array(
                    array(
                        'view' => 'mfcpq-view',
                        'primary' => true,
                    ),
                ),
            ),
        ),
    ),
);
```

- Next, Go to **/custom/modules/mfcpq_MobileForce_CPQ/clients/base**
- Underneath that folder, successively create subfolders as follows: **views/mfcpq-view**
- After everything is created the following path should be accessible: **/custom/modules/mfcpq_MobileForce_CPQ/clients/base/views/mfcpq-view**
- On your PC or Mac, open a Text Editor and create a local file called **mfcpq-view.js** with the following content and upload it to the **mfcpq-view** folder

```javascript
({
    className: 'mfcpq-view',
    
    loadData: function (options) {
        authData=new Object();
        authData.accessToken = localStorage.getItem('prod:SugarCRM:AuthAccessToken');
        authData.refreshToken = localStorage.getItem('prod:SugarCRM:AuthRefreshToken');
        authData.downloadToken = localStorage.getItem('prod:SugarCRM:DownloadToken');
        var pathArray = document.referrer.split('/');
        var instance = pathArray[2];
        authData.instance = instance;
        authData.username = app.user.attributes.user_name;
        authData.display_name = app.user.attributes.full_name;
        authData.email = app.user.attributes.email[0].email_address;
        this.authData = authData;
        this.render();
    }
})
```

- On your PC or Mac, open a Text Editor and create a local file called **mfcpq-view.hbs** with the following content and upload it to the **mfcpq-view** folder

```
<iframe width="100%" height="900" src="https://apps.mobileforcesoftware.com/adlwebui/login.php?account=sugarmf&app=servicevelocity&al=1&target=native%3A%2F%2Fnav%3Fto%3DHome%3BCPQ&param-prefix=sugarcrm-&sugarcrm-instance={{authData.instance}}&sugarcrm-username={{authData.username}}&sugarcrm-display_name={{authData.display_name}}&sugarcrm-email={{authData.email}}&sugarcrm-accessToken={{authData.accessToken}}&sugarcrm-refreshToken={{authData.refreshToken}}&sugarcrm-downloadToken={{authData.downloadToken}}"></iframe>
```

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

## Step 9: Login and Use Your SugarCRM Instance with MobileForce CPQ
- Login to SugarCRM instance as a regular user
- **CPQ** Module names with no sub-menus will be shown in Mega Menu Navigation Bar 
- When user clicks on the **CPQ** in Navigation Bar it will load the iframe to MobileForce
- MobileForce will display the Sugar OAuth2 login page
- Please login with the same credentials as the logged-in user
- **CPQ** list of existing prosposals/quotes screen is shown. It may be empty on first login.
- Click *Add* button on the bottom toolbar to create a new Quote/Proposal
- Alternatively, go to any open *Opportunity* record in SugarCRM
- Click on **+ CPQ** custom button at the top to create a new Quote/Proposal for that *Opportunity*

![Create New Quote/Proposal in SugarCRM](/images/sugar_cpq_launch_points.png)
