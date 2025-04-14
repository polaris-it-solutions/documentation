---
title: OpenProject Wiki
description: Wiki pages for OpenProject
published: true
date: 2024-10-08T06:31:39.237Z
tags: 
editor: markdown
dateCreated: 2024-10-08T06:31:39.237Z
---

# Introduction

OpenProject is our comprehensive open-source solution for efficient project management and collaboration. With features like task management, Agile support, real-time communication, and powerful reporting, OpenProject empowers our teams to plan, execute, and succeed in projects of all sizes. Streamline your project workflows, enhance collaboration, and achieve your project goals with our OpenProject platform. This documentation is a comprehensive guide to using OpenProject effectively. Whether you're new to the platform or looking to expand your knowledge, you'll find step-by-step instructions, best practices, and tips to make the most of OpenProject's features.

# Getting Started

Login to the web interface with the provided credentials to view your home page. From here you can see some of the projects you're owner of or part of, and can select which project you would like to work on.

## Overview Pages

OpenProject home page

Click on Select a project on the top left side to see the list of projects you own, or are part of, or to create a new project. You may also select to view the list of projects, which will redirect you to a dedicated page listing all projects.

The bell icon at the top right allows you to see notifications against your name, such as assigned projects or tasks, changes to tasks you're associated with or are owner of, and any other activity against the tasks. You may expand the item to view more information, as well as Unwatch, Mark as read, make changes to the Assignee, Accountable person and time tracking, as well as other quick actions. On the left side you can see some filters under the Reason section, as well as filter to unread notifications based on the project name

Notifications center

When selecting a project, you will be brought to the Project Overview screen, where you will be able to quick view the Project description, Status, Details, Members and their roles, and an overview of the Work Packages. Default view of the Work is Type, where you can view number of open or closed work packages. The filter can be changed to show WOrk Package overview of Status, Priority, Author and Assignee. The menu bar on the left allows you to jump to the project working pages, such as Work packages, Time and costs, Members and project settings. The most common page to be working on is the Work packages page

Project Overview

Projects can be created under another project, for example: If there is large project, it may have multiple sub projects needing to be completed before the overall project can be closed. Sub projects appear indented on the project quick select menu. All sub projects will have their own work packages needing to be completed to close the sub project.

A project can also be converted to a template if needed. Example: there are multiple construction projects to be initiated, all including similar work packages, create the one, convert to template and make copies of it for all of the construction projects. They will then all have the same work packages. Each project will be managed separately, and additional work packages can be added to them, or removed from them, based on the project needs.

Project quick select list

## Working on a project

Select the project you wish to work on, and select the Work Packages menu. The Project Work packages screen opens. On this page, you can see all work packages as well as their child tasks, status, Assignee and Priority. You will now be able to Add, remove or update work packages. You can change the view depending on your needs, and you can create your own views. From this page you can quickly add work packages from the bottom of the page by clicking on Create new work package, or click on Create and select the Work package type to edit in full screen view. 

You can quickly edit most fields by clicking into the one you want to edit, and the field will become active to editing. It is recommended to add the Progress %, Start Date and End Date fields to the view for faster viewing and editing from within the page.

## Member Assignment

## Project Settings

# Terminologies

**Work Package:** A work package is a general term for any task, activity, or item that requires attention within a project. Work packages can represent different types of work, such as tasks, phases, milestones, features, epics, user stories, and bugs.

**Phase:** A phase is a distinct stage or segment of a project's lifecycle. It represents a grouping of related tasks or activities that must be completed before moving on to the next stage. Phases help in organizing and structuring a project's timeline and progress.

**Milestone:** A milestone is a significant event or achievement in a project. It marks a specific point in time or the completion of a critical task. Milestones are often used to track progress and key project dates.

**Task:** A task is a specific action or activity that needs to be completed to achieve a project's objectives. Tasks are usually smaller, manageable units of work that contribute to the overall project progress.

**Feature:** A feature is a high-level functionality or capability that a software or product should have. Features are often used in software development projects to describe the desired functionalities.

**Epic:** An epic is a large, overarching project or initiative that is typically broken down into smaller, more manageable user stories or tasks. Epics help in organizing and prioritizing work in agile project management.

**User Story:** A user story is a user-centric requirement or description of a specific functionality from an end-user's perspective. User stories are commonly used in agile development to define and prioritize work items.

**Bug:** A bug is an issue or problem within a software application that needs to be fixed. Bugs can be reported, tracked, and resolved as work packages to ensure the software's quality and stability.

**Gantt Chart:** Gantt charts in OpenProject provide a visual representation of project timelines and dependencies. Users can create, edit, and customize Gantt charts to plan and schedule tasks and milestones. Dependencies between tasks are indicated by arrows, helping users understand task sequencing.

**Agile Project Management:** OpenProject supports Agile methodologies like Scrum and Kanban. Agile boards allow teams to manage work in progress (WIP), prioritize tasks, and plan sprints. Backlogs store and prioritize user stories or tasks for future iterations.

**Discussions:** Discussions are collaborative threads where team members can exchange ideas, seek clarification, or discuss project-related topics. Users can attach documents and mention others to involve specific team members in the discussion. Discussions are archived for reference, fostering knowledge sharing.

**Forums:** Forums serve as broader discussion areas for project teams or departments. They are ideal for announcements, general updates, and team-wide conversations. Users can subscribe to forums to receive notifications about new posts.

