**Intended Audience:**  This document is intended for use by an **Administrator**: as such it provides a description of steps to be taken by an Administrator before the Mobileforce Field Service Management (**FSM**) software can be used by Field Service teams. 

Mobileforce Field Service Management (FSM) software helps organizations manage the work they perform at customer locations. FSM Software helps organizations anticipate and respond proactively to their customer's requests for service or support. Effective use of FSM Software enables streamlining of customer requests by  Agents into approved work orders and/or service tasks, then having Dispatchers find, match, and schedule the most appropriate technicians  to best resolve these work orders/service tasks, and then having the technicians go on-site to a customer location, to complete the tasks and thus delight the customers. Mobileforce FSM enables service organizations to provide the best service to complete the most number of customer requests, in the shortest amount of time. In addition, Mobileforce FSM software enables streamlining of related field service activities such as Inventory Tracking, Fleet Tracking, and Digital Forms for data capture and workflow automation in the field.

**Field Service Team Roles**
Typical field service teams consists of users categorized into the following roles. Please note that an actual user may take on multiple roles in an organization:

- Administrator: the intended audience of this Admin Guide. A user who sets up the Field Service Management System for the other users to use. An Administrator has the ability to customize Field Service Tables, create and delete users and roles, and perform configuration not only within the Mobileforce FSM Software, but also related enterprise software such as Customer Relationship Management (CRM) Software.

- Agent: Often a back-office user, who receives requests in the form of calls, email or chat messages from customers and responds to these requests by creating work orders and/or service tasks. An agent typically does NOT assign technicians to service tasks, nor does an agent typically schedule and dispatch technicians. Those tasks are left to a Dispatcher.

- Dispatcher: Often also a back-office user, a dispatcher starts with pre-created work orders or service-tasks and assigns as well as schedules individual field service users (technicians) to complete these tasks. A dispatcher also routes technicians from one task to another, and could perform route optimizations as well as re-scheduling technicians in case there are any changes. Typically a dispatcher controls all tasks that are initiated in one or more branch offices or specific geo-locations or geographic areas, and is able to assign and schedule technicians who are also located in those offices or geo-locations to complete the tasks. Typically a dispatcher has access to the technician skills, their calendar and vacation schedule, their current location, and their flexibility in traveling to customer locations. This enables a dispatcher to "match" the appropriate technician with the right service task and fine-tune the upcoming schedule of the technician to enable the  technician to best complete the tasks without undue travel between tasks, or undue delay in reaching customer locations, or undue delay due to lack of skills or resources necessary to complete the service task.

- Technician: Often a "field" user, a technician is able to travel from an office to a customer location for the purpose of providing service or support to the customer by completing one or more service tasks assigned to them. Service tasks that field service technicians complete can be an installation, a repair, a maintenance, or even diagnostic testing to uncover the root cause of a problem that the customer reports.
A technician often has a fixed schedule for a day, that has been set up previously, by a dispatcher, and starts the day off from a specific starting point (either an office or their home), and then completes the service tasks assigned to them in sequence. As a technician completes a task, they are able to verify if they're still on schedule to get to the customer location for the next task, and if delayed, can communicate with the dispatcher who can re-schedule the remaining tasks for the technician for that day. A technician often works with a mobile device (a tablet or a smartphone) that they need to be able to use, when at a customer location, in front of a customer. Technicians typically capture data at a customer location or in the field via forms, provide estimates to customers, get customer approvals (via e-signatures) on the estimates or work performed, analyze, troubleshoot and then complete the service tasks assigned to them, fill out time-sheets indicating time spent on a task, accept or reject upcoming tasks, and reach back to the office (and the dispatcher) in case there are any issues out in the field. Technicians also often produce service reports and are responsible for documenting processes by taking notes and capturing images at the customer premise.

