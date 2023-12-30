
# Postman Tutorial

This is a basic postman tutorial which could help understand the use of postman in API testing and featurs offered by postman.

## 🔖 Topics
- [Postman Setup](#postman_setup)
- [Start with API Request](#start_with_api_request)
- [Query Parameters](#query_parameters)
- [Path Parameters](#path_parameters)
- [Variables](#variables)
- [Setup Environment Variables](#setup_environment_variables)
- [Pre-request Script](#pre_request_script)
- [Tests](#tests)
- [Validating Schema](#validating_schema)
- [Mock Server using Json Server](#mock_server_using_json_server)
- [API Requests with Mock Server](#api_requests_with_mock_server)
- [End to End Test Execution](#end_to_end_test_execution)
- [Reading Data From CSV File](#reading_data_from_csv_file)
- [Execute Collection via CLI](#execute_collection_via_cli)
- [htmlextra for Better Report](#htmlextra_for_better_report)
- [Documentation](#documentation)
- [About Me](#about_me)
- [Support](#support)
## 🚀 Postman Setup
* Download Postman from [here](https://www.postman.com/downloads/)
* Sign in, install and open the Postman
* Create a Workspace:
    - Select the option as per your requirements. I have selected Blank Workspace.
    - Workspace is the set of collections

    ![Workspace Creation](https://github.com/swatinerkar/postman/blob/main/images/1.%20postman_workspace.png)

* Create Collection:
    - Once workspace is created, create a collections by clicking on Collections on left menu and click on + icon. 
    - Select the Collection as per requirement, I have selected Blank Collection. Give the collection name.
    - Each collections is a set of requests.

    ![Collection Creation](https://github.com/swatinerkar/postman/blob/main/images/2.%20postman_createCollection.png)

* Create a Request:
    - Click on 3 dots at Collection and click 'Add Request'

    ![Request Creation](https://github.com/swatinerkar/postman/blob/main/images/3.%20postman_createRequest.png)




## 💪 Start with API Request
For demo purpose we are using reqres  - https://reqres.in/
It has set of APIs which we can use for practice purpose.
Note that apis are not actually setting any value in backend, these are dummy apis.

- Open https://reqres.in/
- There are many endpoints available. On clicking 

    ![reqres endpoints](https://github.com/swatinerkar/postman/blob/main/images/4.%20reqres_requestEndpoints.png)

- click on request as shown in above image. It will open the requestive request

    ![Clicking request](https://github.com/swatinerkar/postman/blob/main/images/5.%20reqres_afterClickingOnRequestEndPoint.png)

- Copy the request and paste it in Postman request

    ![reqeust paste in postman](https://github.com/swatinerkar/postman/blob/main/images/6.%20copyReqresLink_PasteInPortman.png)









## Query Parameters

- Observe the followings
    * We can see Query Params section, where currently one parameter is present. As query param says fetch the data from page 2, we can see in the respose the "page": 2
    * Verify the status code is 200

    ![queryParam 2nd page](https://github.com/swatinerkar/postman/blob/main/images/7.%20reqres_usersSecondPage_HitRequest.png)

- Remove the queryParam and click Send, observe this time the "page":1
- By default it will send data present on 1st page

    ![queryParam remove](https://github.com/swatinerkar/postman/blob/main/images/8.%20reqres_afterRemoving_QueryParam.png)

## Path Parameters

- Add path param to the request, it is an 'id' of an user, it will only fetch the data of that user whose id matches with parameter value.

    ![pathParam](https://github.com/swatinerkar/postman/blob/main/images/9.%20reqres_addPathparam_id_hardCore.png)

- If you observe, we only have query params section and not path params. If you want to have similar section for path as well use below syntax. 
    
    ``` https://reqres.in/api/users/:id ```

- Now you will get the path variable section. Observe the key is id which we have passed in URL, you need to set a value for this key. Run time it will pick the provided value.

    ![pathParam section](https://github.com/swatinerkar/postman/blob/main/images/10.%20reqres_addPathparam_id_FromPathParamSection.png)
## 🧪 Variables

There are 3 types of variables we have in Postman

    1. Collection Variables
    2. Global Variables
    3. Enviroment Variables


#### Collection Variables

- The scope of these variables are only within Collection. A Collection can have n numbers of requests and all these requests can access the Collection level variables.
- We set these variables at Collection level.
    - Click on Collection
    - There is Variables tab
    - Here you can setup variables with their values in Key-Value pairs

    ![Collection Variables](https://github.com/swatinerkar/postman/blob/main/images/11.%20CollectionLevel_Variables.png)


#### Global Variables

- As name says, these variables are accessible globally.
- To set these variables
    - Go to Enviroments -> Globals
    - Add variables in Key-Value pairs

    ![Global Variables](https://github.com/swatinerkar/postman/blob/main/images/12.%20globalVariables.png)

#### Enviroment Variables

- These variables are Enviroment specific. Different Enviroment variables could have same variable name.
    e.g. API can have dev, qa, prod uri. User can have 3 different envirments with same variable uri.
- To set these variables, need to create envirment
    - Go to Enviroments -> + icon on top -> create envirment 

    ![create env](https://github.com/swatinerkar/postman/blob/main/images/13.%20createEnvVaribles.png)

- Once envirment is created, you can give appropriate name of envirment and add variables in Key-Value pairs

    ![add env Variables](https://github.com/swatinerkar/postman/blob/main/images/14.%20setEnvVariables.png)


**NOTE:** While adding any variable we can see 2 values, Intial and Current. The difference in these are, whenever we share the request with anyone postman will only share the initial value of the variable.

**USE CASE:** If you have any confidencial data and you don't want to share it while sharing request with fellow collegues, you can set initial value as --- and set your actual value as current value. Postman always considers current value in Run time.### Setup Environment Variables

- As shows in below image, user can select Environment from right top dropdown.
- The variable can be used As

    ``` {{url}}/api/users/:id ```

- when you mouse over on {{url}}, you will get the information about that variable.
- For example,
    - here we can see E letter in green square, which represents that the variable is Environment variable.
    - What is the current value and initial value of variable 

    ![env Variables use](https://github.com/swatinerkar/postman/blob/main/images/15.%20select_env_useTheEnvVariable.png)

**USE CASE:** When you are having 3 uris - dev, qa, and prod. You can add 3 create environments respectively and same variable uri and set respective environment value. Now for the same end point whenever you want to change the environment specific uri you just need to select that environment fom dropdown. 
## 🛟 Pre-request Script

- There are some scenarios where we need to do some pre steps before actual hitting a request. Such steps we can add under Pre-request Script.
- Postman will always run scrips present under Pre-request first and then send request to server.
- Portman provides many options under Snippet, you can choose as per your requirement and update it.
- Here is an example of Pre-request. I am generating any random number between 1-10, setting that value in collection variable int

    ![pre-request script](https://github.com/swatinerkar/postman/blob/main/images/16.%20pre-request_script_selectFromSnippets.png)


-  Now passing int variable as as a path parameter in get call as user id to fetch data of that user.
- Observe that

    ![pre-request variable used as pathParam](https://github.com/swatinerkar/postman/blob/main/images/17.%20setCollectionVariable_afterPre-request_Script.png)

- Click on Send, and open the console  
- Observe that, everytime new id is being created and passed in path param

    ![Result](https://github.com/swatinerkar/postman/blob/main/images/18.%20random_id_generations_hitGetRequest.png)

## Tests
* After receieving the response from server, Postman can perform Tests to validate multiple scenarios as expected.
    
    e.g. Status code, Response Time, Response Header, Content of Response, and Schema as well, etc.

* When you go to the Tests tab, under snippet you will see many options to add validations.
* Here are some examples:

```
 // varify status code

pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

// verify response time

pm.test("Response time is less than 600ms", function () {
    pm.expect(pm.response.responseTime).to.be.below(600);
});

// verify response header present

pm.test("Content-Type is present", function () {
    pm.response.to.have.header("Content-Type");
});

// verify value of the field

pm.test("Support url is present", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.support.url).to.eql("https://reqres.in/#support-heading");
});


```

    ![Tests](https://github.com/swatinerkar/postman/blob/main/images/19.%20sampleTests.png)
## Validating Schema

- Schema validation is validating the expected fields with correct data type values are part of response or not. It also checks for mandatory fields are present in response.
- This can be done my postman using Tiny libray.

    - Go to Tests
    - Snippet - scroll down to the end.
    - The last, you will see Use Tiny Validator for JSON data

- To get schema from JSON reponse, you can use - https://www.liquid-technologies.com/online-json-to-schema-converter
- Paste the JSON respnse here and you will get the schema.
- **NOTE** - This is only for practicing schema validation purpose, in real work you will get expected schema as part of requirement.

- Here is an example, this schema is for https://reqres.in/api/users/3

```
    // schema validation
var schema = {
  "$schema": "http://json-schema.org/draft-04/schema#",
  "type": "object",
  "properties": {
    "data": {
      "type": "object",
      "properties": {
        "id": {
          "type": "integer"
        },
        "email": {
          "type": "string"
        },
        "first_name": {
          "type": "string"
        },
        "last_name": {
          "type": "string"
        },
        "avatar": {
          "type": "string"
        }
      },
      "required": [
        "id",
        "email",
        "first_name",
        "last_name",
        "avatar"
      ]
    },
    "support": {
      "type": "object",
      "properties": {
        "url": {
          "type": "string"
        },
        "text": {
          "type": "string"
        }
      },
      "required": [
        "url",
        "text"
      ]
    }
  },
  "required": [
    "data",
    "support"
  ]
};

pm.test('Schema is valid', function () {
    pm.expect(tv4.validate(pm.response.json(), schema)).to.be.true;
});


```

    ![Schema Validation](https://github.com/swatinerkar/postman/blob/main/images/20.%20schema_Validation.png)

### After Tests Execution

    ![Tests Running](https://github.com/swatinerkar/postman/blob/main/images/21.%20Test_Success.png)


## Mock Server using Json Server

- Sometimes you need to test an API but the server isn't ready yet and you can't wait till it will be available. 
- In such situations we can use Mock Server.
- It is a replica of actual server, not a real server. It is only for testing purpose.
- We can create such a server with help of [json-server](https://medium.com/@devmrin/create-a-rest-api-json-server-in-less-than-1-minute-acf286600f03)

#### Pre-requisites
- You need to have nodeJs installed on your machine

- Now follow the steps mentioned on webite.

- **Some tips**
    - Make sure while creating json file you include 'id' field. (It was giving error when I tried.)
    - Here is a sample file

    ![JSON file](https://github.com/swatinerkar/postman/blob/main/images/22.%20JsonFile.png)

    - Go to the location where your json file is present and option command prompt there, you won't need to pass entire file path while starting ther server.
    - Giving port is optional, if you don't specify the port the server will start on port 3000

    ![JSON server start](https://github.com/swatinerkar/postman/blob/main/images/23.%20JsonServer_Start.png)

- Once the server started, you can use the URL shown - http://localhost:3000

    ![JSON server URL](https://github.com/swatinerkar/postman/blob/main/images/24.%20Mock%20Server%20URL.png)


## API Requests with Mock Server
- Create a new Collection.
- Add new GET request
- You can see Resources on your local host. For me it is http://localhost:3000/
- Obervse that for each Json object in Json file, it has created end point
- For instance here, /posts
- Add all requests with supportive http methods for one of your endpoint. Here I have created GET, POST, PUT, DETELE for /ports


## End to End Test Execution

### GET Method

``` http://localhost:3000/posts ```
- Above returns list of all posts
- I have added Test to validate status code

``` 
    pm.test("Status code is 200", function () {
        pm.response.to.have.status(200);
    });
```

    ![GET request](https://github.com/swatinerkar/postman/blob/main/images/25.%20Hit%20Get%20Request%20-%20Mock%20server.png)

### POST Method

``` http://localhost:3000/posts ```

- For POST call, we need to pass body and in body I have used the functions, provided by postman to generate random values. You need to type {{$<press ctrl+space>}}. It will give all possible values.
- I have added Test to assert the status code

``` 
    pm.test("Successful POST request", function () {
    pm.expect(pm.response.code).to.be.oneOf([201, 202]);
    }); 
```

    ![POST request random](https://github.com/swatinerkar/postman/blob/main/images/26.%20Post%20call%20Body%20with%20random%20functions.png)


    ![POST request](https://github.com/swatinerkar/postman/blob/main/images/27.%20Post%20call.png)


- I want to save the newly created records Id, which I can use later in other API calls. To do so I have saved the Id from response to collection variable.

```
    // Need to save the created id in collection variable
    pm.collectionVariables.set("id", pm.response.json().id);

```

- Send the reqeust. Go to collection variable and you can see the variable with value is been present.

    ![after POST request](https://github.com/swatinerkar/postman/blob/main/images/28.%20Collection%20variable%20after%20post%20call.png)

### GET Method
``` 
    http://localhost:3000/posts/<pathParam - id> 
```

- It is the similar call, but we are passing the id which we have stored as collection varible to get that specific id's record.

    ![GET call](https://github.com/swatinerkar/postman/blob/main/images/29.%20Get%20only%20specific%20post.png)


### PUT Method

```
http://localhost:3000/posts/<pathParam - id> 
```

- Pass id as pathparam, to tell that this perticular post we want to update.
- What need to be update that we need to send in body.
- In my case, I passed same Id (collection variable). Keeping id same and updating other 2 values.

```
    {
    "id": {{id}},
    "title": "{{$randomDomainWord}}",
    "author": "{{$randomFullName}}"
    }
```
    ![PUT call](https://github.com/swatinerkar/postman/blob/main/images/30.%20Put%20call.png)

### DELETE Method

``` http://localhost:3000/posts/<pathParam - id> ```

- Deleting the same post which is created by POST call.

    ![DELETE call](https://github.com/swatinerkar/postman/blob/main/images/31.%20Delete.png)


### GET Method

``` http://localhost:3000/posts/<pathParam - id> ```

- Try to fetch deleted record. To verify the data is deleted.

    ![GET call Agaim](https://github.com/swatinerkar/postman/blob/main/images/32.%20Get%20deleted%20record.png)

### Collection Execution

- You can run this End to End Test scenarios via Collection

    ![GET call Agaim](https://github.com/swatinerkar/postman/blob/main/images/33.%20Collection%20Run%20option.png)

- You can arrange the execution sequence. 
- Add deplay between 2 calls.
- You can schedule this execution.
- For now I am selecting run manually. 
- Click Run '<collection_name>'

    ![Collection param](https://github.com/swatinerkar/postman/blob/main/images/34.%20Run%20Collection%20parameters.png)


    ![collection execution](https://github.com/swatinerkar/postman/blob/main/images/35.%20Collection%20Execution.png)
## Reading Data From CSV File
- Prepare csv file with test data which you want to pass in execution.
- Make sure - copy the column name and use wherever you want to parameterize that value of that column.

    ![Data file](https://github.com/swatinerkar/postman/blob/main/images/36.%20Data%20File.png)


    ![column name](https://github.com/swatinerkar/postman/blob/main/images/37.%20Put%20call%20-%20updated%20same%20as%20column%20name.png)

- Go to Colletion -> Run Collection
- Click Select
- Select the csv file

    ![select file](https://github.com/swatinerkar/postman/blob/main/images/38.%20Select%20File.png)

- You can preview the data of csv file which you have selected.

    ![file data](https://github.com/swatinerkar/postman/blob/main/images/39.%20Preview%20file%20data.png)

- Run 
- Observe the save test scenario execution 3 times as we have passed 3 sets of data

    ![collection test execution sets](https://github.com/swatinerkar/postman/blob/main/images/40.%20Execution%20-%203%20test%20sets.png)
## Execute Collection via CLI
- To Run collectio via CLI we need to install newman
    ``` npm install -g newman ```
- to run collection 
 
        1. Go to Collection -> 3 dots -> share -> via API (it might ask to generate token, generate it)
        2. Copy the link
        3. open cmd where the testData.csv file is present
        4. Run command	
``` 
        newman run <copies link from collection> -d <testData.csv> 
```
            In my case it was 
        
            newman run https://api.postman.com/collections/15056817-12b7d377-3912-43ad-887b-cefbfaa668db?access_key=<token> -d testData_Postman.csv
	
        5. Observe all APIs are executed and the number of iternations are the number of date provided in .csv file.

    ![CLI execution](https://github.com/swatinerkar/postman/blob/main/images/41.%20Execution%20via%20CLI.png)

For reference: https://www.npmjs.com/package/newman
## htmlextra for Better Report
- To get better html report, we need to install htmlextra
- Install it by 
    ``` npm install -g newman-reporter-htmlextra ```
- Now open cmd run 

    ```
    newman run <copies link from collection> -d <testData.csv> -r htmlextra
    ```
     For me it is

    ```newman run https://api.postman.com/collections/15056817-12b7d377-3912-43ad-887b-cefbfaa668db?access_key=<token> -d testData_Postman.csv -r htmlextra ```

- It might not show anything on command prompt.
- Go to the same path where you have executed this command.
- newman folder has been generated there.
- When you open it, there will a html file.
- Open the html file. Its a report.

    ![htmlextra](https://github.com/swatinerkar/postman/blob/main/images/42.%20htmlextra%20report.png)





For Reference: https://www.npmjs.com/package/newman-reporter-htmlextra
## 📂 Documentation

- You can add description about collection and each reqeust, to document about it.

#### Collection Document
- To add details about collection, simply click on collection and you will see overview tab. There you can add details.

    ![collection document](https://github.com/swatinerkar/postman/blob/main/images/43.%20Collection%20Desciption.png)

#### Request Document
- For Request, open the reqeust and on right side bar, you will find Document icon. Click on that and you will get field to add desciption about Request

    ![request document](https://github.com/swatinerkar/postman/blob/main/images/44.%20Request%20Description.png)

#### Add Example
- You can add example for references.
- Send the request of an API.
- Copy the response.
- For the same API, click on 3 dots on the Request -> Add Example
- Under Example, you need to paste the copied response.
- Also select expected status code.
- Save it.
- Add such examples for all Requests.

    ![Example Option](https://github.com/swatinerkar/postman/blob/main/images/45.%20Add%20Example%20option.png)

    ![Example](https://github.com/swatinerkar/postman/blob/main/images/46.%20Example.png)

#### Collection Documentation
- Go to Collection 3 dots -> scroll down -> View documentation
- Notice you can seee the complete documentation along with examples.

    ![View Documentation](https://github.com/swatinerkar/postman/blob/main/images/47.%20View%20Documentation.png)

#### Publish the Documentation
- You can see the publish option on right top corner, click on it.
- We will navigate to web postman where you can configure and customise your documentation page.

    ![Configure Publish](https://github.com/swatinerkar/postman/blob/main/images/48.%20webPostman_ConfigureBeforePublish.png)

- Select details as per your requirment and choice. I kept as it is.
- Click Publish

    ![Publish Documentation URL](https://github.com/swatinerkar/postman/blob/main/images/49.%20url%20Ffor%20published%20documentation.png)

- Open the published document URL
- This is published documentation and can be shared with anyone. 

    ![publish Documentation](https://github.com/swatinerkar/postman/blob/main/images/50.%20published%20documentation.png)




## 🌐 About Me
I'm a Software Automation Tester, having 11+ years of experience.

Please have a look on my Portfolio: [@swatinerkar](https://swatinerkar.wordpress.com/)

My LinkedIn Profile: [@swatinerkar](https://www.linkedin.com/in/swatinerkar/)

If you would like to have some guidence, you can book any of my service: [@swatinerkar](https://topmate.io/swati_nerkar)
## 👯 Support

For support, email swatinerkar.mentorship@gmail.com