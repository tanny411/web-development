## The Full Stack Web Development Course: Back End

### 1. Node.js
- Its Asynchronous and optimized for throughput and scalability. It is event-driven. It is single threaded and supports concurrency via events and callbacks.
- Install node with `sudo apt install nodejs` and check versions `node -v` and `npm -v`. Run js files from terminal with `node file.js`. Cannot run browser based functions though.
- `npm install express` installs it in the node_modules folder. `-g` tag installs it globally. Always have a package.json file and used `--save` tag when installing to add stuff to package.json. To create the file call `npm init`. Later on `npm install` with install all required dependencies.
- Create a server with http, set a callback, and set it to listen to a port. Thats it! In the callback send the html file to display.
- `npm install nodemon -g` to watch file and restart server automatically. From termical call `nodemon`.
- With Express:
    - We have certain middlewares that run one after another. We can create custom middlewares too, basically a function that can handle request, response and calls next() to run the next middleware.
    - Set up certain routes, ofcourse also the `get /` route. listen to port and export the app. See code for details.
    - We can have static html files and show express the path. Then localhost/thathtmlfile.html will load it directly.
- Template Engine PUG:
    - With a template engine we can load pages through server to the client. PUG(jade) can be used. `npm install pug --save`. In js, `app.set('set engine', 'pug')` to use it.
    - In a folder called views, we save our .pug files. And from the routes we call `res.render('index')` to render index.pug.
    - html2jade site to fo from html to pug/jade syntax. Indents are wither space or tab. Mixtures give error.
    - We can send data to pug file from the res.render() function and use then with `#{varName}`. 
    - We can use loops and conditionals in pug too.
    - Use `include includes/head.pug` to reuse html codes.