In order to use this FSM Admin Guide, you must have  control of (i.e., knowledge as well as read/write access to) the following objects/records in the Field Service Management Software:

 1 **Work Orders**: which contains all the details of the work that needs to be done. Work orders are typically larger in scope, and can contain several individual work items, to be performed in sequence. Work orders can last from hours to several days, and are typically used as a starting point, to co-ordinate resources and schedule activities. A work order structurally consists of several smaller indivisible components, called service-tasks. 
 
 2 **Service Tasks**: a service task is a single indivisible  unit of work, that can often be scheduled to be performed by one or more technicians. A service task, if scheduled, involves a field service user, often a technician, traveling to a specific customer location and performing a task such as a repair, maintenance, or some activity at the customer location. Service tasks are typically smaller in scope, and can be performed in minutes to hours.
 
 3 **Forms** which empower field service users with powerful data capture and workflow capabilities, while in the field: hence accessible directly on mobile devices such as smartphones and tablets   
 
   - Rich Form Fields: that represent files, images, geolocations, and signatures 
   - Powerful Form actions: including client-side validations, server-side validations, workflow process, auto-completions of form fields, auto-triggering of actions such as sending a completed form by email to a customer, based on form input data 
   - Offline access to forms and other data fields, for data capture and later on sync
   - Structured forms such as Service Estimates and Sales Quotes. 
   - Integration with Enterprise backend systems or record: such as databases and business applications

 4 **Inventory** which enable recording and tracking the use of products, parts, assets, and product bundles, within various field offices of the Field service Company that uses the Mobileforce FSM Software. Inventory can also be associated with customer accounts (customers of the Field Service Company), captured via a product or bar-code that the inventory item has, and even be related to other inventory items.

 5 **Fleet** which enables recording and tracking of vehicles, typically trucks and vans, belonging to the Field Service Company that uses Mobileforce FSM Software. Fleet records include lease/purchase details, vehicle details (including registration, location and odometer), and maintenance details.

 6 **Schedule & Dispatch** which enables the Dispatcher to assign and schedule existing service tasks to specific technicians, to be completed at a specific date/time, and with a specific duration. Service Tasks have an associated "customer location" which is where the technician is dispatched to in order to complete the service task. The act of assigning a specific task to a specific technician, to be completed at a specific date, results in an appointment being created for that task. Service Tasks typically have a 1-1 relationship with appointments. Service Tasks also have a "status" that describes whether they are pending (yet to be scheduled), scheduled (assigned to a technician), in-progress (technician is actively working to complete the service task), or completed. When a "pending" service task is assigned by a dispatcher to a technician, it's status changes from "pending" to "scheduled" (as a result, the service task can no longer be scheduled again). The states of a service task can be configured by the FSM Administrator.

# Field Service Management Admin Guide

