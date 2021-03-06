# Getting started

D7 SMS allows you to reach your customers via SMS over D7's own connectivity to global mobile networks. D7 provides reliable and cost-effective SMS services to businesses across all industries and aims to connect all countries and territories via direct connections.

## How to Build

The generated SDK requires AngularJS framework to work. If you do not already have angular downloaded, please go ahead and do it from [here](https://angularjs.org/).
You will also need to download and link [angular-moment](https://cdnjs.cloudflare.com/ajax/libs/angular-moment/1.0.1/angular-moment.min.js) and [moment.js](https://cdnjs.cloudflare.com/ajax/libs/moment.js/2.17.1/moment.min.js) with your project because the SDK internally uses moment.js.

## How to Use

The following section describes how to use the generated SDK in an existing/new project.

### 1. Configure Angular and Generated SDK
Perform the following steps to configure angular and the SDK:
+ Make a `scripts` folder inside the root folder of the project. If you already have a `scripts` folder, skip to the next step.
+ Move the `angular.min.js` file inside the scripts folder. 
+ Move the `D7SMSLib` folder inside the scripts folder.
+ If any of the Custom Types in your API have `Date`/`Datetime` type fields or any endpoint has `Date`/`Datetime` response, you will need to download angular-moment and moment.js. Move these 2 files into the `scripts` folder as well.

![folder-structure-image](https://github.com/d7networks/D7SMS-SDKs/blob/master/D7SMS-AngularJs/images/angularjs_1.svg)

### 2. Open Project Folder
Open an IDE/Text Editor for JavaScript like Sublime Text. The basic workflow presented here is also applicable if you prefer using a different editor or IDE.  
Click on `File` and select `Open Folder`

Select the folder of your SDK and click on `Select Folder` to open it up in Sublime Text. The folder will become visible in the bar on the left.

![open-folder-image](https://github.com/d7networks/D7SMS-SDKs/blob/master/D7SMS-AngularJs/images/angularjs_2.svg)

### 3. Create an Angular Application
Since Angular JS is used for client-side web development, in order to use the generated library, you will have to develop an application first.
If you already have an angular application, [skip to Step 6](#6-include-sdk-references-in-html-file). Otherwise, follow these steps to create one:

+ In the IDE, click on `File` and choose `New File` to create a new file.
+ Add the following starting code in the file:
```js
var app = angular.module('myApp', []);
app.controller('testController', function($scope) 
{

});
```
+ Save it with the name `app.js` in the `scripts` folder.


### 4. Create HTML File
Skip to the next step if you are working with an existing project and already have an html file. Otherwise follow the steps to create one:
+ Inside the IDE, right click on the project folder name and select the `New File` option to create a new test file.
+ Save it with an appropriate name such as `index.html` in the root of your project folder.
`index.html` should look like this:
```html
<!DOCTYPE html>
<html>
<head>
	<title>Angular Project</title>
	<script></script>
</head>

<body>
</body>

</html>
```

![initial-html-code-image](https://github.com/d7networks/D7SMS-SDKs/blob/master/D7SMS-AngularJs/images/angularjs_3.svg)

### 5. Including links to Angular in HTML file
Your HTML file needs to have a link to `angular.min.js` file to use Angular-JS. Add the link using `script` tags inside the `head` section of `index.html` like:
```html
<script src="scripts/angular.min.js" ></script>
```
If any of the Custom Types that you have defined have `Date`/`Datetime` type fields or any endpoint has `Date`/`Datetime` response, you will also need to link to angular-moment and moment.js like:
```html
<script src="scripts/angular.min.js" ></script>
<script src="scripts/moment.min.js" ></script>
<script src="scripts/angular-moment.min.js" ></script>
```

### 6. Include SDK references in HTML file
Import the reference to the generated SDK files inside your html file like:
```html
<head>
    ...
    <!-- Helper files -->
    <script src="scripts/D7SMSLib/Module.js"></script>
    <script src="scripts/D7SMSLib/Configuration.js"></script>
    <script src="scripts/D7SMSLib/ModelFactory.js"></script>
    <script src="scripts/D7SMSLib/ObjectMapper.js"></script>
    <script src="scripts/D7SMSLib/APIHelper.js"></script>
    <script src="scripts/D7SMSLib/Http/Client/HttpContext.js"></script>
    <script src="scripts/D7SMSLib/Http/Client/HttpClient.js"></script>
    <script src="scripts/D7SMSLib/Http/Request/HttpRequest.js"></script>
    <script src="scripts/D7SMSLib/Http/Response/HttpResponse.js"></script>

    <!-- API Controllers -->
    <script src="scripts/D7SMSLib/Controllers/BaseController.js"></script>
    <script src="scripts/D7SMSLib/Controllers/APIController.js"></script>


    <!-- Models -->
    <script src="scripts/D7SMSLib/Models/BaseModel.js"></script>
    <script src="scripts/D7SMSLib/Models/SendSMSRequest.js"></script>
    <script src="scripts/D7SMSLib/Models/BulkSMSRequest.js"></script>
    <script src="scripts/D7SMSLib/Models/Message.js"></script>

    ...
</head>
```
> The `Module.js` file should be imported before the other files. After `Module.js`, `Configuration.js` should be imported.
> The `ModelFactory.js` file is needed by `ObjectMapper.js` file. The `ObjectMapper` in turn, is needed by `BaseController.js`.

### 7. Including link to `app.js` in HTML file
Link your `app.js` file to your `index.html` file like:
```html
<head>
	...
	<script src="scripts/app.js"></script>
</head>
```
> The link to app.js needs to be included at the very end of the head tag, after the SDK references have been added

### 8. Initializing the Angular App
You need to initialize your app and the controller associated with your view inside your `index.html` file. Do so like:
+ Add ng-app directive to initialize your app inside the `body` tag.
```html
<body ng-app="myApp">
```
+ Add ng-controller directive to initialize your controller and bind it with your view (`index.html` file).
```html
...
<body ng-app="myApp">
	<div ng-controller="testController">
		...
	</div>
	...
</body>
...
```

### 9. Consuming the SDK 
In order to use the generated SDK's modules, controllers and factories, the project needs to be added as a dependency in your angular app's module. This will be done inside the `app.js` file.
Add the dependency like this:

```js
var app = angular.module('myApp', ['D7SMSLib']);
```
At this point, the SDK has been successfully included in your project. Further steps include using a service/factory from the generated SDK. To see working example of this, please head on [over here](#list-of-controllers) and choose any class to see its functions and example usage.  

### 10. Running The App
To run the app, simply open up the `index.html` file in a browser.

![app-running](https://github.com/d7networks/D7SMS-SDKs/blob/master/D7SMS-AngularJs/images/angularjs_4.svg)

## Initialization


The Angular Application can be initialized as following:
```JavaScript
var app = angular.module('myApp', [D7SMSLib]);
// now controllers/services can be created which import
// the factories provided by the sdk
```
### Authentication
In order to setup authentication and initialization of the Angular App, you need the following information.

| Parameter | Description |
|-----------|-------------|
| aPIUsername | API Key |
| aPIPassword | API Token |



```js
var app = angular.module('myApp', [D7SMSLib]);

app.run(function(Configuration) {
    // Configuration parameters and credentials
    Configuration.aPIUsername = 'aPIUsername'; // API Key
    Configuration.aPIPassword = 'aPIPassword'; // API Token
    
});
```



# Class Reference

## <a name="list_of_controllers"></a>List of Controllers

* [APIController](#api_controller)

## <a name="api_controller"></a>![Class: ](https://github.com/d7networks/D7SMS-SDKs/blob/master/D7SMS-AngularJs/images/class.png ".APIController") APIController

### Get singleton instance

The singleton instance of the ``` APIController ``` class can be accessed via Dependency Injection.

```js
	app.controller("testController", function($scope, APIController){
	});
```

### <a name="get_balance"></a>![Method: ](https://github.com/d7networks/D7SMS-SDKs/blob/master/D7SMS-AngularJs/images/method.png ".APIController.getBalance") getBalance

> Check account balance


```javascript
function getBalance()
```

#### Example Usage

```javascript


	app.controller("testController", function($scope, APIController){


		var result = APIController.getBalance();
        //Function call returns a promise
        result.then(function(success){
			//success case
			//getting context of response
			console.log(success.getContext());
		},function(err){
			//failure case
		});

	});
```

#### Errors

| Error Code | Error Description |
|------------|-------------------|
| 500 | Internal Server Error |




### <a name="create_send_sms"></a>![Method: ](https://github.com/d7networks/D7SMS-SDKs/blob/master/D7SMS-AngularJs/images/method.png ".APIController.createSendSMS") createSendSMS

> Send SMS  to recipients using D7 SMS Gateway


```javascript
function createSendSMS(input)
```
#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| body |  ``` Required ```  | Message Body |
| contentType |  ``` Required ```  | TODO: Add a parameter description |
| accept |  ``` Required ```  | TODO: Add a parameter description |



#### Example Usage

```javascript


	app.controller("testController", function($scope, APIController){
        var input = [];
        input['body'] = new SendSMSRequest({"key":"value"});
        input['contentType'] = 'Content-Type';
        input['accept'] = 'Accept';


		var result = APIController.createSendSMS(input);
        //Function call returns a promise
        result.then(function(success){
			//success case
			//getting context of response
			console.log(success.getContext());
		},function(err){
			//failure case
		});

	});
```

#### Errors

| Error Code | Error Description |
|------------|-------------------|
| 500 | Internal Server Error |




### <a name="create_bulk_sms"></a>![Method: ](https://github.com/d7networks/D7SMS-SDKs/blob/master/D7SMS-AngularJs/images/method.png ".APIController.createBulkSMS") createBulkSMS

> Send Bulk SMS  to multiple recipients using D7 SMS Gateway


```javascript
function createBulkSMS(body, contentType, accept)
```
#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| body |  ``` Required ```  | Message Body |
| contentType |  ``` Required ```  | TODO: Add a parameter description |
| accept |  ``` Required ```  | TODO: Add a parameter description |



#### Example Usage

```javascript


	app.controller("testController", function($scope, APIController){
        var body = new BulkSMSRequest({  "messages": [    {      "to": [        "971562316353",        "971562316354",        "971562316355"      ],      "content": "Same content goes to three numbers",      "from": "SignSMS"    }  ]});
        var contentType = 'application/json';
        var accept = 'application/json';


		var result = APIController.createBulkSMS(body, contentType, accept);
        //Function call returns a promise
        result.then(function(success){
			//success case
			//getting context of response
			console.log(success.getContext());
		},function(err){
			//failure case
		});

	});
```



[Back to List of Controllers](#list_of_controllers)



