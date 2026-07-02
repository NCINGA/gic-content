# NCPL_DS_PRJ_004_XHUMA_INTEGRATED_NDB(BRD)_(V2.4) 06_12_2026.docx.pdf

## Page 1

Xhuma : Integrated Platform 
With LIME​
Business Requirement Document (BRD) 
 
 
 
Classification: External Confidential

## Page 2

Document Revision History 
Version 
Date 
Updated By 
Update Details 
V1.0 
03.25.2026 
Nikil Jayasuriya 
Initial Draft Document 
V2.0 
05.22.2026 
Nikil Jayasuriya 
New Exclusions: 
On demand Customer initiated Calls : 
-​
Excluded from the solution and customers 
will not have the option to initiate 
on-demand calls 
-​
Manual Case Creation: Previously discussed 
migrating the standalone platform's 
functionality to allow agent-initiated KYC 
calls, but this has been omitted due to the 
decision not to proceed with the Change 
Request (CR). 
New Inclusions : 
-​
Dual Authorization: A Call Centre Manager 
can review and approve a call once the 
KYC call is completed and marked 
accordingly. 
-​
User Management: User management for 
the ISAM team with Requester and Approver 
options. 
-​
Dashboard Widgets: Finalized dashboard 
widgets to enhance the view of agent 
performance and customer feedback. 
-​
User Feedback Collection: Feedback 
collection from customers post-kyc call. 
V2.1 
01.06.2026 
Nikil Jayasuriya 
Incorporated Handling of returned calls by the 
manager and agent. 
V2.2 
09.06.2026 
Nikil Jayasuriya 
Omitting Dual Authorization Flow as discussed with 
the bank. This functionality is to be handled via 
Lime. 
1

## Page 3

V2.3 
11.06.2026 
Nikil Jayasuriya 
Addressing NDB Comments 
-​
Omitting Call Centre Manager Role and 
distributing role permissions amount KYC 
Agent Inputter and Authorizer. 
-​
Documentation and API Integration List 
Update 
V2.4 
12.06.2026 
Nikil Jayasuriya 
Addressing feedback collected on 12th June 2026 
-​
Incorporated Dual Approval for Admin 
Config Changes. 
-​
Incorporated changes to accommodate 
agent based rescheduling outside of 
working hours. 
-​
Incorporated changes to accommodate 
auto-cancellation in scenarios of 
customer-no show and 
customer-abandonment scenarios. Agent 
will be allowed to stop auto-cancellation 
and proceed to take the call or reschedule. 
-​
Agent no-show timing configuration 
change. 
 
2

## Page 4

Table of Contents 
 
1. Background​
5 
2. Purpose of Document​
5 
3. Project Overview​
6 
3.1. Alignment Business Goals and Objectives​
6 
3.2 Project Scope​
6 
3.2.1. In-Scope Functionality​
6 
3.2.1.1. Core Integration with Lime Platform​
6 
3.2.1.2. Customer-Facing Experience & Scheduling​
7 
3.2.1.3. Backend Automation & Logic​
7 
3.3 Definitions, Acronyms and Abbreviations​
7 
3.4 Assumptions, Dependencies, Constraints​
9 
4. Functional Requirements​
12 
5. Functionalities of Xhuma Integrated Solution​
17 
5.1 Customer View​
17 
5.1.1. VKYC
(Video Know Your Customer - a digital process to verify your identity over a video call) Session Initiation​
17 
5.1.2. Appointment Scheduling Flow​
17 
5.1.3. Appointment Management​
19 
5.1.4. The VKYC Call Experience & Post-Call​
20 
5.2 KYC Agent Inputter View​
23 
5.2.1. Agent Dashboard and Status Management​
23 
5.2.2. Session/Call Handling and Notifications​
24 
5.2.3. Sessions Tab and Viewing Customer Data​
24 
5.2.4. In-Call Interface​
25 
5.2.5. Acceptance of KYC​
26 
5.2.5. Agent-Initiated Cancellation​
28 
5.2.6. Handling Returned Calls​
29 
5.2.7 Agent Call Rescheduling​
29 
5.3 KYC Agent Authorizer View​
29 
5.3.1. Real-time Monitoring Dashboard​
29 
5.3.2. View Historical Data​
31 
5.3.3 Agent Segmentation​
31 
5.4. System Administrator View​
32 
5.4.1. Administrator-Inputter​
32 
5.4.1.1 Slot and Schedule Management (KYC Time Management)​
32 
5.4.1.2. KYC Verification Threshold Configuration​
33 
3

## Page 5

5.4.1.3 Content Configuration​
34 
5.4.1.3.1 Customer Consent Message​
34 
5.4.1.3.2 VKYC SMS Template​
34 
5.4.1.3.3 VKYC Email Template​
34 
5.4.2 Administrator - Authorizer​
35 
5.5 User Management​
35 
5.5.1 User Management (Requester)​
35 
5.5.2 User Management (Approver)​
35 
5.6 System View​
36 
5.6.1. Customer No-Show Workflow​
36 
5.6.2. Call Abandonment Workflow​
37 
5.6.3. Agent No-Show Workflow​
38 
6. Non-Functional Requirements​
39 
6.1. Performance​
39 
6.2. Application Security​
39 
6.3. Application Stability and Resilience​
40 
6.4. Usability and Accessibility​
40 
6.5. Audit and Logging Generation​
41 
6.6 Maximum Agent Access​
41 
6.7 Maximum Calls per Monthly​
41 
7. Documentation Requirements​
41 
7.1. Business Requirement Document (BRD)​
42 
7.2. Scope of Work (SoW)​
42 
7.3 Quality Assurance (QA) Report​
42 
7.4 UAT Deployment Guide​
42 
7.5 Production Deployment Guide​
42 
7.6 Release Notes​
42 
7.7 Production Release Note​
43 
7.7. User Manual​
43 
8. Integration Requirements​
43 
8.1. Lime Onboarding Platform (Lime)​
43 
8.2 Internal Communication Integrations​
44 
8.3. Azure Active Directory Integration​
44 
8.4 External Third-Party Integrations (Xhuma General API)​
45 
9. User Permissions​
45 
10. Sign off​
47 
 
4

## Page 6

1. Background 
NDB Bank is undertaking a strategic initiative to create a fully integrated, digital customer 
onboarding experience. The core of this project is the deep, two-way integration between the 
NCINGA Xhuma Video Know Your Customer (VKYC) platform and NDB's primary digital 
onboarding platform, Lime. 
The project's vision is to deliver a seamless, automated, and truly customer-centric journey. By 
shifting to a process that is driven by the customer, this solution will introduce a new level of 
flexibility and convenience. 
Through capabilities such as customer-led scheduling, and intelligent backend automation, this 
project aims to significantly enhance the customer experience, increase internal operational 
efficiency, and provide greater management oversight for NDB's VKYC operations. 
This Business Requirements Document (BRD) will formally define the scope, functionalities, and 
detailed requirements necessary to build and deliver this integrated solution. 
2. Purpose of Document 
The purpose of this Business Requirements Document (BRD) is to formally define and detail the 
business, functional, and non-functional requirements for the NDB Xhuma Integrated Solution. 
 
This document will serve as the single source of truth for the project scope and will be the foundational 
guide for all subsequent project activities, including: 
 
●​
The creation of the detailed solution architecture and technical design. 
●​
The development and configuration of the software by the NCINGA and Lime development 
teams. 
●​
The creation of test cases for the Quality Assurance (QA) and User Acceptance Testing (UAT) 
phases. 
●​
The formulation of the official Statement of Work (SoW) for this project phase. 
 
This BRD is intended for all project stakeholders, including business and IT teams at NDB Bank, the 
NCINGA project team, and the Lime integration team, to ensure a complete and shared understanding 
of the project's objectives and deliverables before development commences. 
 
5

## Page 7

3. Project Overview 
 
