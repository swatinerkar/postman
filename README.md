
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