Any business that offers any form of Field Service: be it support or installation or maintenance or even sales, needs to organize and arrange the lifecycle processes encompassing field service work. In a typical customer driven Field Service Organization, receiving a customer request for support or service necessitates the identification and them the formal description of the work that needs to be completed in order to address the customer request. This formal description of work, when authorized (often as a result of an entitlement check of the customer to ensure they're entitled to the work that they are requesting, or approval of a service quote by the customer indicating their agreement to pay for the work) is often referred to as a "work order" and typically consists of  a list of (indivisible) service tasks that need to be performed in sequence, in order to complete the work order. Work orders and/or Service Tasks are often the starting point of all FSM activities.

This document first describes the Quick Start Setup sequence of steps that an Administrator needs to perform, in order to enable the rest of the organization to start using the FSM Software. Then the document goes into details of the FSM Administration.

## Setup and Quick Start to Administering your FSM
As a best practice, it behooves an Administrator to perform the following steps *in order*, so as to best set up the FSM Software.

Mobileforce FSM supports the following underlying CRMs: SugarCRM, Zendesk and Hubspot. Several objects and structures are automatically inherited (via API access) from the underlying CRM to Mobileforce FSM. For example, Users and roles are inherited from the underlying CRM into Mobileforce FSM. Similarly, certain features of CRMs (e.g., Cases in SugarCRM) are used as an FSM starting point and mapped to Work Orders and Service Tasks. Additionally, accounts and office objects in SugarCRM are also used to provide location information for tasks as well as schedule & dispatch. Since many of these objects are not implemented similarly across CRMs, this document uses SugarCRM as the underlying CRM, in order to describe the FSM Setup process. Nevertheless, for the most part, the process is similar across the CRMs.



1. **Bind your CRM to your FSM**: 

- If your CRM is Hubspot, please login to your hubspot instance, navigate to the Hubspot marketplace, and find and Install MobileForce from the marketplace. Alternatively you can use the following link to install the Mobileforce app from the Hubspot marketplace: 
https://app.hubspot.com/ecosystem/9190475/marketplace/apps/sales/sales-enablement/mobileforce-cpq-237933

The following screenshot shows MobileForce Application in Hubspot Marketplace

![MobileForce in Hubspot Marketplace ](/fsmimages/MFinHubspot.png)

Once installed, you can find the Mobileforce app in your Hubspot instance under **Preferences --> Integrations --> Connected Apps**

This installation will give you a free 30-day trial of MobileForce in your Hubspot instance. Once this is done, please contact MobileForce support (support@mobileforcesoftware.com) with the details about your hubspot instance, if you have any problems with your MobileForce FSM instance in your Hubspot instance.

- If your CRM is Zendesk, please login to your zendesk instance, navigate to the Zendesk marketplace, and find and Install MobileForce from the marketplace. Alternatively you can use the following link to install the Mobileforce app from the Zendesk marketplace: 
https://www.zendesk.com/marketplace/apps/sell/618399/mobileforce-cpq/ 

The following screenshot shows MobileForce Application in Zendesk Marketplace

![MobileForce in Zendesk Marketplace ](/fsmimages/MFinZendesk.png)

Once installed, you can find the Mobileforce app in your Zendesk instance under **Settings --> Integrations --> Apps**

This installation will give you a free 30-day trial of MobileForce in your Zendesk instance. Once this is done, please contact MobileForce support (support@mobileforcesoftware.com) with the details about your Zendesk instance, if you have any problems with  your MobileForce FSM instance in your Zendesk instance.

- If your CRM is SugarCRM, please fill out the following online form to set up a free 30-day trial which will automatically create a MobileForce FSM instance and bind your SugarCRM instance to it. 

 https://www.mobileforcesoftware.com/solutions/mobileforce-free-trial  

 The following screenshot captures the information you need to provide. Pay close attention to the two fields (a) Your Account Name and (b) Work Email, which will be used to tie together your SugarCRM instance with your FSM Software Instance.

![Set up a MobileForce Free Trial for FSM](/fsmimages/MFFreeTrial.png)

Eventually, Sugar will also migrate to a new Marketplace (Sugar Outfitters), from where you'd be able to install Mobileforce as well, but for now, please instead use the free trial described above.

The following screenshot shows MobileForce Application in the new Sugar Outfitter Sugar Marketplace. At a later point, this would be the starting place to install and try MobileForce from within Sugar.

![MobileForce in Sugar Outfitter Marketplace ](/fsmimages/MFinSugarOutfitter.png)

2. **Field Service Top Level Navigation**:

The Mobileforce FSM Software is accessed from within your CRM instance. It has the same look and feel as your CRM UI, and hence is very easy to use for anyone who's already familiar with their CRM. All you do is log in to your CRM just as you always do, and you'll see Mobileforce FSM within your CRM Instance.

At the top level, the navigation for Mobileforce apps within your CRM looks as follows:

![MobileForce Apps: Top Level ](/fsmimages/MFTopLevel.png)

For Mobileforce Field Service, the "Field Service" tab provides navigation into the Field Service functionality which includes Field Service Setup whereas the "Admin" tab provides navigation into User and Role Management.

Clicking "Field Service" brings you to the Field Service Top Level Screen which looks as follows:

![Field Service Software: Top Level ](/fsmimages/FSMTopLevel.png)

Clicking now on Field Service Setup brings you to the Setup Screen that looks as follows:

![Field Service Software: Setup  ](/fsmimages/FSMSetup.png)

As an FSM Admin, you would configure the following constructs within Field Service Setup.

3. **Field Service Setup: Skills**: Every Field Service Technician has a set of skills, that is used to match them with Service Tasks. In the Skills setup screen, you can create a set of skills. See the following screenshot as an example for the skills that might be created by you.

![Field Service Setup: Skills  ](/fsmimages/Skills.png)

In this example, "multilingual" and "certified" are two examples of skills that a Technician might possess, that a Dispatcher would use to assign the Technician to a Service Task that might need one or more of those skills. Once a set of skills are created on this screen, you can go back to the Mobileforce top level screen, click on "Admin" and then go to the "Users" screen and associate one or more of these skills with each user. 

Skills matching in Mobileforce FSM can be performed one of two ways: finding a Technician that posesses either **ANY** or **ALL** of the skills required to complete a service task. The service task describes whether skills matching is performed via **ANY** or **ALL** matching. The  default behavior of skills matching is to use **ANY** matching, and a specific service task can override this behavior.

4. **Field Service Setup: Offices**: Field Service Operations are broken down into Offices, which correspond to Offices/Locations that the Organization operates. Each office covers a specific "territory" where customers reside. Initially, Mobileforce Field Service comes with one sample office: "Mobileforce Software", which includes an address, and a Lat/Long point on a map, describing the Office location.

Each office also has one or more territories that the office services. Mobileforce FSM Software includes pre-defined territories for each zip code in the US, but you can create your own territories by drawing polygons around an office.

New Offices can be added by simply clicking on the "Add" button on the top right of the Offices screen. The following screenshot shows the addition of an office:

![Field Service Setup: Office  ](/fsmimages/AddOffice.png)
Every office needs an address, and in addition, a Lat/Long point, which is added as follows:

![Field Service Setup: Office Lat/Long  ](/fsmimages/OfficeLatLong.png) 
If you type an address in the "Enter Address" field, the mapping software will map that address with a marker. You can then submit the marked address as the Lat/Long point for the office.

A territory is a geographic area, around an office that is serviced by technicians assigned to that office. An office can service many territories. Territories are used to (a) divide a large area into well defined smaller areas (b) Automate the assignment of a service request originating from a territory to one or more technicians who service the territory (c) reduce travel by technicians: who would only travel within a territory and never outside the territory (d) business demarcation of geographic areas served by different vendors/technicians/offices, thus eliminating conflict.

Once an office is created, within the same Create Office screen, you can click on "+" on the right of Territories to add a specific Territory, typically around that office, which is serviced by the office. Alternatively, you can go up to FSM Setup and click on Territories and then add a territory in the Territories list view.

Adding a territory looks as follows:

![Field Service Setup: Office Territory  ](/fsmimages/AddTerritory.png) 
Any territory is described by a closed polygon, and in the Add Territory screen, you can click on the "Edit Map" button under the Polygon Points field, to create your own territory.

Once in the map, you can use the polygon tool to  create  a Territory via Polygon points.
The polygon tool is highlighted here.
![Field Service Setup:  Polygon Tool ](/fsmimages/PolygonTool.png)

Once you've drawn a few points in a polygon, the polygon look as follows:

![Field Service Setup: Office Territory Polygon  ](/fsmimages/TerritoryPolygonPts.png). 

New points are created by simply clicking on the map in sequence, and when the last point is clicked, you can then click "Submit" and the Territory Polygon is saved.

Note that Mobileforce FSM already includes territories represented via polygons that include each zip code and each state in the USA, so you can use one of the included territories instead of having to create your own, if it serves your purpose.

Each territory needs to be associated with an office: this is done in the territory list view under FSM Setup where the Office can directly be specified. The following screenshot shows the office assignment for a territory.

![Field Service Setup:  Territory Office Assignment  ](/fsmimages/TerritoryOffice.png). 

5. **Field Service Setup: User Schedules**: Typical organizations operate on certain days of the week and between certain hours. The users of such organizations follow specific work schedules which includes (a) days of the week that they work (b) starting hours (c) ending hours. For example, typical business work week may be Mon-Fri: from 8AM to 5 PM. MobileForce FSM includes a predefined "weekday" schedule which precisely captures a work week. The following screenshot captures this predefined schedule:

![Field Service Setup:  User Schedule  ](/fsmimages/UserSchedule.png). 


The following screenshot captures the typical weekday schedule.

![Field Service Setup:  User Weekday Schedule  ](/fsmimages/WeekdaySchedule.png). 

Any changes to the schedule can be made by "Editing" the schedule as follows:

![Field Service Setup:  Edit User  Schedule  ](/fsmimages/EditWeekdaySchedule.png). 


Additional new schedules may be added by clicking on the "+Add" button on the top right of the User Schedules screen. For example, one could create a weekend schedule as follows:

![Field Service Setup:  Add User Schedule  ](/fsmimages/AddUserSchedule.png). 

The purpose of User schedules is to ensure that work is not assigned to technicians outside their workday schedule. An attempt to assign a service task to a technician outside of his or her weekday schedule will fail with an appropriate error. Schedules can be modified to incorporate overtime and weekend work.

Each FSM User is assigned a variety of attributes such as an office, a schedule, a skill, etc. The following fields represent the FSM attributes for a user:

![Field Service Setup:   User Attributes  ](/fsmimages/UserScheduleSkill.png). 


6. **Field Service Setup: Holidays** Just as user schedules provide a guidance of what hours a user works during a day, similarly holidays provides a guidance for when a user doesn't work. No work can be scheduled for holidays, thus ensuring technicians are not called up to work during holidays.

Holidays are another table in Field Service Setup, that the Admin creates entries for, by clicking on the "+Add" on the top right of the Holidays Table. Adding Holidays looks as follows:

![Field Service Setup:  Add Holidays  ](/fsmimages/AddHoliday.png). 


7. **Field Service Setup: Service Task Status**: In Mobileforce FSM, workflow steps encompassing the lifecycle of a service task are modeled via Service Task Status. Mobileforce FSM includes the following service task status values:

![Field Service Setup:  Service Task Status  ](/fsmimages/ServiceTaskStatus.png). 

These service task status values represent the various states of a service task. For example, when a service task is initially created, it is in "Open" status. Once a Dispatcher assigns an open service task to a technician, the service task status changes to "Assigned". Once a service task is completed, its status changes to "Completed". The provided values of Service Task Status often suffice for most FSM users, but if new status needs to be added this can be done by clicking on the "+Add" button on the top right of the Service Task Status table.


8. **Field Service Setup: Service Task Types**: Service tasks are classified based on their "types" which represent the various kinds of Service Tasks that the organization addresses. Types enable an easy triage and technician assignment and also help with improved analytics on the kinds of service and support requests that the organization is receiving.
Mobileforce FSM provides a set of default "Service Task Types" shown here:

![Field Service Setup:  Service Task Types  ](/fsmimages/ServiceTaskTypes.png). 
The provided values of Service Task Types often suffice for most FSM users, but if new types need to be added, this can be done by clicking on the "+Add" button on the top right of the Service Task Type table.


9. **Field Service Setup: Inventory Categories**: In addition to work order management, Mobileforce FSM also provides basic Inventory creation and tracking capabilities. In order to keep track of the often vast inventory of tools and objects needed by a technician to effectively perform field service or support, Mobileforce provides the ability for a FSM Admin to create simple categories into which Inventory objects are organized. The following table illustrates the Inventory categories used by an IT Services company:

![Field Service Setup:  Inventory Categories  ](/fsmimages/InventoryCategories.png). 


10. **Field Service Setup: Inventory Locations**: Inventory is often kept in many different locations such as different offices. The Inventory Locations table enables the attribution of specific locations for inventory objects.

## FSM Administration: Detailed Operations

Please refer to the following sections  for more details on the different components of your FSM system and how to administer each of them.

## 1. Work Orders


## 2. Service Tasks

## 3. Schedule and Dispatch

### 3.1. Skills Matching

#### 3.1.1. Any Skills Match

#### 3.1.2. All Skills Match

### 3.2. Auto Scheduling

### 3.3. Recommend Scheduling

### 3.4. Smart Routing


## 4. Inventory Tracking

### 4.1. Inventory Types

### 4.2. Inventory Categories