3.1. Alignment Business Goals and Objectives 
The development of the NDB Xhuma Integrated Solution is driven by a set of clear business goals 
designed to elevate NDB's digital onboarding capabilities. This project directly aligns with the bank's 
strategic objectives by focusing on the following key areas: 
Enhance Customer Experience and Choice: 
-​
To provide customers with unparalleled flexibility by offering them the choice to complete their 
VKYC verification at their convenience via a self-service scheduling system. 
-​
To create a seamless, frictionless, and premium end-to-end digital journey by deeply 
embedding the VKYC process within the Lime onboarding platform, thereby eliminating jarring 
transitions and manual data re-entry. 
Increase Operational Efficiency through Automation: 
-​
To significantly reduce the manual administrative burden on NDB agents and supervisors by 
automating the entire call scheduling, routing, and agent assignment process. 
-​
To improve data accuracy and processing speed by enabling the seamless, automated flow of 
customer information between the Lime and Xhuma platforms. 
Improve Management Oversight and Future Scalability: 
-​
To empower team leaders with enhanced visibility and control by providing real-time 
dashboards for monitoring agent performance, call queues, and overall operational health. 
-​
To build a scalable and robust architecture capable of handling future growth in customer 
onboarding volumes without requiring a linear increase in staff or manual intervention. 
3.2 Project Scope 
 
3.2.1. In-Scope Functionality 
The scope of this project is to develop and deploy the integrated VKYC solution. The following modules, 
features, and functionalities are in scope for this phase in addition to the base Xhuma solution. 
3.2.1.1. Core Integration with Lime Platform 
6

## Page 8

