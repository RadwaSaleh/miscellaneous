There are different Grant Types/flows to gain access token in OAuth 2.0, the most common flows are:

> Authorization Code

> Client Credentials (Client Id and Client Secret)

> Password (Resource Owner Password)

Authorization Code - Postman

- I hate this flow so much
![auth-code-flow](https://github.com/RadwaSaleh/miscellaneous/blob/main/assets/auth-sequence-auth-code.png)
- I have used it in: Postman, Cypress(javascript) and RestAssured(Java)
- Using Postman is easy pease if you have the required information
- import [this request](https://github.com/RadwaSaleh/miscellaneous/blob/main/assets/postman-oauth2-keycloak.postman_collection.json) in postman to check the needed fields
- Also check out [this post](https://paulbares.medium.com/quick-tip-oauth2-with-keycloak-and-postman-cc7211b693a5)


Authorization Code - Cypress(Javascript)

- I'll upload a POC to clarify how to get the access token using a custom command in Cypress that simulates the login form submission 


Authorization Code - Java

- I won't even try
- Authorization Code flow requires browser to initiate login
- This solution is possible by integrating Selenium Webdriver.
- There are multiple solutions using only RestAssured to gain the code and the access token on two steps but it never worked for me

Client Credentials - Java

- Grant Type is client_credentials
- This flow requires the client to NOT be a public client in keycloak
- This flow is only possible if the "Service Accounts Enabled" option is enabled in keycloak
- Public clients are not allowed to retrieve service accounts

Password - Java

- The Password grant type is only possible when the client has got the "Direct Access Grants Enabled" option enabled
- I need to read more about security risks (if any) of enabling this option
- I have enabled it only for Staging environement
- Here's a code snippet using RestAssured 
 ```
  /**
   * Authenticate accounts against Keycloak service using Password Grant Type flow.
   *
   * @param username is the resource account username
   * @param password is the resource account password
   * @return accessToken string value
   *
   */
  public String keycloakAuthenticate(String username, String password) {

    return given()
        .contentType("application/x-www-form-urlencoded")
        .formParam("grant_type", "password")
        .formParam("username", username)
        .formParam("password", password)
        .formParam("client_id", clientId)
        .when()
        .post(accessTokenURL)
        .then().log().all()
        .extract()
        .path("access_token");
  }
}
```
