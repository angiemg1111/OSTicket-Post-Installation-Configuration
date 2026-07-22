# OSTicket Post-Installation Configuration

## Project Summary

**Description:** A configuration walkthrough covering the setup required to make a freshly-installed OSTicket instance operational for a real help desk team — roles, departments, agents, users, SLAs, and help topics.

**Languages:** N/A (Web-based admin panel configuration)

**Environments:** Windows 10 (Azure VM), local web server (OSTicket)

**Technologies/Services Used:** OSTicket

**Why this matters:** This configuration mirrors how a real  IT department would structure its help desk before going live — clear role-based access, department-based routing, and SLA tiers tied to business urgency. Getting this foundation right up front reduces misrouted tickets and support delays once the system is in active use — directly explored in the scenario walkthrough that follows this project.

---

## Overview

With OSTicket installed and the VM reachable via Remote Desktop, the next phase was configuring the help desk itself — building out the roles, teams, and workflows a real support organization would need before it could go live.

## Part 1: Configure Roles

Roles determine what an agent is permitted to do within OSTicket — view, create, edit, or delete tickets, tasks, and knowledgebase articles.

![Roles overview](images/image11.png)

1. Logged into OSTicket's Admin/Analyst panel at `http://localhost/osTicket/scp/login.php`.
2. From the agent panel (the default view for working tickets), navigated to the Admin Page via the top-right menu.

![Admin page](images/image13.png)

3. Went to **Agents → Roles → Add New Role**. This is where permissions get scoped to job function.

![Roles tab](images/image58.png)

4. Created a new role named **Supreme Admin**.

![Naming the new role](images/image16.png)

5. Assigned full permissions across Tickets, Tasks, and Knowledgebase, then saved the role.

![Assigning permissions](images/image37.png)
![Permission detail](images/image30.png)
![Role saved](images/image52.png)

## Part 2: Configure Departments

Departments categorize tickets by area of expertise; teams group agents across departments who collaborate on shared work.

![Departments overview](images/image48.png)

1. Went to **Agents → Departments → Add New Department**, set Parent to "Top Level Department," and named it **Sysadmins**.

![Creating Sysadmins department](images/image14.png)

2. Went to **Teams → Add New Team** and created a **Finance Team**.

![Creating Finance Team](images/image51.png)

## Part 3: Allow Anyone to Create Tickets

To let end users submit tickets without needing an account first:

1. Went to **Admin Panel → Settings → User Settings**.

![User settings](images/image43.png)

2. Confirmed **"Registration Required"** was unchecked, allowing any end user to open a ticket without registering.

![Registration setting unchecked](images/image26.png)

## Part 4: Configure Agents

Agents are the staff who respond to and resolve tickets. Four agents were added: Crystal Clear (SysAdmins), Al Beback (Support), Justin Time, and Blaze Hunter.

![Adding new agents](images/image25.png)

1. For each agent: entered first/last name, email, and username, and checked "Admin" to grant both admin and agent panel access.

![New agent form](images/image24.png)

2. Set each agent's primary department and role — e.g. Crystal Clear was assigned the **Supreme Admin** role, controlling her access level.

![Setting department and role](images/image12.png)

3. Assigned agents to teams — e.g. adding to the Finance Team.

![Assigning to a team](images/image28.png)

4. Followed the same process for the remaining agents, assigning each to the appropriate department, role, and team — for example, Al Beback was set up under the Support department with **View Only** access and added to the **Level 1 Support** team.

![Al Beback's access configuration](images/image9.png)

5. Set each agent's password directly (rather than emailing a reset link), unchecking "require password change at next login" for the test environment.

![Password confirmation](images/image50.png)
![Setting agent password](images/image17.png)

## Part 5: Configure Users

Users are the ticket owners — the end users submitting requests, as opposed to the agents resolving them.

1. From the Agent Panel, went to **Users → Add New**.

![Adding a new user](images/image49.png)

2. Created new users with full name and email address — Justin Time and Sue Flay were added as test end users.

![New user entries](images/image42.png)

## Part 6: Configure SLA

SLA (Service Level Agreement) plans define how quickly the help desk is expected to resolve tickets of a given severity.

1. Went to **Admin Panel → Manage → SLA**.

![SLA management](images/image32.png)

2. Added three SLA plans reflecting different severity levels:
   - **Sev-A** — 1-hour grace period, 24/7 schedule
   - **Sev-B** — 4-hour grace period, 24/7 schedule
   - **Sev-C** — 8-hour grace period, business hours (M–F)

![SLA plans configured](images/image7.png)
![SLA plan detail](images/image19.png)

## Part 7: Configure Help Topics

Help Topics are the categories end users select when submitting a new ticket.

1. Went to **Admin Panel → Manage → Help Topics**.

![Help Topics overview](images/image21.png)

2. Added top-level categories: **Feedback**, **General Inquiry**, and **Report A Problem** — each linked to the Support department under "New Ticket Options" tab. 

![Adding help topic categories](images/image10.png)

3. Added subcategories under "Report A Problem": Business Critical Outage, Personal Computer Issues, Access Issue, Equipment Request, Password Reset, and Other.

![Adding help topic subcategories](images/image31.png)

---