●​
Development of a robust, two-way API integration layer between the Lime digital onboarding 
platform and the NCINGA Xhuma VKYC solution. 
●​
Seamless transfer of customer data from Lime to Xhuma, including customer 
preference/segment and the reason for the KYC meeting. 
●​
Automated updates sent from Xhuma back to the Lime platform upon the completion or 
change in status of a VKYC session. Updates will include the final status (e.g., ‘PASS’ or ‘FAIL’ ') in 
the case of rejection, a reason for the outcome and ‘ESCALATE’ if the agent has an additional 
comment to provide to calls marked as Fail. 
 
3.2.1.2. Customer-Facing Experience & Scheduling 
●​
Customers will be presented with a calendar view of available agent time slots and can 
schedule, reschedule, or cancel their VKYC appointment. 
Automated SMS and/or email notifications for appointment confirmation via Lime. A reminder 
notification will be sent 10 minutes prior to the scheduled call via Lime 
3.2.1.3. Backend Automation & Logic 
●​
Slot Management Engine: A backend service to manage agent schedules, shifts, working hours, 
and real-time availability. 
●​
Intelligent Call Routing: Automated assignment of incoming customer sessions to the 
appropriate available agent. 
●​
Negative Path Handling: Implementation of automated workflows to manage scenarios such as 
customer no-shows and abandoned calls. This also includes a workflow to manage scenarios 
where an agent fails to join a scheduled call, including notifications to the VKYC Authorizer. 
 
3.3 Definitions, Acronyms and Abbreviations 
 
Definitions: 
 
Term 
Definition 
Agent - Authorizer 
A user with supervisory permissions responsible for monitoring operations, 
managing agent segments, approving status changes, and handling 
escalations. 
7

## Page 9

Agent - Inputter 
A user responsible for conducting the end-to-end VKYC calls with 
customers, including data verification and session management. 
Dual Approval 
A security process requiring two distinct users (an Inputter and an 
Authorizer) to complete a task, ensuring checks and balances for critical 
changes. 
Lime Platform 
NDB's primary digital customer onboarding platform, which is the main 
system integrating with Xhuma for a seamless customer journey. 
Session 
A single, end-to-end VKYC interaction, from the moment a customer joins 
the call until the final outcome (Pass, Fail, Escalate, etc.) is determined. 
Slot Management 
Engine 
The backend component of Xhuma responsible for calculating and 
managing available time slots for VKYC appointments based on agent 
schedules and holidays. 
System 
Administrator 
A user role responsible for configuring core system settings, such as 
operational hours, verification thresholds, and content templates. This role is 
split into an "Inputter" and an "Authorizer" for dual approval. 
User Manager 
A role responsible for managing user accounts within the Xhuma platform, 
split into a "Requester" and an "Approver" for dual control over user creation 
and permissions. 
Xhuma 
The Video Know Your Customer (VKYC) platform provided by NCINGA, which 
is the core subject of this integration project. 
 
Abbreviations: 
 
Abbreviation 
Description 
AD 
Active Directory 
AHT 
Average Handling Time 
API 
Application Programming Interface 
ASM 
Assumption 
AWS 
Amazon Web Services 
BRD 
Business Requirement Document 
CON 
Constraint 
CR 
Change Request 
DEP 
Dependency 
8

## Page 10

IT 
Information Technology 
JSON 
JavaScript Object Notation 
KYC 
Know Your Customer 
LAN ID 
Local Area Network Identifier 
LOS 
Loan Origination System 
NDB 
National Development Bank 
NIC 
National Identity Card 
OCR 
Optical Character Recognition 
OWASP 
Open Web Application Security Project 
QA 
Quality Assurance 
S3 
Simple Storage Service (AWS) 
SAML 
Security Assertion Markup Language 
SLA 
Service Level Agreement 
SMS 
Short Message Service 
SoW 
Scope of Work 
SQL 
Structured Query Language 
SSO 
Single Sign-On 
UAT 
User Acceptance Testing 
UI 
User Interface 
VAPT 
Vulnerability Assessment and Penetration Test 
VKYC 
Video Know Your Customer 
XSS 
Cross-Site Scripting 
 
3.4 Assumptions, Dependencies, Constraints 
Reference ID 
Assumption / Dependency / Constraint 
Assumptions 
ASM-01 
The functional requirements detailed in this Business Requirements Document (BRD) 
are complete and accurately reflect NDB's needs for this project phase. 
9

## Page 11

ASM-02 
The core AI verification services within the Xhuma platform (OCR, Facial Similarity, 
Liveness Detection) are considered stable and will not require modification. 
ASM-03 
All necessary internal business, IT, and security stakeholders from NDB will be made 
available for timely consultation, feedback, and decision-making. 
ASM-04 
If the captured image is unclear, the agent ensures that they retake the image upon 
previewing the picture from the platform. In the instance where the customer’s selfie 
is captured, it is recommended that the agent ensures clothing or accessories 
covering the individual's face are removed (ex: glasses, caps, etc.). The system would 
support in a case such as above however the accuracy of the verifications would 
have been impacted. 
Dependencies 
DEP-01 
(Dependency on NDB) Timely provisioning, configuration, and management of the 
required AWS cloud environments (Sandbox and Production). 
DEP-02 
(Dependency on NDB) Providing the NCINGA team with secure and timely access to 
the AWS environments and any required third-party services (e.g., SMS/Email 
gateways). 
DEP-03 
(Dependency on NDB) Allocation of dedicated business users to define UAT 
scenarios, execute User Acceptance Testing, and provide consolidated feedback 
within the agreed-upon project schedule. 
DEP-04 
(Dependency on Lime) Timely development and delivery of all required APIs on the 
Lime platform to enable the two-way integration specified in this BRD. 
DEP-05 
(Dependency on Lime) Provision of clear, accurate, and comprehensive API 
documentation for all required integration points. 
DEP-06 
(Dependency on Lime) A stable and accessible sandbox environment for the Lime 
platform must be available for NCINGA to perform integration development and 
testing. 
DEP-07 
(Dependency on Lime) The availability of a designated technical point of contact 
from Lime to support joint integration testing and resolve any API-related issues. 
Constraints 
10

## Page 12

CON-01 
The project scope is strictly limited to the functional and non-functional 
requirements defined within this BRD. Any request for additional functionality will be 
subject to a formal Change Control Process. 
CON-02 
All project activities must be completed within the timeline agreed upon in the final 
Project Plan and Statement of Work (SoW). 
CON-03 
The project must be delivered within the budget defined in the final commercial 
agreement for this project phase. 
CON-04 
The solution will be delivered as a purely browser-based experience. The 
development of a native mobile application (iOS/Android) is explicitly a constraint 
and out of scope. 
CON-05 
The solution must be designed to be deployed on NDB's existing AWS infrastructure 
and must adhere to NDB's established IT security and architectural standards. 
 
 
11

## Page 13

4. Functional Requirements 
 
Req. ID 
Feature 
Detailed Functional Requirements 
CUST-1.0 
VKYC Initiation 
1.1: The Lime platform shall present the customer with an 
option to schedule Video KYC after they have completed the 
initial data entry steps. 
1.2: The customer shall be presented with an option to 
“Schedule Call”. 
1.3: Lime should collect and share the customer 
preference/segment 
1.4: Lime should collect and share the reason for the KYC 
meeting regardless of the option selected 
CUST-2.0 
Appointment 
Scheduling Flow 
2.1: Upon selecting "Schedule Call," the customer shall be 
presented with a calendar interface with selectable timeslots 
for 7 days ahead. 
2.2: The calendar must display available VKYC time slots 
based on pre-configured agent availability and schedules. 
2.3: The customer shall be able to select an available date 
and time slot and confirm their booking. 
2.4: Upon confirmation, Lime must send an immediate SMS 
and/or Email confirmation of the appointment, including the 
date, time, and a checklist of required documents. 
2.5: A reminder notification (SMS/Email) containing the 
secure session link shall be automatically sent to the 
customer at a pre-configured interval (10 minutes) before 
the scheduled appointment. 
CUST-3.0 
Appointment 
Management 
3.1: The customer must have a way to view their upcoming 
scheduled appointment within the Lime platform. 
3.2: The customer must have the ability to reschedule their 
appointment, which will take them back to the calendar view 
to select a new slot. 
3.3: The customer must have the ability to cancel their 
appointment. 
3.4: Lime needs to communicate to Xhuma based on 
cancellation or reschedulement that takes place and follow 
the defined workflow 
12

## Page 14

CUST-4.0 
In-Call Experience 
4.1: Before the call connects, the customer must be presented 
with and accept a mandatory Consent Agreement. 
4.2: The interface and agent shall guide the customer 
through the required steps (e.g., "Please show the front of 
your NIC," "Please look at the camera"). 
4.3: The customer shall receive real-time visual feedback on 
their screen (e.g., "Liveness check successful," "Image 
captured"). 
4.4: At the end of the call, the customer shall be presented 
with an optional feedback mechanism (e.g., star rating, 
comment box). 
AGENT_IN
PUT-1.0 
Unified Dashboard 
(Real-time) 
1.1: The agent's dashboard shall display their current status 
(e.g., "Available," "On Call," "Unavailable"). By default it will be 
"Available". 
1.2: Agents must be able to manually change their status (to 
"Out-of-Office" when on leave). 
1.3: The dashboard shall automatically accept and present 
incoming calls to an "Available" agent. 
1.4: An instant notification will be sent in the application when 
a call session is created with session details to the agent 
.1.5 Once a call has been scheduled, the agent should be able 
to view the customer data received from Lime in the 
"sessions" tab. 
AGENT_IN
PUT-2.0 
In-Call Interface 
2.1: When a call starts, the agent's screen must be 
pre-populated with all customer data received from the Lime 
platform. 
2.2: The interface must provide the agent with controls to: 
- Capture images of the customer's face, ID card 
(front/back), signature, and other required documents in the 
form of images. 
- Manually trigger AI verification and Liveliness checks 
- View the results of the AI checks (e.g., Facial Similarity 
Score). 
2.3: The questionnaire will be available on Lime and the agent 
will fill the questionnaire based on the product. 
2.4: Agent refers to the Lime Interface to view the documents 
uploaded at the time of onboarding for verification 
2.5: Agent marks document verification status with respect to 
13

## Page 15

the document verified 
AGENT_IN
PUT-3.0 
Acceptance of KYC 
3.1 If the KYC ratings are above the threshold the call will be 
automatically marked as "PASS" and if below the threshold, 
the call will be marked as “FAIL” 
3.2 Even if the ratings are below the defined threshold value, 
the agent can override the call as "ESCALATE" with a note 
which will be shared with Lime. 
AGENT_IN
PUT-4.0 
Agent Cancellation 
4.1 An agent can cancel within 60 minutes (1 hours) prior to a 
scheduled call 
4.2 The KYC Agent will follow the manual agent reassignment 
flow to accommodate the cancellation request 
4.3. The KYC Agent can view the scheduled time and other 
available agents and assign the call accordingly 
4.4 The newly assigned agent will receive a notification within 
the platform once a new call has been assigned 
AGENT_IN
PUT-5.0 
Handling Returned 
Calls 
5.1 Once a completed KYC call is returned to the agent via 
Lime, the agent can reschedule the call to an available time 
and take the call. 
AGENT_IN
PUT-6.0 
Agent Call 
Rescheduling 
6.1 An agent is able to reschedule calls and it’s assumed the 
agent ensures the customer availability prior to rescheduling. 
AGENT_AU
TH-1.0 
Unified Dashboard 
(Real-time) 
1.1: The Agent Authorizer shall have a dedicated dashboard 
providing a real-time, holistic view of the VKYC operation. 
1.2: The dashboard must display: 
- Overall Daily Summary 
- Agent / Interview Officer Performance Metrics 
- Real-Time Queue Monitoring 
- Customer Experience Metrics 
- Export & Reporting Options 
- Agent KPIs 
AGENT_AU
TH-2.0 
 Viewing Historical 
Data 
2.1:. For historical data, the Agent Authorizer will be allowed to 
view all the cases. 
AGENT_AU
TH-3.0 
Assigning Agent 
Segments 
3.1 The Agent Authenticator has the privilege to add the 
agent segment which will denote how the call assignments 
will take place. 
14

## Page 16

ADMIN_IN
PUT-1.0 
KYC Session Time 
Management 
1.1: The system must allow an Administrator to configure 
agent working hours, and holidays. 
1.2: This engine will be the source of truth that feeds the 
"available slots" to the customer-facing calendar. 
1.3: It must intelligently calculate availability based on existing 
appointments and agent schedules. By default the system 
will have a ~10 minutes buffer for sessions 
ADMIN_IN
PUT-2.0 
KYC Status Threshold 
Management 
2.1 Configure minimum threshold to mark KYC call 
completion status for Liveliness Checks [Default - 70%] and 
Similarity Checks [Default - 42%] 
ADMIN_AU
TH-1.0 
Configuration Change 
Approval 
1.1 All configuration changes will be subject to dual approval 
by the Admin Authorizer. 
USER_MAN
AGER-1.0 
User Manager 
(Requester Role) 
1.1 A user manager with permission to request for a user can 
add a user by specifying the relevant LAN ID. (via SAML 
integration) 
1.2 A user manager (requester) can also specify the user role 
to be assigned for the user. 
USER_MAN
AGER-2.0 
User Manager 
(Approver Role) 
2.1 A user manager (approver) accepts or rejects the 
requests which will be queued by all requesters. 
SYS-1.0 
Customer No-Show 
1.1: If a customer does not join their scheduled call within a 
time limit (15 minutes), the appointment shall be 
automatically marked as "Cancelled". 
1.2: Xhuma communicates to Lime on customer no-show 
incident and the customer will be notified accordingly. 
1.3 In a case the customer manages to notify the agent that 
they are able to join the call, the agent would be able stop 
the auto-cancellation and remain in the call. 
1.4 In a case the customer manages to notify the agent that 
they wish to reschedule, the agent may reschedule the 
session to an available timeslot. 
SYS-2.0 
Customer 
Abandonment 
2.1: Call Abandonment: If a customer drops an active call, the 
case shall be marked as "Incomplete" and rules for a new 
session will be followed. 
2.2 In a case the customer manages to notify the agent that 
they are able to join the call, the agent would be able stop 
the auto-cancellation and remain in the call. 
2.3 In a case the customer manages to notify the agent that 
15

## Page 17

they wish to reschedule, the agent may reschedule the 
session to an available timeslot. 
SYS-3.0 
Agent No-show 
3.1: If an agent does not join within 5 minutes, the call centre 
agents will have the chance re-assign to an available agent 
3.2 : If no agent joins within 10 minutes, the call will be marked 
as "Incomplete" 
 
16

## Page 18

5. Functionalities of Xhuma Integrated Solution 
5.1 Customer View 
The customer journey is designed to be seamless and intuitive. While the user interface is developed 
and owned by Lime, the experience is powered by a set of robust APIs provided by Xhuma. 
5.1.1. VKYC Session Initiation 
The VKYC journey begins within the NDB Lime platform after the customer has completed the initial 
data entry stages. The Lime platform is responsible for capturing all necessary data before handing the 
customer over to the Xhuma VKYC experience. 
●​ CUST-1.1: The Lime platform shall present the customer with an option to begin Video KYC upon 
completion of the initial data entry steps. 
●​ CUST-1.2: The customer shall be presented with the option to “Schedule Call”. 
●​ CUST-1.3: The Lime platform must collect and share the customer's defined preference or 
segment (e.g., Islamic Banking, Language Preference and Gender.). 
●​ CUST-1.4: The Lime platform must also collect and share the specific reason for the KYC meeting 
(e.g., New Account Opening, Address Update). 
 
This information is then passed to Xhuma when a session is created, as shown in the API examples 
below. 
5.1.2. Appointment Scheduling Flow 
When the customer selects "Schedule Call", the Lime platform initiates the appointment booking 
workflow, which is powered by a series of API calls to the Xhuma platform. 
 
●​
CUST-2.1 & CUST-2.2: To display the scheduling calendar, Lime will call a Xhuma API to retrieve a 
list of available appointment slots. The API will provide selectable time slots for the next 7 days, 
based on real-time agent availability and pre-configured schedules. 
 
API Interaction Example: Book Appointment 
●​
Endpoint: POST /api/v1/schedules/book 
●​
Request from Lime: 
 
{ 
 "customer_id": "NDB123456", 
 "customer_name": "Pranitha Muralitharan", 
17

## Page 19

"customer_nic": "199012345678", 
 "language_preference": "English", 
 "islamic_banking": FALSE, 
 “gender” : “FEMALE” 
 “Segment” : “VIP” 
} 
 
API Interaction Example: Get Available Slots 
●​
Endpoint: GET /api/v1/schedules/availability 
●​
Response from Xhuma to Lime: 
 
{ 
 "availability": { 
 "2026-04-08": ["14:00", "14:30", "15:00"], 
 "2026-04-09": ["09:00", "09:30"], 
 // ... up to 7 days of data 
 } 
} 
●​
CUST-2.3: The customer shall be able to select an available date and time slot and confirm their 
booking via the Lime interface. Upon confirmation, Lime will call an API to book the appointment 
in the Xhuma system. 
 
API Interaction Example: Booking Confirmation 
●​
Endpoint: POST /api/v1/schedules/book/confirmation 
●​
Response from Lime: 
 
{ 
 "confirmed_slot": "2026-04-08T14:00:00Z", 
 "customer_id": "NDB123456", 
 "customer_name": "Pranitha Muralitharan", 
 "customer_nic": "199012345678", 
 "language_preference": "English", 
 "islamic_banking": FALSE, 
 “gender” : “FEMALE” 
 “Segment” : “VIP” 
 "kyc_reason": "New Account Opening" 
 "reference_id": "LIME4321"​
 //reference id in LIME/LOS 
} 
 
●​
CUST-2.4: Upon receiving a successful booking confirmation from Xhuma, the Lime platform is 
responsible for sending an immediate SMS and/or Email confirmation to the customer. This 
confirmation should include the appointment date, time, and a checklist of required documents. 
18

## Page 20

API Interaction Example: Booking Confirmation 
●​
Endpoint: GET /api/v1/schedules/book/confirmation 
●​
Response from Xhuma to Lime: 
 
{ 
 "session_id": "XHUMA_APPT_xyz789", 
 "status": "CONFIRMED", 
 "confirmed_slot": "2026-04-08T14:00:00Z", 
 "session_url": "https://vkyc.ndb.com/session/xyz789", 
 "agent_name": "ThinugaW" 
} 
 
●​
CUST-2.5: The Xhuma backend will be responsible for automatically sending a final reminder 
notification (SMS/Email) to the customer 10 minutes before the scheduled appointment. This 
reminder will contain the secure session link (session_url) for joining the call. 
5.1.3. Appointment Management 
To allow customers to manage their booked appointments, Lime will provide the front-end interface, 
which will be powered by a set of APIs from Xhuma for viewing, rescheduling, and cancelling sessions. 
 
●​
CUST-3.1: To allow the customer to view the details of their upcoming appointment within the 
Lime platform, Lime will call a Xhuma API to retrieve this information. 
 
API Interaction Example: Get Appointment Details 
●​
Endpoint: GET /api/v1/schedules/manage/{session_id} 
●​
Response from Xhuma to Lime: 
 
{ 
 "status": "CONFIRMED", 
 "confirmed_slot": "2026-04-12T14:00:00Z" 
 "session_url": "https://vkyc.ndb.com/session/xyz789", 
 "agent_name": "ThinugaW", 
} 
 
●​
The “status” will indicate the real-time status of the KYC call and the current assignment of the 
case. The case status will have the following statuses, 
○​
CONFIRMED : Call has been scheduled and is to be taken. 
○​
PASS : Call has met the minimum requirements set by the Bank 
○​
FAIL : Call has not met the minimum requirements set by the Bank 
19

## Page 21

○​
ESCALATE : Call has not met the minimum requirements set by the Bank and has been 
escalated by inputted to approver 
○​
CANCELLED : Call has been cancelled by Agent/Customer or there has been a no-show. 
 
●​
CUST-3.2 & CUST-3.3: The customer must have the ability to either Reschedule or Cancel their 
appointment through the Lime interface. 
 
●​
CUST-3.4: In either case, the Lime platform is responsible for communicating this action to the 
Xhuma system via the appropriate API endpoint to ensure the agent's schedule is updated. 
○​
Cancellation: When a customer cancels, Lime will call the cancellation endpoint. 
○​
Reschedule: The reschedule workflow will be a two-step process initiated by Lime: 
■​
First, call the "Cancel Appointment" endpoint for the existing appointment. 
■​
Then, redirect the customer back to the calendar view to book a new slot, 
following the booking process defined in section 5.1.2. 
 
API Interaction Example: Cancel Appointment 
●​
Endpoint: POST /api/v1/schedules/manage/cancel 
●​
Request from Lime: 
 
{ 
 "session_id": "XHUMA_APPT_xyz789" 
} 
 
●​
Response from Xhuma to Lime: 
 
{ 
 "status": "CANCELLED" 
 "reason": "CUSTOMER_CANCELLATION" 
} 
 
5.1.4. The VKYC Call Experience & Post-Call 
Once the customer joins the session via the secure link, they enter the Xhuma VKYC interface, which is 
designed to be secure and user-friendly. 
 
●​
CUST-4.1: Before the video session connects to an agent, a mandatory Consent Agreement 
screen will be displayed. The customer must explicitly accept the terms to proceed with the call. 
The consent message can be configured by the system administrator. 
20

## Page 22

●​
CUST-4.2: During the call, the customer will be guided through the required steps. This guidance 
is provided verbally by the agent and supported by clear, simple on-screen instructions within 
the Xhuma interface (e.g., "Please show the front of your NIC," "Please look at the camera"). 
 
●​
CUST-4.3: To create a clear and interactive experience, the customer will receive real-time 
visual feedback on their screen to confirm the successful completion of key actions (e.g., a 
green checkmark and the text "Liveness check successful," or "Image captured"). 
 
21

## Page 23

●​
CUST-4.4: Upon the conclusion of the call, the customer will be automatically redirected to a 
final screen where they can provide optional feedback. This mechanism will include a star rating 
system and a text box for comments. 
 
22

## Page 24

5.2 KYC Agent Inputter View 
5.2.1. Agent Dashboard and Status Management 
The agent's main landing page is the Unified Dashboard, which provides an at-a-glance view of their 
status and upcoming sessions. 
●​ AGENT_INPUT-1.1: The dashboard shall clearly display the agent's current status. The available 
statuses are: 
●​ Available (This is the default status). 
●​ On Call 
●​ Unavailable 
●​ AGENT_INPUT-1.2: The agent must have the ability to request a status change to "Unavailable" 
(e.g., when applying for leave). 
 
23

## Page 25

●​ Note : An agent will only be able to apply for a leave if they do not have any calls assigned to 
them. They may manually assign if any calls are there to available agents. 
 
 
5.2.2. Session/Call Handling and Notifications 
The system will automatically manage how agents are notified of and receive calls based on the call 
type. 
●​ AGENT_INPUT-1.3: When an agent's status is "Available," the system will automatically accept 
and present incoming calls to them. 
●​ AGENT_INPUT-1.4: The notification logic will be as follows for all scheduled calls : 
●​ As a call gets scheduled, the agent will receive an in-app notification (an email can be 
triggered for the same action) to notify the agent of a new call. 
●​ Additionally an instant in-application notification, containing the session details, will be sent 
directly to the assigned agent, 
●​ at the time of the scheduled call 
●​ at the moment the customer joins the session 
5.2.3. Sessions Tab and Viewing Customer Data 
The "Sessions" tab is the agent's primary organizational tool for managing their workload. 
●​ AGENT_INPUT-1.5: The Agent Portal will feature a "Sessions" tab. This tab will contain the 
following view or table: 
●​ Scheduled Calls Table: For upcoming, scheduled calls, the agent will be able to view the 
customer data received from Lime in advance of the call starting. 
24

## Page 26

5.2.4. In-Call Interface 
Upon starting a session, the agent is presented with the Xhuma In-Call Interface. This is the primary 
workspace for conducting the live video verification. However, for certain tasks, the agent will need to 
refer to the corresponding Lime interface, creating a dual-screen or multi-tab workflow. 
 
●​ AGENT_INPUT-2.1: When a call starts, the Xhuma interface will be pre-populated with all 
relevant customer data passed from the Lime platform (e.g., Customer Name, NIC, etc.). This 
data will be displayed in a dedicated, read-only section for easy reference. 
●​ AGENT_INPUT-2.2: The Xhuma interface must provide the agent with a core set of VKYC controls 
to: 
●​ Capture images of the customer's face, ID card (front and back), their signature on a 
blank paper, and any other required supplementary documents as images. 
●​ Manually trigger the AI verification and Liveliness checks if required. 
●​ View the real-time results and confidence scores of the AI checks (e.g., Facial Similarity 
Score) within the Xhuma interface. 
 
●​ AGENT_INPUT-2.3: (Interaction with Lime) The compliance questionnaire is not part of the 
Xhuma interface. The agent will be required to switch to the Lime application interface to view 
and fill out the questionnaire relevant to the customer's product selection. The in-app 
questionnaire will be available in Xhuma if required but will be disabled as it is available in Lime. 
25

## Page 27

●​ AGENT_INPUT-2.4: (Interaction with Lime) To verify documents submitted by the customer 
during the initial onboarding steps, the agent will need to refer to the Lime interface, where these 
documents are stored. 
●​ AGENT_INPUT-2.5: After visually verifying a document shown by the customer on video against 
the version stored in the Lime system, the agent must mark the verification status for that 
document within the Xhuma interface by taking snapshots of the relevant documents in the 
real-time video call. 
 
 
5.2.5. Acceptance of KYC 
This section outlines the business rules for determining the final outcome of the VKYC session, blending 
automated scoring with essential agent oversight and discretion. 
 
●​
AGENT_INPUT-3.1: The system shall automatically determine the call outcome based on a 
pre-configured threshold for the KYC verification scores (e.g., facial similarity score). If the final 
combined KYC rating is above this threshold, the session status will be automatically set to 
"PASS". 
 
API Interaction Example: KYC Pass Webhook 
●​
Webhook from Xhuma to Lime: 
 
{ 
 "session_id": "XHUMA_APPT_xyz789", 
 "status": "PASS", 
 "timestamp": "2026-04-12T14:11:00Z" 
 "face_similarity_score": "99%", 
26

## Page 28

"liveliness_check_score": "80%", 
... ​ ​
​
​
​
//Other KYC Parameters 
 "kyc_report": "URL_ACCESS_TO_EXTRACT_DOCUMENT" 
 “agent_name” : ThinugaW 
} 
 
●​
AGENT_INPUT-3.2: In cases where the final KYC rating is below the defined threshold, the system 
will suggest a "FAIL" status. However, the system must provide the agent with the functionality to 
manually override this outcome. 
○​
When an agent chooses to override and change the status to "ESCALATE", a mandatory 
text box will appear, requiring the agent to enter a clear justification or note explaining 
the reason for the override. 
 
API Interaction Example: KYC Escalate Webhook 
●​
Webhook from Xhuma to Lime: 
 
{ 
 "session_id": "XHUMA_APPT_xyz789", 
 "status": "ESCALATE", 
 “reason” : “Provided documentation is not visible enough” 
 "timestamp": "2026-04-12T14:11:00Z" 
 "face_similarity_score": "99%", 
 "liveliness_check_score": "33%", 
... ​ ​
​
​
​
//Other KYC Parameters 
 "kyc_report": "URL_ACCESS_TO_EXTRACT_DOCUMENT" 
 “agent_name” : ThinugaW 
} 
 
●​
For calls to which the agent decides to leave as “FAIL”. The reason for rejection will be 
auto-generated from Xhuma however the agent can optionally specify the reason for rejecting 
the KYC for the customer. 
 
API Interaction Example: KYC Rejection Webhook 
●​
Webhook from Xhuma to Lime: 
 
{ 
 "session_id": "XHUMA_APPT_xyz789", 
 "status": "FAIL", 
 "reason": "The document you submitted is not in its original form.Please 
provide the original version.", 
 "timestamp": "2026-04-12T14:11:00Z" 
 “Agent_name”: ThinugaW 
} 
 
27

## Page 29

5.2.5. Agent-Initiated Cancellation 
This section outlines the process for an agent to request a cancellation for a scheduled call and 
proceed to assign an available agent. 
●​ AGENT_INPUT-4.1: For any upcoming scheduled call, the agent will have the option to request a 
cancellation. This option will only be enabled if the request is made at least 60 minutes (1 hour) 
prior to the scheduled start time of the call. 
●​ Within the "Sessions" tab, next to each scheduled call, there will be a "Request 
Cancellation" button. This button will be disabled and greyed out if the call is less than 60 
minutes away. 
 
 
●​ AGENT_INPUT-4.2: When an needs to proceed on a cancellation, the request will only go 
through if they are able to manually re-assign the call to another available agent themselves. 
●​ AGENT_INPUT-4.3 : When re-assigning the call, the agent can view a list of the available agents 
at the time and proceed to assign the said agent for the same timeslot. 
API Interaction Example: Agent Re-assignment Webhook 
●​
Webhook from Xhuma to Lime: 
 
{ 
 "session_id": "XHUMA_APPT_xyz789", 
 "status": "CONFIRMED" 
 “agent” : ViduraK 
} 
 
●​ AGENT_INPUT-4.4 : The re-assigned agent will receive a notification within the platform once 
the call has been re-assigned to them. 
28

## Page 30

5.2.6. Handling Returned Calls 
Once LIME notifies Xhuma of a returned call, the agent will be notified of a returned call in the returned 
call queue. The agent will then proceed to communicate with the customer and reschedule the call to 
a feasible time for the customer and agent. The agent can only schedule these calls to an available 
slot on their calendar. 
 
NOTE : It is assumed the agent will manually call the customer to check for the customer’s available 
time to reserve a time slot. 
5.2.7 Agent Call Rescheduling 
●​
AGENT_INPUT-6.1 : An agent may proceed to reschedule a call for the following requests for a 
customer request only which would happen outside of Xhuma (via phone call), in such a 
scenario, the agent may review available timeslots and book the meeting 
 
API Interaction Example: Agent Reschedule Webhook 
●​
Webhook from Xhuma to Lime: 
 
{ 
 "session_id": "XHUMA_APPT_xyz789", 
 "status": "CONFIRMED", 
 "confirmed_slot": "2026-04-08T14:00:00Z", 
 "session_url": "https://vkyc.ndb.com/session/xyz789", 
 "agent_name": "ThinugaW" 
} 
 
NOTE : For agent rescheduling requests, usual working hours do NOT apply. They may schedule the call 
outside of working hours if a customer requests so and the agent is happy to do so. This does not apply 
for Lime bookings (customers) as they may only apply bookings during designated work hours. 
5.3 KYC Agent Authorizer View 
The KYC Agent Authorizer is designed to provide management with the necessary tools for real-time 
oversight, team performance monitoring, and operational control. 
5.3.1. Real-time Monitoring Dashboard 
The primary interface for this role is a comprehensive, real-time dashboard that provides a holistic view 
of the entire VKYC operation at a glance. 
 
29

## Page 31

●​
AGENT_AUTH-1.0: The VKYC Authorizer and System Administrator shall have access to a 
dedicated dashboard that automatically refreshes to provide a live, holistic view of the VKYC 
operation. 
 
●​
AGENT_AUTH-2.0: This dashboard must display the following key real-time information widgets: 
○​
Overall Daily Summary 
■​
Total Cases/Calls Conducted 
■​
Successful VKYC Count 
■​
Rejected Applications 
■​
Pending Interviews 
■​
Rescheduled Interviews 
■​
Cancelled Interviews 
■​
Approval Rate (%) 
■​
Average Handling Time (AHT) : Available 
■​
SLA Achievement (%) 
○​
Agent / Interview Officer Performance 
■​
Interviews per Agent : Available 
■​
Average Interview Duration : Available 
○​
Real-Time Queue Monitoring 
■​
Customers Waiting in Queue 
■​
Active Interviews Count 
■​
Available Officers 
■​
Busy Officers 
■​
Offline Officers 
○​
Customer Experience Metrics 
■​
Customer Satisfaction Score 
■​
Customer Feedback Summary 
30

## Page 32

■​
Average Waiting Experience 
○​
Export & Reporting Options 
■​
PDF Export 
 
 
5.3.2. View Historical Data 
This section outlines the specific data access permissions for the Agent Authorizer. 
●​
AGENT_AUTH-2.0 : Historical Data Access: In addition to their agent duties, the KYC Authorizer 
must have the ability to view and search the historical call data for all the agents within their 
team. This includes access to call outcomes, durations, customer details, and any associated 
agent notes. 
Note : When viewing completed cases, the set thresholds should be indicated in the UI to showcase the 
achieved percentage in comparison to the set threshold. 
5.3.3 Agent Segmentation 
This section outlines the privilege of the agent authenticator to add a segment label to agents. The 
labels are as follows, 
-​
Language Preference [Can be multiple languages] 
-​
English 
-​
Sinhala 
-​
Tamil 
-​
Islamic Banking [True/False] 
31

## Page 33

-​
Gender [Male/Female] 
-​
Customer Segment : Currently not specified by the bank and will be assigned in the future upon 
requirement gathering. 
 
●​
AGENT_AUTH-3.1 : The agent authorizer will proceed to assign the labels accordingly for the 
agent. Upon assignment of labels, the agent call assignment will be dictated by the customer 
segment. 
5.4. System Administrator View 
5.4.1. Administrator-Inputter 
The System Administrator View provides the highest level of configuration for the Xhuma platform. 
These settings control the core business logic, scheduling engine, and overall system parameters. 
5.4.1.1 Slot and Schedule Management (KYC Time Management) 
This section details the administrative functions for managing the platform's overall availability and 
scheduling logic. 
 
●​
ADMIN-1.1: The system must provide an administrative interface for configuring the core 
operational schedule. This includes the ability to: 
○​
Define standard agent working hours (e.g., 9:00 AM to 5:00 PM, Monday to Friday). 
○​
Configure company-wide holidays, during which no VKYC appointments can be 
scheduled for 365 days. 
 
32

## Page 34

●​
ADMIN-1.2: The schedules configured by the Administrator will serve as the foundational "source 
of truth" for the Slot Management Engine. This engine is responsible for generating the list of 
available appointment slots that are presented to the customer in the scheduling calendar (as 
described in CUST-3.1). 
●​
ADMIN-1.3: The Slot Management Engine must intelligently calculate real-time availability. It 
does this by taking the overall working hours and holidays, cross-referencing them with the 
number of active agents and their existing scheduled appointments. 
○​
By default, the system will assume an approximate session duration of 10 minutes when 
calculating slot availability. This buffer ensures that back-to-back appointments are 
manageable for agents. This duration should be a configurable parameter. 
 
5.4.1.2. KYC Verification Threshold Configuration 
This section details the administrative function for setting the system-wide threshold that governs the 
automated pass/fail logic for VKYC sessions. 
●​ ADMIN-2.1: The system must provide an administrative interface to configure the minimum 
threshold required to automatically mark a VKYC call's completion status as "PASS". 
●​ This threshold is based on the combined score from the AI-driven Liveliness and Facial 
Similarity checks. 
●​ The system will have a default threshold value of 42% for Face Similarity Check and 70% 
Liveliness Check. 
●​ The Administrator must have the ability to modify this default value to align with NDB's 
evolving risk and compliance policies. 
 
33

## Page 35

5.4.1.3 Content Configuration 
​
5.4.1.3.1 Customer Consent Message 
Xhuma allows the System Administrator to configure the consent message which would be accepted 
by the customer prior to the KYC call. The same view allows users to preview the consent message 
prior to updating. 
 
 
 
The changes made to the consent message will be applied globally across the platform for all KYC 
calls that take place. 
​
5.4.1.3.2 VKYC SMS Template 
The SMS shared by Xhuma with the meeting link can be configured additionally from the same view as 
above. This SMS message will only be sent with the meeting link. This configuration does not apply to 
reminder SMS messages. 
 
 
​
5.4.1.3.3 VKYC Email Template 
The Email shared by Xhuma with the meeting link can be configured additionally from the same view 
as above. This Email message will only be sent with the meeting link. This configuration does not apply 
to reminder Email messages. 
 
34

## Page 36

Xhuma only allows configuration of the text content on the email. 
 
 
5.4.2 Administrator - Authorizer 
●​
A dual authentication flow will be made available at the administrator level as well to 
accommodate and ensure that acceptance of any changes are run through two levels of users. 
An admin authorizer will not be able to make adjustments, however they would be able to 
accept or reject a change request that was made. 
 
●​
ADMIN-AUTH-1.1 : The admin may proceed to review the change made and proceed to accept 
or reject the option. 
5.5 User Management 
This section highlights the user management option facilitated by Xhuma. Xhuma provides dual 
authorization for adding users where one user has access to add new users and a separate user 
5.5.1 User Management (Requester) 
The “Requester” has the ability to conduct the following activities, 
-​
Provision a User; The individual can specify the LAN ID of the relevant user and the relevant user 
will be added to the platform via the bank’s AD integration (SAML supported). 
-​
Change the user role; The individual can change the user role to either “Agent Authenticator ” or 
“Admin” or “Agent Inputter”. The request will be made only when the role has been selected and 
submitted. 
-​
Deactivate a User; The requester may proceed to request to deactivate any active user. 
5.5.2 User Management (Approver) 
The “Approver” has the ability to conduct the following activities, 
-​
Approve a new user ; The approver simply can proceed to either approve or reject a new user 
and will have visibility to the queue of requests coming in from the requesters. 
35

## Page 37

-​
Approve a user role change ; The approver can similarly proceed to either approve or reject a 
new user. 
-​
Approver user deactivation ; Approves any requests to deactivate a user. 
5.6 System View 
This chapter details the automated backend processes and system-driven logic that operate without 
direct user interaction to ensure the platform runs efficiently and handles various scenarios correctly. 
5.6.1. Customer No-Show Workflow 
This section describes the automated workflow that the system will initiate when a customer fails to join 
their scheduled VKYC appointment. 
 
●​
SYS-1.1: The system shall continuously monitor the status of all scheduled appointments. If a 
customer does not join their scheduled call within a pre-configured time limit of 15 minutes past 
the appointment start time, the system will automatically update the appointment status to 
"Cancelled". This action frees up the assigned agent's time slot, making them available for other 
calls. 
●​
SYS-1.2: Immediately upon marking an appointment as "Cancelled" due to a no-show, the 
Xhuma system must communicate this incident to the Lime platform. This is achieved via a 
webhook or a status update API call. This notification enables the Lime platform to trigger its 
own corresponding business logic, which may include sending a notification to the customer 
informing them of the missed appointment and prompting them to reschedule. 
 
API Interaction Example: No-Show Status Webhook 
●​
Webhook from Xhuma to Lime: 
 
{ 
 "session_id": "XHUMA_APPT_xyz789", 
 "status": "CANCELLED", 
 "reason": "CUSTOMER_NO_SHOW", 
 "timestamp": "2026-04-12T14:11:00Z" 
} 
 
Note : The KYC agent may attempt to call the customer via the mobile number provided outside of 
Xhuma to ensure the customer joins. 
 
●​
SYS-1.3 : In a case where the customer is able to notify the agent that they are able to join with 
sufficient time to complete the KYC call, the agent may proceed to stop the auto-cancellation 
manually. 
36

## Page 38

●​
SYS-1.4 : In a case where the customer notifies the agent that they wish to reschedule the 
session, the agent may proceed to do so for their available timeslot. 
 
API Interaction Example: Agent Reschedule Webhook 
●​
Webhook from Xhuma to Lime: 
 
{ 
 "session_id": "XHUMA_APPT_xyz789", 
 "status": "CONFIRMED", 
 "confirmed_slot": "2026-04-08T14:00:00Z", 
 "session_url": "https://vkyc.ndb.com/session/xyz789", 
 "agent_name": "ThinugaW" 
} 
 
5.6.2. Call Abandonment Workflow 
This section describes the automated workflow the system will initiate when a customer unexpectedly 
disconnects from an active VKYC session. 
 
●​
SYS-2.1: In accordance with requirement SYS-2.1, if a customer who is in an active video session 
with an agent disconnects for any reason (e.g., closes their browser, loses connectivity), the 
system will automatically update the session status to "Incomplete". 
○​
This status change will not be immediately communicated. There will be a grace period 
of 10 minutes to allow the individual to reconnect. If the individual does not connect 
during this time, an API webhook will be triggered and the session will end. 
○​
This allows the Lime platform to update its records and enables the customer to 
re-initiate the VKYC process by following the rules for a new session. The system will not 
attempt to automatically reconnect the dropped session. 
 
API Interaction Example: Call Abandonment Status Webhook 
●​
Webhook from Xhuma to Lime: 
 
{ 
 "session_id": "XHUMA_SESS_abc123", 
 "status": "CANCELLED", 
 "reason": "CUSTOMER_DROPPED_ACTIVE_CALL", 
 "timestamp": "2026-04-08T15:22:00Z" 
} 
 
Note : The KYC agent may attempt to call the customer via the mobile number provided outside of 
Xhuma to ensure the customer joins. 
37

## Page 39

●​
SYS-1.3 : In a case where the customer is able to notify the agent that they are able to join with 
sufficient time to complete the KYC call, the agent may proceed to stop the auto-cancellation 
manually. 
 
●​
SYS-1.4 : In a case where the customer notifies the agent that they wish to reschedule the 
session, the agent may proceed to do so for their available timeslot. 
 
API Interaction Example: Agent Reschedule Webhook 
●​
Webhook from Xhuma to Lime: 
 
{ 
 "session_id": "XHUMA_APPT_xyz789", 
 "status": "CONFIRMED", 
 "confirmed_slot": "2026-04-08T14:00:00Z", 
 "session_url": "https://vkyc.ndb.com/session/xyz789", 
 "agent_name": "ThinugaW" 
} 
 
5.6.3. Agent No-Show Workflow 
This section describes the automated escalation workflow the system will initiate when an assigned 
agent fails to join a scheduled VKYC appointment, ensuring the customer is not left waiting indefinitely. 
●​
SYS-3.1: The system will monitor the status of all agents assigned to scheduled calls. If an agent 
does not join their scheduled call within 5 minutes of the appointment start time, the system will 
automatically trigger an alert. 
○​
This alert will be sent directly to all available Call Centre Agents dashboard as a 
high-priority notification after 5 minutes. 
○​
If one agent picks up the call, the notification will not appear for the other agents. 
 
API Interaction Example: Agent Re-assignment Webhook 
●​
Webhook from Xhuma to Lime: 
 
{ 
 "session_id": "XHUMA_APPT_xyz789", 
 "status": "CONFIRMED" 
 “agent” : ViduraK 
} 
38

## Page 40

●​
SYS-3.2: If, after a total of 10 minutes from the original appointment start time, no agent (neither 
the original nor a manually reassigned one) has joined the call, the system will execute a final 
action to prevent further customer delay. 
○​
The appointment status will be automatically marked as "Incomplete". 
○​
This status change will be communicated to the Lime platform via a webhook, allowing 
them to notify the customer that there was an issue and prompt them to reschedule the 
appointment. 
 
API Interaction Example: Agent No-Show Status Webhook (after 10 minutes) 
●​
Webhook from Xhuma to Lime: 
 
{ 
 "session_id": "XHUMA_APPT_xyz789", 
 "status": "INCOMPLETE", 
 "reason": "AGENT_NO_SHOW", 
 "timestamp": "2026-04-12T14:10:00Z" 
} 
6. Non-Functional Requirements 
6.1. Performance 
This section defines the performance profile of the application itself, assuming it is running on 
adequately provisioned infrastructure provided by NDB. 
●​
API Response Times: The application's APIs must be optimized to ensure 95% of all calls respond 
in under 500ms, excluding network latency. 
●​
Page Load Times: Key application interfaces, such as the Agent and Admin Dashboards, must 
be designed to render completely within 3 seconds on a standard corporate network 
connection. 
●​
Concurrency Support: The application architecture must be stateless and support load 
balancing, enabling it to handle the agreed-upon number of concurrent agent sessions without 
degradation, assuming NDB scales the underlying infrastructure appropriately. 
 
6.2. Application Security 
This section defines the security characteristics that must be built into the Xhuma application code and 
configuration. 
39

## Page 41

●​
Authentication & Session Management: The application must enforce strong password 
complexity rules and secure session management. 
●​
Data Encryption Support: The application must exclusively use secure, encrypted 
communication protocols (e.g., TLS 1.3 or higher) for all data in-transit. For data at-rest, the 
application must be fully compatible with and utilize the native encryption capabilities of the 
NDB-managed AWS services (e.g., RDS database encryption, S3 server-side encryption). 
●​
Code Security Standards: The application code must be developed following secure coding best 
practices (such as the OWASP Top 10) to protect against common web application 
vulnerabilities like Cross-Site Scripting (XSS) and SQL Injection. The application must be able to 
pass a security audit and Vulnerability Assessment Penetration Test (VAPT) conducted by NDB. 
 
6.3. Application Stability and Resilience 
This section defines the application's responsibility for being stable and supporting NDB's 
high-availability and disaster recovery strategies. 
 
●​
Application Stability: The application must be designed to be resilient and avoid single points of 
failure within its own architecture. It must include robust error handling and logging to prevent 
crashes due to unexpected input or downstream service unavailability. 
●​
Cloud-Native Compatibility: The application must be architected to be "cloud-native," meaning 
it should be stateless where possible and support being deployed across multiple AWS 
Availability Zones (AZs). This ensures it is compatible with NDB's high-availability and disaster 
recovery infrastructure plans. 
●​
Maintenance & Deployments: The application must support a deployment process that 
minimizes downtime, allowing NDB's infrastructure team to perform updates and maintenance 
within the agreed-upon maintenance windows. 
 
6.4. Usability and Accessibility 
●​
Ease of Use: States that the interface should be intuitive and require minimal training for new 
agents. 
●​
Browser Support: Specifies the list of web browsers and their versions that the platform must 
fully support (e.g., latest versions of Chrome, Firefox, Edge). 
●​
Accessibility: Specifies the target accessibility standard the platform should adhere to (e.g., 
WCAG 2.1 AA). 
40

## Page 42

6.5. Audit and Logging Generation 
●​
Audit Trail Generation: The application must generate a detailed and immutable audit trail for 
all critical user actions. All actions done by an NDB user should be mapped to the LAN ID 
obtained via AD integration 
●​
Log Forwarding: The application must be configured to forward all system and audit logs in a 
structured format (e.g., JSON) to NDB's centralized logging infrastructure. The responsibility for 
retention and analysis lies with NDB. 
 
6.6 Maximum Agent Access 
Access to the NDB Xhuma Integrated Solution for VKYC agents is governed by the commercial licensing 
agreement between NDB and NCINGA. 
●​
The platform is licensed for a maximum of 10 named agent accounts. 
●​
Any requirement to increase the number of agent accounts beyond this limit will be considered 
a change in scope and will require a review of the commercial agreement and a formal Change 
Request. 
6.7 Maximum Calls per Monthly 
The usage of the NDB Xhuma Integrated Solution is subject to a monthly call volume limit as defined in 
the commercial licensing agreement. 
●​
The platform is licensed for a maximum of 200 completed VKYC calls per calendar month. 
●​
The system should provide administrators with visibility into the current month's call volume 
consumption. 
 
Any usage exceeding the 200 monthly call limit will be subject to the overage rates and terms defined 
in the commercial agreement. Consistent overages may trigger a formal review to adjust the licensing 
tier 
 
7. Documentation Requirements 
The successful delivery and handover of the NDB Xhuma Integrated Solution will be supported by 
a set of clear and comprehensive documentation. The following documents will be produced as 
part of this project. 
41

## Page 43

7.1. Business Requirement Document (BRD) 
This document itself, the Business Requirement Document (BRD), serves as the foundational 
agreement detailing the complete business, functional, and non-functional requirements of the 
NDB Xhuma Integrated Solution. It is the single source of truth for what the system must deliver to 
meet NDB's business objectives and will guide all subsequent design, development, and testing 
activities. 
7.2. Scope of Work (SoW) 
A formal Scope of Work (SoW) will be created based on the requirements detailed in this BRD. The 
SoW will serve as the primary contractual document, outlining the specific project deliverables, 
timelines, key milestones, commercial terms, and the roles and responsibilities of both NDB and 
NCINGA. 
7.3 Quality Assurance (QA) Report 
This report will provide a comprehensive summary of the testing activities and outcomes from 
the Quality Assurance phase. It will detail the overall testing scope, execution statistics (including 
the number of test cases passed, failed, and blocked), and a categorized summary of all 
identified defects. The primary purpose of this document is to certify the software's quality and 
readiness for User Acceptance Testing (UAT). 
7.4 UAT Deployment Guide 
This document will provide detailed, step-by-step instructions for deploying the application to the 
User Acceptance Testing (UAT) environment. It will outline all prerequisites, pre-deployment 
checks, execution steps, post-deployment verification procedures, and a formal rollback plan to 
ensure a smooth and controlled deployment for end-user validation. 
7.5 Production Deployment Guide 
This guide will contain the definitive instructions for deploying the application into the live 
Production environment. It will specify the prerequisites, including all necessary sign-offs, a 
detailed execution plan to minimize downtime, and critical post-deployment smoke tests. A 
comprehensive rollback strategy will be included to ensure production stability can be restored 
quickly in case of unforeseen critical issues. 
7.6 Release Notes 
A set of release notes will be published with the deployment to provide a high-level overview for 
business stakeholders. These notes will summarize the new features, enhancements, and any 
known issues included in the release, communicating the value and impact of the new version to 
a non-technical audience. 
42

## Page 44

7.7 Production Release Note 
This technical document will accompany the production deployment, intended for IT and 
development teams. It will detail the specific changes in the release, including database schema 
updates, new API endpoints, configuration changes, and any critical dependencies. This note 
serves as a technical log of the release and supports future maintenance and troubleshooting 
efforts. 
 
7.7. User Manual 
A comprehensive User Manual will be delivered to NDB upon completion of the project. This 
document will serve as a practical, hands-on guide for the end-users of the platform. It will 
provide step-by-step instructions, complete with screenshots, on how to use all the functionalities 
available to the Agent, User Managers, and System Administrator roles. 
8. Integration Requirements 
This chapter outlines the key integration points between the NDB Xhuma Integrated Solution and the 
required external NDB systems. All integrations will be implemented using secure, industry-standard 
protocols. 
8.1. Lime Onboarding Platform (Lime) 
This is the primary and most critical integration for the project. The deep, two-way communication 
between the Xhuma platform and the Lime onboarding platform enables the seamless end-to-end 
customer journey. The integration will be facilitated via a secure, RESTful API. 
 
The key integration points are as follows: 
●​
Session Initiation: Lime will be responsible for initiating all VKYC sessions by sending customer 
data (including customer segment and KYC reason) to the Xhuma API to create either an 
instant or a scheduled session. In return, Xhuma will provide a secure session URL for customer 
redirection. 
●​
Scheduling and Availability: Xhuma will expose endpoints for Lime to query real-time agent 
availability and time slots for the customer-facing scheduling calendar. Lime will use a 
corresponding endpoint to book, reschedule, or cancel appointments in the Xhuma system. 
●​
Status Synchronization: Xhuma will be responsible for providing real-time status updates back 
to the Lime platform via webhooks. This is crucial for closing the loop on the customer journey. 
The statuses communicated will include, but are not limited to: 
○​
CONFIRMED : Call has been scheduled and is to be taken. 
○​
PASS : Call has met the minimum requirements set by the Bank 
43

## Page 45

○​
FAIL : Call has not met the minimum requirements set by the Bank 
○​
ESCALATE : Call has not met the minimum requirements set by the Bank and has been 
escalated by inputted to approverCANCELLED : Call has been cancelled by 
Agent/Customer or there has been 
(Example API interactions and data payloads are described in Chapter 5.1: Customer View.) 
 
8.2 Internal Communication Integrations 
To facilitate efficient workflows and timely alerts among internal stakeholders, the system will integrate 
with standard communication gateways. These channels are strictly designated for internal use by 
agents and bank staff. 
 
●​
Email Service Integration: The application will integrate with the bank’s designated email 
server/gateway (e.g., SMTP). This will enable the system to trigger automated email 
notifications, workflow routing alerts, and system reports directed exclusively to internal agents 
and bank personnel. 
 
●​
SMS Gateway Integration: The system will integrate with the bank's approved SMS gateway to 
deliver time-sensitive text messages. This channel will be utilized solely for internal 
communications, such as critical alerts, fast-track notifications, and verification codes intended 
for agents and bank staff. 
 
Note : Customer facing communication will be done via Lime directly. 
8.3. Azure Active Directory Integration 
To ensure secure and centralized user management, the Xhuma platform must integrate with NDB's 
existing identity provider, Azure Active Directory (Azure AD), for all internal user authentication (Agents, 
User Manager, and System Administrators). 
 
●​
Single Sign-On (SSO): All internal users will authenticate against the Xhuma platform using their 
existing NDB corporate credentials via Azure AD. This eliminates the need for separate 
passwords for the Xhuma application. 
 
●​
Authentication Protocol: The integration will be implemented using a standard, secure 
authentication protocol supported by Azure AD, such as SAML 2.0 or OpenID Connect. 
 
44

## Page 46

●​
User Provisioning: While authentication will be handled by Azure AD, the creation of user 
accounts and the assignment of their specific roles (Agent, User Managers, Admin) and 
specialties will be managed within the Xhuma platform itself, as detailed in Chapter 5.3.3. 
8.4 External Third-Party Integrations (Xhuma General API) 
Xhuma Open API Gateway: To support future scalability and ecosystem expansion, Xhuma will expose a 
general-purpose, standardized API layer. Similar to the integration model of the Lime platform, this 
open API will allow authorized external third-party systems to securely integrate with Xhuma. 
 
●​
Protocol & Standards: The API will be built using standard web protocols (RESTful APIs with JSON 
payloads) to ensure ease of integration for external developers. 
 
●​
Security & Authentication: Access will be strictly controlled through industry-standard 
authentication and authorization mechanisms (such as OAuth 2.0 and secure API keys) 
alongside rate-limiting to protect the system's integrity and performance. 
9. User Permissions 
 
This is the User permissions below explains the permissions of the user roles to be assigned to 
NDB’s staff: 
 
Main Feature 
Sub-Feature 
Agent - 
Inputter 
Agent - 
Authoriz
er 
System 
Admin 
User 
Manage
r 
(Reques
ter) 
User 
Manage
r 
(Approv
er) 
Call & Session 
Management 
Conduct VKYC Call 
✓ 
 
 
 
 
View Own Scheduled Calls ✓ 
 
 
 
 
Handle Returned Calls 
✓ 
 
 
 
 
Initiate Call 
Cancellation/Reassignmen
t 
✓ 
 
 
 
 
Supervision & 
Monitoring 
View Real-time 
Operational Dashboard 
✓ 
✓ 
✓ 
 
 
View Historical Data for All 
Agents 
 
✓ 
✓ 
 
 
45

## Page 47

Manually Reassign Calls 
(for Agent No-Show) 
 
✓ 
 
 
 
Agent Status 
Management 
Request Own Status 
Change (e.g., for Leave) 
✓ 
 
 
 
 
Approve Agent Status 
Change Requests 
 
✓ 
 
 
 
Administration 
Configure Schedules & 
Holidays 
 
 
✓ 
 
 
Configure KYC Verification 
Thresholds 
 
 
✓ 
 
 
Configure Content 
(Consent, Email/SMS 
Templates) 
 
 
✓ 
 
 
User 
Management 
Request New User Creation 
 
 
✓ 
 
Request User Deactivation 
 
 
✓ 
 
Request User Role Change 
 
 
✓ 
 
Approve/Reject New User 
Requests 
 
 
 
 
✓ 
Approve/Reject User 
Deactivation Requests 
 
 
 
 
✓ 
Approve/Reject User Role 
Change Requests 
 
 
 
 
✓ 
 
Agent Segment Adding 
 
✓ 
 
 
 
 
 
 
46

## Page 48

10. Sign off 
 
This section confirms that the stakeholders listed below have reviewed and approved the 
Business Requirements Document (BRD) and agree that it accurately reflects the business needs 
and requirements. 
 
Authorized Person 
Name 
Position 
Signature 
Approved Date 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
--------------------------------End of the Document--------------------------- 
47