- Template Engine EJS:
    - `npm install ejs --save`
    - `app.set('set engine', 'ejs')`
    - Wont pick pickup views file autmatically, so set that path as well `app.set('views', path.join(__dirname, 'views'))`.
    - In views folder, create your index.ejs file, put your html there, similar like before, res.render(filename, params) and access those params in the .ejs file by <%= param %>. Use conditionals and all etc too <% if (someThing){ %>.
- MongoDB (details covered later in the course)
    - Mongo executable from the bin folder is run
    - We don't even have to create database or anything, it can be created throug the application, if it doesnt find the dabase or collection we specify it's gonna create it automatically.
    - In the project `npm install mongojs --save`.
    - In app.js
        ```javascript
        const MongoClient = require('mongodb').MongoClient;
        const url = 'mongodb://localhost:27017/myproject';
        MongoClient.connect(url, function(err, db){
            if(err){
                return console.dir(err);
            }
            console.log('Connected to mongodb');
        });
        ```
        Within this function, after connection has been established, you can set and get stuff in/out of the database.
- **Login Project**:
    - express, ejs, mongojs, express-messages, express-validator (see github docs), express-session (see github docs), connect-flash, passport, passport-local, body-parser, bcryptjs, bootstrap (can be installed with npm too), nodemon
    - In package.json, in scripts add `"start" : :nodemon"`. Now you can start your app with `npm start`.
    - We create a localstrategy of the passport which checks username and password from database. passport uses this localstrategy and performs authentication of user login.
    - For registering, the form values are taken an inserted in db simply.
    - To keep the login information accessible after successful login, we need to serialize, deserialize using passport.

### 2. Meteor.js
- **Full stack** js framework, for both front and back end. Both web and mobile applications.
- Meteor uses mongodb in the backend.
- You can install packages from atmosphere that are written specifically for meteor with `meteor add pkg` or also use npm packages by `meteor npm install pkg`.
- Meteor supports 3 UI rendering libraries: Blaze, React, Angular.
- Some built-in user-accounts systems are available.
- Meteor offers testing:
    - Unit testing: testing modules separately
    - Integration testing: testing modules together
    - Acceptance testing: testing browser button functionality etc
    - Load testing: test how app handles load
- Install meteor, check `meteor --version`.
- Create a project with `meteor create project_name`. cd into project_name folder, run `meteor`. that will open up your project. In browser go to `localhost:3000`.
- We will work on the client and server folder. 
- In html files, we can define templates and use them.
- We basically create functions in main.js inside of template_name.helpers(), and we can use those funtion names in the html to get values.
- With a folder outside the server and client folder, it will be accessible to both the server and the client.
- With `meteor mongo` in shell, you can access the database. Also use it from the browser console, it's accessible both server and client as we created the file as such.
- `meteor remove insecure` and now you cant't access db directly from client, that has to be done by the server on clients request.
- By default meteor has autopublish which allows any collection to be published anywhere. Run `meteor remove autopublish`. Publish a db from server, subscribe to it from client side.
- To style with bootstrap use `meteor add twbs:bootstrap`. It will be automatically in effect, we don't have to link to it or anything. 

### 3. Angular
- Client side framework (so its actually front-end but taught in the backend section of the course for relevance).
- Used often with Single Page Applications (SPA).
- Components in Angular divide the code into reusable chunks, make it easier to read, and makes it easy for multiple developers to collaborate.
- It has components, a class for that component, and those are accessed from html by tag name of the components selector. Html is put in the template part of the component.
- It uses Typescript which is a typed superset of javascript that compiles down to javascript.
- Create app from scratch:
    - Have `nodejs`, `npm` the install `Angular`. See angular docs to replace package.json contents, which you created by `npm init`. You can start your application by `npm start`.
    - Also create tsconfig.json, typings.json, system.config.js. See docs. Btw, all these can be created with angular quick start.
    - Then do `npm install`. 
- Quick Start: 
    - Clone their github repo (see docs).
    - `npm install`, `npm start`.
- Instead of putting html in template string, use template url and link to html file.
- ngModel data binding, connects data in all places for a variable, like in a text input box, h1 tag etc.
- Services grab data from wherever, and components can use these data provided by the services. Add the service as a provider in the post service. Set it up as a promise to perform asynchronous data transfer.
- Use `jsonplaceholder.typicode.com` as a dev tool, it offers a json api to which we can make requests to.
- We can use observables to do asynchronous data streaming from services, and subscribe to those from components.

### 4. PHP
- Powerful open source server side programming language, executed on server then generates html to show on client side. Interpreted at runtime, no compiling. 
- Directly embedded in html using <?php ?>.
- XAMPP is a bundled software that bundles together php, mysql and apache server for use. Server parses the .php files.
- It has drivers to work with noSQL too. php is also multi-paradigm, so both functional and OOP.
- Installation:
    - Linux installation more suited for actual hosting:
        ```
        sudo apt-get update
        sudo apt-get install apache2 (check in localhost)
        sudo apt-get install php7.0 php-pear libapache2-mod-php7.0 php7.0-mysql
        sudo systemctl restart apache2
        sudo gedit /var/www/html/test.php (<?php echo 'Hello World'?>, and then check in localhost/test.php)
        sudo apt-get install mysql-server (put root password when asked)
        mysql -u root -p
        CREATE DATABASE testdb;
        SHOW DATABASES;
        exit
        ```
    - For development purposes just get xampp. In windows run xampp-control.exe as administrator. Click the red crosses of apache and mysql and turn 'em to green ticks, meaning they will now be installed as services and will run in the background. Start apache and mysql. Now localhost should show you xampp. You will have your htmls in xampp >> htdocs. Create your website folder here.
    - For Linux, download xampp, then 
        ```
        sudo chmod +x xampp-linux-1.8.3-installer.run
        sudo ./xampp-linux-1.8.3-installer.run
        ```
        - /opt/lampp/htdocs (put your web files here)
        -  sudo chmod -R a+rwx htdocs (from lampp folder)
        - In browser: http://localhost/phpmyadmin/
- PHP language:
    - Constant: `define('CONSTVAR', 'value'); echo CONSTVAR;`. Constants don't use dollar sign.
    - Variables always start with $ sign. `$user`.
    - String concat by a `.` like `$user.' has '.$num.' books.'`.
    - `$ara = Array('one', 'two', 'three')`
    - `$ara = ['one', 'two', 'three']`. Array append dynamically, `$ara[3]='newNumber'`.
    - Associative array: `$nums = Array('one' => 1, 'two' => 2)`
    - Looping for arrays: `foreach($item as $ara){}`
    - `var_dump($var)` will show the data type.
    - `date('Y/m/d')` or l, M, Y, 'h:i:sa' etc. Set timezone with `date_default_timezone_set('America/New_york')`.
    - `$d = strtotime('tomorrow')` or today , 11 January 2020. Then display with `date('Y-m-d', $d)`.
- PHP Super Globals
    - $_POST['fieldname'] and $_GET['fieldname'] are used to access variables from html to php.
    - To give get parameters, `header("Location: index.php?error=Please%20fill%20all")`.
    - `if():` and `endif;` and you don't have to use the curly braces. Similarly, `foreach():` and `endforeach;`.
    - To use cookies `setcookies($cookie_name, $cookie_val, time()+secs)`, third parameter is till when to make the cookie last. Access it with `$_COOKIES[$cookie_name]` and can be used across pages. Cookies are set in clients browser.
    - Session does the same kind of thing, except its on the server and not on the clients browser. Every page you are using session, you have to include `session_start();`. Then set with `$_SESSION['username']='myName'`. These can be used across pages. These will last until you close the browser.
    - `$_SERVER[PHP_SELF]` can be used to post to the same page.
    - Check with `isset(var)` and unset it with `unset(var)`.
    - To unset all session variables, `session_unset();` and you can `session_destroy();`.
- OOP: No need for explanation if a code snippet is all you need.
    ```php
	class Book{
		// Properties
		protected $price;
		protected $title;
		public static $store = 'My Store';

		public function __construct($title, $price){
			$this->title = $title;
			$this->price = $price;
			echo '<br>The class "',__CLASS__,'" was instantiated!<br>';
		}

		public function __destruct(){
			echo '<br>The class "',__CLASS__,'" was destructed!<br>';
		}

		public function __toString(){
			return $this->getTitle();
		}

		// Methods
		public function setTitle($title){
			$this->title = $title;
		}

		public function getTitle(){
			return $this->title;
		}

		public static function getStore(){
			return self::$store;
		}
	}

	class Magazine extends Book {
		public $month;
		public $year;

		// Constructor
		public function __construct($title, $price, $month, $year){
			$this->month = $month;
			$this->year = $year;

			parent::__construct($title, $price);
			echo '<br>The class "',__CLASS__,'" was instantiated!<br>';
		}

		public function getYear(){
			return $this->year;
		}
    }
    ```
    ```php
    include 'Book.php';

    echo Book::getStore();

	$book1 = new Book('My Book', 9.99);
	echo $book1->setTitle('My Book');
	echo $book1->getTitle();
    ```
- MySQL with PHP
    - Two main choices, mysqli and PDO. mysqli is barely faster, pdo is a little hard to learn but safe and supports lots of other data drivers, not just mysql.
    - `mysqli_connect()` to connect, `mysqli_connect_errorno()` to check connection and `mysqli_connect_error()` to show error.
    - `mysqli_query()` to give query and `mysqli_fetch_assoc()` to get the result as an associative array.
- **The OOP way**
    - Folder Structure: 
        - lib (has class files including Template class, Database class etc)
        - config (has config file, which has all the includes)
        - templates
            - inc (has the header, footer files)
            - other pages
        - index.php 
    - Create a class called **Template** that will take in a template file path to display and bunch of parameters along with it.
    - Now we create templates for all the files like first_page, about_page and pass in the path to these files along with the variables it will need and echo the template object from the index page. It will work kindof like a template engine.
    - Also have a config file that has all the includes you need for all files. So instead of bunch of includes, we include only the config file. Also has all the constants etc.
    - We can use autoloader, which will do the require_once only when the class is instantiated.
- ERROR:
    - Error Types: 
        - E_ERROR: Fatal errors, causes the script to terminate. Php understands the code, but it cant be done.
        - E_WARNING: Runtime error that doesn't cause the script to terminate. Missing includes, incorrect number of params etc.
        - E_PARSE: Compile time parse error. Typo in your code.
        - E_NOTICE: Runtime notice. Less severe warnings, could cause problems later.
    - In debug mode we wanna see all errors, but disable them in production. We can enable or disable in the code itself, or from the  `php.ini` file to apply it server wide.
    - Look for `display_errors` in php.ini file and `error_reporting` and more. Make sure `display_errors=On` is not commented out. Similarly log errors, startup errors, error reporting. 
    - To turn off error in certain page, `error_reporting(0);` or turn on all error, put `-1` or `E_ALL` even if off in php.ini. Other combinations, like `E_ALL & ~E_NOTICE` means all errors except notices.
    - We can set values to php,ini by `ini_set('display_errors', 'off')`
    - Generate errors: 
        - `trigger_error('This is a fatal error', E_USER_ERROR)`
        - `trigger_error('This is a notice', E_USER_NOTICE)`
        - `trigger_error('This is a warning', E_USER_WARNING)`
- DEBUG: Check values on the fly. 
    - print_r($arr)
    - var_dump($foo), gives type, values, type of every element in array 
    - PHP to console hack
        ```php
        function console_log($data){
            echo '<script>';
            echo 'console.log('.json_encode($data).')';
            echo '</script>';
        }
        $foo = [0,1,2,3,4];
        console_log($foo);
        ```
    - call `var_dump(debug_backtrace())` to know how you got there and dump of everything you encountered along the line.
- ```php
    try{
        throw new Exception('Fatal Error!');
    }
    catch(Exception $e){
		echo 'ERROR: '.$e->getFile().'(Line '.$e->getLine().'): '. $e->getMessage();
	}
  ```
- Check php config settings: `phpinfo();`. You can see the error settings here too, can't edit though. We can pass in INFO_GENERAL, INFO_VARIABLES, INFO_CONFIGURATIONS etc to view specific parts of the info page.

### 5. Ruby On Rails
- Ruby is a multi paradigm programming language with dynamic type system. Everything is considered as objects.
- RubyGems is the package manager for ruby. Bundler is used to manage and track gems. RubyGems and Bundler both come with RailsInstaller in windows.
- Rails is a server-side web application framework written in ruby. Uses the **MVC** design pattern. Model manages the data and logic, View is the output representation and Controller controls the flow of information between model and view.
- Check installation with `ruby -v`, `rails -v`, `gems -v`, `bundler -v`.
- Working with Rails
    - `rails new app_name` to create a new app, cd into Sites folder rails had created.
    - cd into your app folder and do `bundle install`.
    - `rails server` to start the app
    - `rails generate controller Pages` to create the Pages controller.
    - You can add method names which will also generate view files like this `rails generate controller Pages index about services`. It will also add the get routes.
    - Instead of all individual get routes we can do this `resources :controller_name`.
    - See all your routes from CLI by `rake routes`.
    - In routes.rb you set the routes for your controller methods. Controller method and views page name matches.
    - Dynamic data from controller methods can be used in respective views.
    - To avoid repetitive code create a `partials` folder and then render partial files in your desired places. 
- Rails DB:
    - Rails uses sqlite by default. We can easily change it.
    - No matter what database we are using, with database migration, most things are gonna remain the same.
    - We create models with `rails generate Post title:string body:text` and this creates a migration file and model file.
    - The migration is gonna create tables, to run this migration and create the table we do `rake db:migrate`.
- **Take aways**
    - Its good for super fast development and prototyping, much of the typical stuff are ready made. DB connections, queries nothing required, all happens from the code directly, like PUT updates and DELETE deletes etc.
    - It goes a little beyond the typical html and turns into something else completely on its own. Its own way to interact with DB, with forms etc. Which is fast but tricky to understand whats going on behind the scenes. If you are comfortable ignoring the backstage, you can go ahead.
    - Need to first understand the relationship between the various components of MVC, how they interact and work together.
    - Basically turns web development into a sort of high level language which has a lot of abstractions.

