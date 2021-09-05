# Keycloak Example

This is a simple example of using keycloak to build an authentication system for a python flask application


# How to run?

git clone this repo

To start keycloak service
```
./run_keycloak.sh
```

Keycloak server should be visible at http://localhost:8080/auth/admin

To start flask server, start another terminal
```
cd api
python -m venv venv
source venv/bin/activate
python -m pip install -r requirements.txt
cd ..
./run_api_server.sh
```

Python flask server should be visible at `http://localhost:5000/`


# How to enable authentication?

Visit keycloak at http://localhost:8080/auth/admin
Enter the username and password from `./run_keycloak.sh`
You should now be able to see the realm `Master`.

![Screen Shot 2021-09-04 at 9 48 31 PM](https://user-images.githubusercontent.com/3619841/132112231-df631926-640d-4035-87e0-976483ee8133.png)

Create a new realm for your app called `hello-world` and hit `Create`
![Screen Shot 2021-09-04 at 9 51 05 PM](https://user-images.githubusercontent.com/3619841/132112266-3523a65c-c392-40ce-a072-a32480a74c01.png)

Enable `User Registration` and `Email as username`

<img width="979" alt="Screen Shot 2021-09-04 at 10 05 47 PM" src="https://user-images.githubusercontent.com/3619841/132112540-69a04a57-3fe0-4d3d-81be-b36c8364e64f.png">


In this new realm, create a new client with the name `hello-world-app`
![Screen Shot 2021-09-04 at 9 51 54 PM](https://user-images.githubusercontent.com/3619841/132112287-3e3cef44-db36-4ab2-9fcc-c37d2b697566.png)

![Screen Shot 2021-09-04 at 9 53 00 PM](https://user-images.githubusercontent.com/3619841/132112294-0fdc12c5-5ae8-4134-99e3-037dbf72a80d.png)


Make access type `confidential` for this client

![Screen Shot 2021-09-04 at 9 53 45 PM](https://user-images.githubusercontent.com/3619841/132112318-b8208659-646c-4b91-805c-1e53f67b82a5.png)


Set `Root URL`, `Valid Redirect URIs` and `Web Origins` to appropriate urls


![Screen Shot 2021-09-04 at 10 02 49 PM](https://user-images.githubusercontent.com/3619841/132112491-f9507204-af87-4d69-bc97-c0e44553842d.png)




Don't forget to click `Save` at the bottom

Get the client id and secret for `hello-world-app`. The client id is exactly the name of the client `hello-world-app`. The client secret is generated as shown in the screenshot below.

![Screen Shot 2021-09-04 at 9 57 22 PM](https://user-images.githubusercontent.com/3619841/132112357-fa2f61eb-9c2f-4d10-a5b5-834cebde3466.png)

Open the file `client_secrets.json` in an editor. Insert the client id and secret into this file.

![Screen Shot 2021-09-04 at 9 59 00 PM](https://user-images.githubusercontent.com/3619841/132112392-9cf88672-9e87-47de-96bb-3788d4282f75.png)


Rerun `./run_api_server.sh`. Now visit `localhost:5000` and click on `Log in`

<img width="508" alt="Screen Shot 2021-09-04 at 10 01 34 PM" src="https://user-images.githubusercontent.com/3619841/132112499-9c55e3bf-003d-41a9-84d0-39865ae64295.png">


You should now be able to register and user and log in with that user

<img width="960" alt="Screen Shot 2021-09-04 at 10 07 16 PM" src="https://user-images.githubusercontent.com/3619841/132112556-7f638eff-da89-4f03-95d9-e546cf43a732.png">





