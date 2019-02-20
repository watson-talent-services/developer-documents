---
copyright: 'Copyright IBM Corp. 2019'
link: v1-talent-match
is: 'beta'
---

# IBM Watson Talent Match 

IBM Watson Talent Match (aka Talent Match) is an API offering that performs Artificial Intelligent (AI) analysis of a 
requisition requirements and an applicant’s resume and returns a Talent Match Score that represents how well an 
applicant’s skills match the requisition’s requirements. Talent Match not only matches skills from a candidate’s profile 
to a requisition but also identifies and analyzes indirect skills and competencies from a candidate’s resume that are not 
explicitly identified. The Talent Match API can parse structured and unstructured data.

Talent Match provides a way for you to submit your job requisition (job data) and applicant resumes (person data) using the 
Talent Match APIs and receive a Talent Match Score that indicates how well an applicant (person) meets the requisition (job) 
requirements. 

![IBM Watson Talent Match API](https://github.ibm.com/WatsonTalent/TMS-Developer-Experience/blob/master/images/TalentMatchDiagram.png)

Currently, the Talent Match APIs execute a one-to-one Watson Talent Match. The means the Talent Match API accepts one API call 
at a time that contains a pair (job data and person data) and returns one Talent Match Score. 

Talent Match APIs provide a multi-faceted, cognitive approach to talent acquisition and allow you to:

- Submit raw and / or parsed job and person parameters (data) to the Talent Match API
- Receive Talent Match API responses with Talent Match Scores

### How Does this API Work?

The Talent Match API accepts both raw and parsed job (requisition) and person (applicant) data files. A raw data file is 
simply a file in **text** or **pdf** format. So, a raw job is a job description in text or pdf format and a raw person is a 
resume in text or pdf format. Any new job description or new person file must first be sent as raw data. 

For the raw job parameter, you can provide a text or pdf file of the job description. For the raw person parameter, 
you can provide a text or pdf file resume of the person. The Talent Match API will process this raw content and returns a 
JSON body that has the job and person parsed into JSON. When you send any of the parameter combinations shown below, the 
API returns a parsed job, a parsed person, and a Talent Match Score in json format that indicates how well the person’s 
preferred skills matched the job’s requirements.

The next step in the workflow allows you to send the parsed job and either a raw person or a parsed person to the API endpoint.

When posting to the Talent Match API, you must post in one of the following combinations, the first two parameters for 
each combination are required:

- rawJob, rawPerson, atsJob (optional) and atsPerson (optional)
- rawJob, parsedPerson, atsJob (optional) and atsPerson (optional)
- parsedJob, rawPerson, atsJob (optional), atsPerson (optional)
- parsedJob, parsedPerson, atsJob (optional), atsPerson (optional)

This procedure allows you to send the parsed job and multiple person (raw or parsed) files to the one parsed job to 
obtain a Watson Talent Match. Sending a parsed job and a raw or parsed person allows you to obtain multiple Talent Match 
Scores for one job.

Note: After the Watson Talent Match API processes the job and resume data and returns a Watson Talent Match Score, 
the job and resume are discarded. The parameter data does not persist. Data sent to the Talent Match API is 
encrypted via TLS 1.2.

### Objects

There are 7 objects to consider here;


| Object                   | Description |
| ------------             |:----------- |
| **rawJob**               | this is the unstructured natural language description of a job requistion. |
| **rawPerson**            | this is the unstructured natural language description of a person in terms of their work experience, etc. |
| **parsedJob**            | this is a JSON representation of the job requisition. |
| **parsedPerson**         | this is a JSON representation of the person's work experience.|
| **atsJob**               | this is the JSON input of additional job data coming structured data from sources like ATS, CRM, Job Board etc. |
| **atsPerson**            | this is the JSON input of additional person data coming structured data from sources like ATS, CRM, Job Board etc.  |
| **Match Score Response** | this is the JSON response to the Match call | 

### Using Optional Parameters atsJob and atsPerson

The Job and Person API calls (either of these parameters can be raw or parsed) return the Match Score and limited profile 
details. For example, when you send rawJob and rawPerson parameters, the Match Score json Response details contain matching 
elements, but only contains preferred skills matches and does not include a required skills value. 

To receive a Match Score response that contains a required skills match, you must input the optional parameters atsJob 
and atsPerson with the Job and Person (raw or parsed) parameters. For example, to receive a required skills match you 
can use any of the input parameter combinations, making sure you are including the atsJob and atsPerson parameters.

### IBM Watson Talent Match API Authentication

The Talent Match application uses authentication for secure access to the API. The authentication process requires you 
to obtain client credentials, a Client ID called **X-IBM-Client-Id** and a Client Secret called **X-IBM-Client-Secret-Id**, 
for the Talent Match API. 

You will receive an e-mail once signed-up as a customer and the invitation email includes;

- a URL to access the Talent Match API in the API Explorer application 
- your Client-ID and Secret

Note: API keys authenticate you to your subscription to Talent Match API and it is required that you keep them secure and 
secret. 
Do not share the X-IBM-Client-Secret portion of any API key in publicly accessible places. When you access the Talent Match 
API in the API Explorer application, you use your Client-ID and Secret-ID to authenticate into the application. 
This will allow you to access the API securely. 

Follow these steps to generate your ID and Secret. 

- Select the API Explorer URL in your invitation email. This will open API Explorer landing page.
- Select **Security** in the left side navigation
- Select Pick a Key.
- Locate and select your Client-ID and Secret

![API Explorer Security Screen](https://github.ibm.com/WatsonTalent/TMS-Developer-Experience/blob/master/images/APIConnectSecurityScreen.png)

The system authenticates your credentials and you are now ready to use the Talent Match API.

Note: You can manage your keys (credentials) in the API Explorer application by selecting 
**Overview** > **Security** > **Manage your keys** (at the bottom of the page).


Now that you are authenticated into the API Explorer application, you can use the ID and Secret in your authentication 
header is sent with each request.

Here is the required header format:

| API            | /Match       |
| -------------  |:-------------|
| Verb           | POST         |
| Version        | 1.0          | 
| Custom Headers | **clientId** the unique ID of the client for Watson Talent. |
|                | **X-IBM-Client-Id** The Client Id. |
|                | **X-IBM-Client-Secret** The Client Secret. |
| Content-type   | application/json |


When parsing into Match API, you must post one of the following combinations in your payload. The first two parameters for 
each combination are required.

- rawJob, rawPerson, atsJob (optional) and atsPerson(optional)
- rawJob, parsedPerson, atsJob(optional) and atsPerson(optional)
- parsedJob, rawPerson, atsJob (optional), atsPerson(optional)
- parsedJob, parsedPerson, atsJob (optional), atsPerson(optional)

### IBM Watson Talent Match APIs Parameters

**rawJobA**

**rawJob** can be a raw text representation of a job description or it can be the job description in one of the supported file formats (pdf, txt, docx, or html). 

When you send your rawJob you select either a jobdescription.pdf or a jobdescription.txt or any of the supported formats. A rawJob contains the UNPARSED raw job. A job passed into this method will be parsed into json before matching.

When posting to the Match API, you must post one of the following combinations. The first two parameters for each combinationare required.

- rawJob, rawPerson, atsJob (optional) and atsPerson(optional)
- rawJob, parsedPerson, atsJob (optional) and atsPerson(optional)
- parsedJob, rawPerson, atsJob (optional), atsPerson(optional)
- parsedJob, parsedPerson, atsJob (optional), atsPerson(optional)

The following is an example of a rawJob text sample. For illustration purposes, only the first few paragraphs of the text job description are shown.

![DB Administrator Job Description](https://github.ibm.com/WatsonTalent/TMS-Developer-Experience/blob/master/images/DBAdmin.png)

You can also select a pdf file as a rawJob. The following is an example of a rawJob pdf example. For illustration purposes, only the first few paragraphs of the pdf job description are shown.

![DB Administrator Job Description PDF](https://github.ibm.com/WatsonTalent/TMS-Developer-Experience/blob/master/images/DBAdminPDFSnap.png)


**rawPerson**

A **rawPerson** can be a raw text representation of a person’s resume or it can be the person’s resume in one of the supported file formats (pdf, txt, docx, or html). When you send your rawPerson file, you select either a persondescription.pdf or a persondescription.txt  (or any of the other supported formats). A rawPerson contains the UNPARSED raw person profile/resume. A person resume passed into this method will be parsed into json before matching.  



When posting to the Match API, you must post one of the following combinations. The first two parameters for each combination are required.

- rawJob, rawPerson, atsJob (optional) and atsPerson (optional)
- rawJob, parsedPerson, atsJob (optional) and atsPerson (optional)
- parsedJob, rawPerson, atsJob (optional), atsPerson (optional)
- parsedJob, parsedPerson, atsJob (optional), atsPerson (optional)

The following is an example of a raw person text sample. For illustration purposes, only the first few paragraphs of the text person description are shown.

![Resume](https://github.ibm.com/WatsonTalent/TMS-Developer-Experience/blob/master/images/Resume.png)

You can also select a pdf file as a rawPerson. The following is an example of a rawPerson pdf example. For illustration purposes, only the first few paragraphs of the pdf resume are shown.

![Resume PDF](https://github.ibm.com/WatsonTalent/TMS-Developer-Experience/blob/master/images/ResumePDF.png)

### ParsedJob API Input Schema

**match_JobParse_Response.json**

A parsedJob contains the PARSED json representation of the job used for matching. It is assumed the job passed in this parameter has been parsed first into json format via /match response on can be either a pdf file or a text file of a person’s resume.

When posting to the Match API, you must post one of the following combinations. The first two parameters for each combination are required.

- rawJob, rawPerson, atsJob (optional) and atsPerson (optional)
- rawJob, parsedPerson, atsJob (optional) and atsPerson (optional)
- parsedJob, rawPerson, atsJob (optional), atsPerson (optional)
- parsedJob, parsedPerson, atsJob (optional), atsPerson (optional) This section outlines the parsedJob.


|JSON Schema                      |Datatype|Required|Description                                                                                                                                                            |
|---------------------------------|---------|---------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|{                                |         |         |                                                                                                                                                                       |
|"job" : [ {                      |         |         |                                                                                                                                                                       |
|"title" : {                      |         |Optional|                                                                                                                                                                       |
|"description: "text",            |string   |Optional|Job description.                                                                                                                                                       |
|"role" : "text",                 |string   |Required|Job role.                                                                                                                                                              |
|"jobClassification" : "text",    |string   |Optional|Job classification.                                                                                                                                                    |
|"locationName" : "text",         |string   |Optional|Job location.                                                                                                                                                          |
|"requiredExperience" : "text",   |string   |Optional|How many years experience is required                                                                                                                                  |
|},                               |         |         |                                                                                                                                                                       |
|"education" :	{,                 |string   |Optional|Education                                                                                                                                                              |
|"degrees" : "text",[{            |string   |Optional|Degree                                                                                                                                                                 |
|"degree" : "text",               |string   |Required|Degree                                                                                                                                                                 |
|"required" : "text",             |string   |Boolean  |                                                                                                                                                                       |
|} ],                             |         |         |                                                                                                                                                                       |
|"majors" : ,[{                   |string   |Optional|Major                                                                                                                                                                  |
|"major" : "text",                |string   |Required|Major                                                                                                                                                                  |
|"required" : "true",             |string   |Boolean  |                                                                                                                                                                       |
|} ],                             |         |         |                                                                                                                                                                       |
|"gpaScale" : "4",                |         |         |Candidate's Grade Point Average Scale (e.g. GPA of 3.75 with GPAScale of 4.0)                                                                    |
|"gpa" : "text",                  |string   |Optional|Person's Grade Point Average while at the school                                                                                                                       |
|}                                |         |         |                                                                                                                                                                       |
|"competency" : [ {               |         |         |                                                                                                                                                                       |
|"competencyType" : "text” ,      |string   |Optional|                                                                                                                                                                       |
|"competencyName" : "text",       |string   |Required|                                                                                                                                                                       |
|"competencyCategory" : "text",   |string   |Optional|                                                                                                                                                                       |
|"competencyGroup" : "text"       |
|string"                          |Optional|         |
|} ]                              |         |         |                                                                                                                                                                       |
|"competencyClassification" : [ {|         |         |                                                                                                                                                                       |
|"allClasses" : "text” ,[ {       |string   |Optional|                                                                                                                                                                       |
|"top_class" : "text",            |string   |Optional|Position in class                                                                                                                                                      |
|"text" : "text",                 |string   |Optional|Details                                                                                                                                                                |
|"top_class_confidence" : "text",|string   |Optional|Class confidence                                                                                                                                                       |
|} ]                              |         |         |                                                                                                                                                                       |
|"competencyAggregations" : [ {   |         |         |                                                                                                                                                                       |
|"count" : "text” ,[ {            |string   |Optional|How many competency aggregations                                                                                                                                       |
|"class_name" : "text",           |string   |Optional|Class name                                                                                                                                                             |
|"details" : "text",              |string   |Optional|Details                                                                                                                                                                |
|} ]                              |         |         |                                                                                                                                                                       |
|"errors" : {                     |         |         |                                                                                                                                                                       |
|"fieldName" : "text” ,[ {        |string   |Optional|Field name where error occurred                                                                                                                                        |
|"traceCode" : "text",            |string   |Optional|Internal support identifier. This attribute is provided in the event of a System Processing Failure to provide useful information necessary to isolate the root cause.|
|"errorCode" : "text",            |string   |Optional|Error code                                                                                                                                                             |
|"errorDescription" : "text",     |string   |Optional|Error description                                                                                                                                                      |
|}                                |         |         |                                                                                                                                                                       |
|}                                |         |         |                                                                                                                                                                       |

### parsedPerson API Input Schema

**match_PersonParse_Response.json**

A parsedPerson contains the PARSED json representation of the person profile used for matching. It is required that the person passed in this parameter has been parsed first into json format via /match response.
When posting to the Match API, you must post one of the following combinations. The first two parameters for each combination are required.

- rawJob, rawPerson, atsJob (optional) and atsPerson (optional)
- rawJob, parsedPerson, atsJob (optional) and atsPerson (optional)
- parsedJob, rawPerson, atsJob (optional), atsPerson (optional)
- parsedJob, parsedPerson, atsJob (optional), atsPerson (optional)

This section outlines the parsedPerson.

|JSON Schema                                   |Datatype|Required                                         |Description                                                                                                                                                            |
|----------------------------------------------|---------|-------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|{                                             |         |                                                 |                                                                                                                                                                       |
|"jobExerience" : {                            |         |                                                 |                                                                                                                                                                       |
|"jobExperiences" : [ {                        |         |                                                 |A job experience instance.                                                                                                                                             |
|"expSequence" : "test",                       |string   |Required                                         |Sequence in the order of Most Recent Experience (1 being the most recent)                                                                                              |
|"companyName" : "text",                       |string   |Required                                         |Company name                                                                                                                                                           |
|"jobTitle" : "text",                          |string   |Required                                         |Job title                                                                                                                                                              |
|startDate" : "2018-05-02T15:46:38.117Z",      | string                                       |Required|Start date                                       |
|"endDate" : "2018-05-02T15:46:38.117Z",       |string   |Required                                         |End date                                                                                                                                                               |
|"state" : "text",                             |string   |Optional                                         |                                                                                                                                                                       |
|"country" : "textojJK051310",                 |string   |Optional                                         |Country                                                                                                                                                                |
|"ongoing" : "true",                           |Boolean  |                                                 |Is experience current?                                                                                                                                                 |
|"jobDescription" : "text",                    |string   |Optional                                         |Job role description                                                                                                                                                   |
|"companyName_normalized" : "text",            |string   |Required Bounded                                 |Company name                                                                                                                                                           |
|"duration" : "2",                             |integer  |Options                                          |Number of years                                                                                                                                                        |
|} ]                                           |         |                                                 |                                                                                                                                                                       |
|},                                            |         |                                                 |                                                                                                                                                                       |
|"education" : {                               |         |                                                 |                                                                                                                                                                       |
|"educations" : [ {                            |         |                                                 |                                                                                                                                                                       |
|"schoolName" : "text"                   |string                                    |Required|Name of the school the candidate attended.       |
|"schoolLocation" : "text",                    |string   |Optional                                         |Current location - City                                                                                                                                                |
|"schoolCountry" : "text",                     |string   |Optional                                         |Current location - State                                                                                                                                               |
|"major" : "text"      |string                              |Optional|Current location - Country                       |
|"educationLevel" : "secondary"     |string                  |Optional|Education Level                                  |
|"degree" : "text"                            |string                                     |Optional|Degree that the candidate earned from the school|
|"startDate" : "2000-05-02T15:46:38.117Z",     |date     |Optional                                         |Month and Year that the candidate attended this education                                                                                                              |
|"endDate" : "2008-05-02T15:46:38.117Z",       |date     |Optional                                         |Month and Year that the candidate completed this education                                                                                                             |
|"ongoing" : true,                             |boolean  |Optional                                         |Undergoing the education.                                                                                                                                              |
|"gpaScale" : "4",                             |integer   |Optional                                         |Person's Grade Point Average while at the school                                                                                                                       |
|"gpa" : "Optional text”                       |string   |Optional Bounded                                 |Candidate's Grade Point Average Scale (e.g. GPA of3.75 with GPAScale of 4.0) 4, 10, 100                                         |
|"eduSequence" : 2                             |integer  |Required                                         |Sequence in the order of Most Recent Education (1 being the most recent)                                                                                               |
|"schoolLocation_normalized" : "Optional text”|string   |Optional                                         |                                                                                                                                                                       |
|"schoolName_normalized"            |string                                 |Optional|                            |
|"major_normalized" : "text”                   |string   |Optional                                         |                                                                                                                                                                       |
|"majorFieldName" : "text”                     |string   |Optional                                         |                                                                                                                                                                       |
|"majorFieldType" : "text”                     |         |Optional                                         |                                                                                                                                                                       |
|"duration” : "2”                              |Integer  |                                                 |                                                                                                                                                                       |
|} ]                                           |         |                                                 |                                                                                                                                                                       |
|}                                             |         |                                                 |                                                                                                                                                                       |
|"competencyClassification" : [ {              |         |                                                 |                                                                                                                                                                       |
|"allClasses" : "text” ,[ {                    |string   |Optional                                         |An array of up to ten class-confidence pairs sorted in descending order of confidence. These are delimitted by pipe | symbol.                                          |
|"top class" : "text",                         |string   |Optional                                         |Top Class from the list of all Classess which has highest confidence                                                                                                   |
|"text" : "text",                              |string   |Optional                                         |                                                                                                                                                                       |
|"top_class_confidence" : "text"      |string            |Optional|Numerical value for the top class                |
|} ]                                           |         |                                                 |                                                                                                                                                                       |
|"competencyAggregations" : [ {                |         |                                                 |                                                                                                                                                                       |
|"count" : "text” ,[ {                         |string   |Optional                                         |Number of instances this Class was identified across all Classes                                                                                                       |
|"class_name" : "text",                        |string   |Optional                                         |Competency Class Name                                                                                                                                                  |
|"details" : "text",                           |string   |Optional                                         |Details                                                                                                                                                                |
|} ],                                          |         |                                                 |                                                                                                                                                                       |
|"errors”: {                                   |         |                                                 |                                                                                                                                                                       |
|"fieldName" : "text",                         |string   |Optional                                         |The field that has the error.                                                                                                                                          |
|"traceCode" : "text",                         |         |Optional                                         |Internal support identifier. This attribute is provided in the event of a System Processing Failure to provide useful information necessary to isolate the root cause.|
|"errorCode" : "text",                         |string   |Optional                                         |                                                                                                                                                                       |
|"errorDescription" : "text",                  |string   |Optional                                         |                                                                                                                                                                       |
|}                                             |         |                                                 |                                                                                                                                                                       |
|"competency" : {                             |         |                                                 |                                                                                                                                                                       |
|"yearsInIndustry" : "text",                   |string   |Optional                                         |Years in industry related to the competency                                                                                                                            |
|"competencies" : [ {                          |         |                                                 |                                                                                                                                                                       |
|"expertiseLevel" : "basic",                   |string   |Required                                         |Competency Unique Identifier                                                                                                                                           |
|"lastUsedDate" : "2008-05- 02T15:46:38.117Z",|string   |Required                                         |Date skill was last used.                                                                                                                                              |
|"skillCategory" : "text",                     |string   |Optional                                         |Skill category. level-0 lookup with Talent framework skill database based on skill Name                                                                                |
|"skillGroup" : "text",                        |string   |Optional                                         |Skill group. level-1 lookup with Talent framework skill database based on skill Name                                                                                   |
|"competencyName" : "required text",           |string   |Required                                         |Name of competency.                                                                                                                                                    |
|"yearsofExperience" : "1",                    |integer  |Optional                                         |Numbers of years of experience. Numeric value.                                                                                                                         |
|"competencyType" : "Management"              |string                                 |Required|Competency Type.                                 |
|} ]                                           |         |                                                 |                                                                                                                                                                       |
|}                                             |         |                                                 |                                                                                                                                                                       |
|}                                             |         |                                                 |                                                                                                                                                                       |





### atsJob API Input

**match_atsJob.json**

The atsJob contains the FORMATTED json representation of the job position used in matching as defined by the ATS system.

When posting to the Match API, you must post one of the following combinations. The first two parameters for each combination are required.

- rawJob, rawPerson, atsJob (optional) and atsPerson (optional)
- rawJob, parsedPerson, atsJob (optional) and atsPerson (optional)
- parsedJob, rawPerson, atsJob (optional), atsPerson (optional)
- parsedJob, parsedPerson, atsJob (optional), atsPerson (optional) This section outlines the atsJob.

This section outlines the atsJob.

| JSON Schema                                   |Datatype|Required                                         |Description     |
|-------------------------------|---------|--------------------------------|---------------------|
|{                                                |        |                 |                                            |   
|"Job" : {                                        |        |                 |                                                                                                                                       |
|"fields" : {                                     |        |                 |                                                                                                                                       |
|"locale" : " en-US",                             |string  |Required         |Country-Language Locale of the Job. See locale file.                                                                                   |
|"title" : " JK051310",                           |string  |Required         |Job title                                                                                                                              |
|"description" : " en-US",                        |string  |Required         |Please provide all the information related to Job Requirement, Educations, Experiences, Skills etc required for the Job in this field.|
|                                                 |        |                 |                                                                                                                                       |
|"roleId" : "M-2130 ",                            |string  |Required         |Unique code identifying the job role                                                                                                   |
|"role" : "Supervisor",                           |string  |Required         |Job Role Id of the Requisition provided by the Client.                                                                                 |
|"status" : "open",                               |string  |Required Bounded|Job Status (open, approved, closed, deleted, pending, cancelled, declined, onHold, other)                                             |
|"isManagementPosition" : true,                   |boolean|Optional         |Is this Management Position.                                                                                                           |
|"positionType" : "Permanent",                    |string  |Optional         |Position Type (Permanent, Contract etc).                                                                                               |
|"experienceLevel" : "entry",                     |string  |Optional Bounded|Experience Level, (entry, intermediate, senior, executive)                                                                 |
|"minSeniorityLevel" : 2,                         |integer|Optional         |Minimum seniority level required for this job. Where 1 is the lowest level.                                                            |
|"maxSeniorityLevel" : 2,                         |integer|Optional         |Maximum seniority level required for this job. Where 1 is the lowest level.                                                            |
|"primaryJobCategoryCode" :
"JC235",              |string  |Optional         |Primary Job Category (aka Job Family) Code to which Job belongs.                                                                       |
|"primaryJobCategory" :
"Regional Sales",         |string  |Optional         |Primary Job Category (aka Job Family) Name to which Job belongs.                                                                       |
|"secondaryJobCategoryCode" :
"JC235",            |string  |Optional         |Primary Job Category (aka Job Family) Code to which Job belongs.                                                                       |
|"secondaryJobCategory" :
"Regional Sales",       |string  |Optional         |Primary Job Category (aka Job Family) Name to which Job belongs.                                                                       |
|"travelRequired" : "none",                       |string  |Optional         |Description of how much travel is required for this job.                                                                               |
|"isLocationMandatory" : true,                    |boolean|Optional         |Should Location be considered.                                                                                                         |
|"locationName" : "Orlando",                      |string  |Optional         |Short name of the Location used by Client to distinguish location information. (comma separated).                                      |
|"city" : "Orlando",                              |string  |Optional         |Location where the Job is created - city.                                                                                              |
|"state" : "FL",                                  |string  |Optional         |Location where the job is created - state.                                                                                             |
|"country" : "US",                                |string  |Optional         |Location where the job is created - country.                                                                                           |
|"isExperienceMandatory" : true,                  |boolean|Optional         |Should education requirements be considered mandatory?                                                                                 |
|"isEducationMandatory" : true,                   |boolean|                 |                                                                                                                                       |
|"passingDate" :                                  |string  |Optional         |                                                                                                                                       |
|"isSkillMandatory" : true,                       |boolean|                 |                                                                                                                                       |
|"SkillKeywords" : ,                              |string  |                 |                                                                                                                                       |
|"industry" : ,                                   |        |                 |                                                                                                                                       |
|"education" : {                                  |        |Optional         |List of education.                                                                                                                     |
|"levels" : [ {                                   |        |                 |                                                                                                                                       |
|"level" :                                        |string  |Required         |The education level name                                                                                                               |
|"required" : true                                |boolean|Required         |Is this level required?                                                                                                                |
|"majors" : [ {                                   |        |                 |                                                                                                                                       |
|"major" :                                        |string  |Required         |Major area of study that the candidate should hold.                                                                                    |
|"required" : true                                |boolean|Required         |Is this major required?                                                                                                                |
|} ],                                             |        |                 |                                                                                                                                       |
|"gpaScale" : "4",                                |integer|Optional         |Person's Grade Point Average while at the school                                                                                       |
|"gpa" : ,                                        |string  |Optional         |Candidate's Grade Point Average Scale (e.g. GPA of 3.75 with GPAScale of 4.0)                                              |
|} ]                                              |        |                 |                                                                                                                                       |
|},                                               |        |                 |                                                                                                                                       |
|"experience" : [ {                               |        |Optional         |List of experience.                                                                                                                    |
|"description" :                                  |string  |Optional         |Free form textual description of required experience.                                                                                  |
|"required" : true                                |boolean|Required         |Is this experience required?                                                                                                           |
|} ],                                             |        |                 |                                                                                                                                       |
|"skills" : [ {                                   |        |Optional         |List of skills.                                                                                                                        |
|"description" :                                  |string  |Optional         |Free form textual description of required skills.                                                                                      |
|"required" : true                                |boolean|Required         |Is this skill required?                                                                                                                |
|} ],                                             |        |                 |                                                                                                                                       |
|"eligibility" : [ {                              |        |Optional         |                                                                                                                                       |
|"description" : "US Citizen or valid work visa”,|string  |Required         |Any specific requirements for this job (e.g. citizenship requirements).                                                                |
|"required" : true                                |boolean|Optional         |Is this required?                                                                                                                      |
|} ]                                              |        |                 |                                                                                                                                       |
|}                                                |        |                 |                                                                                                                                       |
|}                                                |        |                 |                                                                                                                                       |
|}                                                |        |                 |                                                                                                                                       |


### atsPerson API Input

**match_atsPerson.json**

The atsPerson contains the FORMATTED json representation of the person profile used in matching as defined by the ATS system.

When posting to the Match API, you must post oe of the following combinations. The first two parameters for each combination are required.

- rawJob, rawPerson, atsJob (optional) and atsPerson (optional)
- rawJob, parsedPerson, atsJob (optional) and atsPerson (optional)
- parsedJob, rawPerson, atsJob (optional), atsPerson (optional)
- parsedJob, parsedPerson, atsJob (optional), atsPerson (optional) This section outlines the atsPerson.json

This section outlines the atsPerson.json

|JSON Schema                                                                   |Datatype                   |Required                                                 |Description                                                                                              |
|------------------------------------------------------------------------------|---------------------------|---------------------------------------------------------|---------------------------------------------------------------------------------------------------------|
|{                                                                             |                           |                                                         |                                                                                                         |
|"person" : {                                                                  |                           |                                                         |                                                                                                         |
|"employeeType" : "regular",                                                   |string                     |Required                                                 |Unique Identifier from Client (may be ATS_ID, HRIS_ID, or client defined)                                |
|"candidateType" : "internal",                                                 |string                     |Required                                                 |Candidate Type (Internal, External)                                                                      |
|"personType" : "candidate",                                                   |string                     |Required                                                 |Determine if record if for employee or candidate                                                         |
|"locale" : "en-US",                                                           |string                     |Optional                                                 |Country-Language Locale in which Person exists.                                                          |
|}                                                                             |                           |                                                         |                                                                                                         |
|"contactInfoAddress" : { "John Smith",                                        |                           |                                                         |                                                                                                         |
|"addresses":[{"regular",                                                      |                           |                                                         |                                                                                                         |
|"city" : "Optional Text",                                                     |string                     |Optional                                                 |City                                                                                                     |
|"state" : "Optional Text",                                                    |string                     |Optional                                                 |State                                                                                                    |
|"country" : "Required text",                                                  |string                     |Required                                                 |Country                                                                                                  |
|} ]                                                                           |                           |                                                         |                                                                                                         |
|},                                                                            |                           |                                                         |                                                                                                         |
|"jobExperience" : {                                                           |string                     |Required Bounded                                         |                                                                                                         |
|"JobExperiences" :[{                                                          |string                     |Required                                                 |Candidate or Employee related job experience                                                             |
|"expSequence" : "Required Text"                          |String                                                                    |Required                   |                                                         |
|"companyName": "Required Text"                                |String                                                                   |Required                   |Name of all companies’ applicant worked for              |
|"jobTitle" : "Required Text"                                          |        |Required                                                                   |Job Title                  |
|"isLeadershipRole" : "true"                                                  |Boolean                                                               |Required                   |Leadership role designation                              |
|"isManager" : "true"                                                          |Boolean                                                                    |Required                   |Manager role designation                                 |
|"employeeType" : "Regular"                                             |       |Required                                                                |Employee type              |
|"startDate" : "2018-05-02T15:46:38.117Z",                                     |                           |Required                                                 |Start date                                                                                               |
|"endDate" : "2018-05-02T15:46:38.117Z",                                       |                           |                                                         |End date                                                                                                 |
|"state" : "Required Text"                                                     | |Optional                                                                  |Location of job – state.   |
|"country" : "Optional"                                                        | |Optional                                                                     |Location of job – country.|
|"ongoing" : "true",                                                           |                           |Boolean                                                  |                                                                                                         |
|"seniorityLevel" : "Optional Text"                                            | |Optional                                                                     |Seniority level            |
|"primaryCompetencies" : [“Optional Text"],                                    |string                     |Optional                                                 |Job competencies                                                                                         |
|"primaryExpertise" : [“Optional Text"],                                       |string                     |Optional                                                 |                                                                                                         |
|"jobDescription" : "OptionaL Text",                                           |string                     |Optional                                                 |Job Description                                                                                          |
|"companyName normalized" : "Optional"                                         |string                                                                      |Optional                   |                                                         |
|"duration" : "2"                                                              |Integer                                                                    |                           |Number of years in each position                         |
|} ]                                                                           |                           |                                                         |                                                                                                         |
|},                                                                            |                           |                                                         |                                                                                                         |
|"training" : {                                                                |                           |Optional                                                 |                                                                                                         |
|"trainings" : [ {                                                             |                           |                                                         |                                                                                                         |
|"trainingId" : "Required Text"                             |string                                                                    |                           |Training                                                 |
|"trainingName" : "Six Sigma Project Simulation",                              |string                     |Required                                                 |Training course name                                                                                     |
|"startDate" : "2018-05-02T15:46:38.117Z",                                     |date                       |Optional                                                 |Date the course started                                                                                  |
|"endDate" : "2018-05-02T15:46:38.117Z",                                       |date                       |Optional                                                 |Date the course completed                                                                                |
|"description" : "Perform case study based on real-world scenario…",           |string                     |Required                                                 |Training Description                                                                                     |
|"schoolName" : "XYZ Training Academy",                                        |string                     |Optional                                                 |School name                                                                                              |
|"schoolLocation" : "San Francisco",                                           |string                     |Optional                                                 |Location where Training was taken                                                                        |
|"schoolCountry" : "USA",                                                      |string                     |Optional                                                 |County where Training was taken                                                                          |
|"completionStatus" : "graduated",                                             |string                     |Optional                                                 |Course completion status                                                                                 |
|"completionScore" : "95",                                                     |string                     |Optional                                                 |Score achieved                                                                                           |
|"completionScoreScale" : "100",                                               |string                     |Optional                                                 |Score Scale (e.g. completionScore = 97 and completionScoreScale = 100)                                   |
|"competencyType" : "Lean Six Sigma",                                          |string                     |Required                                                 |Type of competency                                                                                       |
|"expertiseType" : "1",                                                        |string                     |Optional                                                 |Expertise Level (1 - Basic, 2 - Working, 3 - Extensive experience, 4 - Subject matter depth and breadth)|
|"certificationName" : "Lean Green Belt”,                                      |string                     |Optional                                                 |Certification Name associated to that Training                                                           |
|"certificateIssuedBy" : "National board"                                   |string                                    |Optional                   |Certification Issuing authority                          |
|} ]                                                                           |                           |                                                         |} ]                                                                                                      |
|},                                                                            |                           |                                                         |},                                                                                                       |
|"PublicationHistory" : {                                                      |                           |Optional Section                                         |                                                                                                         |
|"publications" : [ {                                                          |                           |                                                         |                                                                                                         |
|"publicationId" : "zy899s720-892x2",                                          |string                     |Required                                                 |                                                                                                         |
|"comment" : "Dedicated to providing…",                                        |string                     |Optional                                                 |                                                                                                         |
|"publicationDescription" : "If you’re looking for advice on retail sales, ",  |string                     |Optional                                                 |                                                                                                         |
|"publicationTitle" : "5 secrets to…",                                         |string                     |Optional                                                 |                                                                                                         |
|"publicationDate" :"2018-05-02T15:46:38.117Z"            |date                                                                      |Optional                   |                                                         |
|} ]                                                                           |                           |                                                         |                                                                                                         |
|},                                                                            |                           |                                                         |                                                                                                         |
|"patentHistory" :	{                                                           |                           |                                                         |                                                                                                         |
|"patents" : [ {                                                               |                           |                                                         |                                                                                                         |
|"patentId" : "877389" [ {                                                     |string                     |Required                                                 |Patent ID                                                                                                |
|"inventorName" : "John Smith",                                                |string                     |Required                                                 |Inventor Details                                                                                         |
|"patentTitle" : "3D Stock…",                                                  |string                     |Required                                                 |Patent Title                                                                                             |
|"patentDescription" : "This system lets stockers take…",                      |string                     |Optional                                                 |Patent Description                                                                                       |
|"filingDate" : "2018-05-02T15:46:38.117Z",                                    |date                       |Optional                                                 |Patent filling date                                                                                      |
|"issuingAuthority" : "uspto",                                                 |string                     |Optional                                                 |Issuing Authority                                                                                        |
|"patentStatus" : "filed"                                                      |string                                                                      |Optional                   |Current Patent Status                                    |
|} ]                                                                           |                           |                                                         |                                                                                                         |
|},                                                                            |                           |                                                         |                                                                                                         |
|"Education" : {                                                               |                           |Optional Section                                         |                                                                                                         |
|"educations" : [ {                                                            |                           |                                                         |                                                                                                         |
|"schoolName" : "ABC University",                                              |string                     |Required                                                 |Name of the school that the candidate attended                                                           |
|"schoolLocation" : "San Francisco",                                           |string                     |Optional                                                 |Education School Location                                                                                |
|"schoolCountry" : "US",                                                       |string                     |Optional                                                 |Education School Country                                                                                 |
|"major" : "Business Administration",                                          |string                     |Optional                                                 |Major area of study that the candidate participated in while at the school                               |
|"educationLevel" : c,                                                         |string                     |Optional Bounded                                         |Education Level Values, (secondary, vocational, university, bachelors, masters, phd, course)               |
|"degree" : "BS in Computer Science",                                          |string                     |Required                                                 |Degree that the candidate earned from the school                                                         |
|"startDate" : "2000-05-02T15:46:38.117Z",                                     |date                       |Optional                                                 |Month and Year that the candidate attended this education                                                |
|"endDate" : "2008-05-02T15:46:38.117Z",                                       |date                       |Optional                                                 |Month and Year that the candidate completed this education                                               |
|"ongoing" :	,                                                                 |boolean                    |Optional                                                 |Undergoing the education.                                                                                |
|"gpaScale" : "4",                                                             |intger                     |Optional                                                 |Person's Grade Point Average while at the school                                                         |
|"gpa" : "Optional text”                                                       |string                     |Optional Bounded                                         |Candidate's Grade Point Average Scale (e.g. GPA of 3.75 with GPAScale of 4.0)         |
|"eduSequence" : 2                                                             |integer                    |Required                                                 |Sequence in the order of Most Recent Education (1 being the most recent)                                 |
|"schoolLocation_normalized" : "Optional text”                                 |                           |Optional                                                 |                                                                                                         |
|"major_normalized" : "Optional text”                                          |                           |Optional                                                 |                                                                                                         |
|"majorFieldName" : "Optional text”                                            |                           |Optional                                                 |                                                                                                         |
|"majorFieldType" : "Optional text”                                            |                           |Optional                                                 |                                                                                                         |
|"duration” : "2”                 |Integer                                                  |                                                                                                         |
|} ]                                                                           |                           |                                                         |                                                                                                         |
|},                                                                            |                           |                                                         |                                                                                                         |
|"Certification" : {                                                           |                           |Optional Section                                         |                                                                                                         |
|"certifications" : [ {                                                        |                           |                                                         |Certification ID given by instituion                                                                     |
|"certificationId" : "crt99810",                                               |string                     |Required                                                 |                                                                                                         |
|"certificationName" : "Certified Retail Manager",                             |string                     |Required                                                 |Certification name                                                                                       |
|"issuer" : "ABC University",                                                  |string                     |Required                                                 |Education institute certificate issuer                                                                   |
|"country" : "US",                                                             |string                     |Optional                                                 |Country location of Education institute                                                                  |
|"description" : "The key focus of this certification is…",                    |string                     |Optional                                                 |Certificate information – what is the certificate certify?                                               |
|"receivedDate" :
"2009-05-02T15:46:38.117Z",                                  |date                       |Optional                                                 |Date certificate received                                                                                |
|"firstCertifiedDate" :
"2009-05-02T15:46:38.117Z",                            |date                       |Optional                                                 |Date of first certificate                                                                                |
|"numberOfRecertifications" : "9"                                              |string                                                                      |Optional                   |Number of certifications                                 |
|} ]                                                                           |                           |                                                         |                                                                                                         |
|},                                                                            |                           |                                                         |                                                                                                         |
|"award" : {                                                                   |                           |Optional Section                                         |                                                                                                         |
|"awards" : [ {                                                                |                           |                                                         |                                                                                                         |
|"awardName" : "Independent Retail Manager of the Year",                       |string                     |Required                                                 |Name of award                                                                                            |
|"recognitionPoint" : "text",                                                  |string                     |Optional                                                 |Recognition point                                                                                        |
|"awardType" : "Retail",                                                       |string                     |Optional                                                 |Award type                                                                                               |
|"achieveDate" :
"2018-05-02T15:46:38.117Z",                                   |date                       |Optional                                                 |Date award was given                                                                                     |
|"expiryDate" : "2018-05-02T15:46:38.117Z",                                    |date                       |Optional                                                 |Expiration date if any                                                                                   |
|"remark" : "For your success and achievements to be recognized as the best…"|string                                                                       |Optional                   |                                                         |
|} ]                                                                           |                           |                                                         |                                                                                                         |
|},                                                                            |                           |                                                         |                                                                                                         |
|"assessment" : {                                                              |                           |Optional Section                                         |                                                                                                         |
|"assessments" : [ {                                                           |                           |                                                         |                                                                                                         |
|"assessmentId" : "a130586",                                                   |string                     |Required                                                 |Assessment ID or Unique Assessment Identifier                                                            |
|"achievedScore" : "10",                                                       |string                     |Required                                                 |Score achieved                                                                                           |
|"assessmentName" : "Retail Management…",                                      |string                     |Required                                                 |Assessment Name taken                                                                                    |
|"dateTaken" : "2018-05-02T15:46:38.117Z",                                     |date                       |Optional                                                 |Date Assessment taken                                                                                    |
|"assessmentType" : "Standard",                                                |string                     |Optional                                                 |Assessment Type                                                                                          |
|"minScoreRequired" : "text"                                                   |string                                                                       |Optional                   |Minimum qualification score                              |
|} ]                                                                           |                           |                                                         |                                                                                                         |
|},                                                                            |                           |                                                         |                                                                                                         |
|"Competency" : {                                                              |                           |Optional Section                                         |                                                                                                         |
|"YearsInIndustry" "Optional Text",                                            |                           |Optional                                                 |Number of years in industry                                                                              |
|"competencies" : [ {                                                          |                           |                                                         |                                                                                                         |
|"isAssessed" : true,                                                          |Boolean                    |Optional                                                 |How assessed                                                                                             |
|"expertiseLevel" : "basic",                                                   |string                     |Required Bounded                                         |Expertise Level, (basic, working, extensiveExperience, subjectMatterDepthAndBreadth)                        |
|"expSequence" : "text",                                                       |string                     |Optional                                                 |Experience Sequence value from Experiences where this competency was used                                |
|"lastUsedDate" :
"2018-05-02T15:46:38.117Z",                                  |date                       |Optional                                                 |Year when the competency was last used                                                                   |
|"assessmentId" : "a130586",                                                   |string                     |Optional                                                 |If isAssessed is true then provide the corresponding assessmentId value from Assessments section         |
|"skillCategory"                                                               |string                                                                       |Optional                   |                                                         |
|"skillGroup"                                                                  |string                                                                       |                           |                                                         |
|"competencyName" : "Management"                                               |string                                                                       |Required                   |Competency Type.                                         |
|"competencyCode" : "Required Text"                                            |string                                                                       |Required                   |Total years of experience in the Industry                |
|"yearsofExperience" : "1"                                                     |string                                                                       |Optional                   |Total years of experience in association with competency|
|"competencyDescription" : "Optional Text"                                     |string                                                                       |Optional                   |Competency description                                   |
|"competencyType" : "Required Text"                                            |string                                                                       |Required                   |Competency type                                          |
|} ]                                                                           |                           |                                                         |                                                                                                         |
|}                                                                             |                           |                                                         |                                                                                                         |
|}                                                                             |                           |                                                         |                                                                                                         |


### Match Score Response API Ouput

**match_scoreResponse.json**

This section outlines the Match ScoreResponse.json

|JSON Schema                                   |Datatype|Required                                                         |Description                                                                                                                                                            |
|----------------------------------------------|---------|-----------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|{                                             |         |                                                                 |                                                                                                                                                                       |
|"job" : [ {                                   |         |                                                                 |                                                                                                                                                                       |
|"title" : {                                   |         |Optional                                                         |                                                                                                                                                                       |
|"description: "text",                         |string   |Optional                                                         |Job description.                                                                                                                                                       |
|"role" : "text",                              |string   |Required                                                         |Job role.                                                                                                                                                              |
|"jobClassification" : "text",                 |string   |Optional                                                         |Job classification.                                                                                                                                                    |
|"locationName" : "text",                      |string   |Optional                                                         |Job location.                                                                                                                                                          |
|"requiredExperience" : "text",                |string   |Optional                                                         |How many years experience is required                                                                                                                                  |
|},                                            |         |                                                                 |                                                                                                                                                                       |
|"education" :	{,                              |string   |Optional                                                         |Education                                                                                                                                                              |
|"degrees" : "text",[{                         |string   |Optional                                                         |Degree                                                                                                                                                                 |
|"degree" : "text",                            |string   |Required                                                         |Degree                                                                                                                                                                 |
|"required" : "true",                          |string   |Boolean                                                          |                                                                                                                                                                       |
|} ],                                          |         |                                                                 |                                                                                                                                                                       |
|"majors" : ,[{                                |string   |Optional                                                         |Major                                                                                                                                                                  |
|"major" : "text",                             |string   |Required                                                         |Major                                                                                                                                                                  |
|"required" : "true",                          |string   |Boolean                                                          |                                                                                                                                                                       |
|} ],                                          |         |                                                                 |                                                                                                                                                                       |
|"gpaScale" : "4",                             |         |                                                                 |Candidate'sGradePointAverage Scale (e.g. GPA of 3.75 with GPAScale of 4.0)                                                                                             |
|"gpa" : "text",                               |string   |Optional                                                         |Person's Grade Point Average while at the school                                                                                                                       |
|}                                             |         |                                                                 |                                                                                                                                                                       |
|"competency" : [ {                            |         |                                                                 |                                                                                                                                                                       |
|"competencyType" : "text” ,                   |string   |Optional                                                         |Competency Type e.g. Computer Skills                                                                                                                                   |
|"competencyName" : "text",                    |string   |Required                                                         |Competency Name                                                                                                                                                        |
|"competencyCategory" : "text",                |string   |Optional                                                         |Level-0 lookup with Talent framework skill database based on Name                                                                                                      |
|"competencyGroup" : "text"                    |string                                      |Optional|Level-0 lookup with Talent Framework still
database based on Name|
|} ]                                           |         |                                                                 |                                                                                                                                                                       |
|"competencyClassification" : [ {              |         |                                                                 |                                                                                                                                                                       |
|"allClasses" : "text” ,[ {                    |string   |Optional                                                         |An array of up to ten class-confidence pairs sorted in descending order of confidence. These are delimited by pipe symbol                                              |
|"top_class" : "text",                         |string   |Optional                                                         |Top Class from the list of all Classess which has highest confidence.                                                                                                  |
|"text" : "text",                              |string   |Optional                                                         |Text Phrase from the Job Description where the Classes were identified                                                                                                 |
|"top_class_confidence" : "text",              |string   |Optional                                                         |Class confidence – numerical value for the top class                                                                                                                   |
|} ],                                          |         |                                                                 |                                                                                                                                                                       |
|"competencyAggregations" : [ {                |         |                                                                 |                                                                                                                                                                       |
|"count" : "text” ,[ {                         |string   |Optional                                                         |How many competency aggregations                                                                                                                                       |
|"class_name" : "text",                        |string   |Optional                                                         |Class name                                                                                                                                                             |
|"details" : "text",                           |string   |Optional                                                         |Competency class details – text phrase                                                                                                                                 |
|} ],                                          |         |                                                                 |                                                                                                                                                                       |
|"errors" : {                                  |         |                                                                 |                                                                                                                                                                       |
|"fieldName" : "text",                         |string   |Optional                                                         |The field that has the error.                                                                                                                                          |
|"traceCode" : "text",                         |         |Optional                                                         |Internal support identifier. This attribute is provided in the event of a System Processing Failure to provide useful information necessary to isolate the root cause.|
|"errorCode" : "text",                         |string   |Optional                                                         |                                                                                                                                                                       |
|"errorDescription" : "text",                  |string   |Optional                                                         |                                                                                                                                                                       |
|}                                             |         |                                                                 |                                                                                                                                                                       |
|}                                             |         |                                                                 |                                                                                                                                                                       |
|"person" : {                                  |         |                                                                 |                                                                                                                                                                       |
|{                                             |         |                                                                 |                                                                                                                                                                       |
|"jobExerience" : {                            |         |                                                                 |                                                                                                                                                                       |
|"jobExperiences" : [ {                        |         |                                                                 |A job experience instance.                                                                                                                                             |
|"expSequence" : "test",                       |string   |Required                                                         |Sequence in the order of Most Recent Experience (1 being the most recent)                                                                                              |
|"companyName" : "text",                       |string   |Required                                                         |Company name                                                                                                                                                           |
|"jobTitle" : "text",                          |string   |Required                                                         |Job title                                                                                                                                                              |
|startDate" : "2018-05-02T15:46:38.117Z",      |string                                       |Required|Start date                                                       |
|"endDate" : "2018-05-02T15:46:38.117Z",       |string   |Required                                                         |End date                                                                                                                                                               |
|"state" : "text",                             |string   |Optional                                                         |                                                                                                                                                                       |
|"country" : "textojJK051310",                 |string   |Optional                                                         |Country                                                                                                                                                                |
|"ongoing" : "text",                           |Boolean  |                                                                 |Is experience current?                                                                                                                                                 |
|"jobDescription" : "text",                    |string   |Optional                                                         |Job role description                                                                                                                                                   |
|"companyName_normalized" : "text",            |string   |Required Bounded                                                 |Normalized company name lookup with TF dictionary.                                                                                                                     |
|"duration" : "2",                             |integer  |Options                                                          |Number of years                                                                                                                                                        |
|} ]                                           |         |                                                                 |                                                                                                                                                                       |
|},                                            |         |                                                                 |                                                                                                                                                                       |
|"education" : {                               |         |                                                                 |                                                                                                                                                                       |
|"educations" : [ {                            |         |                                                                 |                                                                                                                                                                       |
|"schoolName" : "text"                         |string                                    |Required|Name of the school the candidate attended.                       |
|"schoolLocation" : "text",                    |string   |Optional                                                         |Current location - City                                                                                                                                                |
|"schoolCountry" : "text",                     |string   |Optional                                                         |Current location - State                                                                                                                                               |
|"major" : "text"                              |string                                    |Optional|Current location - Country                                       |
|"educationLevel" : "secondary"                |string                                       |Optional|Education Level                                                  |
|"degree" : "text"                             |string                                       |Optional|Degree that the candidate earned from the school                 |
|"startDate" : "2000-05-02T15:46:38.117Z",     | date     |Optional                                                         |Month and Year that the candidate attended this education                                                                                                              |
|"endDate" : "2008-05-02T15:46:38.117Z",       |date     |Optional                                                         |Month and Year that the candidate completed this education                                                                                                             |
|"ongoing" : true,                             |boolean  |Optional                                                         |Undergoing the education.                                                                                                                                              |
|"gpaScale" : "4",                             |intger   |Optional                                                         |Person's Grade Point Average while at the school                                                                                                                       |
|"gpa" : "Optional text”                       |string   |Optional Bounded                                                 |Peron’s Grade Point Average Scale (e.g. GPA of 3.75 with GPAScale of 4.0)                                                                                              |
|eduSequence" : 1                              |integer  |Required                                                         |Sequence in the order of Most Recent Education (1 being the most recent)                                                                                               |
|"schoolLocation_normalized" : "Optional text”|string   |Optional                                                         |Normalized School location by lookup with TF dictionary.                                                                                                               |
|"schoolName_normalized"                       |string                                    |Optional|Normalized School Name by lookup with TF dictionary.             |
|"major_normalized" : "text”                   |string   |Optional                                                         |Major by lookup with TF dictionary based on major
if not found then polished(removed special character and stop words defined in TF) value.                            |
|"majorFieldName" : "text”                     |string   |Optional                                                         |Field name by lookup with TF dictionary.                                                                                                                               |
|"majorFieldType" : "text”                     |         |Optional                                                         |                                                                                                                                                                       |
|"duration” : "2”                              |Integer  |                                                                 |                                                                                                                                                                       |
|} ]                                           |         |                                                                 |                                                                                                                                                                       |
|}                                             |         |                                                                 |                                                                                                                                                                       |
|"competencyClassification" : [ {              |         |                                                                 |                                                                                                                                                                       |
|"allClasses" : "text” ,[ {                    |string   |Optional                                                         |An array of up to ten class-confidence pairs sorted in descending order of confidence. These are delimitted by pipe | symbol.                                          |
|"top class" : "text",                         |string   |Optional                                                         |Top Class from the list of all Classess which has highest confidence                                                                                                   |
|"text" : "text",                              |string   |Optional                                                         |Text Phrase from the Job Description where the Classes were identified                                                                                                 |
|"top_class_confidence" : "text"               |string                                      |Optional|Numerical value for the top class                                |
|} ]                                           |         |                                                                 |                                                                                                                                                                       |
|"competencyAggregations" : [ {                |         |                                                                 |                                                                                                                                                                       |
|"count" : "text” ,[ {                         |string   |Optional                                                         |Number of instances this Class was identified across all Classes                                                                                                       |
|"class_name" : "text",                        |string   |Optional                                                         |Competency Class Name                                                                                                                                                  |
|"details" : "text",                           |string   |Optional                                                         |Details                                                                                                                                                                |
|} ],                                          |         |                                                                 |                                                                                                                                                                       |
|"errors”: {                                   |         |                                                                 |                                                                                                                                                                       |
|"fieldName" : "text",                         |string   |Optional                                                         |The field that has the error.                                                                                                                                          |
|"traceCode" : "text",                         |         |Optional                                                         |Internal support identifier. This attribute is provided in the event of a System Processing Failure to provide useful information necessary to isolate the root cause.|
|"errorCode" : "text",                         |string   |Optional                                                         |                                                                                                                                                                       |
|"errorDescription" : "text",                  |string   |Optional                                                         |                                                                                                                                                                       |
|},                                            |         |                                                                 |                                                                                                                                                                       |
|"compentency" : {                             |         |                                                                 |                                                                                                                                                                       |
|"yearsInIndustry" : "text",                   |string   |Optional                                                         |Years in industry related to the competency                                                                                                                            |
|"competencies" : [ {                          |         |                                                                 |                                                                                                                                                                       |
|"expertiseLevel" : "basic",                   |string   |Required                                                         |Competency Unique Identifier                                                                                                                                           |
|"lastUsedDate" : "2008-05- 02T15:46:38.117Z",|string   |Required                                                         |Date skill was last used.                                                                                                                                              |
|"skillCategory" : "text",                     |string   |Optional                                                         |Skill category. level-0 lookup with Talent framework skill database based on skill Name                                                                                |
|"skillGroup" : "text",                        |string   |Optional                                                         |Skill group. level-1 lookup with Talent framework skill database based on skill Name                                                                                   |
|"competencyName" : "required text",           |string   |Required                                                         |Name of competency.                                                                                                                                                    |
|"yearsofExperience" : "1",                    |integer  |Optional                                                         |Numbers of years of experience. Numeric value.                                                                                                                         |
|"competencyType" : "Management"               |string                                       |Required|Competency Type.                                                 |
|} ]                                           |         |                                                                 |                                                                                                                                                                       |
|}                                             |         |                                                                 |                                                                                                                                                                       |
|}                                             |         |                                                                 |                                                                                                                                                                       |
|{                                             |         |                                                                 |                                                                                                                                                                       |
|"match" : {                                   |         |                                                                 |                                                                                                                                                                       |
|"scores" : [ {                                |         |                                                                 |                                                                                                                                                                       |
|"matchScore" : "-100",                        |integer  |Required                                                         |Match score results are between 0 and 100 with 100 being the best possible match.                                                                                      |
|"preferredSkillScore": "text”,                |string   |Optional text                                                    |Integer representing Preferred Skill Score.                                                                                                                            |
|"requiredSkillScore" : "text”,                |string   |Optional text                                                    |                                                                                                                                                                       |
|"foundationalSkillScore" : "text”,            |string   |Optional text                                                    |Watson Recruitment – required if using Watson Recruitment User Interface.                                                                                              |
|"requiredEducationScore" : "text”,            |string   |Optional                                                         |                                                                                                                                                                       |
|"preferredEducationScore" : "text”,           |string   |Optional                                                         |                                                                                                                                                                       |
|"previousJobScore" : "text",                  |string   |Optional                                                         |                                                                                                                                                                       |
|"experienceLevelScore" : "text",              |string   |Optional                                                         |                                                                                                                                                                       |
|"preferredSkillScoreDetails" : [ {"text",     |string   |Optional                                                         |                                                                                                                                                                       |
|"skillName" : "text”,                         |string   |Optional                                                         |Skill from requisition For example, Java                                                                                                                               |
|"skillMatchType" : "text”,                    |integer  |Optional                                                         |                                                                                                                                                                       |
|"skillMatchValue" :] "text”,                  |string   |Optional                                                         |Matching skills from candidate.                                                                                                                                        |
|} ],                                          |         |                                                                 |                                                                                                                                                                       |
|"requiredSkillScoreDetails" : ["integer", [{  |         |                                                                 |                                                                                                                                                                       |
|"skillName" : "text”,                         |string   |Optional                                                         |Skill from requisition For example, Microsoft Office                                                                                                                   |
|"skillMatchType" : "text”,                    |integer  |Optional                                                         |                                                                                                                                                                       |
|"skillMatchValue" : "text”,                   |string   |Optional                                                         |Matching skills from candidate. For example, Microsoft Office                                                                                                          |
|} ],                                          |         |                                                                 |                                                                                                                                                                       |
|"foundationSkillScoreDetails”: [ {            |string   |Optional                                                         |                                                                                                                                                                       |
|"foundationSkillName”: "text”,                |         |                                                                 |Drive to achieve, foundation skills                                                                                                                                    |
|"requisition” :[ {                            |         |                                                                 |Relevant text from requisition ().                                                                                                                                     |
|"text” : ()”"text”,                           |string   |Optional                                                         |Relevant text from requisition.                                                                                                                                        |
|} ],                                          |         |                                                                 |                                                                                                                                                                       |
|"candidate” : [ {                             |string   |Optional                                                         |                                                                                                                                                                       |
|"text” :                                      |string   |Optional                                                         |Relevant text from the candidate for this soft skill.                                                                                                                  |
|} ]                                           |         |                                                                 |                                                                                                                                                                       |
|} ],                                          |         |                                                                 |                                                                                                                                                                       |
|"preferredEducationScoreDetails" : [,         |string   |                                                                 |                                                                                                                                                                       |
|{                                             |         |                                                                 |                                                                                                                                                                       |
|"requisition” : [                             |         |                                                                 |                                                                                                                                                                       |
|{                                             |         |                                                                 |                                                                                                                                                                       |
|"level":	"text”,                              |string   |Optional                                                         |Bachelor                                                                                                                                                               |
|"major": "text”,                              |string   |Optional                                                         |Computer Science                                                                                                                                                       |
|} ]                                           |         |                                                                 |                                                                                                                                                                       |
|"candidate” : [ {                             |         |                                                                 |                                                                                                                                                                       |
|"level": "text”,                              |string   |Optional                                                         |Bachelor                                                                                                                                                               |
|"major": "text”,                              |string   |Optional                                                         |Computer Engineering                                                                                                                                                   |
|"levelMatchType": "text”,                     |string   |Optional                                                         |                                                                                                                                                                       |
|"degreeMatchType:": "text”,                   |string   |Optional                                                         |                                                                                                                                                                       |
|} ]                                           |         |                                                                 |                                                                                                                                                                       |
|} ],                                          |         |                                                                 |                                                                                                                                                                       |
|"requiredEducationScoreDetails" : [ {,        |string   |                                                                 |                                                                                                                                                                       |
|"requisition” : [ {                           |         |                                                                 |                                                                                                                                                                       |
|"level": "text”,                              |         |                                                                 |Bachelor                                                                                                                                                               |
|"major": "text”,                              |         |                                                                 |Spanish                                                                                                                                                                |
|} ],                                          |         |                                                                 |                                                                                                                                                                       |
|"candidate” : [ {                             |         |                                                                 |                                                                                                                                                                       |
|"level": "text”                               |string   |Optional                                                         |Bachelor                                                                                                                                                               |
|"major": "text”                               |string   |Optional                                                         |French                                                                                                                                                                 |
|"levelMatchType": "text”                      |integer  |Optional                                                         |                                                                                                                                                                       |
|"degreeMatchType:": "text”                    |integer  |Optional                                                         |                                                                                                                                                                       |
|} ]                                           |         |                                                                 |                                                                                                                                                                       |
|} ],                                          |         |                                                                 |                                                                                                                                                                       |
|"previousJobScoreDetails" : [ {               |         |                                                                 |                                                                                                                                                                       |
|"requistion” :[ {                             |         |                                                                 |                                                                                                                                                                       |
|"title” : "text”                              |         |Optional                                                         |Software developer                                                                                                                                                     |
|} ],,                                         |         |                                                                 |                                                                                                                                                                       |
|"candidate” : {                               |         |                                                                 |                                                                                                                                                                       |
|"title” : "text”                              |         |Optional                                                         |Software engineer                                                                                                                                                      |
|"previousJobMatchType” : "text”               |integer  |Optional                                                         |                                                                                                                                                                       |
|} ],                                          |         |                                                                 |                                                                                                                                                                       |
|} ],,                                         |         |                                                                 |                                                                                                                                                                       |
|"experienceLevelDetails” : [ {                |         |                                                                 |                                                                                                                                                                       |
|"requisition” : [ {                           |         |                                                                 |                                                                                                                                                                       |
|"experienceLevel” : "text”                    |string   |Optional                                                         |                                                                                                                                                                       |
|} ],                                          |         |                                                                 |                                                                                                                                                                       |
|"candidate” : [ {                             |         |                                                                 |                                                                                                                                                                       |
|"yearsOfExperience” : "text”                  |string   |Optional                                                         |                                                                                                                                                                       |
|"experienceLevelMatchType” : "text”           |string   |Optional                                                         |                                                                                                                                                                       |
|} ]                                           |         |                                                                 |                                                                                                                                                                       |
|} ]                                           |         |                                                                 |                                                                                                                                                                       |
|"errors”: {                                   |         |                                                                 |                                                                                                                                                                       |
|"fieldName" : "text",                         |string   |Optional                                                         |The field that has the error.                                                                                                                                          |
|"traceCode" : "text",                         |         |Optional                                                         |Internal support identifier. This attribute is provided in the event of a System Processing Failure to provide useful information necessary to isolate the root cause.|
|"errorCode" : "text",                         |string   |Optional                                                         |                                                                                                                                                                       |
|"errorDescription" : "text",                  |string   |Optional                                                         |                                                                                                                                                                       |
|} ]                                           |         |                                                                 |                                                                                                                                                                       |
|} ]                                           |         |                                                                 |                                                                                                                                                                       |
|}                                             |         |                                                                 |                                                                                                                                                                       |
|}                                             |         |                                                                 |                                                                                                                                                                       |


