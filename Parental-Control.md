If user access is disabled due to parental controls, responses will contain **401** status codes and should be handled with the authentication workflow described at:

Authentication

A response header of **X-Application-Error-Code** will contain **ParentalControl**. This will allow applications to display message if they choose to.