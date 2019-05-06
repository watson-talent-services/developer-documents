---
copyright: 'Copyright IBM Corp. 2019'
link: basic-talent-match
is: 'beta'
---

# Basic Talent Match

In this tutorial, you'll see how to make a basic call to the IBM Watson Talent Match API using a tool for making REST calls. 
In this case, we used Postman, but you can use whatever tool your comfortable with. 

We've made this into a checklist so you can follow along. You can also grab this file, and open it with Postman to set all the right fields (you'll still need to get your ID/Secret and upload the files) - [Postman file for this tutorial](https://github.com/watson-talent-services/developer-documents/blob/master/tutorials/WTP-Talent%20Match%20v1.postman_collection.json).

You can begin your free trial by visting the [IBM Marketplace for the Talent Match API](https://www.ibm.com/us-en/marketplace/watson-talent-match/details). 

### 1. Fire up Postman, Enter the Talent Match API and set to POST

- [ ] Fire up your REST test tool

![Firing up Postman](https://github.com/watson-talent-services/developer-documents/blob/master/images/PostmanStep1.png)

- [ ] Enter Talent Match API and change request verb to POST

We also added the version paramater to the URL itself, and Postman picks that up and adds as a parameter

![Entering the Talent Match API endpoint](https://github.com/watson-talent-services/developer-documents/blob/master/images/PostmanStep2.png)

![Entering the Talent Match API endpoint](https://github.com/watson-talent-services/developer-documents/blob/master/images/PostmanStep2-A.png)

### 2. Update the Authorization type

- [ ] Update the authorization type to **No Auth**

![Update authorization type](https://github.com/watson-talent-services/developer-documents/blob/master/images/PostmanStep3.png)

![Update authorization type](https://github.com/watson-talent-services/developer-documents/blob/master/images/PostmanStep3-A.png)

### 3. Enter the Headers and Items

- [ ] Switch to the Headers tab

![Go to the Headers tab](https://github.com/watson-talent-services/developer-documents/blob/master/images/PostmanStep4.png)

You will need to get the credentials you received from the IBM API Explorer, you'll get one for your **ID* called **x-ibm-client-id** and one for your **Secret** called **x-ibm-client-secret**. [Get your credentials here](https://developer.ibm.com/api/view/watsontalent-prod:watson-talent-match:title-Watson_Talent_Match). 

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

Since we're using a file we need to tell Postmant to upload it.

- [ ] Select the **Text** menu on the right of the **rawJob** object name.
- [ ] Select **File** from the drop down menu

![Get ready to upload a file](https://github.com/watson-talent-services/developer-documents/blob/master/images/PostmanStep7.png)

![Get ready to upload a file](https://github.com/watson-talent-services/developer-documents/blob/master/images/PostmanStep7-A.png)

### 6. Browse and add the file

- [ ] Select the right file from your computer, we used []()

![Select the file](https://github.com/watson-talent-services/developer-documents/blob/master/images/PostmanStep8.png)

![Select the file](https://github.com/watson-talent-services/developer-documents/blob/master/images/PostmanStep8-A.png)

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
            "title": "DevOps Engineer",
            "requiredExperience": "",
            "jobClassification": "Information and Communication Technology",
            "description": "DevOps Engineer with +5 years of experience in managing cloud infrastructure and system administration, integrating AWS cloud based infrastructure components, and developing automation solutions. IT Professional bringing outstanding record in maintaining optimum information access, infrastructure performance and synchronization across server platforms while ensuring clear communications with senior engineers, project managers, and executives., * Design solutions for data storage, monitoring, and deployment automation while continually enhancing DevOps tools, processes, and procedures * Maintain +99% up-time and quick turnaround of deployment through development and optimization of infrastructure, server, deployment strategies * Automate deployment of applications, system configurations, and security settings in AWS cloud based environment while implementing integrations, updates, and fixes * Improve customer experience by building, deploying, and scaling web services on virtual infrastructure, swiftly investigating and resolving technical issues Western, Ltd. DevOps Engineer December 2012 - December 2014 * Provided supreme server support during deployment of traffic management services and shared infrastructure, improving system reliability by 35% * Augmented cybersecurity through compilation of custom code in JavaScript, HTML, and CSS while ensuring compliance with regulatory standards * Collaborated with developers to enhance stability and scalability while prioritizing requests from operations, development and product teams Professional Licenses and Certifications AWS Certified DevOps Engineer - Professional",
            "role": ""
        },
        "competency": [
            {
                "competencyType": "ComputerSkill",
                "competencyGroup": "[\"JavaScript Programming\",\"Java Programming\",\"Object Oriented Programming\",\"Web Client Programming\"]",
                "competencyCategory": "[\"Frontend Development/Scripting\",\"Java Technologies\",\"Javascript\"]",
                "competencyName": "JavaScript"
            },
            {
                "competencyType": "ComputerSkill",
                "competencyGroup": "[\"JavaScript Programming\",\"Web Client Programming\"]",
                "competencyCategory": "[\"Frontend Development/Scripting\",\"HTML\"]",
                "competencyName": "HTML"
            },
            {
                "competencyType": "ComputerSkill",
                "competencyGroup": "[\"Operating Systems\",\"Unix Operating System\"]",
                "competencyCategory": "[\"Operating System\",\"UNIX\"]",
                "competencyName": "Unix"
            },
            {
                "competencyType": "ComputerSkill",
                "competencyGroup": "[\"Operating Systems\",\"Unix Operating System\"]",
                "competencyCategory": "[\"Linux\",\"Operating System\"]",
                "competencyName": "Linux"
            },
            {
                "competencyType": "ComputerSkill",
                "competencyGroup": "[\"Mobile Programming\",\"Operating Systems\"]",
                "competencyCategory": "[\"Android\",\"Operating System\",\"Mobile Devices\"]",
                "competencyName": "Android"
            },
            {
                "competencyType": "ComputerSkill",
                "competencyGroup": "[\"Software Development\"]",
                "competencyCategory": "[\"Software Engineering Related\"]",
                "competencyName": "App Development"
            },
            {
                "competencyType": "ComputerSkill",
                "competencyGroup": "[\"Cloud Computing\"]",
                "competencyCategory": "[\"Cluster Management Technologies\"]",
                "competencyName": "Docker"
            },
            {
                "competencyType": "ComputerSkill",
                "competencyGroup": "",
                "competencyCategory": "",
                "competencyName": "Object Oriented Development"
            },
            {
                "competencyType": "ComputerSkill",
                "competencyGroup": "[\"Engineering\",\"Object Oriented Programming\"]",
                "competencyCategory": "[\"Programming\",\"C++\"]",
                "competencyName": "C++"
            },
            {
                "competencyType": "ComputerSkill",
                "competencyGroup": "[\"Java Programming\",\"Object Oriented Programming\"]",
                "competencyCategory": "[\"Core Java\",\"Java Technologies\"]",
                "competencyName": "Java"
            },
            {
                "competencyType": "ComputerSkill",
                "competencyGroup": "[\"Data Science Programming Languages\",\"Procedural Programming\"]",
                "competencyCategory": "[\"Python\",\"Scripting Languages\"]",
                "competencyName": "Python"
            },
            {
                "competencyType": "ComputerSkill",
                "competencyGroup": "[\"Web Programming\"]",
                "competencyCategory": "[\"CSS\"]",
                "competencyName": "CSS"
            },
            {
                "competencyType": "ComputerSkill",
                "competencyGroup": "[\"Server Side Programming\"]",
                "competencyCategory": "[\"PHP\"]",
                "competencyName": "PHP"
            },
            {
                "competencyType": "ComputerSkill",
                "competencyGroup": "[\"IT Systems Management\"]",
                "competencyCategory": "[\"System Administration\"]",
                "competencyName": "system administration"
            },
            {
                "competencyType": "ComputerSkill",
                "competencyGroup": "[\"Cloud Computing\"]",
                "competencyCategory": "[\"AWS\",\"IAAS\"]",
                "competencyName": "AWS"
            },
            {
                "competencyType": "ComputerSkill",
                "competencyGroup": "[\"System Design and Architecture - IT\"]",
                "competencyCategory": "[\"Computing Systems / Software / Platforms\"]",
                "competencyName": "infrastructure"
            },
            {
                "competencyType": "ComputerSkill",
                "competencyGroup": "[\"Test - IT\"]",
                "competencyCategory": "[\"Testing Related\"]",
                "competencyName": "automation"
            },
            {
                "competencyType": "ComputerSkill",
                "competencyGroup": "[\"Database Technologies\",\"Storage\"]",
                "competencyCategory": "[\"Data / Database Related\",\"Data Warehousing Architecture\",\"Storage Management Systems/Solutions\"]",
                "competencyName": "data storage"
            },
            {
                "competencyType": "ComputerSkill",
                "competencyGroup": "[\"Cloud Computing\"]",
                "competencyCategory": "[\"Deployment Models\"]",
                "competencyName": "deployment"
            },
            {
                "competencyType": "ComputerSkill",
                "competencyGroup": "[\"Web Programming\"]",
                "competencyCategory": "[\"Web Service Specifications\"]",
                "competencyName": "web services"
            },
            {
                "competencyType": "ComputerSkill",
                "competencyGroup": "[\"Virtualization - IT\"]",
                "competencyCategory": "[\"Hardware Virtualization\",\"Virtual Machine\"]",
                "competencyName": "virtual"
            },
            {
                "competencyType": "ComputerSkill",
                "competencyGroup": "",
                "competencyCategory": "",
                "competencyName": "system reliability"
            },
            {
                "competencyType": "ComputerSkill",
                "competencyGroup": "[\"Operating Systems\"]",
                "competencyCategory": "[]",
                "competencyName": "Operating Systems"
            },
            {
                "competencyType": "ComputerSkill",
                "competencyGroup": "[\"Engineering\"]",
                "competencyCategory": "[\"Programming\"]",
                "competencyName": "C"
            },
            {
                "competencyType": "ComputerSkill",
                "competencyGroup": "[\"Software Development\"]",
                "competencyCategory": "[\"Software Engineering Related\"]",
                "competencyName": "Coding"
            },
            {
                "competencyType": "ComputerSkill",
                "competencyGroup": "",
                "competencyCategory": "",
                "competencyName": "SDA"
            },
            {
                "competencyType": "ComputerSkill",
                "competencyGroup": "[\"Machine Learning\"]",
                "competencyCategory": "[\"AI / Machine Learning Related\"]",
                "competencyName": "Artificial Intelligence"
            },
            {
                "competencyType": "KeywordSkill",
                "competencyGroup": "",
                "competencyCategory": "",
                "competencyName": "\"managing cloud infrastructure\""
            },
            {
                "competencyType": "KeywordSkill",
                "competencyGroup": "[\"Business Process Engineering\",\"Education, Training, Research\",\"Engineering\"]",
                "competencyCategory": "[\"Engineering\"]",
                "competencyName": "\"Engineering\""
            },
            {
                "competencyType": "KeywordSkill",
                "competencyGroup": "[\"Environment Health and Safety\",\"IT Systems Management\",\"IT Systems Monitoring\"]",
                "competencyCategory": "[\"Environment, Health and Safety\",\"System Administration\",\"System Monitoring\"]",
                "competencyName": "\"monitoring\""
            },
            {
                "competencyType": "KeywordSkill",
                "competencyGroup": "",
                "competencyCategory": "",
                "competencyName": "\"configurations\""
            },
            {
                "competencyType": "KeywordSkill",
                "competencyGroup": "",
                "competencyCategory": "",
                "competencyName": "\"security\""
            },
            {
                "competencyType": "KeywordSkill",
                "competencyGroup": "",
                "competencyCategory": "",
                "competencyName": "\"swiftly investigating\""
            },
            {
                "competencyType": "KeywordSkill",
                "competencyGroup": "",
                "competencyCategory": "",
                "competencyName": "\"resolving technical issues\""
            },
            {
                "competencyType": "KeywordSkill",
                "competencyGroup": "[]",
                "competencyCategory": "[\"Customer Support\"]",
                "competencyName": "\"support\""
            },
            {
                "competencyType": "KeywordSkill",
                "competencyGroup": "[\"Media and Entertainment\"]",
                "competencyCategory": "[\"Radio\"]",
                "competencyName": "\"traffic management\""
            },
            {
                "competencyType": "KeywordSkill",
                "competencyGroup": "",
                "competencyCategory": "",
                "competencyName": "\"stability\""
            },
            {
                "competencyType": "KeywordSkill",
                "competencyGroup": "",
                "competencyCategory": "",
                "competencyName": "\"scalability while prioritizing\""
            },
            {
                "competencyType": "KeywordSkill",
                "competencyGroup": "",
                "competencyCategory": "",
                "competencyName": "\"iOS App Development\""
            },
            {
                "competencyType": "KeywordSkill",
                "competencyGroup": "",
                "competencyCategory": "",
                "competencyName": "\"ECS\""
            },
            {
                "competencyType": "KeywordSkill",
                "competencyGroup": "",
                "competencyCategory": "",
                "competencyName": "\"CI\""
            },
            {
                "competencyType": "KeywordSkill",
                "competencyGroup": "",
                "competencyCategory": "",
                "competencyName": "\"CD workflows\""
            }
        ],
        "competencyAggregations": [
            {
                "details": "Collaborated with developers to enhance stability and scalability while prioritizing requests from operations, development and product teams Professional Licenses and Certifications AWS Certified DevOps Engineer - Professiona^^0.8520208321300901",
                "count": "1",
                "class_name": "Collaboration"
            },
            {
                "details": "Improve customer experience by building, deploying, and scaling web services on virtual infrastructure, swiftly investigating and resolving technical issues Western, Ltd^^0.9780703282776365",
                "count": "1",
                "class_name": "Customer Focus"
            },
            {
                "details": "DevOps Engineer with +5 years of experience in managing cloud infrastructure and system administration, integrating AWS cloud based infrastructure components, and developing automation solutions^^0.6341025161955255",
                "count": "1",
                "class_name": "Planning and Organizing"
            }
        ],
        "education": {},
        "competencyClassifications": [
            {
                "top_class": "Planning and Organizing",
                "text": "DevOps Engineer with +5 years of experience in managing cloud infrastructure and system administration, integrating AWS cloud based infrastructure components, and developing automation solutions",
                "allClasses": "Planning and Organizing--0.6341025161955255|Operational Management--0.241307166294153|Information Management--0.035417745148755814|Collaboration--0.007916692013525923|Problem Solving and Decision Making--0.007577459014204556|Customer Focus--0.00745499551124856|Creativity and Innovation--0.007315801475011666|Responsibility and Diligence--0.00727273054349615|Drive--0.0065983019024534965|Conflict and Risk Management--0.005680945829382689|",
                "top_class_confidence": "0.6341025161955255"
            },
            {
                "text": "IT Professional bringing outstanding record in maintaining optimum information access, infrastructure performance and synchronization across server platforms while ensuring clear communications with senior engineers, project managers, and executives.,",
                "allClasses": "Information Management--0.33167840117007363|Operational Management--0.2967291751721925|Responsibility and Diligence--0.08199727134525475|Collaboration--0.06963023116338546|Planning and Organizing--0.04139067958328871|Influence--0.024598519840865418|Communications--0.023027765413389453|Learning Orientation--0.017425473768814627|Ethics and Trust--0.015511947463599891|Customer Focus--0.01505577218045392|"
            },
            {
                "text": "Design solutions for data storage, monitoring, and deployment automation while continually enhancing DevOps tools, processes, and procedures",
                "allClasses": "Information Management--0.2828217996764215|Operational Management--0.27492333891617127|Creativity and Innovation--0.15919601356105403|Analytical Thinking--0.06687274445953027|Math and Statistics--0.02809092923570333|Planning and Organizing--0.020796796057087733|Problem Solving and Decision Making--0.020200152418663405|Conflict and Risk Management--0.016775880563388704|Ethics and Trust--0.0159901198930832|Responsibility and Diligence--0.014803761519614845|"
            },
            {
                "text": "Maintain +99% up-time and quick turnaround of deployment through development and optimization of infrastructure, server, deployment strategies",
                "allClasses": "Planning and Organizing--0.3587088662512521|Operational Management--0.14083582001310124|Analytical Thinking--0.10694611587145236|Responsibility and Diligence--0.05322591847441114|Learning Orientation--0.0483557027780647|Creativity and Innovation--0.043931115858238924|Customer Focus--0.036920051338947976|Problem Solving and Decision Making--0.036819392737592986|Leadership--0.02081716260298167|Information Management--0.020038996521369763|"
            },
            {
                "text": "Automate deployment of applications, system configurations, and security settings in AWS cloud based environment while implementing integrations, updates, and fixes",
                "allClasses": "Planning and Organizing--0.5825527959484574|Information Management--0.17305884462457538|Ethics and Trust--0.04950511512409832|Learning Orientation--0.02940223994503645|Operational Management--0.02502818531567995|Analytical Thinking--0.021016550493733716|Problem Solving and Decision Making--0.015044654975380812|Conflict and Risk Management--0.014689066607979414|Drive--0.01346804466000476|Influence--0.009954341487596259|"
            },
            {
                "top_class": "Customer Focus",
                "text": "Improve customer experience by building, deploying, and scaling web services on virtual infrastructure, swiftly investigating and resolving technical issues Western, Ltd",
                "allClasses": "Customer Focus--0.9780703282776365|Communications--0.0022573379303039488|Ethics and Trust--0.002126478183742453|Operational Management--0.002037259572893641|Analytical Thinking--0.0019755607587097043|Collaboration--0.0019157305054702603|Math and Statistics--0.0018371346962033053|Planning and Organizing--0.0017189418206628487|Influence--9.846682502074138E-4|Learning Orientation--8.6833851079311E-4|",
                "top_class_confidence": "0.9780703282776365"
            },
            {
                "text": "DevOps Engineer December 2012 - December 2014",
                "allClasses": "Responsibility and Diligence--0.2279303942764652|Operational Management--0.17112820513567853|Information Management--0.12848160371906425|Planning and Organizing--0.08855680807441858|Drive--0.06103837459467942|Collaboration--0.05207028247199885|Creativity and Innovation--0.03174155522926111|Building Relationships--0.030441783238245007|Learning Orientation--0.023175417355147526|Problem Solving and Decision Making--0.022999273199955872|"
            },
            {
                "text": "Provided supreme server support during deployment of traffic management services and shared infrastructure, improving system reliability by 35%",
                "allClasses": "Responsibility and Diligence--0.5630976591038948|Operational Management--0.12177153281703516|Analytical Thinking--0.06335293135456722|Math and Statistics--0.047017094619230294|Customer Focus--0.027815460237215425|Information Management--0.020798122285429398|Ethics and Trust--0.017825089891436018|Drive--0.01752006979539068|Planning and Organizing--0.01673036781238342|Problem Solving and Decision Making--0.01672330819795117|"
            },
            {
                "text": "Augmented cybersecurity through compilation of custom code in JavaScript, HTML, and CSS while ensuring compliance with regulatory standards",
                "allClasses": "Ethics and Trust--0.49041874959477794|Information Management--0.26695991270786756|Drive--0.07306316324643135|Responsibility and Diligence--0.022026736595384632|Customer Focus--0.017119555577567693|Planning and Organizing--0.015346257705384156|Operational Management--0.013755387959595307|Learning Orientation--0.01161533490253566|Math and Statistics--0.01149615588637557|Problem Solving and Decision Making--0.010432816512752149|"
            },
            {
                "top_class": "Collaboration",
                "text": "Collaborated with developers to enhance stability and scalability while prioritizing requests from operations, development and product teams Professional Licenses and Certifications AWS Certified DevOps Engineer - Professiona",
                "allClasses": "Collaboration--0.8520208321300901|Planning and Organizing--0.0579869741706837|Building Relationships--0.013525872955137496|Responsibility and Diligence--0.011065102644959463|Creativity and Innovation--0.01083173347569009|Information Management--0.0054612048565910705|Operational Management--0.005132170052882467|Learning Orientation--0.005050791686223909|Conflict and Risk Management--0.004528198084090244|Customer Focus--0.004421348700142514|",
                "top_class_confidence": "0.8520208321300901"
            }
        ]
    },
    "person": {
        "competencyClassifications": [
            {
                "top_class": "Leadership",
                "text": "strong teaming skills and show leadership potential",
                "allClasses": "Leadership--0.9271827999479699|Building Relationships--0.015933604158495696|Collaboration--0.012858066482073209|Planning and Organizing--0.007896670207269408|Influence--0.004439698921825298|Conflict and Risk Management--0.00334552481522634|Customer Focus--0.0030999313636394677|Analytical Thinking--0.0028309846299760318|Ethics and Trust--0.002727569497834164|Adapting to Change--0.0024808364612725806|",
                "top_class_confidence": "0.9271827999479699"
            },
            {
                "top_class": "Adapting to Change",
                "text": "able to work in a high energy environment",
                "allClasses": "Adapting to Change--0.7250922475988367|Drive--0.13312129271916753|Building Relationships--0.03357905386399854|Ethics and Trust--0.013369990122083588|Planning and Organizing--0.011558754425503042|Creativity and Innovation--0.009992887253402473|Conflict and Risk Management--0.008008912601348736|Communications--0.006773872901945253|Leadership--0.0066679681710479725|Customer Focus--0.006465494877457643|",
                "top_class_confidence": "0.7250922475988367"
            },
            {
                "top_class": "Creativity and Innovation",
                "text": "exhibit creative thinking",
                "allClasses": "Creativity and Innovation--0.9749598667318653|Collaboration--0.004187397872091241|Learning Orientation--0.002955129263538445|Adapting to Change--0.0020200568243996823|Math and Statistics--0.0018755979776567443|Analytical Thinking--0.0017719940748966046|Problem Solving and Decision Making--0.0014804351092026207|Drive--0.0012469977971153938|Communications--0.0010959473833875443|Leadership--0.0010186853209275177|",
                "top_class_confidence": "0.9749598667318653"
            },
            {
                "top_class": "Collaboration",
                "text": "collaboration",
                "allClasses": "Collaboration--0.9655916393197375|Planning and Organizing--0.013863428946619972|Conflict and Risk Management--0.00267586226137704|Building Relationships--0.0023283358656200795|Influence--0.0016854523945686933|Analytical Thinking--0.0013802698016373634|Creativity and Innovation--0.0012743198291273953|Leadership--0.001254813259435904|Math and Statistics--0.0012356052853186405|Information Management--0.0011685889753881588|",
                "top_class_confidence": "0.9655916393197375"
            },
            {
                "top_class": "Communications",
                "text": "communicate",
                "allClasses": "Communications--0.9717662961783213|Collaboration--0.007512994754338188|Influence--0.002122524982491216|Responsibility and Diligence--0.0018719021582710553|Math and Statistics--0.0015780120181716909|Operational Management--0.0013531354786989018|Building Relationships--0.0013333412099955047|Customer Focus--0.0013137587852079555|Information Management--0.0012874604208331956|Planning and Organizing--0.0012793838332366655|",
                "top_class_confidence": "0.9717662961783213"
            },
            {
                "top_class": "Collaboration",
                "text": "work closely",
                "allClasses": "Collaboration--0.9176886206701923|Planning and Organizing--0.023430276246232826|Responsibility and Diligence--0.015458272316712852|Building Relationships--0.004389185721900204|Drive--0.003960480487226407|Ethics and Trust--0.0034745587029122874|Creativity and Innovation--0.0033749118481946707|Operational Management--0.0032682949236636023|Information Management--0.0029842788423726655|Influence--0.002946188248606347|",
                "top_class_confidence": "0.9176886206701923"
            },
            {
                "text": "in",
                "allClasses": "Responsibility and Diligence--0.5474618629224813|Drive--0.08756802607744067|Problem Solving and Decision Making--0.07263824469303241|Adapting to Change--0.05470030059828937|Operational Management--0.02623727556356908|Math and Statistics--0.022659122308987405|Planning and Organizing--0.021009274257038083|Ethics and Trust--0.01947955436174915|Conflict and Risk Management--0.018530850355192502|Learning Orientation--0.01702866870867422|"
            },
            {
                "text": "Interact",
                "allClasses": "Building Relationships--0.387636659500488|Collaboration--0.3832557835291734|Leadership--0.04385901263007793|Responsibility and Diligence--0.029348960917649842|Operational Management--0.01524470267701748|Planning and Organizing--0.013952226436389667|Communications--0.013709621444142485|Analytical Thinking--0.013648498785923354|Conflict and Risk Management--0.013242197964843026|Influence--0.010270719336106538|"
            },
            {
                "text": "great software",
                "allClasses": "Building Relationships--0.20422452489807463|Analytical Thinking--0.20062532111757467|Planning and Organizing--0.1135313997350758|Information Management--0.06424602165871109|Creativity and Innovation--0.05224669410921429|Leadership--0.04072835995184169|Problem Solving and Decision Making--0.035388276201743785|Ethics and Trust--0.032400245541414865|Adapting to Change--0.031934139856445304|Conflict and Risk Management--0.031179334527100613|"
            },
            {
                "text": "understanding of",
                "allClasses": "Communications--0.25423015350050354|Analytical Thinking--0.21396682201604847|Responsibility and Diligence--0.11324244151148992|Building Relationships--0.054774212214167096|Creativity and Innovation--0.04091466879088529|Customer Focus--0.030562011840945594|Operational Management--0.029829490398857048|Math and Statistics--0.028288169199125725|Leadership--0.026826489689848222|Collaboration--0.02547769548324029|"
            },
            {
                "top_class": "Problem Solving and Decision Making",
                "text": "Exceptional problem solving skills",
                "allClasses": "Problem Solving and Decision Making--0.9707696927677726|Planning and Organizing--0.0075923036121742764|Drive--0.004318940292512991|Analytical Thinking--0.002332265978997156|Math and Statistics--0.0014754366526261197|Influence--0.001396966044020776|Collaboration--0.001361964387690195|Creativity and Innovation--0.0011868412844650712|Customer Focus--0.0011090966133978698|Conflict and Risk Management--0.0010364446484561307|",
                "top_class_confidence": "0.9707696927677726"
            },
            {
                "top_class": "Communications",
                "text": "Excellent verbal communication skills",
                "allClasses": "Communications--0.9746729415503619|Collaboration--0.004650631038712136|Planning and Organizing--0.002661502709246021|Customer Focus--0.0024007109329399986|Math and Statistics--0.0021389014771981568|Influence--0.0015962248334137296|Building Relationships--0.0013440771378416365|Operational Management--0.0012412068602542692|Ethics and Trust--0.001223314640270316|Creativity and Innovation--0.0010606607314706494|",
                "top_class_confidence": "0.9746729415503619"
            },
            {
                "top_class": "Operational Management",
                "text": "transform slow,expensive and disconnected performance planning and management processes into dynamic, efficient and",
                "allClasses": "Operational Management--0.8214274974035426|Adapting to Change--0.0696327180920707|Planning and Organizing--0.048013666744474694|Problem Solving and Decision Making--0.005373178531253834|Responsibility and Diligence--0.005249841894895618|Learning Orientation--0.004605940642257929|Conflict and Risk Management--0.004574707538648613|Analytical Thinking--0.004493505406832807|Drive--0.0044137446319028216|Information Management--0.00418726130372821|",
                "top_class_confidence": "0.8214274974035426"
            },
            {
                "top_class": "Analytical Thinking",
                "text": "technical and critical thinking skills, a passion for technology and software",
                "allClasses": "Analytical Thinking--0.9617648925532448|Problem Solving and Decision Making--0.005618104545001406|Planning and Organizing--0.004037440876975405|Learning Orientation--0.0037233445820126975|Creativity and Innovation--0.0034336836869766907|Leadership--0.002606915215050924|Drive--0.0025873751206799234|Influence--0.0021127563107226793|Communications--0.002084741127803175|Information Management--0.0017077874289135226|",
                "top_class_confidence": "0.9617648925532448"
            },
            {
                "top_class": "Collaboration",
                "text": "organizations",
                "allClasses": "Collaboration--0.8150775355588888|Operational Management--0.04130183332763179|Information Management--0.017451641709404723|Planning and Organizing--0.013821836488219531|Responsibility and Diligence--0.013382164073349499|Customer Focus--0.012217831778691516|Leadership--0.010814970532555803|Building Relationships--0.010012228592488836|Influence--0.009779165382892812|Communications--0.008510477054168587|",
                "top_class_confidence": "0.8150775355588888"
            },
            {
                "top_class": "Creativity and Innovation",
                "text": "* Building new software",
                "allClasses": "Creativity and Innovation--0.6168981533971428|Collaboration--0.0980823930527488|Learning Orientation--0.06830726239489861|Analytical Thinking--0.0507218139854424|Adapting to Change--0.031469879317496174|Math and Statistics--0.01490013453269723|Information Management--0.013694688551049407|Communications--0.013521487822899525|Operational Management--0.011243616831180851|Drive--0.010483197170891707|",
                "top_class_confidence": "0.6168981533971428"
            },
            {
                "top_class": "Creativity and Innovation",
                "text": "architecture design",
                "allClasses": "Creativity and Innovation--0.9440625518339569|Information Management--0.01731103910860212|Operational Management--0.004548740161860294|Learning Orientation--0.003929587488548344|Communications--0.0030707266486493293|Conflict and Risk Management--0.0024317843917842532|Analytical Thinking--0.0023856329982573196|Planning and Organizing--0.0023555927778230305|Adapting to Change--0.0022611192128736816|Customer Focus--0.002240376618410539|",
                "top_class_confidence": "0.9440625518339569"
            },
            {
                "text": "technical guidance",
                "allClasses": "Information Management--0.4036935306923833|Planning and Organizing--0.1542603603169775|Communications--0.076404130695024|Influence--0.06521616633854567|Operational Management--0.05312923183306645|Ethics and Trust--0.04086970859708917|Responsibility and Diligence--0.04042376782835244|Collaboration--0.021312947511724252|Learning Orientation--0.01698222632923662|Problem Solving and Decision Making--0.016520562155597458|"
            },
            {
                "top_class": "Collaboration",
                "text": "Collaborating with global development teams",
                "allClasses": "Collaboration--0.9765231080247054|Building Relationships--0.004396561691676632|Leadership--0.0024317130713868117|Learning Orientation--0.0019425096546637616|Operational Management--0.001584751562957738|Influence--0.0014349453873745508|Ethics and Trust--0.001286788092833886|Creativity and Innovation--0.001276092875299288|Customer Focus--0.001223778178466569|Planning and Organizing--9.988025627512608E-4|",
                "top_class_confidence": "0.9765231080247054"
            },
            {
                "text": "achieve business goals",
                "allClasses": "Drive--0.5490278462275727|Collaboration--0.3326019192563466|Analytical Thinking--0.021398656273661366|Operational Management--0.0208882238610545|Leadership--0.010971278537325465|Planning and Organizing--0.006301152061301838|Responsibility and Diligence--0.0057157305246646846|Building Relationships--0.0053177858486495545|Math and Statistics--0.005300867081408743|Information Management--0.005284002141962633|"
            },
            {
                "text": "database theory",
                "allClasses": "Information Management--0.5785581387505122|Math and Statistics--0.2852553016319541|Leadership--0.02101048217314884|Analytical Thinking--0.016632955065329604|Communications--0.011194541157911565|Learning Orientation--0.008585649130045196|Ethics and Trust--0.008200705249326992|Problem Solving and Decision Making--0.007765013114147398|Creativity and Innovation--0.007632173027192265|Conflict and Risk Management--0.006505465190396609|"
            },
            {
                "text": "software development life cycle",
                "allClasses": "Creativity and Innovation--0.3310002235277529|Learning Orientation--0.1633979108544083|Adapting to Change--0.08066120616787623|Planning and Organizing--0.08004020242735593|Drive--0.07927237349515222|Analytical Thinking--0.04110142953948585|Information Management--0.03477609925971178|Operational Management--0.023866118565988293|Problem Solving and Decision Making--0.023701053545084495|Conflict and Risk Management--0.017614256095464208|"
            },
            {
                "text": "Finance business needs",
                "allClasses": "Analytical Thinking--0.4182489037811998|Planning and Organizing--0.21528267809755658|Customer Focus--0.07427317493156771|Operational Management--0.05470109903637755|Ethics and Trust--0.04028655350393314|Building Relationships--0.026881995509132367|Drive--0.02241675685271727|Learning Orientation--0.019700421681082173|Math and Statistics--0.015079136006621951|Communications--0.014201024508049154|"
            },
            {
                "text": "Experience working on large scale development projects",
                "allClasses": "Operational Management--0.3568752948379446|Drive--0.2102822807696292|Adapting to Change--0.11444212688728485|Math and Statistics--0.06456405519991487|Learning Orientation--0.041673541357798466|Responsibility and Diligence--0.03814300028146065|Creativity and Innovation--0.02933152165752787|Collaboration--0.017589674432886518|Planning and Organizing--0.016672495908773642|Building Relationships--0.015558734152446223|"
            }
        ],
        "jobExperience": {
            "jobExperiences": []
        },
        "education": {
            "educations": []
        },
        "competencyAggregations": [
            {
                "details": "Exceptional problem solving skills^^0.9707696927677726",
                "count": "1",
                "class_name": "Problem Solving and Decision Making"
            },
            {
                "details": "transform slow,expensive and disconnected performance planning and management processes into dynamic, efficient and^^0.8214274974035426",
                "count": "1",
                "class_name": "Operational Management"
            },
            {
                "details": "strong teaming skills and show leadership potential^^0.9271827999479699",
                "count": "1",
                "class_name": "Leadership"
            },
            {
                "details": "able to work in a high energy environment^^0.7250922475988367",
                "count": "1",
                "class_name": "Adapting to Change"
            },
            {
                "details": "collaboration^^0.9655916393197375|work closely^^0.9176886206701923|organizations^^0.8150775355588888|Collaborating with global development teams^^0.9765231080247054",
                "count": "4",
                "class_name": "Collaboration"
            },
            {
                "details": "exhibit creative thinking^^0.9749598667318653|* Building new software^^0.6168981533971428|architecture design^^0.9440625518339569",
                "count": "3",
                "class_name": "Creativity and Innovation"
            },
            {
                "details": "communicate^^0.9717662961783213|Excellent verbal communication skills^^0.9746729415503619",
                "count": "2",
                "class_name": "Communications"
            },
            {
                "details": "technical and critical thinking skills, a passion for technology and software^^0.9617648925532448",
                "count": "1",
                "class_name": "Analytical Thinking"
            }
        ],
        "competency": {
            "competencies": [
                {
                    "competencyType": "ComputerSkill",
                    "skillCategory": "[\".Net Programming Tools\",\"Microsoft Applications\"]",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "[\"Microsoft .net Programming\",\"Microsoft Enterpise Systems\"]",
                    "yearsOfExperience": 0,
                    "competencyName": "Microsoft .Net Framework"
                },
                {
                    "competencyType": "ComputerSkill",
                    "skillCategory": "[\"C#\"]",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "[\"Microsoft .net Programming\"]",
                    "yearsOfExperience": 0,
                    "competencyName": "C#"
                },
                {
                    "competencyType": "ComputerSkill",
                    "skillCategory": "[\"Software Engineering Related\"]",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "[\"Software Development\"]",
                    "yearsOfExperience": 0,
                    "competencyName": "Software development"
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
                    "skillCategory": "[\"Programming\",\"C++\"]",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "[\"Engineering\",\"Object Oriented Programming\"]",
                    "yearsOfExperience": 0,
                    "competencyName": "C++"
                },
                {
                    "competencyType": "ComputerSkill",
                    "skillCategory": "[\".Net Programming Tools\"]",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "[\"Microsoft .net Programming\"]",
                    "yearsOfExperience": 0,
                    "competencyName": "Net Framework"
                },
                {
                    "competencyType": "ComputerSkill",
                    "skillCategory": "[\"Microsoft Applications\"]",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "[\"Microsoft Enterpise Systems\"]",
                    "yearsOfExperience": 0,
                    "competencyName": "Microsoft Office Suite"
                },
                {
                    "competencyType": "LanguageSkill",
                    "skillCategory": "",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "",
                    "yearsOfExperience": 0,
                    "competencyName": "English"
                },
                {
                    "competencyType": "SoftSkill",
                    "skillCategory": "",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "",
                    "yearsOfExperience": 0,
                    "competencyName": "strong teaming skills and show leadership potential"
                },
                {
                    "competencyType": "SoftSkill",
                    "skillCategory": "",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "",
                    "yearsOfExperience": 0,
                    "competencyName": "able to work in a high energy environment"
                },
                {
                    "competencyType": "SoftSkill",
                    "skillCategory": "",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "",
                    "yearsOfExperience": 0,
                    "competencyName": "exhibit creative thinking"
                },
                {
                    "competencyType": "SoftSkill",
                    "skillCategory": "",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "",
                    "yearsOfExperience": 0,
                    "competencyName": "collaboration"
                },
                {
                    "competencyType": "SoftSkill",
                    "skillCategory": "",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "",
                    "yearsOfExperience": 0,
                    "competencyName": "communicate"
                },
                {
                    "competencyType": "SoftSkill",
                    "skillCategory": "",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "",
                    "yearsOfExperience": 0,
                    "competencyName": "work closely"
                },
                {
                    "competencyType": "SoftSkill",
                    "skillCategory": "",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "",
                    "yearsOfExperience": 0,
                    "competencyName": "in"
                },
                {
                    "competencyType": "SoftSkill",
                    "skillCategory": "",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "",
                    "yearsOfExperience": 0,
                    "competencyName": "Interact"
                },
                {
                    "competencyType": "SoftSkill",
                    "skillCategory": "",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "",
                    "yearsOfExperience": 0,
                    "competencyName": "great software"
                },
                {
                    "competencyType": "SoftSkill",
                    "skillCategory": "",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "",
                    "yearsOfExperience": 0,
                    "competencyName": "understanding of"
                },
                {
                    "competencyType": "SoftSkill",
                    "skillCategory": "",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "",
                    "yearsOfExperience": 0,
                    "competencyName": "Exceptional problem solving skills"
                },
                {
                    "competencyType": "SoftSkill",
                    "skillCategory": "",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "",
                    "yearsOfExperience": 0,
                    "competencyName": "Excellent verbal communication skills"
                },
                {
                    "competencyType": "ProfessionalSkill",
                    "skillCategory": "",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "",
                    "yearsOfExperience": 0,
                    "competencyName": "transform slow,expensive and disconnected performance planning and management processes into dynamic, efficient and"
                },
                {
                    "competencyType": "ProfessionalSkill",
                    "skillCategory": "",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "",
                    "yearsOfExperience": 0,
                    "competencyName": "technical and critical thinking skills, a passion for technology and software"
                },
                {
                    "competencyType": "ProfessionalSkill",
                    "skillCategory": "[\"Organization Development\"]",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "[\"Training and Development\"]",
                    "yearsOfExperience": 0,
                    "competencyName": "organizations"
                },
                {
                    "competencyType": "ProfessionalSkill",
                    "skillCategory": "",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "",
                    "yearsOfExperience": 0,
                    "competencyName": "* Building new software"
                },
                {
                    "competencyType": "ProfessionalSkill",
                    "skillCategory": "",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "",
                    "yearsOfExperience": 0,
                    "competencyName": "architecture design"
                },
                {
                    "competencyType": "ProfessionalSkill",
                    "skillCategory": "",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "",
                    "yearsOfExperience": 0,
                    "competencyName": "technical guidance"
                },
                {
                    "competencyType": "ProfessionalSkill",
                    "skillCategory": "",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "",
                    "yearsOfExperience": 0,
                    "competencyName": "Collaborating with global development teams"
                },
                {
                    "competencyType": "ProfessionalSkill",
                    "skillCategory": "",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "",
                    "yearsOfExperience": 0,
                    "competencyName": "achieve business goals"
                },
                {
                    "competencyType": "ProfessionalSkill",
                    "skillCategory": "[\"Computational Learning Theory\",\"Database\",\"Database Concepts\"]",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "[\"Data Science\",\"Database\",\"Database Technologies\"]",
                    "yearsOfExperience": 0,
                    "competencyName": "database theory"
                },
                {
                    "competencyType": "ProfessionalSkill",
                    "skillCategory": "[\"Software Development Methodologies\"]",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "[\"Software Development\"]",
                    "yearsOfExperience": 0,
                    "competencyName": "software development life cycle"
                },
                {
                    "competencyType": "ProfessionalSkill",
                    "skillCategory": "[\"Finance\"]",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "[\"Finance\"]",
                    "yearsOfExperience": 0,
                    "competencyName": "Finance business needs"
                },
                {
                    "competencyType": "ProfessionalSkill",
                    "skillCategory": "",
                    "lastUsedDate": "",
                    "expertiseLevel": "basic",
                    "skillGroup": "",
                    "yearsOfExperience": 0,
                    "competencyName": "Experience working on large scale development projects"
                }
            ],
            "yearsInIndustry": "0"
        }
    },
    "match": {
        "scores": {
            "preferredSkillScoreDetails": [
                {
                    "skillName": "JavaScript",
                    "skillMatchValue": [
                        "java technologies"
                    ],
                    "skillMatchType": "2"
                },
                {
                    "skillName": "JavaScript",
                    "skillMatchValue": [
                        "java programming",
                        "object oriented programming"
                    ],
                    "skillMatchType": "3"
                },
                {
                    "skillName": "HTML",
                    "skillMatchValue": [
                        "HTML"
                    ],
                    "skillMatchType": "0"
                },
                {
                    "skillName": "Unix",
                    "skillMatchValue": [
                        "Unix"
                    ],
                    "skillMatchType": "0"
                },
                {
                    "skillName": "Linux",
                    "skillMatchValue": [
                        "Linux"
                    ],
                    "skillMatchType": "0"
                },
                {
                    "skillName": "Android",
                    "skillMatchValue": [
                        "Android"
                    ],
                    "skillMatchType": "0"
                },
                {
                    "skillName": "App Development",
                    "skillMatchValue": [
                        "software engineering related"
                    ],
                    "skillMatchType": "2"
                },
                {
                    "skillName": "App Development",
                    "skillMatchValue": [
                        "software development"
                    ],
                    "skillMatchType": "3"
                },
                {
                    "skillName": "Docker",
                    "skillMatchValue": [
                        "Docker"
                    ],
                    "skillMatchType": "0"
                },
                {
                    "skillName": "Object Oriented Development",
                    "skillMatchValue": [
                        "Object Oriented Development"
                    ],
                    "skillMatchType": "0"
                },
                {
                    "skillName": "C++",
                    "skillMatchValue": [
                        "C++"
                    ],
                    "skillMatchType": "1"
                },
                {
                    "skillName": "C++",
                    "skillMatchValue": [
                        "programming",
                        "c++"
                    ],
                    "skillMatchType": "2"
                },
                {
                    "skillName": "C++",
                    "skillMatchValue": [
                        "engineering",
                        "object oriented programming"
                    ],
                    "skillMatchType": "3"
                },
                {
                    "skillName": "Java",
                    "skillMatchValue": [
                        "Java"
                    ],
                    "skillMatchType": "1"
                },
                {
                    "skillName": "Java",
                    "skillMatchValue": [
                        "core java",
                        "java technologies"
                    ],
                    "skillMatchType": "2"
                },
                {
                    "skillName": "Java",
                    "skillMatchValue": [
                        "java programming",
                        "object oriented programming"
                    ],
                    "skillMatchType": "3"
                },
                {
                    "skillName": "Python",
                    "skillMatchValue": [
                        "Python"
                    ],
                    "skillMatchType": "0"
                },
                {
                    "skillName": "CSS",
                    "skillMatchValue": [
                        "CSS"
                    ],
                    "skillMatchType": "0"
                },
                {
                    "skillName": "PHP",
                    "skillMatchValue": [
                        "PHP"
                    ],
                    "skillMatchType": "0"
                },
                {
                    "skillName": "system administration",
                    "skillMatchValue": [
                        "system administration"
                    ],
                    "skillMatchType": "0"
                },
                {
                    "skillName": "AWS",
                    "skillMatchValue": [
                        "AWS"
                    ],
                    "skillMatchType": "0"
                },
                {
                    "skillName": "infrastructure",
                    "skillMatchValue": [
                        "infrastructure"
                    ],
                    "skillMatchType": "0"
                },
                {
                    "skillName": "automation",
                    "skillMatchValue": [
                        "automation"
                    ],
                    "skillMatchType": "0"
                },
                {
                    "skillName": "data storage",
                    "skillMatchValue": [
                        "database technologies"
                    ],
                    "skillMatchType": "3"
                },
                {
                    "skillName": "deployment",
                    "skillMatchValue": [
                        "deployment"
                    ],
                    "skillMatchType": "0"
                },
                {
                    "skillName": "web services",
                    "skillMatchValue": [
                        "web services"
                    ],
                    "skillMatchType": "0"
                },
                {
                    "skillName": "virtual",
                    "skillMatchValue": [
                        "virtual"
                    ],
                    "skillMatchType": "0"
                },
                {
                    "skillName": "system reliability",
                    "skillMatchValue": [
                        "system reliability"
                    ],
                    "skillMatchType": "0"
                },
                {
                    "skillName": "Operating Systems",
                    "skillMatchValue": [
                        "Operating Systems"
                    ],
                    "skillMatchType": "0"
                },
                {
                    "skillName": "C",
                    "skillMatchValue": [
                        "programming"
                    ],
                    "skillMatchType": "2"
                },
                {
                    "skillName": "C",
                    "skillMatchValue": [
                        "engineering"
                    ],
                    "skillMatchType": "3"
                },
                {
                    "skillName": "Coding",
                    "skillMatchValue": [
                        "software engineering related"
                    ],
                    "skillMatchType": "2"
                },
                {
                    "skillName": "Coding",
                    "skillMatchValue": [
                        "software development"
                    ],
                    "skillMatchType": "3"
                },
                {
                    "skillName": "SDA",
                    "skillMatchValue": [
                        "SDA"
                    ],
                    "skillMatchType": "0"
                },
                {
                    "skillName": "Artificial Intelligence",
                    "skillMatchValue": [
                        "Artificial Intelligence"
                    ],
                    "skillMatchType": "0"
                },
                {
                    "skillName": "\"Engineering\"",
                    "skillMatchValue": [
                        "\"Engineering\""
                    ],
                    "skillMatchType": "1"
                },
                {
                    "skillName": "\"Engineering\"",
                    "skillMatchValue": [
                        "engineering"
                    ],
                    "skillMatchType": "3"
                },
                {
                    "skillName": "\"monitoring\"",
                    "skillMatchValue": [
                        "\"monitoring\""
                    ],
                    "skillMatchType": "0"
                },
                {
                    "skillName": "\"support\"",
                    "skillMatchValue": [
                        "\"support\""
                    ],
                    "skillMatchType": "0"
                },
                {
                    "skillName": "\"traffic management\"",
                    "skillMatchValue": [
                        "\"traffic management\""
                    ],
                    "skillMatchType": "0"
                }
            ],
            "requiredSkillScore": "N/A",
            "matchScore": "26.0",
            "requiredSkillScoreDetails": [],
            "foundationalSkillScore": "17.0",
            "foundationalSkillScoreDetails": [
                {
                    "requisition": [
                        {
                            "text": "Collaborated with developers to enhance stability and scalability while prioritizing requests from operations, development and product teams Professional Licenses and Certifications AWS Certified DevOps Engineer - Professiona"
                        }
                    ],
                    "candidate": [
                        {
                            "text": "collaboration"
                        },
                        {
                            "text": "work closely"
                        },
                        {
                            "text": "organizations"
                        },
                        {
                            "text": "Collaborating with global development teams"
                        }
                    ],
                    "foundationalSkillName": "Collaboration"
                },
                {
                    "requisition": [
                        {
                            "text": "Improve customer experience by building, deploying, and scaling web services on virtual infrastructure, swiftly investigating and resolving technical issues Western, Ltd"
                        }
                    ],
                    "candidate": [],
                    "foundationalSkillName": "Customer Focus"
                },
                {
                    "requisition": [
                        {
                            "text": "DevOps Engineer with +5 years of experience in managing cloud infrastructure and system administration, integrating AWS cloud based infrastructure components, and developing automation solutions"
                        }
                    ],
                    "candidate": [],
                    "foundationalSkillName": "Planning and Organizing"
                }
            ],
            "preferredSkillScore": "9.0"
        }
    }
}
```

Congratulations, if you made it this far, you have made your first call to the IBM Watson Talent Match API - happy matching!
