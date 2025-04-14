---
title: Kimai Wiki
description: Wiki pages for Kimai time tracking software
published: true
date: 2024-10-08T06:45:40.861Z
tags: 
editor: markdown
dateCreated: 2024-10-08T06:45:40.861Z
---

# Introduction

Kimai is a time tracking system that Polaris IT Solutions Inc. uses for tracking hours spent per customer, and billing purposes. This system is also used for internal billing between companies under the WBHS Group. Kimai can be used on Web, Desktop or Mobile.

# Customer Tracking Specifications

Carefully select the Project and Activity based on the customer and task to complete

## Koruna Assist

| Field | Name | Description | Billable? | Rate | Kimai |
| --- | --- | --- | --- | --- | --- |
| **Project** | **Koruna Assist Non SLA IT Support** | **Any support requests outside of business hours, with appropriate approval from Koruna Assist and Polaris Solutions** |     |     |     |
| Activity | Koruna Assist Out of SLA User Support | Default option for Koruna Assist Non SLA IT Support for any support requests outside of business hours | Yes | TBA | Yes |
| **Project** | **Koruna Assist SLA IT Support** | **Any support requests in normal business hours (07:00 - 16:00, Mon - Fri)** |     |     |     |
| Activity | Koruna Assist Computer Setup | Computer setup within business hours | No  | N/A | Yes |
| Activity | Koruna Assist SLA User Support | User support within business hours | No  | N/A | No\* |

\* All Koruna Assist tickets must be logged in the [Help Desk system](/polaris-solutions/wiki/zammad-sd)

Refer to customer [SLA](/polaris-solutions/sla/koruna-assist) for further details

## Kaesim Cybersecurity

| Field | Name | Description | Billable? | Rate\* | Kimai |
| --- | --- | --- | --- | --- | --- |
| **Project** | **Kaesim Non SLA User Support** | **Any user support which does not include the Polaris Solutions RMM & VPN service** |     |     |     |
| Activity | Kaesim Non SLA User Support | Any user support which does not include the Polaris Solutions RMM & VPN service within business hours. Support out of business hours must be approved by Kaesim Cybersecurity and Polaris Solutions and rate agreed. | Yes | 529 | Yes |
| **Project** | **Kaesim SLA IT Support** | **Any user setup and support which includes the Polaris Solutions RMM & VPN service** |     |     |     |
| Activity | Kaesim SLA User Setup | User setup on Kaesim infrastructure and Polaris RMM & VPN services | Yes | 445 | Yes |
| Activity | Kaesim SLA User Support | User support within business hours | No\*\* | N/A | Yes |

\* Rate is changeable depending on the monthly AUD to PHP conversion rate

\*\* User support up to 20 hours per month is included. Refer to the Kaesim [User List](/polaris-solutions/customer-list) 

Refer to customer [SLA](/polaris-solutions/sla/kaesim-cybersecurity) for further details

# User Time Tracking

Referring to the table above, time tracking should be done according to the support request

## Web Application

To start time tracking, open the browser and navigate to [https://time.wbhsgroup.com](https://time.wbhsgroup.com/) and login with the credentials provided.

Kimai Home Screen

To start a new time recording, click the play button on the top right of the page and fill in the relevant customer information based on the ticket logged. Do not enter To or Duration as they will auto calculate at the end of the session.

Click save

Time Tracking log creation

Once the ticket has been resolved, and ticket updated and closed, click on the Stop icon at the top right of the screen to conclude the time tracking

Stopping Time Tracking

## Mobile Application

## Desktop Application

# Team Lead Functions

## Creating Customers

## Creating Projects

## Creating Activities

## Reporting

# Administrative Functions

## Creating User Accounts

## Creating Customer User Accounts