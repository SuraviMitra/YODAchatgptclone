<img width="960" alt="chatgpt1" src="https://github.com/SuraviMitra/YODAchatgptclone/assets/119784780/7783cd82-dcde-4a7e-8e1f-b2374f3da09f">
# YODAchatgptclone

<-------------------------------------------------------------------CHATGPT APP CLONE------------------------------------------------------------------------->

1.SERVER
2.CLIENT
------------------------------------------------------------------------------------------------------------------

1.Lets make the ******************************************SERVER*************************************************first------------------------------------->


-------------->In the terminal first we have to install npm to initialize the package for installing all the dependencies are maintained in a package.json
                1.npm init (package.json will be installed in server side)
                2.In my project the entry point will be server.js but in default it is always index.js.
                3.npm i express (from this package-lock.json and node modules will be installed)->from this we can create rest APIs.


Package-lock.json-->IT contains the dependencies for all the dependencies present in out package.json
                    for ex=> our package.json contains cors..So,for cors to work it also has some dependencies which contains in the package-lock.json. 


***NOTE
---------
(REST API) 
is an architectural style that defines a set of constraints to be used for creating web services. REST API is a way of accessing web services in a simple and flexible way without having any processing.
 
                    5. Now we can see one dependency already in the package.json .i.e. EXPRESS
                    6. DEPENDENCY--->
                                     1. Express- npm i express
                                     2. Mongoose- npm i mongoose (to connect to database)
                                     3. dotevn - npm i dotenv (to secure the databse)
                                     4. Morgan - npm i morgan (To check the Rest APIs--it shows the status of the rest API in the console)
                                     5. cors - npm i cors (To estalish connection between react to node & node to react)
                                     6. bodyparser - npm i body-parser (Used to send json data from node to react)
                                     7. colors - npm i colors (Used to print colours in the console(interactive package))
****                          **     8. nodemon- npm i nodemon (automatically restarting the node application when file changes in the directory)
NOTE---------------->To implement nodemon we have to go to the package.json file and write a script server:nodemon server.js &  start:node server.js.(now our Project can also run with the commands npm run server or npm start) & after installing concurrently add client:"npm start --prefix ./client" & "dev": "concurrently \"npm run server\" \"npm run client\"".
                                     9. bcryptjs - npm i bcryptjs (Used to hash passwords)
                                     10.jsonwebtoken - npm i jsonwebtoken (It is a token based authentication where a token is generated which we can decrypt with the  help of a unique key)
                                     11. cookie - npm i cookie 
                                     12. concurrently - npm i concurrently (with one single command we can run both node and react)
                                     13. openai - npm i openai



Now, we have to create a new file in the root directory and name as Server.js


**server.js--------------------------------->

