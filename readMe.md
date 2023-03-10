## To setup a new project using express
    - Create a directory
    - Get in that directory
    - Run 
        npm init

        - this qill asks you some questions regarding the proejct setup. Answers them and this will generate package.json file 
    - run 
        npm i express 
    - Create a file with any name you want and build express application 

### API Formatting 
    - All the response will be on json format
        - {
            result: <any>,
            status: <boolean>,
            msg: <string>,
            meta: <object | null | undefined>
        }

## CRUD Operation using REST
    - Create 
        - post method
    - Read
        - get method
    - Update 
        - put/patch
    - Delete
        - delete

e.g. 
    User 
    - Register User (Create Request)
    - Login/List/Detail Fetch (Read Request)
    - Edit user,Password change, Reset Password => Update Operation
    - Remove from system (Delete Operation)

    Brand 
    Category
    Product
    Stock 
    Order 
## MVC Pattern 
    - Model => DB 
    - View => Html/CSS(not required)
    - Controller => Logic 


### Response Codes
    - 200 =>  Success response 
    - 201 


    400 =>  Bad request /validation 
    401 =>  Unauthorized 
    403 =>  Access Denied
    404 =>  Resource not found 

    500 =>  Internal Server Error 
    502 =>  Bad Gateway
    503 =>  Service Unavailable


## Middlewares in Express
    route => Endpoint => (req, res) => {}


### Software design architecture 
- MVC pattern 
- Repository Design Pattern
- Factroy Design pattern
- Singleton Design Pattern


/app 
    - define  all the logical content 
    /controllers
        - to define all the actions that the routes need to perform based on methods 
        - process 
    /middlewares 
        - which needed to be executed before some action calls
    /models 
        - Data structure for the different modules, defined by the database 
    /services
        - the helpers that connects controller with model 
/config 
    - defines all the static configuration that the project needs to store 
/public 
    - all the static files/folders which the public is going to access in our project
/routes 
    - to map action with the url 


app.js 
    ---> routes/index.js
            ---> routes/module.routes.js
                    (optional) ----->app/middlewares/name.middleware.js
                        -----> app/controllers/module.controller.js
                                ----> app/services/module.service.js
                                        ----> app/models/module.model.js



DWRX

7654

admin 
usergroup 
other

AGO
777


Routes 
- Public Routes
    - can be access by anyone without login 

- Private Routes
    - needs login access

    Category CRUD Opeartion 
        - Create request 
            - only loggedin user

### Authentication and authorization 
    SMTP 
        => ISP depend 
        => Server port SMTP 

        Application =====> Third party Provider ====> Email send / Queue

## Data store 
- File store

- Database 


# Database 
-> Server which stores data in different format 
-> Relational DB and Non-relational 
-> Sql Database and NoSQL Databse


orders 
--------------
id   name           product         price       qty         amount      date
--------------------------------------------------------------------------------------------
1   Ram            iPhone 12       128000      1           128000      2023-02-21
--------------------------------------------------------------------------------------------
2   ram            iphone12        120000      1           120000      2023-02-21
--------------------------------------------------------------------------------------------
3   Ram             iPhone12        12800       1           128000      2023-02-22


users                                           products
--------------------------------------------    --------------------------------------------
id          name                                id      name            price 
--------------------------------------------    --------------------------------------------
1           Ram Bd.                             1       iPhone 12       120000
--------------------------------------------    --------------------------------------------
2           Ram pd.

orders
----------------------------------------------------------------------------------------
id      user_id     product_id         qty              amount              date 
----------------------------------------------------------------------------------------
1       1           1                   1               120000              2023-02-21
----------------------------------------------------------------------------------------
2       1           1                   1               120000              2023-02-21
----------------------------------------------------------------------------------------
3       2           1                   1               120000              2023-02-22


## Setup Mongodb
- protocol
- host 
- port 
- user 
- password 
- db 

protocol://user:pwd@host:port/dbName?options
e.g. 
    mongodb://127.0.0.1:27017/

### CRUD Operation 
    - Create 
        - insertOne(data)
            where data is a json/js object
        - insertMany(data)
            where data is an array of json/js Object
    - Read
        - find(filter, projection)
        - findOne(filter, projection)
    - Update
        - updateOne(filter, update, options)
        - updateMany(filter, update, options)
    - Delete
        - deleteOne(filter)
        - deleteMany(filter)

    Mongo used JSON based data structure

#### Filter operation 
    - json content 
    e.g 
        users => all the users address => Kathmandu
        db.users.find({
            address: "Kathmandu"
        });

        1. {key: value, key1: value1}
        key = "value" and key1 = "value1"
        
        2. {
            $or: [
                {key: "value"},
                {key: "value2"}
            ]
        }
        => key= "value" OR key = "value2"

        3. {
            $gt: number
        },
        {
            $gte: number
        }
        $lt, $lte, $in, $nin, $ne

        {key: "value"}
        {$ne: {"key": "value"}}

        // key != "value"

        {$gte: {key: value}}
        =>
        key >= "value"

        {
            role: ["admin",'user']
        }

        db.table.find({
            role: {
                $in: []
            }
        })


{
    $operator: expression
}

{
    key: {
        $operator: expression
    }
}


[
  {
    $lookup:
      {
        from: "users",
        localField: "user_id",
        foreignField: "_id",
        as: "user",
      },
  }
]

// to run aggregation: 
db.collection_name.aggregate([pipeline])


// SELECT fields


{
    $set: update
}

dbeaver

## Mongodb Core Driver


users
id      name            role        create
--------------------------------------------------------------------
1       Ram             1              
--------------------------------------------------------------------
2       Shyam           2           1
--------------------------------------------------------------------
3       Hari            2           1


roles 
------------------
id          name
------------------
1           Admin
------------------
2           Customer



Role based permission 

// Ecommerce 
- Auth and Authorization
- Banner
- Brands
- Category Feature 
- Product Feature 
- User Features 
- Order Feature 
- Personilazation 
- Tracking
- Paynment Integraion 
- Feedback/reviews
- Offer / coupons 


CMS Project 
Web feature 
User Feature 

Permission Rule 
// admin, seller, customer 
-> For admin 
    all access 
        except cannot create order 
-> For Seller 
    - A seller can register a product
    - A seller can view his/her only order 
    - seller cannot create order 
-> For Customer 
    - A customer can create Order
    - Customer can view his/her order