**Time Tracking:** Time tracking in OpenProject allows users to record hours worked on tasks and work packages. Users can specify the date, time spent, and a description of the work done. Time tracking data is useful for project costing, resource allocation, and progress analysis.

**Custom Fields:** Custom fields enable users to tailor work packages and projects to their organization's specific needs. Fields can be created for different data types, such as text, numeric, date, or list fields. Custom fields can be used for tracking unique project-related information.

**Workflows:** Workflows define the life cycle stages of work packages and how they transition from one stage to another. Users can customize workflows to match their project management processes. Workflow automation helps ensure consistency in project execution.

**User Roles and Permissions:** OpenProject defines various user roles, including administrators, project managers, and members. Each role has specific permissions and access levels, ensuring appropriate access to features and data. Roles and permissions can be configured to align with your organization's hierarchy.

# **Collaboration and Communication**

# **Time Tracking and Reporting**

## Web Time Tracking

## Mobile Application Time Tracking

### Google Play Store

From Google Play store, search for Open Time Tracker and install the app

Google Play Store app

Open the app and select Configure Instance. Enter https://projects.wbhsgroup.com as the Base URL and enter the Client ID: `VMHppmbUEeWMgPcbpJv1WIeqxRCAJLkPEj3STCaoPdg`

You will then be requested to login with your OpenProject username and password.

## Reporting

# **User Management and Permissions**

# **Integration and Plugins**

# **Deployment**

OpenProject has been deployed on Docker Swarm as a stack. Make sure to define the Volumes first

```plaintext
version: "3.7"

networks:
  frontend:
  backend:

volumes:
  pgdata:
    driver: local
    driver_opts:
      type: 'none'
      device: '/mnt/glusterfs/projects/pgdata/'  # Replace this with the local directory you want to mount
      o: 'bind'
  opdata:
    driver: local
    driver_opts:
      type: 'none'
      device: '/mnt/glusterfs/projects/opdata/'  # Replace this with the local directory you want to mount
      o: 'bind'

x-op-restart-policy: &restart_policy
  restart: unless-stopped
x-op-image: &image
  image: openproject/community:13.0.3
x-op-app: &app
  <<: [*image, *restart_policy]
  environment:
    OPENPROJECT_HTTPS: "${OPENPROJECT_HTTPS:-true}"
    OPENPROJECT_HOST__NAME: "${OPENPROJECT_HOST__NAME:-projects.wbhsgroup.com}"
    OPENPROJECT_HSTS: "${OPENPROJECT_HSTS:-true}"
    RAILS_CACHE_STORE: "memcache"
    OPENPROJECT_CACHE__MEMCACHE__SERVER: "cache:11211"
    OPENPROJECT_RAILS__RELATIVE__URL__ROOT: "${OPENPROJECT_RAILS__RELATIVE__URL__ROOT:-}"
    DATABASE_URL: "${DATABASE_URL:-postgres://postgres:p4ssw0rd@db/openproject?pool=20&encoding=unicode&reconnect=true}"
    RAILS_MIN_THREADS: ${RAILS_MIN_THREADS:-4}
    RAILS_MAX_THREADS: ${RAILS_MAX_THREADS:-16}
    IMAP_ENABLED: "${IMAP_ENABLED:-true}"
  volumes:
    - "${OPDATA:-opdata}:/var/openproject/assets"

services:
  db:
    image: postgres:13.10
    <<: *restart_policy
    stop_grace_period: "3s"
    volumes:
      - "${PGDATA:-pgdata}:/var/lib/postgresql/data"
    environment:
      POSTGRES_PASSWORD: ${POSTGRES_PASSWORD:-p4ssw0rd}
      POSTGRES_DB: openproject
    networks:
      - backend

  cache:
    image: memcached
    <<: *restart_policy
    networks:
      - backend

  proxy:
    <<: [*image, *restart_policy]
    command: "./docker/prod/proxy"
    ports:
      - "${PORT:-8080}:80"
    environment:
      APP_HOST: web
      OPENPROJECT_RAILS__RELATIVE__URL__ROOT: "${OPENPROJECT_RAILS__RELATIVE__URL__ROOT:-}"
      OPENPROJECT_HOST__NAME: "projects.wbhsgroup.com"
    depends_on:
      - web
    networks:
      - frontend

  web:
    <<: *app
    command: "./docker/prod/web"
    networks:
      - frontend
      - backend
    depends_on:
      - db
      - cache
      - seeder
    labels:
      - autoheal=true
    healthcheck:
      test: ["CMD", "curl", "-f", "http://projects.wbhsgroup.com:8080${OPENPROJECT_RAILS__RELATIVE__URL__ROOT:-}/health_checks/default"]
      interval: 10s
      timeout: 3s
      retries: 3
      start_period: 30s

  autoheal:
    image: willfarrell/autoheal:1.2.0
    volumes:
      - "/var/run/docker.sock:/var/run/docker.sock"
    environment:
      AUTOHEAL_CONTAINER_LABEL: autoheal

  worker:
    <<: *app
    command: "./docker/prod/worker"
    networks:
      - backend

    depends_on:
      - db
      - cache
      - seeder

  cron:
    <<: *app
    command: "./docker/prod/cron"
    networks:
      - backend
    depends_on:
      - db
      - cache
      - seeder

  seeder:
    <<: *app
    command: "./docker/prod/seeder"
    restart: on-failure
    networks:
      - backend
```