1.So firstly to create server we have to add the packages using express..So, import the express first (const express = require("express").
2.Now using this we can now create the rest object. The rest object will give us a app object with the help of which we can listen to the server at any PORT.
   const app=express();
  Now all the functions of the express are included in this app object.
3.Now we will try to listen the server with the given respective PORT given(here given 8080) followed by a call back function (()=>{}) in which we write a console.log message SERVER RUNNING ON PORT 8080.
4.Now we have to open the terminal and run 
   node server.js
  O/P-->SERVER RUNNING ON PORT 8080 
5.Now add the packages morgan, cors, body-parser, colors.
6.Now we have to add the MIDDLEWARES 
  app.use()---->In this () we have to add the middlewares for ex->cors()
  similarly import body-parser..Here we got an option for urlencoded where we true/false the extended properties.
  similarly import morgan..Here in morgan we need dev
  similarly import express.json()..Using this we can transfer json data.
Here we have basically initialize all the functions.
7.**For the application security we have to import a very main package .i.e. dotenv & now configure the dotenv by 
    dotenv config()...By this we can config our all environmental variables.
8.Now make the .env file.
9.After creating the.env file now can create a variable name PORT where we can get or access the port using process.env.PORT.(IF this is not fond then we can add the or condition the port we have provided).
10.Now instead of directly writing the port number we can write the PORT.
11.Now run the application we can see the message in the terminal.
    SERVER RUNNING ON DEVELOPMENT ON 8080.
12.After creating the db.js importing it into the server.js to connect to the database.**Add it after the dotenv.config() write
   connectDB().
13.Now run the terminal (npm run server). 
14.After making authRoutes in the below steps we will import routes path by creating a variable const authRoutes=require(path).
15.Now we can make routing here & add the routes--->app.use("/api/v1/auth", authRoutes);
16.After creating the errorHandler below now we will import the error handler here-->app.use(errorHandler).
17.After router in openaiRouter.js importing summary in the server.js file.(app.use followed by end points & routes).
18.




Now in the root we have to create a file .env for environmental variable

**.env---------------------------->
1.Here we can keep all our confidencial data like
   1.PORT(here we use 8080).
   2.DEV_MODE-->that is the development mode(we can use it in the server.js file).
   3.MONGO_URL-->(our mongodb Url).
   4.JWT-->(Secret key for the json web token).
   5.After establishing the database create a variable 
     MONGO_URI-->here copy the connection string that we copied from the mongodb(**change the username & password with your respective username & password)and then write    your database name.
   6.Now connect the database for connecting create a new folder in the root name config in which we will create a new file name db.js.
   7.Now we have to do configuration in .env 
   8.For this we will first create secret for jsonwebtoken
          JWT_ACCESS_SECRET = we can add here our secret key (with the help of this our token will be decrypt).Now lets add its expirein
          JWT_ACCESS_EXPIREIN = here we can add when it will expire (for ex->15min).
   9.Now create the refresh token which we will create with the help of cookie
         JWT_REFRESH_TOKEN = we can add here our secret key.Now lets add its expirein
          JWT_REFRESH_EXPIREIN = here we can add when it will expire duration (for ex->15days).
   10.After creating the secret key for openai for creating api add it in the .env file with name OPEN_API_KEY=The api key you have generated.
          


Now we have to establish the database connection------------------------>
1.First go to the mongodb.com
2.Then after signup and login then create a new cluster for using free cluster hosting we have to select the shared option
3.Now create cluster.
4.If you already have any database then it will show in the Browse Collections. If you don't have then in the browse collection you can add create database.
5.Then Go to the Database Access in the left-side here you to create a new user with permission and password.
6.Now in the Network Access create the ip address.Here we have add (0.0.0.0/0) .i.e. our database can use any ip address.
7.Now get back to the database where we get a connect option through we can connect our database.
8.In the connect option we have to select connect using mongodb compass Then we have to copy the connection string & and then go to the .env file we have created earlier.



**db.js---------------------------->
1.Now for connecting to mongodb we have to first import the mongoose package.
2.Similarly importing the colors.
3.Now we have to create a function
4.Create a variable name ConnectDB followed by a async function.
   1.Now in the async function we will first implement try-catch block so that we can easily handle the response and the error.
   2.try{
       1. we will check our connections are properly estalished or not for that we will use await
       2. we will use await to connect to the database by (await mongoose.connect(process.env.MONGO_URI)) using the variables we made in .env to establish the connection.
       3.Now console.log to show CONNECTED TO THE DATABASE if it is securely connected to the mongodb.
       }
   3.catch{
       1.catch is use to catch the error using  console.log showing message MONGODB DATABASE ERROR.
           }
5.Now export the connectDB.
6.Now connect the database file db.js to the server.


 
-------------------------------------NOW YOU CAN SEE A MESSAGE IN THE TERMINAL------------------------------------------------------------------
--------------------------------------------------CONNECTED TO THE DATABASE SUCCESSFULLY--------------------------------------------------------


Now we will create the React Application------>
1.In the root we will create the react application.for this in the terminal we have to first write.
2.npx create-react-app client--->Here our application name is client.and This commad will help to create react-app in the client side.
3.For designing purpose we will use @material-ui
4.Now let us install all the depencies in the client side package.json
          DEPENDENCY---->
                        1.axios - npm i axios(for dealing network requests axios is use)
                        2.react-router-dom - npm i react-router-dom (for dealing with routing functionality)
                        3.material ui - npm install @mui/material@emotion/react @emotion/styled (from the material ui website) 
                        4.material icons - npm install @mui/icons-material (installing icons from the same material ui website)

5.Now when we run the command npm start in the terminal we will see that a default layout of our website will run in the port https://localhost:3000.
6.Now let us move to the app.js in the client side.


**app.js---------------------->
1.First remove the deafult header file and one <h1> tag WELCOME TO CHATGPT.
2.Remove the logo.
3.Similarly we will chnage the index.css according to our website requirement.
4.Similar with app.css.
5.Now in the browser we can see a blank page with writter  WELCOME TO CHATGPT.
6.After creating all the openai routes create  a route in the app.js <Route path="/" element={} /> for(register, login, summary)



Now we will create the Rest APIs---------------------->
1.Here we will work in MVC pattern where we will have (model, view layers, controller) all work & handel separately. This will help the application to build fast and also it increases the efficiency.
2.In the root we will first make a new folder name models----->Here in the models we will add all our user schemas.
3.Similarly we will create a folder name routes in the root------>Here all the routes in the application will be shown or here we will create the routes separately.
4.Similarly we will create a folder name controllers----->Here all the callback funstions a handel separately in the controller holder.
5.Similarly we will create a folder name Middelwares------>Here we will all the middelwares (next functions are called the middelwares).
6.Similarly we will create a folder name utils----->Here we will create a class or a funtion as a utility file.




Now we will create the model------------------>
1.Firstly create a new file in the model name userModel.js (As because it is related to the user).

**userModel.js------------------------------>
1.Here firstly we will import the mongoose.
2.Now import bcrypt.
3.As soon as our model will be created we will create functions to hash our password.
4.Now import jsonwebtoken.
5.Now we will create the model
6.Here we will basically create the schemas.As it is related to the user so we will name it here userSchema.
   const UserSchema = new Schema({object})
7.Now we will define the types here({})
   1.Firstly here will get the username. we have to make the object (type:string, required:[true,(error message) USERNAME IS REQUIRED).
   2.Similarly we will create email. we have to make the object (type:string, required:[true,(error message) EMAIL IS REQUIRED).
     As the email should be unique so we will add the unique property (unique: true).
   3.Similarly we will create password. we have to make the object (type:string, required:[true,(error message) PASSWORD IS REQUIRED).
     we will give minimum length of the password (minlength: [6, "Password length should be 6 characters long"]).
   4.Similarly we will create customerId. we have to make the object (type:string, and default we will add empty string here).
   5.we will add subscription model here.(subscription type)(type:string, and default we will add empty string here).
8.NOW WE WILL HASH OUR PASSWORD-->
   1.We will first create a function for hashed password.
   2.Here with the help of userSchema we will use pre(.i.e before save) & do the function call (async) where we will recieve the next
      userSchema.pre("save", async function (next)
     Here it will act like a middleware-->when next will be called our Schema will be save.
   3.pre->before save execute the hash function
   4.Check wheather the password is modified or not.
     If not modified---> then we will simply call next.
   5.Now to hash password here we will create a variable string salt (as it is a async function so we will await) Here with the help of bcrypt we will generate the salt.
     Now here we will use gensalt where we have to pass the routes.(in my project min 10 we will keep because more than that if we will keep it will take a lot of execution time).
   6.Now we will hash it-----> this.password = await hash(this.password, salt);
      Here we will again await & use hash function (In hash firstly we will pass the password we recieve and then salt).As soon as it hash the password we will again call next().(So that our execution will be continued).
   7.Now we will check the match password .i.e. (wheather the password send by the user is correct or not).
   8.In userSchema again we have to call a function & we will use methods here.We will create a new method which contains match password that will conatin a async function(Here we will normal function because it will not support arrow function) & password is recieved as a argument here.
        userSchema.methods.matchPassword = async function (password) {};
   9.Now we will bcrypt it & compare the password we have & the password contains within the schema.
   10.Now we will manage token here also since we are using cookie
   11.Here we will use JWT. For that We will again create a new--->userSchema.methods.getSignedToken = function (res)
      Here in the function we will recieve the response.
   12.Now lets create the token-->
       1.Create a variable accessToken where we will environmental variables(use sign function based on id which is generated by the schema bydefault)
       2.Now add the secret as we made earlier in the .env file (JWT_ASSCESS_TOKEN) & the expirein (JWT_ASSCESS_EXPIREIN).
       3.Similarly add the referesh token with the help of cookie here & its expirein.   
       4.Now we will generate token here eith the help of cookie(for this import the cookie).
9.Now export the Schema..To export first we will make a variable name User= model('User',userSchema)
   Here userSchema is the reference type.
10.Now export the model----> module.exports = User;



Now to use this model we have create route--------->
Now in the route folder we will create a new file as it is realated to the autentication so name authRoutes.js

**authRoutes.js------------>
1.Firstly importing express package.
2.Now we will create the router object through which we can create routing.
   const router = express.Router();
3.Now creating the routers here->
   1.router.post("/register", registerController)---->Here we are posting the router for login.It is followed by a call back function which we will made separately in the controller function where we will make a file name authController.js.
   2.similarly we will do for login & for logout.
   3.There call back functions  are present in the controller folder .i.e. authController.js.
4.Now export the router successfully.
5.Then importing it into our main file server.js.




**authController.js----------------->
1.Here we will create a new function registerContoller followed by a async arrow function.
2.Similarly we will create a new function for login.
3.Similarly for logout also.
4.Before working into the Controller we to first create utility files in the util folder.
5.Now after handling the error we also need token. Now to send send we have to make a new function so that whenever we will login a token will be generated.
  1.exports.sendToken--->It is also followed by a arrow function It will contain (user,statuscode,response) during login & register.
  2.Now we will make a variable const token & we will use user here and we will use getSigned token that we made in the models (userModel.js) after that we will import the userModel.js.
  3.Now we will send the response status with statuscode followed by json & we will pass token.
6.Now we will work on register --->
  1.In register we will access (request,response & next(middleware)) followed by try-catch error.
  2. If error will occur we will next..we will pass it as a middleware beacuse we have errorResponse.js.
  3.Now in try{
       we will request(username,email,password) from the body.
       IF the email already exists then we will validate on the basis of email then we will await and find the existing user using findOne..If existing 
        email then we will return next and using error response we will send a message EMAIL ALREADY EXISTS with status code 500.
  4.Now we will create a user we will use await in userModel and create user with get (username,email,password) & now call the function sendToken where we have to pass the (user,201,response).
7.Now similarly we will work on login-------->
   1.This also async function here also we will recieve (request,response,next) Here also we will add the try-catch block
   2.In catch if error will occur then we will show error in the console and call next with error.
   3.In the try{
      First we will take the (email,password) from the body
      Now we will look upon the validation here we will chaeck the user  
      if user don't have (email & password) then return..In return we will send middleware (new errorResponse) & we will pass the message here 
      PLEASE PROVIDE EMAIL OR PASSWORD.
      Now we will check the user on the basis of email by using findOne function 
      if not user-->then return and next error response message INVALID CREDENTIAL with status code 401.
      we will also check the password-->In the model (userModel.js) we have already made a function for matchPassword we will use it here
      Here we will pass password as an argument-->If password does not match we will restunr next with an error message INVALID with status
      code 401.
      Now send Token where we will pass the user with its reqponse.
8.Now lets work on logout---------->
   1.firstly we will clear the refreshtoken by using response.clearCookie
   2.Now return next success with status code 200 and a message LOGOUT SUCCESSFULLY.
9.Now we can connect all this in the frontend side.for frontend we will first go to the client. In the client we will go to src.






Now in the utils folder create a file name errorResponse.js
**errorResponse.js------->
1.Here we will handel the error response.
2.Here we will use an instance of the class & extends the original error present here--->class errorResponse extends Error
3.Here we will use constructor where we will add the statuscode and the message.
4.Inside the constructor we will use super class constructor & pass the messgae.
5.Now we have to pass the status code that we will pass.
6.Now we will export the errorResponse.
7.So here we have create a utility file through we we can easily show the error message with satuscode.
8.After this we will create a middelware also in the middelware folder we have already created name errorMiddleware.js for handeling error middelwares.
9.Now we will work on the callback functions.
10.Here we will alos need token..So for that we will make a function here to generate a token whenever we will register.
11.we will export sendToken followed by a arrow function



**errorMiddleware.js----->
1.First we have to import the class here errorResponse that we have created in the utility folder.
2.Now we will create here a function name errorHandler as this is a middleware so it will aslo contains (error,request,response,next) followed by a arrow function.
   1.Now in this we will first make a variable err.(Here we have used let so that we change it later if we want in the application)
   2.Now we will use the error message-->error.message = error.message (here we can use it directly as we get it from the error object).
   3.Now 1st we will handel the mongoose error-->
      1.we will check if err.name is equivalent to the castError then we will create a variable message to show error message
            RESOURCES NOT FOUND
      2.Then we will pass the error from the errorResponse we have already created..Now pass the error here with a status code 404 not found.
   4.Now we will handel the duplicate key error
      1.we will check if err.code==1100..then we will create a variable message to show error message
            DUPLICATE FIELD VALUE ENTERED.
      2.Then we will pass the error from the errorResponse we have already created..Now pass the error here with a status code 400 not found.
   5.Now we will handel the validation error err.name=(error name).But here we cannot directly show the error message beacuse here it constains the nested message so here first we have to get the message
       const message = Object.values(err.errors).map((val) => val.message)
 We will map the error here so that we can get a single value that we can print directly.Now we will replace the value with message & and get the message 
   6.Now we will pass the error here with a message and a status code 400.
   7.Now send the response-->the status(500).
   8.Now we send the json response here and show a error message SERVER ERROR.
3.Now wxport the errorHandler.
4.Now import it into the server.js file.



****Now for the frontend work-------------------------->
1. we will go to the client and in client go to src.
2. In src we will create a folder name pages 
3.In src we will make another folder also name components



**In the components folder we will create a new file name Navbar.js(es7 extension installed in vs code to automatically import react with callback arrow function)
***Navbar.js--------------->
1.Import react.
2.Now go to pages.
3.Now in the navbar we will first import (box,link(because we can see the navigation menu here),typography(for text)) from material-ui.
4.In the box we will add the width , padding & text allign & inline style.
   1. Here we will use <typography> & in typography we have to set the variants and its color as white.
   2.Now we will change its fondweight.
   3.Now with the help of <Link> we will create the navigation menu & redirect it to the register page.
   4.Similarly for login we will use <Link>.
5.Instead of using Link we can also use NavLink that we get in the react-router-dom. we can also replace all the <Link> as NavLink and href to to.
6.In the src we will make a file Theme.js where we can write all the background css of the application.
7.Now import the theme by creating a variable const theme = useTheme().
8.Now we will configure this theme in the root file app.js.Go to app.js



**In the pages folder we will now make files-------->

***@1.Homepage.js------------------>

       1.The component imports necessary dependencies from React, Material-UI components, and react-router-dom.
       2.The component function Homepage is defined using an arrow function.
       3.Inside the function, the useNavigate hook is used to manage navigation within the component.
       4.The component renders a series of Card components wrapped in Box and Typography components. Each Card represents a different feature or section of the application.
       5.Each Card has an onClick event handler that navigates to a specific route when clicked. The route is determined by the navigate function from useNavigate.
       6.Each Card has a similar structure but with different icons and text. The icons are imported from the Material-UI icon library and displayed using the sx prop to customize their size, color, and position.
       7.The Card components are styled using the sx prop to define their appearance, including the box shadow, border radius, size, and hover effect.
       8.Inside each Card, there is a Stack component that contains Typography components for the title and description of the feature or section.
       9.The component is wrapped in an empty fragment (<>...</>) because it needs to return adjacent JSX elements without a parent container element.
       10.Finally, the component exports the Homepage component as the default export, which can be used in other parts of the application.

In summary, the Homepage component renders a homepage with different feature cards, allowing users to navigate to different sections or features of the application by clicking on the respective cards.


***@2.Login.js-------------------->

       1. The component imports necessary dependencies from various libraries, including React, React Router, react-hot-toast, axios, and Material-UI components.
       2.The component function Login is defined using an arrow function.
       3.Inside the function, hooks like useState and useNavigate are used to manage state and navigation within the component.
       4.The component defines states for email, password, and error using the useState hook. These states will be updated based on user input.
       5.The handleSubmit function is an asynchronous function that handles the form submission. It prevents the default form submission behavior, sends a POST request to a login API endpoint using axios, and handles success and error scenarios. If the login is successful, a success message is displayed using react-hot-toast, and the user is navigated to the home page. The authentication token is also stored in the local storage using localStorage.setItem.
       6.The component renders a form using Material-UI components like Box, Typography, TextField, Button, and Alert. The form includes input fields for email and password, and a submit button for signing in.
       7.If there is an error, it is displayed in an Alert component wrapped in a Collapse component.Finally, the component exports the Login component as the default export, which can be used in other parts of the application.

In summary, the Login component provides a user interface for logging in to an existing account and handles the form submission and error handling logic using React, React Router, and Material-UI.



***@3.Register.js------------------>

   1.It imports necessary dependencies from various libraries, including React, React Router, react-hot-toast, axios, and Material-UI components.
   2.The component function Register is defined using an arrow function.
   3.Inside the function, hooks like useState and useNavigate are used to manage state and navigation within the component.
   4.The component defines states for username, email, password, and error using the useState hook. These states will be updated based on user input.
   5.The handleSubmit function is an asynchronous function that handles the form submission. It prevents the default form submission behavior, sends a POST request to a registration API endpoint using axios, and handles success and error scenarios. If the registration is successful, a success message is displayed using react-hot-toast, and the user is navigated to the login page.
   6.The component renders a form using Material-UI components like Box, Typography, TextField, Button, and Alert. The form includes input fields for username, email, and password, and a submit button for signing up.
   7.If there is an error, it is displayed in an Alert component wrapped in a Collapse component.
Finally, the component exports the Register component as the default export, which can be used in other parts of the application.
   8.Overall, the Register component provides a user interface for registering a new account and handles the form submission and error handling logic using React, React Router, and Material-UI.



***@4.Summary.js------------------>

       1.The component imports necessary dependencies from React, Material-UI components, and axios.
       2.The component function Summary is defined using an arrow function.
       3.Inside the function, the useTheme and useMediaQuery hooks are used to access the current theme and media query information, respectively.
       4.The component defines several states using the useState hook. These states include text for storing the user input text, summary for storing the generated summary, and error for displaying any error messages.
       5.The component defines the handleSubmit function, which is called when the form is submitted. Inside this function, an HTTP POST request is made to a specific API endpoint (/api/v1/openai/summary) using axios. The user input text is sent in the request payload.
       6.If the request is successful, the response data is logged to the console, and the summary state is updated with the generated summary.
       7.If an error occurs during the request, the error message is logged to the console, and the error state is updated with the corresponding error message.
       8.The component renders a Box component that contains the form and the summary display.
       9.The form is wrapped in a Collapse component, which displays the Alert component containing the error message when the error state is truthy.
       10.The form includes a TextField component where users can enter their text for summarization. The entered text is stored in the text state using the onChange event handler.
       11.The form also includes a submit button (Button component) that triggers the handleSubmit function when clicked.
       12.Below the form, there is a Typography component with a link to go back to the homepage. The link is provided by the Link component from react-router-dom.
       13.The component conditionally renders the summary display based on whether the summary state has a value.
       14.If a summary exists, a Card component is rendered with the generated summary displayed inside a Typography component.
       15.If no summary exists, another Card component is rendered with a placeholder message displayed inside a Typography component.
       16.The Card components are styled using the sx prop to define their appearance, including the box shadow, height, border radius, border color, and background color.
       17.Finally, the component exports the Summary component as the default export, which can be used in other parts of the application.

In summary, the Summary component renders a form where users can enter text for summarization. It communicates with an API endpoint to generate the summary and displays the result in a separate card. If an error occurs during the process, an error message is displayed.



***@5.ChatBot.js------------------>

       1.The component imports necessary dependencies from React, Material-UI components, and axios.
       2.The component function ChatBot is defined using an arrow function.
       3.Inside the function, the useTheme and useMediaQuery hooks are used to access the current theme and media query information, respectively.
       4.The component defines several states using the useState hook. These states include text for storing the user input text, response for storing the chatbot's response, and error for displaying any error messages.
       5.The component defines the handleSubmit function, which is called when the form is submitted. Inside this function, an HTTP POST request is made to a specific API endpoint (/api/v1/openai/chatbot) using axios. The user input text is sent in the request payload.
       6.If the request is successful, the response data is logged to the console, and the response state is updated with the chatbot's response.
       7.If an error occurs during the request, the error message is logged to the console, and the error state is updated with the corresponding error message.
       8.The component renders a Box component that contains the form and the chatbot response display.
       9.The form is wrapped in a Collapse component, which displays the Alert component  containing the error message when the error state is truthy.
      10.The form includes a TextField component where users can enter their text to interact with the chatbot. The entered text is stored in the text state using the onChange event handler.
       11.The form also includes a submit button (Button component) that triggers the handleSubmit function when clicked.
       12.Below the form, there is a Typography component with a link to go back to the homepage. The link is provided by the Link component from react-router-dom.
       13.The component conditionally renders the chatbot response display based on whether the response state has a value.
       14.If a response exists, a Card component is rendered with the chatbot's response displayed inside a Typography component.
       15.If no response exists, another Card component is rendered with a placeholder message displayed inside a Typography component.
       16.The Card components are styled using the sx prop to define their appearance, including the box shadow, height, border radius, border color, and background color.
       17.Finally, the component exports the ChatBot component as the default export, which can be used in other parts of the application.

In summary, the ChatBot component renders a form where users can enter text to interact with an AI chatbot. It communicates with an API endpoint to get the chatbot's response and displays the response in a separate card. If an error occurs during the process, an error message is displayed.


***@6.Paragraph.js------------------>
      
1.The component imports necessary dependencies from React, Material-UI components, and axios.
      2.The component function Paragraph is defined using an arrow function.
      3.Inside the function, the useTheme and useMediaQuery hooks are used to access the current theme and media query information, respectively.
      4.The component defines several states using the useState hook. These states include text for storing the user input text, para for storing the generated paragraph, and error for displaying any error messages.
      5.The component defines the handleSubmit function, which is called when the form is submitted. Inside this function, an HTTP POST request is made to a specific API endpoint (/api/v1/openai/paragraph) using axios. The user input text is sent in the request payload.
      6.If the request is successful, the response data is logged to the console, and the para state is updated with the generated paragraph.
      7.If an error occurs during the request, the error message is logged to the console, and the error state is updated with the corresponding error message.
      8.The component renders a Box component that contains the form and the generated paragraph display.
      9.The form is wrapped in a Collapse component, which displays the Alert component containing the error message when the error state is truthy.
      10.The form includes a TextField component where users can enter their text to generate a paragraph. The entered text is stored in the text state using the onChange event handler.
      11.The form also includes a submit button (Button component) that triggers the handleSubmit function when clicked.
      12.Below the form, there is a Typography component with a link to go back to the homepage. The link is provided by the Link component from react-router-dom.
      13.The component conditionally renders the generated paragraph display based on whether the para state has a value.
      14.If a paragraph exists, a Card component is rendered with the generated paragraph displayed inside a Typography component.
      15.If no paragraph exists, another Card component is rendered with a placeholder message displayed inside a Typography component.
      16.The Card components are styled using the sx prop to define their appearance, including the box shadow, height, border radius, border color, and background color.
      17.Finally, the component exports the Paragraph component as the default export, which can be used in other parts of the application.

In summary, the Paragraph component renders a form where users can enter text and generate a paragraph based on their input. It communicates with an API endpoint to generate the paragraph and displays the result in a separate card. If an error occurs during the process, an error message is displayed.




***@7.ScifiImage.js------------------>
    
      1.The component imports necessary dependencies from React, Material-UI components, and axios.
      2.The component function ScifiImage is defined using an arrow function.
      3.Inside the function, the useTheme and useMediaQuery hooks are used to access the current theme and media query information, respectively.
      4.The component defines several states using the useState hook. These states include text for storing the user input text, image for storing the generated sci-fi image URL, and error for displaying any error messages.
      5.The component defines the handleSubmit function, which is called when the form is submitted. Inside this function, an HTTP POST request is made to a specific API endpoint (/api/v1/openai/scifi-image) using axios. The user input text is sent in the request payload.
      6.If the request is successful, the response data (URL of the generated image) is logged to the console, and the image state is updated with the generated image URL.
      7.If an error occurs during the request, the error message is logged to the console, and the error state is updated with the corresponding error message.
      8.The component renders a Box component that contains the form and the generated sci-fi image display.
      9.The form is wrapped in a Collapse component, which displays the Alert component containing the error message when the error state is truthy.
      10.The form includes a TextField component where users can enter their text. The entered text is stored in the text state using the onChange event handler.
       11.The form also includes a submit button (Button component) that triggers the handleSubmit function when clicked.
       12.Below the form, there is a Typography component with a link to go back to the homepage. The link is provided by the Link component from react-router-dom.
       13.The component conditionally renders the generated sci-fi image display based on whether the image state has a value.
       14.If an image URL exists, a Card component is rendered with the generated sci-fi image displayed inside an img element.
       15.If no image URL exists, another Card component is rendered with a placeholder message displayed inside a Typography component.
       16.The Card components are styled using the sx prop to define their appearance, including the box shadow, height, border radius, border color, and background color.
       17.The generated image is centered using the Box component with the display and justifyContent properties set.
       18.Finally, the component exports the ScifiImage component as the default export, which can be used in other parts of the application.

In summary, the ScifiImage component renders a form where users can enter text and generate a sci-fi image based on their input. It communicates with an API endpoint to generate the image and displays the result in a separate card. If an error occurs during the process, an error message is displayed.



***@8.JsConverter.js------------------>
    
    1.The component imports necessary dependencies from React, Material-UI components, and axios.
    2.The component function JsConverter is defined using an arrow function.
    3.Inside the function, the useTheme and useMediaQuery hooks are used to access the current theme and media query information, respectively.
    4.The component defines several states using the useState hook. These states include text for storing the user input text, code for storing the converted JavaScript code, and error for displaying any error messages.
    5.The component defines the handleSubmit function, which is called when the form is submitted. Inside this function, an HTTP POST request is made to a specific API endpoint (/api/v1/openai/js-converter) using axios. The user input text is sent in the request payload.
    6.If the request is successful, the response data (converted JavaScript code) is logged to the console, and the code state is updated with the converted code.
    7.If an error occurs during the request, the error message is logged to the console, and the error state is updated with the corresponding error message.
    8.The component renders a Box component that contains the form and the converted JavaScript code display.
    9.The form is wrapped in a Collapse component, which displays the Alert component containing the error message when the error state is truthy.
    10.The form includes a TextField component where users can enter their text. The entered text is stored in the text state using the onChange event handler.
    11.The form also includes a submit button (Button component) that triggers the handleSubmit function when clicked.
    12.Below the form, there is a Typography component with a link to go back to the homepage. The link is provided by the Link component from react-router-dom.
    13.The component conditionally renders the converted JavaScript code display based on whether the code state has a value.
    14.If converted code exists, a Card component is rendered with the converted code displayed inside a pre element.
    15.If no converted code exists, another Card component is rendered with a placeholder message displayed inside a Typography component.
    16.The Card components are styled using the sx prop to define their appearance, including the box shadow, height, border radius, border color, background color, and overflow property.
    17.The converted code is displayed inside a Typography component nested within a pre element to preserve the formatting of the code.
    18.Finally, the component exports the JsConverter component as the default export, which can be used in other parts of the application.

In summary, the JsConverter component renders a form where users can enter text and convert it into JavaScript code. It communicates with an API endpoint to perform the conversion and displays the converted code in a separate card. If an error occurs during the process, an error message is displayed.




**Now in the client side index.js file----->
1.we will quote the application with BrowserRouter form react-router-dom.
2.Now in our application the routing functionality is enabled.
3.Now we can use in in the app.js.Go to app.js



**app.js----------------->
1.Firstly we will import react-router-dom & in react-router-dom we will need Routes which will work as a container & Route by which we can create the route.
2.Now first import the navbar.
3.Now we will use the Routes container where we can perform routing Now in the route we will define the path.
  <Route path="/" element={<Homepage />} />
  This is for homepage 
4.Similarly create routes for login and resgister also.
5.Now we will install a new package.
6.We will create header Navbar.
7.Now after the navbar we will use here useMemo from react.
8.Then we have to import theme from @mui/system.
9.Now we will import theme from theme.js.
10.Now using usememo we will basically configure the theme.
11.Import themeProvider &cssBaseLine from @mui/material.
12.Now create a variable theme =useMemo followed by a callback function which contains empty array.


*****Now we will add the API of chat gpt--------->
1.for that go to platform.openai.com or https://openai.com/api/ 
2.first login and signup here.
3.Now you have to click the icon on the right side and then click on API keys on the left side & then generate new secret key 
4.Now you have to copy the secret key & paste it in the .env file.
5.Now in the documentation click on the completion & there we will select node js. Now we will copy the api as it is & paste it in the openiaController.js.



**Now in the controller folder we have to make one more file name openiaController.js

***openiaController.js---------->
1.paste the code in the openiaController.js that you have copies from the openai platform.
2.To use it we need env file for that we will import dotenv.
3.config dotenv.
4. now we have copy the OPEN_API_KEY and replace it in the .env file also
5.Now again restart the server.
6.maxToken are the words we need we will include it in a call back function.
7.Now we will create a new call back function.
    1.First we will create API for the summary.
       1. followed by a async function we recieve request and response in it.
       2. Now using the try-catch block.
       3.In the catch we will print the error with an error status code 404 with json message
       4.In the try we will destructure the data & we will await & using openai we will create completion 
         1.Inside create completion we will pass the object.
       5.then we will get text from the user and summarise it.
       6.Then we will prompt the text.
          1.If we found data in it then check the 0th position and then get the text..Now we will return.
       7.Now we will create routes for it.




**Now in the router folder we will create route

***openaiRoutes.js----->
1.Firstly we will import the express.
2.Then we will create the router object const router = express.Router()
3.Now we will our 1st router(Summary)
  1. we will give post and end points for summary folled by a call back function that we have created in controller name SummaryController now import it into the server.js file.
  2.Now in the pages create a file summary.js.
4.similarly create all the routes for(chatbot,paragraph,scifimage,javasript).


                                 
