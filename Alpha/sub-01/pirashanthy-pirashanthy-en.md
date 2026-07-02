# DocQuery_ReleaseNote V 1.5.docx (1).pdf

## Page 1

DocQuery: Gen-AI Powered 
Information Retrieval Solution 
Release Note v 1.5 
11th of February 2026

## Page 2

DOCUMENT INFORMATION 
Product Name: DocQuery: Gen-AI Powered 
Information Retrieval Solution 
 
Module Name: N/A 
Client: PanAsiaBank 
Release Date: 11/02/2026 
Document Version: 1.4 
Main Release No.: 1.0 
Patch No.: N/A 
CR Release No: N/A 
Build No: N/A 
SRN Type: N/A​ ​ 
PREPARED BY: ​
 
Name: Pirashanthy Balakrishnan 
Designation: Engineer – Quality Assurance 
Signature : N/A 
Date: 11/01/2026 
REVIEW & APPROVAL 
 
 
Name 
Designation 
Signature 
Date 
Tested By: 
Pirashanthy 
Balakrishnan 
Dewmini 
Abeywardhana 
Engineer – Quality 
Assurance 
Engineer – Quality 
Assurance 
N/A 
11/02/2026 
Reviewed By: 
Kemali 
Munasinghe 
Lead-Quality Assurance 
N/A 
11/02/2026 
Approved By: 
Nikil Jayasuriya 
Associate Project Manager 
 N/A 
11/02/2026

## Page 3

DOCUMENT REVISION HISTORY 
Issue Version No. 
Date 
Description 
Author (name) 
1.0 
13/01/2026 
DocQuery: Gen-AI Powered 
Information Retrieval 
Solution 
 
Pirashanthy Balakrishnan 
1.1 
21/01/2026 
Bug fix release 
Pirashanthy Balakrishnan 
1.2 
23/01/2026 
Bug fix release 
Pirashanthy Balakrishnan 
1.3 
27/01/2026 
Bug fix release 
Pirashanthy Balakrishnan 
1.5 
30/01/2026 
Bug fix release 
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
5 
4.0 Known Issues​
5 
5.0 Known Limitations​
6 
6.0 Bug Fixes​
7 
7.0 Deliverables​
8 
8.0 Supporting Documents​
9

## Page 5

1.0 Overview of the Document 
This release note provides a summary of bug fixes in phase 1 release for DocQuery: Gen-AI 
Powered Information Retrieval Solution. 
2.0 Features included in this release 
This is a bug fix release and the scope included in the main release still applies to this release 
as well. 
3.0 Features not included in this release 
N/A 
4.0 Known Issues 
Known issues listed in the main release still apply to this release as well. 
 
Module 
Feature 
Known Issue 
Preview 
In some cases, the total 
page count displayed for 
an uploaded PDF 
document may not exactly 
match the original page 
count of the source 
document 
The discrepancy is limited to the page 
count display.​
Document content remains accessible.​
AI responses and document querying are 
not affected. 
 
Left panel 
If a user performs 
continuous login activity 
and the session 
subsequently expires due 
to inactivity, navigating 
Chat history visibility is restricted as per 
user role.​
AI 
chat 
functionality 
and 
document 
querying 
remain 
available 
within 
permitted environments.​

## Page 6

back to the home page 
may result in a “403 – 
Access Forbidden” 
message appearing in the 
left panel chat area. 
No impact to system security or data 
integrity. 
Users are advised to open and use only 
one active DocQuery session per browser 
at a time. 
If the issue occurs, refreshing the page or 
re-logging into the application will restore 
normal behavior. 
File upload 
File uploads outside the 
folder are not supported for 
now. In addition, uploaded 
files are not displayed until 
the user refreshes the page 
We are currently experiencing this issue 
and for the time being, kindly upload files 
inside the folder and check. We will 
address this issue in the next release. 
5.0 Known Limitations 
All applicable limitations are mentioned in the main release.

## Page 7

6.0 Bug Fixes 
The following bug fixes are included in this release. This includes UAT reported bugs and some 
internally reported fixes. 
 
Module 
Issue Number 
Description 
TARIFF READING 
ISSUE 
Issue 10 
“Source document name: BANK TARIFF 2026.pdf 
Asked Question: How much is the charge for CEFT 
Transactions?” 
Different 
Responses 
Issue 11 
“Two 
significantly 
different 
responses 
were 
generated when the same question was asked.” 
This issue is fixed for the TARIFF document 
Response 
Generation 
Issue 16 
“Unnecessary information is provided by chatbot.” 
Response 
Generation 
Issue 17 
“The answer is not given to the asked questions.” 
This issue is fixed for the TARIFF document 
Response 
Generation 
Issue 18 
“The given answer contains details that are not 
mentioned in the question. (The question is raised 
commonly; however, the answer is given in relation 
to special deposit account.) 
Selecting the 
environment 
Doc_054 
“Without selecting the environment , chats are 
appearing” 
Sign in the system ->Click chat option from the left 
panel

## Page 8

Module 
Issue Number 
Description 
Selecting the 
environment 
Doc_056 
“All the environment not showing in the drop down” 
Sign in the system ->Go to the chat left panel 
->Observe the behavior 
Chat feedback 
Doc_058 
“Page Number field in Chat Feedback form accepts 
letter e also” 
In the chat response feedback form (Correct/ 
Incorrect), the page number field allows invalid 
inputs such as the letter “e”, even though the field is 
intended to accept only numeric values.t 
Update from OCR 
option 
Doc_062 
“While uploading the file with ocr the page is 
,blinking “ 
Upload the file->Select OCR ->Observe the behavior 
7.0 Deliverables 
The following deliverables are also released with this version: 
 
Module 
Details 
FrontEnd 
https://pabc.docquery.app/

## Page 9

8.0 Supporting Documents 
DocqueryBRD 
:https://drive.google.com/file/d/1T_0kJYqIv0E17qy1nGUAvhi107TZeh2c/view?usp=sharing 
 
Answer Comparison Sheet 
https://docs.google.com/spreadsheets/d/15sGWAIXLo0QkwgKijywV91ZsHrwJE5A7_meqpbD3sTU/ed
it?gid=0#gid=0
