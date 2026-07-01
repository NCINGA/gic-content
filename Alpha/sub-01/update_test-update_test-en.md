# Nanosoft ReleaseNote v1.1.pdf
up
## Page 1

Nanosoft -Release Note v 1.1 
8th of May 2026

## Page 2

DOCUMENT INFORMATION 
Product Name: Nanosoft Chat Bot 
Module Name: Nanosoft v 1.1 
Client: Nanosoft 
Release Date: 08/05/2026 
Document Version: 1.1 
Main Release No.: 1.0 
Patch No.: N/A 
CR Release No: N/A 
Build No: N/A 
SRN Type: N/A​ ​ 
PREPARED BY: ​
 
Name: Hirunisha Nirmani 
Designation: Intern – Quality Assurance 
Signature : N/A 
Date: 08/05/2026 
REVIEW & APPROVAL 
 
 
Name 
Designation 
Signature 
Date 
Tested By: 
Hirunisha Nirmani 
Pirashanthy 
Balakrishnan 
Intern – Quality Assurance 
Engineer - Quality 
Assurance 
N/A 
08/05/2026 
Reviewed By: 
Kemali 
Munasinghe 
Lead-Quality Assurance 
N/A 
08/05/2026 
Approved By: 
Nikil Jayasuriya 
Associate Project Manager 
 N/A 
08/05/2026

## Page 3

DOCUMENT REVISION HISTORY 
Issue Version No. 
Date 
Description 
Author (name) 
1.0 
16/10/2025 
Release document for 
Nanosoft Agentic AI Solution 
Pirashanthy Balakrishnan

## Page 4

Table Of Contents 
 
Table Of Contents​
4 
1.0 Overview of the Document​
5 
2.0 Features included in this release​
5 
3.0 Features not included in this release​
6 
4.0 Known Issues​
7 
5.0 Known Limitations​
7 
6.0 Bug Fixes​
7 
7.0 Deliverables​
8 
8.0 Supporting Documents​
8

## Page 5

1.0 Overview of the Document 
This document outlines the Quality Assurance (QA) validation results, scope, and 
observations for the latest release of the Nanosoft Agentic AI Solution. 
The chatbot is designed to scrape and process content from the official Nanosoft Global 
website and provide AI-generated responses to user queries. 
This QA cycle focuses on validating UI responsiveness, content accuracy, and AI guardrails 
prior to production deployment. 
2.0 Features included in this release 
This release is a controlled release of the Nanosoft Chat Bot and includes the following 
features and functionalities as communicated via the email for the QA testing request 
Feature 
Functionality 
Multilingual support 
●​
Chat Bot operates in English, Sinhala and Tamil 
languages 
AI-Powered Query 
Handling 
●​
Natural language understanding for user queries 
●​
Context-based response generation from scraped data 
Responsive User 
Interface 
●​
Cross-device compatibility (desktop, tablet, mobile) 
●​
Smooth interaction and rendering across screen sizes 
Browser 
Compatibility 
●​
Cross-browser compatibility (Google Chrome, Microsoft 
Edge, Mozilla Firefox, and Safari. ) 
Content-Based 
Answering 
●​
Responses generated strictly based on available website 
content 
●​
Reduced hallucination through prompt constraints

## Page 6

AI Guardrails 
Implementation 
●​
Controlled responses aligned with company information 
●​
Restrictions to avoid misleading or unsupported answers 
Chatbot Analysing 
Dashboard 
●​
Full overview of chatbot’s user engagement. 
●​
Session count with duration, query counts, semantic 
score distribution , user satisfaction 
 
3.0 Features not included in this release 
Anything not listed under section 2.0 are excluded from the scope of work of this project. 
These include: 
Feature 
Remark 
External Data Source 
Integration 
The chatbot does not connect to or retrieve data from 
third-party systems, APIs, or databases outside the Nanosoft 
website. 
Advanced 
Personalization 
The chatbot does not support user-specific personalization 
such as remembering past interactions or tailoring responses 
based on user history.

## Page 7

4.0 Known Issues 
Known issues of this release are listed below. These are medium and low priority issues and 
will be fixed in the next release. 
 
Issue 
Description 
Edge 
Case 
Response 
Variability 
Certain ambiguous or complex queries may result in inconsistent 
phrasing or partial answers. 
5.0 Known Limitations 
Known limitations of the system are as below. 
●​
Dependency on Source Content - Accuracy is fully dependent on the correctness and 
consistency of website content. 
●​
Sinhala content should be more fine tuned. 
 
 
6.0 Bug Fixes 
This is a main release and not a bug fix release.

## Page 8

7.0 Deliverables 
The following deliverables are also released with this version: 
 
Module 
Details 
Remarks 
FrontEnd 
https://ds-nanosoft-chatbot-stage-7772
32604101.asia-southeast1.run.app/test 
Updated chatbot (Please 
use this chatbot for testing 
purposes.) 
Dashboard https://ds-nanosoft-chatbot-stage-7772
32604101.asia-southeast1.run.app/dashb
oard/ 
 
email= 
nanosoft.test@ncinga.net 
Password = 
fheuio8fe83rh!diDIHdw 
Web Site 
Nanosoft Global 
Only the website content is 
scraped. The chatbot 
available on the website is 
not used 
 
8.0 Supporting Documents 
N/A
