# surveygizmo
Promise based Javascript client for the Survey Gizmo API

``npm install surveygizmo-client``

    var SurveyGizmo = require('surveygizmo-client');
    var sgizmo = new SurveyGizmo({
      username: 'xxxxx',
      password: 'xxxxxx',
      version: 'v4'
    });
    sgizmo.getResponses(surveyId,options).then(function(responses){
        console.log(responses);
    }).catch(function(err){
        console.log(err)
    });


Options :

  username: Survey Gizmo username (***required***)

  password : Survey Gizmo password (***required***)

  version : API Version (***optional***) Defaults to head

API
=======


***Examples***

Get two responses with a status complete and where question 5 has a value of 'Yes'

    sgizmo.getResponses(surveyId, {
        resultsperpage: 2,
        filter : [
            {field : 'status', operator : '=', value : 'complete'},
            {field: '[question(5)]', operator : '=', value: 'Yes'}
          ]
        }).then(function(res){
          console.log(res)
        });

Create a new question in a survey

    sgizmo.createQuestion(surveyId, pageId, {
        type : 'text',
        description : 'This is a description',
        title : 'Enter your name',
        after : '1',
        varname : 'name',
        shortname : 'short',
        properties : {
          disabled : false,
          hidden : false,
          exclude_number : true,
          hide_after_response: true,
          orientation : 'VERT'
        }
    }).then(function(res){
        console.log(res);
    });

Create a new Poll

    sgizmo.createSurvey({
        title : 'Test Poll',
        type : 'poll',
        status : 'launched',
        theme	: 63989,
        polloptions	: ['Red Sox', 'Yankees'],
        polltype : 'ranking',
        pollwidth: 600
    }).then(function(res){
         console.log(res);
    });



### Account Object

https://apihelp.alchemer.com/help/account-object

``getAccount()``

### Account Team Object
Available Options:

https://apihelp.alchemer.com/help/accountteams-object

``getTeams(options)``

``createTeam(options)``

``updateTeam(options)``

``deleteTeam(teamId)``


## Account User Object

Available Options:

https://apihelp.alchemer.com/help/accountuser-object


``getUsers(options)``

``createUser(options)``

``updateUser(userId,options)``

``getUser(userId)``

``deleteUser(userId)``

## Contact List Object

Available Options:

https://apihelp.alchemer.com/help/contactlist-object

``getContactLists(options)``

``getContactList(listId)``

``createContactList(options)``

``updateContactList(listId, options)``

## Survey Object

Available Options:


https://apihelp.alchemer.com/help/survey-object

``getSurveys(options)``

``getSurvey(surveyId)``

``createSurvey(options)``

``updateSurvey(surveyId, options)``

``deleteSurvey(surveyId)``


## Survey Page Sub-Object

Available Options:


https://apihelp.alchemer.com/help/surveypage-sub-object

``getPages(surveyId,options)``

``getPage(surveyId, pageId)``

``createPage(surveyId,options)``

``updatePage(surveyId,pageId,options)``

``deletePage(surveyId,pageId)``

## Survey Question Sub-Object

Available Options:

https://apihelp.alchemer.com/help/surveyquestion-sub-object

``getQuestions(surveyId)``

``getQuestion(surveyId, questionId)``

``createQuestion(surveyId,pageId,options)``

``updateQuestion(surveyId,pageId,questionId,options)``

``deleteQuestion(surveyId,pageId,questionId)``

## Survey Option Sub-Object

Available Options:


https://apihelp.alchemer.com/help/surveyoption-sub-object


``getOptions(surveyId,questionId)``

``getOption(surveyId, questionId, optionId)``

``createOption(surveyId,pageId,questionId,options)``

``updateOption(surveyId,pageId,questionId,optionId, options)``

``deleteQuestion(surveyId,pageId,questionId)``

## Survey Campaign Sub-Object

Available Options:


https://apihelp.alchemer.com/help/surveycampaign-sub-object

``getCampaigns(surveyId)``

``getCampaign(surveyId, campaignId)``

``createCampaign(surveyId,options)``

``updateCampaign(surveyId,campaignId,options)``

``deleteCampaign(surveyId,campaignId)``


## Contact Sub-Object

Available Options:

https://apihelp.alchemer.com/help/contact-sub-object

``getContacts(surveyId,campaignId)``

``getContact(surveyId,campaignId,contactId)``

``createContact(surveyId,campaignId,options)``

``updateContact(surveyId,campaignId,contactId,options)``

``deleteContact(surveyId,campaignId)``

## Email Message Sub-Object

Available Options:

https://apihelp.alchemer.com/help/emailmessage-sub-object

``getMessages(surveyId,campaignId)``

``getMessage(surveyId,campaignId,contactId,messageId)``

``createMessage(surveyId,campaignId,options)``

``updateMessage(surveyId,campaignId,messageId,options)``

``deleteMessage(surveyId,campaignId,messageId)``


## Survey Response Sub-Object

Available Options:

https://apihelp.alchemer.com/help/surveyresponse-sub-object

``getResponses(surveyId,options)``

``getResponse(surveyId,responseId)``

``createResponse(surveyId,options)``

``updateResponse(surveyId,responseId,options)``

``deleteResponse(surveyId,responseId)``


## Survey Statistic Sub-Object

Available Options:

https://apihelp.alchemer.com/help/surveystatistic-sub-object

``getStats(surveyId,options)``

## Survey Statistic Sub-Object

Available Options:

https://apihelp.alchemer.com/help/surveystatistic-sub-object

``getStats(surveyId,options)``

## Survey Report Sub-Object

Available Options:

https://apihelp.alchemer.com/help/surveyreport-sub-object

``getReports(surveyId,options)``

``getReport(surveyId,reportId)``

``updateReport(surveyId,reportId,options)``

``deleteReport(surveyId,reportId)``

## Tests

Make a json file named account.json with your username and password and put it in the test/fixtures directory. Optionally add a surveyId and reportId of an actual report to run tests that endpoint. There is no way to create reports through the API at this time, so using an existing report is necessary.


    {
      "username" : "xxxxxxx",
      "password" : "xxxxxxx",
      "reportId" : "2214722",
      "surveyId" : "537561"
    }

Run : ``npm test``
