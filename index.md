## Table of contents

* [Overview](#overview)
* [Mock-Ups](#mock-ups)
* [Checklist](#checklist)
* [Team](#team)

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
| ![Sign in Page](/PDF-Folder/LandingPage-mockup.png) | 

**Sign In & Sign Up Page**

| Sign In                             | Sign Up                             |
| ----------------------------------- | ----------------------------------- |
| ![Sign in Page](/PDF-Folder/SignIn-mockup.png)  | ![Sign up Page](/PDF-Folder/SignUp-mockup.png)  |


**Vendor Page**

| Vendor Page | 
| ----------------------------------- |
| ![Sign in Page](/PDF-Folder/vendorpagemock.png)  | 

**Admin Exclusive**

| Add Users | 
| ----------------------------------- |
| ![Sign in Page](/PDF-Folder/add-user.png)  | 
| ![Sign in Page](/PDF-Folder/add-customer.png)  | ![Sign up Page](/PDF-Folder/add-vendor.png)  | ![Sign up Page](/PDF-Folder/add-admin.png)  |

## Checklist
- [X] Mock-Ups
- [ ]   Landing Page
- [ ]   Sign In/Sign Up Page
- [ ]   Vendor Page
- [ ]   Admin Page
- [ ]   Cart Page
- [ ]   Logo
- [ ]   MongoDB for storing/retrieving information
- [ ]   Making a map with "pins" at eatery locations
- [ ]   Deployment

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


