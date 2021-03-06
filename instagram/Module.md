Connects to Instagram from Ballerina.

# Module Overview

The Instagram connector allows you to get users, posts details, search media, comments, tags and get information about
locations through the Instagram REST API. It handles OAuth 2.0 authentication.

**User Operations**

The `chanakal/instagram` module contains operations to get the Instagram account details.

## Compatibility
|                          |    Version     |
|:------------------------:|:--------------:|
| Ballerina Language       | 0.983.0        |
| Instagram API            | v1             |

## Sample
First, import the `chanakal/instagram` module into the Ballerina project.
```ballerina
import chanakal/instagram;
```

**Obtaining Tokens to Run the Sample**

1. Visit [Instagram](https://www.instagram.com/developer/) and create a Instagram Developer Account.
2. Create a connected app and obtain the following credentials:
- Access Token

You can now enter the credentials in the Instagram endpoint configuration.
```ballerina
endpoint instagram:Client instagramEP {
   clientConfig:{
       auth:{
           scheme:http:OAUTH2,
           accessToken:"<your_access_token>"
       }
   }
};
```
The `getOwnerInfo` function returns the information about the owner of the access_token.
```ballerina
    var details = instagramClient->getOwnerInfo();
    match details {
        instagram:Account account => io:println(account);
        instagram:InstagramError instagramError => test:assertFail(msg = instagramError.message);
    }
```
The `getMostRecentMedia` function returns the most recent media published by the owner of the access_token.
```ballerina
    var details = instagramClient->getMostRecentMedia();
    match details {
        json response => io:println(response);
        instagram:InstagramError instagramError => test:assertFail(msg = instagramError.message);
    }
```