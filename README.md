# Best Tacos
This project is a sample of how to develop a RESTful web application using the Python framework Flask along with implementing third-party OAuth authentication. You will then learn when to properly use the various HTTP methods available to you and how these methods relate to CRUD (create, read, update and delete) operations.

This app will allow you to store your favorite place to eat Tacos


## Requirements 
- This application was developed using python and the modules included in the file `requirements.txt` are mandatory.
```
itsdangerous==1.1.0
Flask_HTTPAuth==3.2.4
requests==2.21.0
Flask==1.0.2
passlib==1.7.1
httplib2==0.12.0
SQLAlchemy==1.2.15
google_api_python_client==1.7.7
```
- Python
- pip
- Port 5000 available (or change it in the app.py)

## Installation
1. Clone the repository 
```
$ git clone git@github.com:womeat/my-udacity-crud-project.git
```
2. cd into the directory `my-udacity-crud-project` and install the requirements
```
$ cd my-udacity-crud-project
$ sudo pip install -r requirements.txt
```

3. Create the database `best_tacos.db`
```
$ python database_setup.py
```
4. Add your valid credentials to use Google as authentication provider in the file `client_secret.json` 
```
{"web":
  {
    "client_id":"XXXXXXX",
    "client_secret":"XXXXXXX",
    "project_id":"mymenuapp",
    "auth_uri":"https://accounts.google.com/o/oauth2/auth",
    "token_uri":"https://www.googleapis.com/oauth2/v3/token",
    "auth_provider_x509_cert_url":"https://www.googleapis.com/oauth2/v1/certs",
    "javascript_origins":["http://localhost:5000"],
    "redirect_uris":["https://localhost:5000/callback","http://localhost:5000/callback"]
    }
  }
```
5. Add your valid credentials to use Facebook as authentication provider in the file `fb_client_secrets.json` 
```
{
  "web": {
    "app_id": "XXXXXXX",
    "app_secret": "XXXXXXX"
  }
}
```
6. Initialize the database with some sample data
```
$ python lotsoftacos.py
```

## Usage

1. Start the app
```
$ python app.py
```

2. Open your browser with the following url [http://localhost:5000](http://localhost:5000)

You can perform the following operations:
* Login
* Register for an account
* Create/Edit/Delete a Place
* Add/Edit/Delete tacos to a Place

## API

The following API endpoints are available and basic authentication is required
- Query places
`http://localhost:5000/places/JSON`
Example:
```
$ curl -u 'foobar@example.com:foobar' http://localhost:5000/places/JSON
{
  "Places": [
    {
      "id": 1,
      "name": "Metro Balderas 1",
      "rate": {
        "id": 2,
        "rate": 1
      }
    }
  ]
}
```
- Query a place
`http://localhost:5000/places/<place_id>/JSON`
Example:
```
$ curl -u 'foobar@example.com:foobar' http://localhost:5000/places/1/JSON
{
  "id": 1,
  "name": "Metro Balderas 1",
  "rate": {
    "id": 2,
    "rate": 1
  }
}
```
- Query tacos per place
`http://localhost:5000/places/<place_id>/tacos/JSON`
Example:
```
$ curl -u 'foobar@example.com:foobar' http://localhost:5000/places/1/tacos/JSON
{
  "Tacos": [
    {
      "description": "Marinated pork with corn tortilla",
      "id": 1,
      "meatType": {
        "id": 1,
        "name": "Pork"
      },
      "name": "Pastor",
      "picture": "http://zonaguadalajara.com/wp-content/uploads/2015/10/Tacos-al-Pastor-Jalisco.jpg",
      "price": "6.50"
    }
  ]
}
```