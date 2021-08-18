# spring-jwt
Spring Security with JWT Access and Refresh Token Project

Application Testing:
1. Run SpringJwtApplication.java file as a spring boot project.

2. First we need to register a user, open Postman and send a POST request on localhost:8080/register to register a user.
The database in SQL server will automatically created if it's not present and you'll have to register a new user every time you run the project because we've set ddl.auto as create-drop, you can change that according to your preference.

Ex: 
{
    "username":"nikshay",
    "password":"inexture",
    "role":"ROLE_ADMIN"
}

Enter this in body as JSON format.

3.To get the user authenticated we need to pass the credentials in postman as a POST request on localhost:8080/authenticate to get the access token for that particular user.

4. Select body tab and enter your credentials in this manner as JSON 

Ex :
{
    "username":"admin",
    "password":"admin"
}

5.You will get an access token which will look something like : eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJtZXJsaW4iLCJpc1VzZXIiOnRydWUsImV4cCI6MTYyOTI4NjI2NSwiaWF0IjoxNjI5MjgxMDY1fQ.GK_FV0pAQpjolY0bhazWS1ryABsQX3vUuph8EqHKs4icZvkeBnKF-VBoKurB4k02orRYtlritkj8rRY4H-4kQg

6. Use this token to call APIs :
7. Create a GET request and enter localhost:8080/hellouser to call this API which is accessible by both User and Admin.

Set the authorization type to Bearer Token and enter the access token which we generated above.

OUTPUT will look like : Hello User

8.Create another GET request and enter localhost:8080/helloadmin to call this API which is only accessible by ADMIN.

9.This access token is accessible for a particular time limit which is defined in the appliocaion.properties file.

10.By now we've done the testing of Access Token, to test Refresh Token we need to set app.expTime as 0.

11.Generate a new access token (follow step 4) and use it to generate a refresh token.

12.To generate refresh token we need make a GET request on localhost:8080/refreshtoken.

13.Enter the generated access token (which is expired because we have set the timer = 0)

Set the authorization type to Bearer Token and enter the expired access token.

OUTPUT : eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJtZXJsaW4iLCJpc1VzZXIiOnRydWUsImV4cCI6MTYyOTEwODI3NSwiaWF0IjoxNjI5MDk5Mjc1fQ.T2u4wWqz7NRiPnbX5xIm738YcOeG61Q2Hr2W62oRoaKPl21YEeUq7ZFvTQQF5BR-B4vK6F7JvwIgHb6_6dAutw

Now we've gotten the refresh token and use to call the APIs just like we did for access token (follow step 7).

14.You've successfully tested the application, generated access and refresh token to make authorized API calls.


