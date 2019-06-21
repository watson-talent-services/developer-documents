---
copyright: 'Copyright IBM Corp. 2019'
link: v1-talent-frameworks-guide
is: 'beta'
---

# Talent Frameworks Guide

To understand Talent Frameworks, consider the basic model for jobs and people in an organization. There are many jobs that make up an organization, and each job can be thought of as requiring a set of specific skills. For each skill, there are different levels of proficiency that are tied into that specific job. Similarly, people have a set of skills that reflect their experience, training, education and personality, and a person has a certain proficiency for each skill.

### Talent Frameworks Model

This basic model is at the core of Talent Frameworks. 

![Talent Frameworks Core Model](https://github.com/watson-talent-services/developer-documents/blob/master/images/TFCoreModel.png)

---

Watson Talent Frameworks also includes interview questions, coaching tips, development goals, and prescriptive learning suggestions for each competency and skill level.

- Job profiles can be customized to meet the needs of your organization.
- Job profiles can be easily deployed across a wide range of HR applications, both IBM and non-IBM.
- New jobs and skills are continually added, curated by Watson.


![puzzle](https://github.com/watson-talent-services/developer-documents/blob/master/images/puzzle5.png)


### What can you do with Talent Frameworks?


### Stay current on job requirements

_Problem_

Recruiters need an up-to-date job description with skills and or competency levels necessary for the position. Sometimes the hiring managers don’t know what interview questions to ask to verify the skill level. 

_Solution_

Watson Talent Frameworks provides skill taxonomies and interview questions for over 3000 jobs across 16 industries.

---

### Data to infuse Artificial Intelligence (AI) into your HR applications

_Problem_

Machine Learning relies on good data to learn from. It needs consistent “vocabulary” and accurate jobs and skills data. Better the data, more accurate the results will be.

_Solution_

Watson Talent Frameworks provides accurate and comprehensive skills data for thousands of jobs. It provides a solid foundation to build AI applications, from interpreting paper resumes to matching skills to jobs.

---

### Identify skill gaps

_Problem_

Employees need to identify the skills required to progress their career and how to close the gaps.

_Solution_

Watson Talent Frameworks provides skill proficiency descriptions, development statements and learning references. Employees can take those learning paths to gain new skills and advance their career.

---

### Set clear performance goals

_Problem_

Managers need to set clear expectations for each job to objectively evaluate employee performance.

_Solution_

Watson Talent Frameworks provides not just the skills but also the level of skill needed for each job and coaching tips for managers

---

## How you can use the Talent Frameworks APIs

Watson Talent Frameworks Publisher includes API functionality to easily access your entitled Talent Frameworks content. 
To learn how to access these, please read 
[Accessing Watson Talent Frameworks API](https://github.com/watson-talent-services/developer-documents/blob/master/developer-guide/v1-accessing-wtfp-api.md). 
These pull APIs, accessed with your IBMID by using the IBM Marketplace, can be used with a third-party connector to integrate 
with the APIs of other human capital management applications. IBM Global Business Services can be contracted to support 
integration with Workday, Oracle, Cornerstone OnDemand and SAP SuccessFactors, or you can build your own. 

Here's an overview of the API's

| Content | HTTP action | Output Type | Format | Notes |
| ------- | ----------- | ----------- | ------ | -----|
| Full Library | GET | Interactive | JSON | All fields |
| Competencies | GET | Interactive | JSON |	All competency fields including coaching tips, development statements, learning references and interview questions mapped to each competency |
| Base Jobs    | GET | Interactive | JSON |	All base job fields including job band, job focus, job description and key responsibilities.  This API does not include competencies or additional content |
| Competencies | GET | Download File* |	Excel, XML | All competency fields including coaching tips, development statements, learning references and interview questions mapped to each competency |
| Jobs | GET | Download File* |	Excel, XML |	All base job fields including job band, job focus, job description and key responsibilities.  This API does not include competencies or additional content |
| Additional Content | GET |	Download File* | Excel, XML |	All additional content or by type such as Job Band, Job Focus, Coaching Tips or Interview Questions |
| Full Library | GET | Download File* |	Excel, XML | All fields.  An additional API call will be required to retrieve the generated document |
| Single Entity | GET | Download File* | Excel, XML |	Any single entity by code, at any level such as Base Job, Competency, Framework, Job Family.  This API does not include associated entities |
| Cart | GET | Download File* |	Excel, XML | Multiple entities, by code, at any level such as Base Job, Competency, Framework, Job Family.  This API does not include associated entities |

`* An additional API call is required to retrieve the generated document `

---

### The Talent Frameworks model in-depth

### Frameworks

IBM has developed a concept of **Frameworks**, and has developed sets of these, to structure an entire organization around specific industries. 

![Frameworks](https://github.com/watson-talent-services/developer-documents/blob/master/images/FrameworksFull.png)

### Job Families

**Frameworks** are made up of sets of **Job Families**.

![Job Families](https://github.com/watson-talent-services/developer-documents/blob/master/images/JobFamilyDef.png)

Consider this example of a **Framework** for **Banking & Financial Services**, it is composed of many **Job Families**, like Accounting, Mortgage Lending, Investment Services and many more. 

![Job Families](https://github.com/watson-talent-services/developer-documents/blob/master/images/JobFamilyBankingExample.png)

### Job and Job Profile

A **Job** represents the basic definition of a job in the organization.

A **Job Profile** connects a specific **Job** to those competencies that constitute the **Job**. Each competency in a **Job Profile** needs to indicate a proficiency level. A scale of 0 to 4 is used to represent the proficiency of that competency, with 4 being the highest level (whiule 0 indicates no level at all).

![Job and Profile](https://github.com/watson-talent-services/developer-documents/blob/master/images/JobAndProfile.png)

### Competency

**Competency** represents the entirety of skills needed for all jobs in the organization and for the skills each person possesses .

![Competency](https://github.com/watson-talent-services/developer-documents/blob/master/images/Compentencies.png)


**Competency Accelerators** represent items that can help people improve their proficiency in a competency, such as Learning References. **Competency Accelerators** are linked to **Job Profiles** and provide the actions people take to progress their careers.

![Competency Accelerator](https://github.com/watson-talent-services/developer-documents/blob/master/images/CompetencyAccelerator.png)
