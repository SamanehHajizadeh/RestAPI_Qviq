Download code Or just clone it from : https://github.com/SamanehHajizadeh/RestAPI_Qviq
Go to project path in terminal and run: mvn spring-boot:run

Follow as below:
In the postman or browser send these Requests URL :

1. return "Hello World!" with status 200 on GET to /
 * http://localhost:8080/
 ------------------------------------------------------------------------
 2. Create a @Repository with
 getLog(int logId) and
 addMessage(String name, int logId, String info) methods that maps to an internal data object. Each info that gets added to a log should also get  a timestamp added to it. The "name" field is intended to identify the submitting party.
------------------------------------------------------------------------
  3. Add rest methods for the functionality described in step 2.

  * http://localhost:8080/all
  * http://localhost:8080/getLog/1
  * http://localhost:8080/addMessage?name=samane&logId=10&info=First_test

  * GET: getting all messages
    http://localhost:8080/all
  * GET: getting specific message via id
    http://localhost:8080/getLog/1
  * PUT: For changing content of message in Info Object:
    http://localhost:8080/addMessage?name=samane&logId=1&message=mnbvcxeffsf****
  * POST: For  adding a new OBJ:
    http://localhost:8080/NewMessage
        {"name": "Bob",  "messageContent": "messageContent B ", "date": "2021-09-03T07:32:30.000+0000" }
  -----------------------------------------------------------------------------
  4. Make sure your solution so far is thread safe, if it is not already.

 Send those req in the same time
  http://localhost:8080/addMessage?name=samane&logId=10&message=First_test
  http://localhost:8080/addMessage?name=samane&logId=10&message=First_test
  --------------------------------------------------------------------------------
  5. Add one or more integration tests using bash/sh, curl, and jq. Use alternate or additional tools as you see fit. See if you can test for thread safety.

  RUN:
      *HttpRequestTest
      *CrulTest
      *MessageLogsController_IT
      *MessageLogsControllerTest
Note: For CRUL test please check our path, if U use Windows. Some guide as hard code is in CrulTest, otherwise it's ok :)
-----------------------------------------------------------------------
6. Add the possibility to configure a maxAge for returned messages.
Any messages older than maxAge should not be returned.
Add a rest method under /set_max_age that takes an integer describing the number of seconds a message should be available.

Insert your prefer MaxAge in application.properties

* GET: getting All messages Less Than specific Age(in_second):
    http://localhost:8080/set_max_age/71914430
* GET: getting age of specific message:
    http://localhost:8080/max_age_message/1
------------------------------------------------------------------------------------
7. Change the behaviour of the endpoint on / described in step 1 to instead return some json describing the state of the service.
The data returned should include at least
_the current number of stored logs, : * /all
_the maxAge limit,
_the total number of messages,
_the average number of messages per log.


In LogsController.java comment First methode @GetMapping(value = "/")  and uncomment last methode @GetMapping(value = "/")
--------------------------------------------------------------------------------------
8. Update your integration tests to cover the functionality described in step 7.

*In MessageLogsController_IT uncomment last Test
-----------------------------------------------------------------------------------------
9. Document the service in a README.md. The doc should describe how to run the service and the integration tests. The rest API can be documented here too.
--------------------------------------------------------------------------------------------------
extra credit:
set up a spring cron job to remove messages older than maxAge.
Set it to run every minute by default.
It should be possible to set an alternate interval by
passing a command line argument when starting the service.
