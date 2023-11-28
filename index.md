## Table of contents

* [Overview](#overview)
* [Mock-Ups](#mock-ups)
* [Checklist](#checklist)
* [User Guide](#user-guide)
* [Developer Guide](#developer-guide)
* [Backend Design](#backend-design)
* [Team](#team)
* [Deployment](#deployment)


## Overview

![Logo](/PDF-Folder/Food_Now_Logo_1.png)

Food Now is a web application to help find a place to eat on campus! With the multitude of options offered here at UH Manoa, choosing may be difficult. 

Food Now enables users to log in with their UH emails and:
* Search for eateries based on a list of categories
* Locate eateries with a top-down view of the UH Manoa campus highlighting the location of the desired eatery.
* Provide a star rating for an eatery
* If given enough time, users will be able to discover menu items at specific eateries
  * View the price of each item
  * Add items to a "cart" that tracks all items added and the total cost before arrival


## Mock-Ups 

Our Mock-up design includes 4 pages: 

**User Home Page**

| User Home Page                                      | 
|-----------------------------------------------------|
| ![Sign in Page](/PDF-Folder/UserHomePage.png) | 

**Landing Page**

| Landing Page | 
| ----------------------------------- |
| ![Sign in Page](/PDF-Folder/LandingPage1.png) |
| ![Sign up Page](/PDF-Folder/LandingPage2.png) |

**Sign In & Sign Up Page**

| Sign In                             | Sign Up                             |
| ----------------------------------- | ----------------------------------- |
| ![Sign in Page](/PDF-Folder/SignIn-mockup.png)  | ![Sign up Page](/PDF-Folder/SignUp-mockup.png)  |


**Vendor Page**

| Vendor Page | 
| ----------------------------------- |
| ![Sign in Page](/PDF-Folder/vendorpagemock.png)  | 

**Add Vendor Item Page**

| Add Vendor Item Page | 
| ----------------------------------- |
| ![Item Add Page](/PDF-Folder/AddStuffPageMockUp.JPG)  | 

**Admin Exclusive**

| Add Users | 
| ----------------------------------- |
| ![Sign in Page](/PDF-Folder/add-user.png)  | 
| ![Sign in Page](/PDF-Folder/add-customer.png)  |
| ![Sign up Page](/PDF-Folder/add-vendor.png)  |
| ![Sign up Page](/PDF-Folder/add-admin.png)  |

**User Profile Page**
| ![User Profile Page Image](/PDF-Folder/UserProfilePage.png)  |

## Checklist
- [X] Mock-Ups
- [X]   Landing Page
- [X]   Sign In/Sign Up Page
- [X]   Vendor Page
- [X]   Admin Page
- [X]   Logo
- [X]   MongoDB for storing/retrieving information
- [X]   Deployment

## User Guide

This section provides an explination of the current features Food Now provides to our users.

When a user first visits our site, they will be met with the **landing page**: 
![Landing Page](/PDF-Folder/LandingPage1.png)

Here you can login in the top right. Alternatively you can scroll down to find our list of vendors, view our map of vendors on and around campus, or if you're in the mood for a specific type of food you can even check out the different cuisine types we offer.

![Landing Page](/PDF-Folder/LandingPage2.png)

When you click Login in the top right, you will be directed to our **Login Page** where you can either login with an existing account or register for a new one:

| Sign In                             | Sign Up                             |
| ----------------------------------- | ----------------------------------- |
| ![Sign in Page](/PDF-Folder/SignIn-mockup.png)  | ![Sign up Page](/PDF-Folder/SignUp-mockup.png)  |

Upon succesfully loging in, you currently will have access to two tabs. The first is called **Add Item**:

![Landing Page](/PDF-Folder/Add-Item.png)

The add item page allows you to select <!-- LIAM EXPLAIN THAT SHTTTTT -->

The other page you will currently have access to is the **Vendors and Items** page:

![Landing Page](/PDF-Folder/Vendors-Items.png)

This page should be the main focus for most of our site's users. Through here, you will have access to our full list of vendors. Each vendor will display its name, address, contact info, menu items, as well as a link to their site. You will be able to sort through our many options with provided filters on the left. On the far right side of the page we also provide a map of campus that display all vendors in and around UH Manoa.

## Developer Guide

There are many features of our site that are only available for developers. This section aims to provide a step by step guide for downloading, installing, running, and operating Food Now.

First you will want to visit our github page at [Food Now Github](https://github.com/food-now/MM). Here you can clone our main branch onto your local machine and open using your favorite IDE. 

*We reccomend Intellij*

Once you have it opened you're going to want to CD into the app directory and run 'meteor npm install'.
After this finishes you can then run 'meteor run start' to launch the site on your local host.

Now that you have the site up and running, you can view the previous [User Guide](#user-guide) for insight on what you can do as a regular customer. But since we already covered that, we will now move onto what admins have access to.

After loging in as an admin (*credintials for respective accounts can be found in app/config/settings.development.json*) you will be routed to this page: 

![Admin Landing](/PDF-Folder/Admin-Landing.png)

As you can see, admins have access to two pages that regular customers do not: **All Users** and **Add Users**. First we will explore the **All Users** page:

![All Users](/PDF-Folder/All-Users.png)

This page allows admins to browse through the lists of users for each user type. The three different types being: Vedors, Customers, and Admins.

The next page currently available for admins is the **Add Users** page:
![Sign in Page](/PDF-Folder/add-customer.png)  
![Sign up Page](/PDF-Folder/add-vendor.png)  
![Sign up Page](/PDF-Folder/add-admin.png)  

This page will allow you too add users. The input fields will also change depending on the type of user you are trying to create.

## M1 Board

![Sign in Page](/PDF-Folder/m1new.png)

## Backend Design

This section encompasses the organization of the backend databases and associated functionality.

**Users**

Three roles: admin, vendor, and customer.

User must be either in admin, vendor, or customer role.
No default role. If user is not in one of these roles, then they won’t get any published data from anything.
Vendors must have a profile picture. Other roles do not have one.

Customer:
- sign up on sign up page

Vendor:
- sign up is on a page that only admins can access. Admins can create a vendor user.
- Vendor user can create a vendor.
- Vendor user can create menuItems.

Admin:
- Admin has an sign up admin page where they can create customer, vendor, or admin users.
- Admin has a users page that displays all accounts and their roles.
- Admin can remove accounts (can be its own page or implemented into the users page).


**Databases**

menuItems: collection of menuItems.
- Issue: Both customers and vendors will need to subscribe to their respective menuItems publications. We need to limit this to where customers get served the data, but cannot write back, and for vendors they can do both. Not exactly sure how to do this with Meteor publications.

Example menuItem:
```
{
	_id: String;

	owner: String;

	dateCreated: Date;

	vendorName: “McDonalds”;

	name: “Big Mac”;

	price: 6.3;

	allergens: [tree nuts, gluten, dairy];

	daysOfWeekAvaliable: [m, t, w, th, f];

	special: false;

	specialDate: Date (optional. Should only be set if item is a special. This indicates the day that it is going to be available.)

	image: String (optional);
}
```

## Team

Food Now is designed, implemented, and maintained by [Liam Tapper](https://github.com/tliam1), [Kai Matsuska](https://github.com/kairemUH), [Connor Narowetz](https://github.com/kairemUH), [Jonah Lene](https://github.com/jonahlene), [Joshua Lorica](https://github.com/loricaj), and [Gavyn Gostage](https://github.com/gavyngostage).

[Team Contract](https://github.com/food-now/food-now.github.io/blob/b8e72eb11ee5c67fb3f4d7d08c6871e3282a7ca7/PDF-Folder/Contract.pdf) 
<br>
[Milestone 1](https://github.com/orgs/food-now/projects/1)
<br>
[Milestone 2](https://github.com/orgs/food-now/projects/2)
<br>
[Milestone 3](https://github.com/orgs/food-now/projects/3)

## Deployment

[Site](http://67.205.186.185/)




