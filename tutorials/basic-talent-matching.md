---
copyright: 'Copyright IBM Corp. 2019'
link: basic-talent-match
is: 'beta'
---

# Basic Talent Match

In this tutorial, you'll see how to make a basic call to the IBM Watson Talent Match API using a tool for making REST calls. 
In this case, we used Postman, but you can use whatever tool your comfortable with. 

We've made this into a checklist so you can follow along. You can also grab this file, and open it with Postman to set all the right fields (you'll still need to get your ID/Secret and upload the files) - [Postman file for this tutorial](https://github.com/watson-talent-services/developer-documents/blob/master/tutorials/WTP-Talent%20Match%20v1.postman_collection.json).

You can begin your free trial by visiting the [IBM Marketplace for the Talent Match API](https://www.ibm.com/us-en/marketplace/watson-talent-match/details). 

### 1. Fire up Postman, Enter the Talent Match API and set to POST

- [ ] Fire up your REST test tool

![Firing up Postman](https://github.com/watson-talent-services/developer-documents/blob/master/images/PostmanStep1.png)

- [ ] Enter Talent Match API and change request verb to POST

We also added the version parameter to the URL itself, and Postman picks that up and adds as a parameter

![Entering the Talent Match API endpoint](https://github.com/watson-talent-services/developer-documents/blob/master/images/PostmanStep2.png)

![Entering the Talent Match API endpoint](https://github.com/watson-talent-services/developer-documents/blob/master/images/PostmanStep2-A.png)

### 2. Update the Authorization type

- [ ] Update the authorization type to **No Auth**

![Update authorization type](https://github.com/watson-talent-services/developer-documents/blob/master/images/PostmanStep3.png)

![Update authorization type](https://github.com/watson-talent-services/developer-documents/blob/master/images/PostmanStep3-A.png)

### 3. Enter the Headers and Items

- [ ] Switch to the Headers tab

![Go to the Headers tab](https://github.com/watson-talent-services/developer-documents/blob/master/images/PostmanStep4.png)

You will need to get the credentials you received from the IBM API Explorer, you'll get one for your **ID** called **x-ibm-client-id** and one for your **Secret** called **x-ibm-client-secret**. [Get your credentials here](https://developer.ibm.com/api/view/watsontalent-prod:watson-talent-match:title-Watson_Talent_Match). 

- [ ] Enter the Client ID key - called **x-ibm-client-id**, then enter the value to the **ID** value you received from API Explorer
- [ ] Enter the Secret key  - called **x-ibm-client-secret**, , then enter the value to the **Secret** value you received from API Explorer
- [ ] Enter the **Content-type** key and set the value to **multipart/form-data**
- [ ] Enter the **Accept** key and set the value to **application/json**

Holy optometrists winfall Batman - we had to blur the ID and Secret we used, because, well, some joker may lift it...no worries, you can use your own.

![Enter the keys](https://github.com/watson-talent-services/developer-documents/blob/master/images/PostmanStep5.png)

![Enter the keys](https://github.com/watson-talent-services/developer-documents/blob/master/images/PostmanStep5-A.png)

### 4. Enter the Body

Here we will use two files, one for the Job Requisition and one for the Person's work experience. We have a job requisition for a Dev Ops person [Job Requisition PDF](https://github.com/watson-talent-services/developer-documents/blob/master/pdf/JobDescription.pdf) and a fictional resume for a person [Joe Schmoe's CV PDF](https://github.com/watson-talent-services/developer-documents/blob/master/pdf/JoeSchmoeFakeResume.pdf).

- [ ] Change the Content type to **form-data** by selecting that radio button
- [ ] Enter the name for the Job Requisition object, **rawJob**

![Enter the **rawJob** object](https://github.com/watson-talent-services/developer-documents/blob/master/images/PostmanStep6.png)

![Enter the **rawJob** object](https://github.com/watson-talent-services/developer-documents/blob/master/images/PostmanStep6-A.png)

### 5. Select the file to use

Since we're using a file we need to tell Postman to upload it.

- [ ] Select the **Text** menu on the right of the **rawJob** object name.
- [ ] Select **File** from the drop down menu

![Get ready to upload a file](https://github.com/watson-talent-services/developer-documents/blob/master/images/PostmanStep7.png)

![Get ready to upload a file](https://github.com/watson-talent-services/developer-documents/blob/master/images/PostmanStep7-A.png)

### 6. Browse and add the file

- [ ] Select the right file from your computer, we used []()

![Select the file](https://github.com/watson-talent-services/developer-documents/blob/master/images/PostmanStep8.png)

![Select the file](https://github.com/watson-talent-services/developer-documents/blob/master/images/PostmanStep8-A.png)

![Select the file](https://github.com/watson-talent-services/developer-documents/blob/master/images/PostmanStep8-B.png)

### 7. Enter the Person information

We'll follow the same steps as above, but now for the **rawPerson** object to upload the person's work experience.

- [ ] Enter the name for the Person object, **rawPerson**
- [ ] Select the **Text** menu on the right of the **rawPerson** object name.
- [ ] Select **File** from the drop down menu
- [ ] Select the right file from your computer, we used [Joe Schmoe's CV PDF](https://github.com/watson-talent-services/developer-documents/blob/master/pdf/JoeSchmoeFakeResume.pdf)

![Select the file](https://github.com/watson-talent-services/developer-documents/blob/master/images/PostmanStep9.png)

### 8. Get the Match Results!

Ok, we've got everything ready to go, now we click the **Send** button and...

![Select the file](https://github.com/watson-talent-services/developer-documents/blob/master/images/PostmanStep10.png)

We get the results

![Select the file](https://github.com/watson-talent-services/developer-documents/blob/master/images/PostmanStep11.png)

And here's the whole JSON response.

```
{
    "job": {
        "job": {
            "title": "",
            "requiredExperience": "",
            "jobClassification": "Other",
            "description": "* Participating in the entire software development cycle by analyzing, designing, and developing new features and products. * Solving complex business problems for our world-class client organizations * Building new software using Microsoft .Net Framework and C# * Enhancing the functionality, performance, and scalability of our product suite * Interact with clients, understand their unique situations and ensure client success * Learning and contributing to products on a variety of architectures: cloudbased, RESTFul APIs, oData, client-server, n-tier * Researching new technology and tools to improve our product and processes * Mentoring junior development staff on architecture design and technical guidance * Collaborating with global development teams to achieve business goals",
            "role": ""
        },
        "competency": [
            {
                "competencyType": "ComputerSkill",
                "competencyGroup": "[\"Microsoft .net Programming\"]",
                "competencyCategory": "[\".Net Programming Tools\"]",
                "competencyName": "Net Framework"
            },
            {
                "competencyType": "ComputerSkill",
                "competencyGroup": "[\"Microsoft .net Programming\"]",
                "competencyCategory": "[\"C#\"]",
                "competencyName": "C#"
            },
            {
                "competencyType": "ComputerSkill",
                "competencyGroup": "[\"Java Programming\",\"Object Oriented Programming\"]",
                "competencyCategory": "[\"Core Java\",\"Java Technologies\"]",
                "competencyName": "Java"
            },
            {
                "competencyType": "ComputerSkill",
                "competencyGroup": "[\"Engineering\",\"Object Oriented Programming\"]",
                "competencyCategory": "[\"Programming\",\"C++\"]",
                "competencyName": "C++"
            },
            {
                "competencyType": "ComputerSkill",
                "competencyGroup": "[\"Microsoft Enterpise Systems\"]",
                "competencyCategory": "[\"Microsoft Applications\"]",
                "competencyName": "Microsoft Office Suite"
            },
            {
                "competencyType": "ComputerSkill",
                "competencyGroup": "[\"Microsoft .net Programming\",\"Microsoft Enterpise Systems\"]",
                "competencyCategory": "[\".Net Programming Tools\",\"Microsoft Applications\"]",
                "competencyName": "Microsoft .Net"
            },
            {
                "competencyType": "ComputerSkill",
                "competencyGroup": "[\"Test - IT\"]",
                "competencyCategory": "[\"Software Performance Testing\",\"System Testing\",\"Testing Methods\"]",
                "competencyName": "scalability"
            },
            {
                "competencyType": "ComputerSkill",
                "competencyGroup": "[\"IT Integration\",\"Web Programming\"]",
                "competencyCategory": "[\"Web Service Protocols\"]",
                "competencyName": "RESTFul"
            },
            {
                "competencyType": "ComputerSkill",
                "competencyGroup": "[\"Application Programming Interface\",\"Database Technologies\",\"Java Programming\"]",
                "competencyCategory": "[\"Database APIs\",\"Java APIs\",\"Social Media APIs\"]",
                "competencyName": "APIs"
            },
            {
                "competencyType": "ComputerSkill",
                "competencyGroup": "[\"Application Programming Interface\",\"Web Programming\"]",
                "competencyCategory": "[\"REST\"]",
                "competencyName": "oData"
            },
            {
                "competencyType": "ComputerSkill",
                "competencyGroup": "[\"System Design and Architecture - IT\"]",
                "competencyCategory": "[\"Software Architecture and Design\"]",
                "competencyName": "client-server"
            },
            {
                "competencyType": "ComputerSkill",
                "competencyGroup": "[\"System Design and Architecture - IT\"]",
                "competencyCategory": "[\"Software Architecture and Design\"]",
                "competencyName": "n-tier"
            },
            {
                "competencyType": "ComputerSkill",
                "competencyGroup": "[\"Software Development\"]",
                "competencyCategory": "[\"Software Engineering Related\"]",
                "competencyName": "Computer Science"
            },
            {
                "competencyType": "ComputerSkill",
                "competencyGroup": "[\"Software Development\"]",
                "competencyCategory": "[\"Software Engineering Related\"]",
                "competencyName": "Software Engineering"
            },
            {
                "competencyType": "ComputerSkill",
                "competencyGroup": "[\"Object Oriented Programming\"]",
                "competencyCategory": "[\"Object Oriented Paradigm\"]",
                "competencyName": "Object Oriented Design"
            },
            {
                "competencyType": "ComputerSkill",
                "competencyGroup": "[\"Software Development\"]",
                "competencyCategory": "[\"Software Engineering Related\"]",
                "competencyName": "Software development"
            },
            {
                "competencyType": "ComputerSkill",
                "competencyGroup": "[\"Engineering\"]",
                "competencyCategory": "[\"Programming\"]",
                "competencyName": "C"
            },
            {
                "competencyType": "ComputerSkill",
                "competencyGroup": "[\"Data Science\",\"Database\",\"Database Technologies\"]",
                "competencyCategory": "[\"Computational Learning Theory\",\"Database\",\"Database Concepts\"]",
                "competencyName": "database theory"
            },
            {
                "competencyType": "ComputerSkill",
                "competencyGroup": "[\"Software Development\"]",
                "competencyCategory": "[\"Software Development Methodologies\"]",
                "competencyName": "software development life cycle"
            },
            {
                "competencyType": "ComputerSkill",
                "competencyGroup": "[\"Cloud Computing\"]",
                "competencyCategory": "[\"Deployment Models\"]",
                "competencyName": "cloud"
            },
            {
                "competencyType": "ComputerSkill",
                "competencyGroup": "[\"Software Development\"]",
                "competencyCategory": "[\"Software Development Methodologies\"]",
                "competencyName": "agile development methodologies"
            },
            {
                "competencyType": "KeywordSkill",
                "competencyGroup": "[\"Software Development\"]",
                "competencyCategory": "[\"Software Development Methodologies\"]",
                "competencyName": "\"software development cycle\""
            },
            {
                "competencyType": "KeywordSkill",
                "competencyGroup": "[\"Software Development\"]",
                "competencyCategory": "[\"Software Engineering Related\"]",
                "competencyName": "\"software\""
            },
            {
                "competencyType": "KeywordSkill",
                "competencyGroup": "[\"Engineering\"]",
                "competencyCategory": "[\"Frameworks and Standards\"]",
                "competencyName": "\"Framework\""
            },
            {
                "competencyType": "KeywordSkill",
                "competencyGroup": "",
                "competencyCategory": "",
                "competencyName": "\"functionality\""
            },
            {
                "competencyType": "KeywordSkill",
                "competencyGroup": "[\"System Design and Architecture - IT\"]",
                "competencyCategory": "[\"Software Architecture and Design\"]",
                "competencyName": "\"architecture\""
            },
            {
                "competencyType": "KeywordSkill",
                "competencyGroup": "[\"Business Management\"]",
                "competencyCategory": "[\"Business Management Responsibility\"]",
                "competencyName": "\"communication\""
            },
            {
                "competencyType": "KeywordSkill",
                "competencyGroup": "[\"Finance\"]",
                "competencyCategory": "[\"Finance\"]",
                "competencyName": "\"Finance\""
            },
            {
                "competencyType": "IWRSkill",
                "competencyGroup": "[\"Software Development\"]",
                "competencyCategory": "[\"Software Development Methodologies\"]",
                "competencyName": "development"
            },
            {
                "competencyType": "IWRSkill",
                "competencyGroup": "[\"Microsoft Enterpise Systems\"]",
                "competencyCategory": "[\"Microsoft Applications\"]",
                "competencyName": "Microsoft"
            },
            {
                "competencyType": "IWRSkill",
                "competencyGroup": "[\"Software Development\"]",
                "competencyCategory": "[\"Software Development Methodologies\"]",
                "competencyName": "software development cycle"
            },
            {
                "competencyType": "IWRSkill",
                "competencyGroup": "[\"Business Management\"]",
                "competencyCategory": "[\"Business Management Responsibility\"]",
                "competencyName": "business goals"
            },
            {
                "competencyType": "IWRSkill",
                "competencyGroup": "[\"Training and Development\"]",
                "competencyCategory": "[\"Career Development\"]",
                "competencyName": "Mentoring"
            }
        ],
        "competencyAggregations": [
            {
                "details": "Mentoring junior development staff on architecture design and technical guidance ^^0.7969664232974246",
                "count": "1",
                "class_name": "Operational Management"
            },
            {
                "details": "Collaborating with global development teams to achieve business goals^^0.9789837732829163",
                "count": "1",
                "class_name": "Collaboration"
            },
            {
                "details": "Researching new technology and tools to improve our product and processes ^^0.9629745660496432",
                "count": "1",
                "class_name": "Creativity and Innovation"
            },
            {
                "details": "Solving complex business problems for our world-class client organizations ^^0.9394633095866014|Interact with clients, understand their unique situations and ensure client success ^^0.9286259388897697",
                "count": "2",
                "class_name": "Customer Focus"
            },
            {
                "details": "Participating in the entire software development cycle by analyzing, designing, and developing new features and products^^0.8471756333896564",
                "count": "1",
                "class_name": "Analytical Thinking"
            },
            {
                "details": "Learning and contributing to products on a variety of architectures: cloudbased, RESTFul APIs, oData, client-server, n-tier ^^0.9071751225790211",
                "count": "1",
                "class_name": "Learning Orientation"
            }
        ],
        "education": {},
        "competencyClassifications": [
            {
                "top_class": "Analytical Thinking",
                "text": "Participating in the entire software development cycle by analyzing, designing, and developing new features and products",
                "top_class_confidence": "0.8471756333896564"
            },
            {
                "top_class": "Customer Focus",
                "text": "Solving complex business problems for our world-class client organizations ",
                "top_class_confidence": "0.9394633095866014"
            },
            {
                "text": "Building new software using Microsoft"
            },
            {
                "text": "Enhancing the functionality, performance, and scalability of our product suite "
            },
            {
                "top_class": "Customer Focus",
                "text": "Interact with clients, understand their unique situations and ensure client success ",
                "top_class_confidence": "0.9286259388897697"
            },
            {
                "top_class": "Learning Orientation",
                "text": "Learning and contributing to products on a variety of architectures: cloudbased, RESTFul APIs, oData, client-server, n-tier ",
                "top_class_confidence": "0.9071751225790211"
            },
            {
                "top_class": "Creativity and Innovation",
                "text": "Researching new technology and tools to improve our product and processes ",
                "top_class_confidence": "0.9629745660496432"
            },
            {
                "top_class": "Operational Management",
                "text": "Mentoring junior development staff on architecture design and technical guidance ",
                "top_class_confidence": "0.7969664232974246"
            },
            {
                "top_class": "Collaboration",
                "text": "Collaborating with global development teams to achieve business goals",
                "top_class_confidence": "0.9789837732829163"
            }
        ]
    },
    "person": {
        "competencyClassifications": [
            {
                "text": "Design solutions for data storage, monitoring, and deployment automation while continually enhancing DevOps tools, processes, and procedures"
            },
            {
                "top_class": "Operational Management",
                "text": "Maintain +99% up-time and quick turnaround of deployment through development and optimization of infrastructure, server, deployment strategies",
                "top_class_confidence": "0.7223123209470571"
            },
            {
                "text": "Automate deployment of applications, system configurations, and security settings in AWS cloud based environment while implementing integrations, updates, and fixes"
            },
            {
                "top_class": "Customer Focus",
                "text": "Improve customer experience by building, deploying, and scaling web services on virtual infrastructure, swiftly investigating and resolving technical issues",
                "top_class_confidence": "0.9785680231476441"
            },
            {
                "top_class": "Responsibility and Diligence",
                "text": "Provided supreme server support during deployment of traffic management services and shared infrastructure, improving system reliability by 35%",
                "top_class_confidence": "0.6900252716849796"
            },
            {
                "text": "Augmented cybersecurity through compilation of custom code in JavaScript, HTML, and CSS while ensuring compliance with regulatory standards"
            },
            {
                "top_class": "Collaboration",
                "text": "Collaborated with developers to enhance stability and scalability while prioritizing requests from operations, development and product teams",
                "top_class_confidence": "0.8689140680726448"
            },
            {
                "text": "maintaining optimum information access"
            },
            {
                "text": "infrastructure performance and synchronization across server platforms"
            },
            {
                "text": "ensuring clear communications with senior engineers"
            },
            {
                "top_class": "Operational Management",
                "text": "project",
                "top_class_confidence": "0.9718604912562715"
            }
        ],
        "jobExperience": {
            "jobExperiences": [
                {
                    "startDate": "2015-01-01",
                    "duration": 60,
                    "ongoing": true,
                    "expSequence": "1",
                    "companyName_normalized": "edgewater",
                    "state": "",
                    "endDate": "2019-07-12",
                    "companyName": "Edgewater, Inc.",
                    "jobDescription": "*    Design solutions for data storage, monitoring, and deployment automation while     continually enhancing DevOps tools, processes, and procedures*    Maintain +99% up-time and quick turnaround of deployment through development     and optimization of infrastructure, server, deployment strategies*    Automate deployment of applications, system configurations, and security settings in     AWS cloud based environment while implementing integrations, updates, and fixes*    Improve customer experience by building, deploying, and scaling web services on     virtual infrastructure, swiftly investigating and resolving technical issues",
                    "country": "",
                    "jobTitle": "DevOps Engineer"
                },
                {
                    "startDate": "2012-12-01",
                    "duration": 24,
                    "ongoing": false,
                    "expSequence": "2",
                    "companyName_normalized": "western",
                    "state": "",
                    "endDate": "2014-12-31",
                    "companyName": "Western, Ltd.",
                    "jobDescription": "*    Provided supreme server support during deployment of traffic management services     and shared infrastructure, improving system reliability by 35%*    Augmented cybersecurity through compilation of custom code in JavaScript, HTML,     and CSS while ensuring compliance with regulatory standards*    Collaborated with developers to enhance stability and scalability while prioritizing     requests from operations, development and product teams",
                    "country": "",
                    "jobTitle": "DevOps Engineer"
                }
            ]
        },
        "education": {
            "educations": [
                {
                    "schoolLocation": "",
                    "startDate": "",
                    "schoolName": "Mount Agnes University",
                    "major_normalized": "Computer Hardware Engineering",
                    "majorFieldName": "engineering",
                    "majorFieldType": "science",
                    "endDate": "2012-11-30",
                    "schoolName_normalized": "mount agnes university",
                    "schoolCountry": "",
                    "eduSequence": 1,
                    "ongoing": false,
                    "degree": "Bachelor's",
                    "gpaScale": 4,
                    "educationLevel": "bachelors",
                    "schoolLocation_normalized": "",
                    "major": "Bachelor in Computer Engineering"
                },
                {
                    "schoolLocation": "",
                    "startDate": "",
                    "schoolName": "",
                    "major_normalized": "Engineering",
                    "majorFieldName": "engineering",
                    "majorFieldType": "science",
                    "endDate": "",
                    "schoolName_normalized": "",
                    "schoolCountry": "",
                    "eduSequence": 2,
                    "ongoing": false,
                    "degree": "Bachelor's",
                    "gpaScale": 4,
                    "educationLevel": "bachelors",
                    "schoolLocation_normalized": "",
                    "major": "AWS Certified DevOps Engineer - Professional"
                }
            ]
        },
        "competencyAggregations": [
            {
                "details": "Maintain +99% up-time and quick turnaround of deployment through development and optimization of infrastructure, server, deployment strategies^^0.7223123209470571|project^^0.9718604912562715",
                "count": "2",
                "class_name": "Operational Management"
            },
            {
                "details": "Provided supreme server support during deployment of traffic management services and shared infrastructure, improving system reliability by 35%^^0.6900252716849796",
                "count": "1",
                "class_name": "Responsibility and Diligence"
            },
            {
                "details": "Collaborated with developers to enhance stability and scalability while prioritizing requests from operations, development and product teams^^0.8689140680726448",
                "count": "1",
                "class_name": "Collaboration"
            },
            {
                "details": "Improve customer experience by building, deploying, and scaling web services on virtual infrastructure, swiftly investigating and resolving technical issues^^0.9785680231476441",
                "count": "1",
                "class_name": "Customer Focus"
            }
        ],
        "competency": {
            "competencies": [
                {
                    "competencyType": "ComputerSkill",
                    "skillCategory": "[\"Software Deployment Tools\"]",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "[\"IT Systems Management\"]",
                    "yearsOfExperience": 7,
                    "competencyName": "DevOps"
                },
                {
                    "competencyType": "ComputerSkill",
                    "skillCategory": "[\"Data / Database Related\",\"Data Warehousing Architecture\",\"Storage Management Systems/Solutions\"]",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "[\"Database Technologies\",\"Storage\"]",
                    "yearsOfExperience": 5,
                    "competencyName": "data storage"
                },
                {
                    "competencyType": "ComputerSkill",
                    "skillCategory": "[\"AWS\",\"IAAS\"]",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "[\"Cloud Computing\"]",
                    "yearsOfExperience": 5,
                    "competencyName": "AWS"
                },
                {
                    "competencyType": "ComputerSkill",
                    "skillCategory": "[\"Web Service Specifications\"]",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "[\"Web Programming\"]",
                    "yearsOfExperience": 5,
                    "competencyName": "web services"
                },
                {
                    "competencyType": "ComputerSkill",
                    "skillCategory": "",
                    "lastUsedDate": "2014-12-31",
                    "expertiseLevel": "basic",
                    "skillGroup": "",
                    "yearsOfExperience": 2,
                    "competencyName": "system reliability"
                },
                {
                    "competencyType": "ComputerSkill",
                    "skillCategory": "[\"Frontend Development/Scripting\",\"Java Technologies\",\"Javascript\"]",
                    "lastUsedDate": "2014-12-31",
                    "expertiseLevel": "basic",
                    "skillGroup": "[\"JavaScript Programming\",\"Java Programming\",\"Object Oriented Programming\",\"Web Client Programming\"]",
                    "yearsOfExperience": 2,
                    "competencyName": "JavaScript"
                },
                {
                    "competencyType": "ComputerSkill",
                    "skillCategory": "[\"Frontend Development/Scripting\",\"HTML\"]",
                    "lastUsedDate": "2014-12-31",
                    "expertiseLevel": "basic",
                    "skillGroup": "[\"JavaScript Programming\",\"Web Client Programming\"]",
                    "yearsOfExperience": 2,
                    "competencyName": "HTML"
                },
                {
                    "competencyType": "ComputerSkill",
                    "skillCategory": "[\"CSS\"]",
                    "lastUsedDate": "2014-12-31",
                    "expertiseLevel": "basic",
                    "skillGroup": "[\"Web Programming\"]",
                    "yearsOfExperience": 2,
                    "competencyName": "CSS"
                },
                {
                    "competencyType": "ComputerSkill",
                    "skillCategory": "[\"System Administration\"]",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "[\"IT Systems Management\"]",
                    "yearsOfExperience": 0,
                    "competencyName": "System Administration"
                },
                {
                    "competencyType": "ComputerSkill",
                    "skillCategory": "[\"Operating System\",\"UNIX\"]",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "[\"Operating Systems\",\"Unix Operating System\"]",
                    "yearsOfExperience": 0,
                    "competencyName": "Unix"
                },
                {
                    "competencyType": "ComputerSkill",
                    "skillCategory": "[\"Linux\",\"Operating System\"]",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "[\"Operating Systems\",\"Unix Operating System\"]",
                    "yearsOfExperience": 0,
                    "competencyName": "Linux"
                },
                {
                    "competencyType": "ComputerSkill",
                    "skillCategory": "[\"Android\",\"Operating System\",\"Mobile Devices\"]",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "[\"Mobile Programming\",\"Operating Systems\"]",
                    "yearsOfExperience": 0,
                    "competencyName": "Android"
                },
                {
                    "competencyType": "ComputerSkill",
                    "skillCategory": "[\"Apple\"]",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "[\"Apple Operating System\"]",
                    "yearsOfExperience": 0,
                    "competencyName": "iOS"
                },
                {
                    "competencyType": "ComputerSkill",
                    "skillCategory": "",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "",
                    "yearsOfExperience": 0,
                    "competencyName": "Enterprise"
                },
                {
                    "competencyType": "ComputerSkill",
                    "skillCategory": "",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "",
                    "yearsOfExperience": 0,
                    "competencyName": "AWS ECS"
                },
                {
                    "competencyType": "ComputerSkill",
                    "skillCategory": "[\"Cluster Management Technologies\"]",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "[\"Cloud Computing\"]",
                    "yearsOfExperience": 0,
                    "competencyName": "Docker"
                },
                {
                    "competencyType": "ComputerSkill",
                    "skillCategory": "",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "",
                    "yearsOfExperience": 0,
                    "competencyName": "Object Oriented Development (C++"
                },
                {
                    "competencyType": "ComputerSkill",
                    "skillCategory": "[\"Core Java\",\"Java Technologies\"]",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "[\"Java Programming\",\"Object Oriented Programming\"]",
                    "yearsOfExperience": 0,
                    "competencyName": "Java"
                },
                {
                    "competencyType": "ComputerSkill",
                    "skillCategory": "[\"Software Engineering Related\"]",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "[\"Software Development\"]",
                    "yearsOfExperience": 0,
                    "competencyName": "Coding"
                },
                {
                    "competencyType": "ComputerSkill",
                    "skillCategory": "[\"Python\",\"Scripting Languages\"]",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "[\"Data Science Programming Languages\",\"Procedural Programming\"]",
                    "yearsOfExperience": 0,
                    "competencyName": "Python"
                },
                {
                    "competencyType": "ComputerSkill",
                    "skillCategory": "[\"PHP\"]",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "[\"Server Side Programming\"]",
                    "yearsOfExperience": 0,
                    "competencyName": "PHP"
                },
                {
                    "competencyType": "ComputerSkill",
                    "skillCategory": "",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "",
                    "yearsOfExperience": 0,
                    "competencyName": "SDA platforms"
                },
                {
                    "competencyType": "ComputerSkill",
                    "skillCategory": "",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "",
                    "yearsOfExperience": 0,
                    "competencyName": "CI/CD workflows"
                },
                {
                    "competencyType": "ProfessionalSkill",
                    "skillCategory": "",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "",
                    "yearsOfExperience": 0,
                    "competencyName": "maintaining optimum information access"
                },
                {
                    "competencyType": "ProfessionalSkill",
                    "skillCategory": "",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "",
                    "yearsOfExperience": 0,
                    "competencyName": "infrastructure performance and synchronization across server platforms"
                },
                {
                    "competencyType": "ProfessionalSkill",
                    "skillCategory": "",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "",
                    "yearsOfExperience": 0,
                    "competencyName": "ensuring clear communications with senior engineers"
                },
                {
                    "competencyType": "ProfessionalSkill",
                    "skillCategory": "",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "",
                    "yearsOfExperience": 0,
                    "competencyName": "project"
                },
                {
                    "competencyType": "KeywordSkill",
                    "skillCategory": "[\"Computing Systems / Software / Platforms\"]",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "[\"System Design and Architecture - IT\"]",
                    "yearsOfExperience": 0,
                    "competencyName": "infrastructure"
                },
                {
                    "competencyType": "KeywordSkill",
                    "skillCategory": "",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "",
                    "yearsOfExperience": 0,
                    "competencyName": "security"
                },
                {
                    "competencyType": "KeywordSkill",
                    "skillCategory": "[\"Deployment Models\"]",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "[\"Cloud Computing\"]",
                    "yearsOfExperience": 0,
                    "competencyName": "cloud"
                },
                {
                    "competencyType": "KeywordSkill",
                    "skillCategory": "[\"Customer Support\"]",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "[]",
                    "yearsOfExperience": 0,
                    "competencyName": "support"
                },
                {
                    "competencyType": "KeywordSkill",
                    "skillCategory": "[\"Regulatory & Compliance\"]",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "[]",
                    "yearsOfExperience": 0,
                    "competencyName": "compliance"
                },
                {
                    "competencyType": "KeywordSkill",
                    "skillCategory": "",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "",
                    "yearsOfExperience": 0,
                    "competencyName": "configurations"
                },
                {
                    "competencyType": "KeywordSkill",
                    "skillCategory": "",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "",
                    "yearsOfExperience": 0,
                    "competencyName": "swiftly investigating"
                },
                {
                    "competencyType": "KeywordSkill",
                    "skillCategory": "",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "",
                    "yearsOfExperience": 0,
                    "competencyName": "resolving technical issuesWestern"
                },
                {
                    "competencyType": "KeywordSkill",
                    "skillCategory": "",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "",
                    "yearsOfExperience": 0,
                    "competencyName": "Computer Engineering"
                }
            ],
            "yearsInIndustry": "7"
        }
    },
    "match": {
        "scores": {
            "preferredSkillScoreDetails": [
                {
                    "skillName": "cloud",
                    "skillMatchValue": [
                        "cloud"
                    ],
                    "skillMatchType": "2"
                },
                {
                    "skillName": "Java",
                    "skillMatchValue": [
                        "Java"
                    ],
                    "skillMatchType": "2"
                },
                {
                    "skillName": "agile development methodologies",
                    "skillMatchValue": [
                        "infrastructure performance synchronization across server platforms",
                        "devops",
                        "ci/cd workflows"
                    ],
                    "skillMatchType": "1"
                },
                {
                    "skillName": "C#",
                    "skillMatchValue": [
                        "object oriented development c",
                        "object oriented development c++"
                    ],
                    "skillMatchType": "1"
                },
                {
                    "skillName": "development",
                    "skillMatchValue": [
                        "infrastructure performance synchronization across server platforms",
                        "devops",
                        "ci/cd workflows"
                    ],
                    "skillMatchType": "1"
                },
                {
                    "skillName": "C++",
                    "skillMatchValue": [
                        "object oriented development c",
                        "object oriented development c++"
                    ],
                    "skillMatchType": "1"
                },
                {
                    "skillName": "C",
                    "skillMatchValue": [
                        "object oriented development c",
                        "object oriented development c++"
                    ],
                    "skillMatchType": "1"
                },
                {
                    "skillName": "Software development",
                    "skillMatchValue": [
                        "infrastructure performance synchronization across server platforms",
                        "project",
                        "computer engineering",
                        "devops",
                        "linux",
                        "ci/cd workflows",
                        "sda platforms"
                    ],
                    "skillMatchType": "1"
                },
                {
                    "skillName": "n-tier",
                    "skillMatchValue": [
                        "devops"
                    ],
                    "skillMatchType": "1"
                },
                {
                    "skillName": "oData",
                    "skillMatchValue": [
                        "infrastructure performance synchronization across server platforms",
                        "devops",
                        "ci/cd workflows"
                    ],
                    "skillMatchType": "1"
                },
                {
                    "skillName": "APIs",
                    "skillMatchValue": [
                        "java"
                    ],
                    "skillMatchType": "1"
                },
                {
                    "skillName": "Object Oriented Design",
                    "skillMatchValue": [
                        "infrastructure performance synchronization across server platforms",
                        "object oriented development c",
                        "devops",
                        "ci/cd workflows",
                        "object oriented development c++"
                    ],
                    "skillMatchType": "2"
                },
                {
                    "skillName": "Net Framework",
                    "skillMatchValue": [
                        "enterprise",
                        "infrastructure performance synchronization across server platforms",
                        "devops",
                        "ci/cd workflows"
                    ],
                    "skillMatchType": "1"
                },
                {
                    "skillName": "client-server",
                    "skillMatchValue": [
                        "web services",
                        "infrastructure performance synchronization across server platforms",
                        "data storage",
                        "java",
                        "devops",
                        "maintaining optimum information access",
                        "ci/cd workflows",
                        "javascript",
                        "sda platforms",
                        "unix"
                    ],
                    "skillMatchType": "1"
                },
                {
                    "skillName": "scalability",
                    "skillMatchValue": [
                        "infrastructure performance synchronization across server platforms",
                        "devops",
                        "maintaining optimum information access",
                        "ci/cd workflows"
                    ],
                    "skillMatchType": "1"
                },
                {
                    "skillName": "software development life cycle",
                    "skillMatchValue": [
                        "infrastructure performance synchronization across server platforms",
                        "devops",
                        "ci/cd workflows"
                    ],
                    "skillMatchType": "1"
                },
                {
                    "skillName": "Software Engineering",
                    "skillMatchValue": [
                        "infrastructure performance synchronization across server platforms",
                        "computer engineering",
                        "devops",
                        "ci/cd workflows"
                    ],
                    "skillMatchType": "1"
                },
                {
                    "skillName": "Computer Science",
                    "skillMatchValue": [
                        "computer engineering",
                        "devops",
                        "ci/cd workflows"
                    ],
                    "skillMatchType": "1"
                },
                {
                    "skillName": "Microsoft",
                    "skillMatchValue": [
                        "infrastructure performance synchronization across server platforms",
                        "devops"
                    ],
                    "skillMatchType": "1"
                },
                {
                    "skillName": "Microsoft .Net",
                    "skillMatchValue": [
                        "infrastructure performance synchronization across server platforms",
                        "devops"
                    ],
                    "skillMatchType": "1"
                },
                {
                    "skillName": "software development cycle",
                    "skillMatchValue": [
                        "infrastructure performance synchronization across server platforms",
                        "project",
                        "computer engineering",
                        "devops",
                        "ci/cd workflows"
                    ],
                    "skillMatchType": "1"
                },
                {
                    "skillName": "Microsoft Office Suite",
                    "skillMatchValue": [
                        "infrastructure performance synchronization across server platforms",
                        "devops"
                    ],
                    "skillMatchType": "1"
                },
                {
                    "skillName": "business goals",
                    "skillMatchValue": [
                        "business goals"
                    ],
                    "skillMatchType": "0"
                },
                {
                    "skillName": "Mentoring",
                    "skillMatchValue": [
                        "Mentoring"
                    ],
                    "skillMatchType": "0"
                },
                {
                    "skillName": "database theory",
                    "skillMatchValue": [
                        "database theory"
                    ],
                    "skillMatchType": "0"
                },
                {
                    "skillName": "RESTFul",
                    "skillMatchValue": [
                        "RESTFul"
                    ],
                    "skillMatchType": "0"
                }
            ],
            "requiredSkillScore": "N/A",
            "matchScore": "57.051282051282044",
            "requiredSkillScoreDetails": [],
            "foundationalSkillScore": "50.0",
            "foundationalSkillScoreDetails": [
                {
                    "requisition": [
                        {
                            "text": "Mentoring junior development staff on architecture design and technical guidance "
                        }
                    ],
                    "candidate": [
                        {
                            "text": "Maintain +99% up-time and quick turnaround of deployment through development and optimization of infrastructure, server, deployment strategies"
                        },
                        {
                            "text": "project"
                        }
                    ],
                    "foundationalSkillName": "Operational Management"
                },
                {
                    "requisition": [
                        {
                            "text": "Collaborating with global development teams to achieve business goals"
                        }
                    ],
                    "candidate": [
                        {
                            "text": "Collaborated with developers to enhance stability and scalability while prioritizing requests from operations, development and product teams"
                        }
                    ],
                    "foundationalSkillName": "Collaboration"
                },
                {
                    "requisition": [
                        {
                            "text": "Researching new technology and tools to improve our product and processes "
                        }
                    ],
                    "candidate": [],
                    "foundationalSkillName": "Creativity and Innovation"
                },
                {
                    "requisition": [
                        {
                            "text": "Solving complex business problems for our world-class client organizations "
                        },
                        {
                            "text": "Interact with clients, understand their unique situations and ensure client success "
                        }
                    ],
                    "candidate": [
                        {
                            "text": "Improve customer experience by building, deploying, and scaling web services on virtual infrastructure, swiftly investigating and resolving technical issues"
                        }
                    ],
                    "foundationalSkillName": "Customer Focus"
                },
                {
                    "requisition": [
                        {
                            "text": "Learning and contributing to products on a variety of architectures: cloudbased, RESTFul APIs, oData, client-server, n-tier "
                        }
                    ],
                    "candidate": [],
                    "foundationalSkillName": "Learning Orientation"
                },
                {
                    "requisition": [
                        {
                            "text": "Participating in the entire software development cycle by analyzing, designing, and developing new features and products"
                        }
                    ],
                    "candidate": [],
                    "foundationalSkillName": "Analytical Thinking"
                }
            ],
            "preferredSkillScore": "62.69230769230768",
            "previousJobScore": "N/A",
            "previousJobScoreDetails": [],
            "requiredEducationScore": "N/A",
            "preferredEducationScore": "N/A",
            "requiredEducationScoreDetails": [],
            "preferredEducationScoreDetails": [],
            "foundationalSkillsScoreWeighted": "22.22222222222222",
            "requiredSkillScoreWeighted": "N/A",
            "preferredSkillScoreWeighted": "34.82905982905982",
            "previousJobScoreWeighted": "N/A",
            "requiredEducationScoreWeighted": "N/A",
            "preferredEducationScoreWeighted": "N/A",
            "experienceLevelScoreWeighted": "N/A"
        }
    }
}
```

Congratulations, if you made it this far, you have made your first call to the IBM Watson Talent Match API - happy matching!
