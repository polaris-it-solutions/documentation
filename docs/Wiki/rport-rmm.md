---
title: RPort RMM Wiki
description: Wiki pages for the RPort RMM
published: true
date: 2024-10-08T08:38:30.378Z
tags: 
editor: markdown
dateCreated: 2024-10-08T08:38:30.378Z
---

# Introduction

# Web Interface

# Adding Clients

## Client Access Token

## Desktop Setup & Configuration

### Installing RPort

#### Automated install with pairing code - Windows

1. Login to the RPort RMM web page.
2. Click Profile button on the left access menu (looks like a cog)
3. Click Client Access
4. Find the customer / group client access ID that you intend to install RPort on, and click the 3 dots and click on Install client
5. Click COPY TO CLIPBOARD next to Windows to select the PowerShell script
6. On the client PC, click the Start menu, and type PowerShell. Right click the option and select Run as Administrator
7. Paste the PowerShell script and press enter
8. Read the screen output to ensure that installation was successful

Step 5 - Copy the PowerShell script, paste and execute on client PC

#### Automated install with pairing code - Linux

#### Manual install - Windows

1. Download and run the RPort installer: [https://downloads.rport.io/rport/stable/latest.php?arch=Windows\_x86\_64](https://downloads.rport.io/rport/stable/latest.php?arch=Windows_x86_64)
2. Copy the client config file from the below Additional Resources section to "C:\\Program Files\\rport" folder
3. Click start and type cmd, right click "Command Prompt" and run as administrator
4. Paste this line: cd "C:\\Program Files\\rport"
5. Paste this line: rport.exe --service install -c rport.conf and confirm that the client appears on the RPort dashboard
6. Paste this line: sc query rport. Read the output to confirm success
7. Paste this line: sc start rport. Read the output to confirm success
8. Login to the RPort server and check under Kaesim that the client has successfully registered

#### Manual install - Linux

#### Manual install - MacOS

### Installing TightVNC - Windows

### Installing TightVNC - Linux

### Installing TightVNC - MacOS

# Remote Control PC's

# Remote Script Execution

# Additional Features

## Documentation

## Audit

## Meta Data

# Administration

## Adding Users & Groups

## Adding Client Groups

## Creating Client Access Tokens

## Additional Resources

Kaesim Cybersecurity Config file [/rport.conf](/rport.conf)

Koruna Assist Config file [/rport.conf](/rport.conf)