<table class="tbl-heading"><tr><td class="td-logo">![](images/obe_tag.png)

April 15, 2020
</td>
<td class="td-banner">
# Lab 17 - Part-3: Creating an APEX application using the data loaded into Oracle Database using Python SDK and REST Service.
</td></tr><table>

## Introduction

In this lab, you will be installing 2 python applications and load tweets into the Oracle Database.

You can load data into Oracle Database by multiple methods but in this exercise we will use the Python SDK and a REST Service to load tweets.

This lab shows how to integrate the SDK and a REST Service with the Python application and use it to load data from Python Application to Oracle Database.

- The First Python Application will upload data to oracle database using the Python SDK. This application will parse tweets and unpacks the tweets from a file using the Python SDK for Oracle DB before uploading it to the database.

- The second Python Application will upload tweets in the form of JSON objects using the REST Service we created in the earlier exercise. Please refer Lab - [Create_a_RestService_on_DBCS](Create_a_RestService_on_DBCS.md) for more information. 

- To Demonstrate the native JSON support in Oracle Database, we will then create an APEX application which will directly extract data from these JSON objects without having to parse them first like any other data structure within the database.

To **log issues**, click [here](https://github.com/oracle/learning-library/issues/new) to go to the github oracle repository issue submission form.

## Objectives

- Learn how to load JSON data into Oracle Database using the Python SDK and a REST Service.
- Learn how to create a sample apex application on top of that data.
- Demonstrate native JSON support in oracle database.

## Required Artifacts

- Please ensure you completed the previous parts of this lab before you start this lab. Refer [Part-1](SetupORDSandAPEXonDBCS.md) and [Part-2](Create_a_RestService_on_DBCS.md) for more info.

## Steps

### **STEP 1: Download the Python Applications**

- For this lab, you can download the application available in the following repositories. 

- Click <a href="https://github.com/Abdul-Rafae-Mohammed/LoadDataintoOracleDBusingSDK.git" target="_blank">here</a> to download a zipfile of the first Python Application. Copy the zip file to the developer client we provisioned in lab-4 for our database and unzip it to a directory on your machine.

    - You will see:
        - Python Application: **jsonapp.py**
        - Config file: **parameters.txt**

    **Note : This Application will store the data in "TWEETSDATA" table which you can use to verify that the data is loaded**

- Click <a href="https://github.com/Abdul-Rafae-Mohammed/Load-Data-into-Oracle-DB-using-REST.git" target="_blank">here</a> to download a zipfile of the first Python Application. Copy the zip file to the developer client we provisioned in lab-4 for our database and unzip it to a directory on your machine.

    - You will see:
        - Python Application: **pythonapp.py**
        - Tweet Dataset file: **testjson.json**

    **Note : This Application will store the data in "JSONTWEETS" table which you can use to verify that the data is loaded**

### **STEP 2: Setting up the configuration file for the Python App**

- The Python Application you installed is going to load the tweets from tweets stores in JSON format into the Oracle Database.

- Since, JSON is natively supported by the Oracle Database. You dont have to worry about reformatting the JSON object or parsing the JSON object to extract the data and then store it. You can directly store the JSON objects in the Oracle database.


- Now, Modify the application config to work with your environment.

- Navigate to the folder where you have unzipped the application.

- open the config file

    ```
    vi parameters.txt
    ```

- change all the parameters based on your environment.

    ```
    jsonfile=<file containing Tweets>.json
    ip=<DB IP>
    port=<DB Port>
    service=<DB Service Name>
    sys_password=<Database SYS Password>
    ```

![](./images/apex/paramfile.png)

### **STEP 3: Running the Python Applications**

- Make sure you are in the folder with the Python App.

- Run the First Python App.

    ```
    python jsonapp.py parameters.txt
    ```
    
- Run the script.

![](./images/apex/pythonapprun.png)

- verify that the tweets are being stored in the database by connecting to the database, using SQL Developer, as the same user for which you created the REST Service.

- Run the second Python App. 

    - This app will directly store JSON objects in Oracle Database because JSON data is natively supported in Oracle Database.

    ```
    python3 pythonapp.py <REST Endpoint URL> <JSON File Name with extension>
    ```
![](./images/apex/pythonapp2run.png)

- verify that the tweets are being stored in the database by connecting to the database, using SQL Developer, as the same user for which you created the REST Service.

![](./images/apex/pythonapp1verify.png)
![](./images/apex/pythonapp2verify.png)

- Alternatively, you can also verify using the REST GET request as shown below.

![](./images/apex/REST_GET.png)

- Now lets log in to APEX installed on Oracle Database and create an application.

### **STEP 4: Create an APEX Application**

- Login to APEX using the following URL : 
   http://<ip_address>:\<ORDS Port\>/ords
   
![](./images/apex/Picture400-4.png)

- Click on Create an Application tab and then click on New Application option.

![](./images/apex/CreateApexApp-1.png)
![](./images/apex/CreateApexApp-01.png)

- Enter the name for the application and click on "Add Page" to add a page to the application.

![](./images/apex/CreateApexApp-2.png)

- Select Interactive Grid from the options.

![](./images/apex/CreateApexApp-3.png)

- Enter a name for the Page, Select the "Table or View" option and make sure the "Interactive Report" option is selected. Select the correct table (which is TWEETSDATA for us) by click on the button beside the field. Finally click on Add Page button.
   
![](./images/apex/CreateApexApp-4.png)

- Observe that a new page has been added to the application

![](./images/apex/CreateApexApp-5.png)

- Similarly, click on Add Page option again and select Interactive Grid option.

- **This page will display the data extracted from the json objects, ingested into the Oracle database using the REST Service in the previous step, using a simple sql statement. Since JSON is natively supported in oracle database, it is really simple to deal with data in JSON format.**

![](./images/apex/CreateApexApp-3.png)

- Enter a name for the Page, Select the "SQL Query" option and make sure the "Interactive Report" option is selected. Enter the query mentioned below in the query box. Finally click on Add Page button.

    ```
    SELECT a.tweetjson.created_at, a.tweetjson.id, a.tweetjson.text, a.tweetjson.source, a.tweetjson.place, a.tweetjson.retweet_count, a.tweetjson.retweeted FROM   appschema.jsontweets a;
    ```

    **Note : As you can see in this query, since JSON is supported natively in Oracle Database, we can very easily extract data from JSON objects using the dot notation.**

    - Here in this example, we have extracted the attribute tweet id from the JSON object as follows :
    \<tablename\>\.\<column_consisting_json_object\>\.\<attribute_to_be_extracted\>

![](./images/apex/CreateApexApp-9.png)
![](./images/apex/CreateApexApp-10.png)
![](./images/apex/CreateApexApp-11.png)

- Select APPSCHEMA user under the settings section and click Create Application

![](./images/apex/CreateApexApp-6.png)

- Observe that the application has been created under the apps builder tab.

![](./images/apex/CreateApexApp-7.png)

- Click on the application and click on the Run Application button on top right corner of the screen.

- On the Panel on left side, click on Report Page under Home to see the data we loaded into the database. This page loads the data up-loaded by the first python appliction

![](./images/apex/CreateApexApp-13.png)

- Similarly, click on the Extracted Data option on the same panel to see the data we loaded using the REST Service.

![](./images/apex/CreateApexApp-12.png)

- You have now successfully loaded data using an SDK, send GET and POST data requests using REST Service and also created a Web Application using APEX and ORDS on top of the loaded data.

<table>
<tr><td class="td-logo">[![](images/obe_tag.png)](#)</td>
<td class="td-banner">
## Great Work - All Done!
</td>
</tr>
<table>