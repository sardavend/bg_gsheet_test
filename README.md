# bg_gsheet_test
bigpictures's application assignment

## Introduction

Hello Big Pictures team, this document is in part documentation of the assignment's resolution and in part my feedback about the SDK,  I hope it helps to improve the product :D

## About the assigment
5 of 6 :s functionalities were implemented, I refactor the code and added the following improvements:

- Alerts if there are some errors in the custom variables spreesheetId and range (validated by the gapi sdk), see:
```javascript 
GSheetApp.prototype.showMessage()
```
- Render a Message  instead of the empty data table, see:
```javascript
GSheetApp.prototype.tryAgain()
```
- Separate the rendering and configuration of the library from the retrieve of the data, see:
```javascript
GSheetApp.prototype.getData()
GSheetApp.prototype.configureAndRenderTable()
```

- Added a dynamic range generator for Server Side processing with sheets gapi, see:
```javascript
/***
 * for EX: if the variable range= Sheet1!C3:F504( 501 rows)
 * this function returns a list of Ranges(with 100 rows each) to be used 
 * from a custom pagination fuction:
 * [Sheet1!C3:F103,Sheet1!C103:F203,Sheet1!C203:F303,Sheet1!C303:F403,Sheet1!C403:F504]
 */
GSheetApp.prototype.getRanges()
```
On the other hand, the assigemnt works great showing the current state of the SDK, but sometimes(maybe its just me) it feels more like an Datatable's assigment, than a Big Pictures's assigment(I know this part was optional but there is a lot of references to that library) :D

It also feels that we are trying to recreate the Google Sheets functionality with Datatables, maybe the assigment should be a little different, how about implementing a alternative data visualitation(differente than a chart) of the data grid?

## About the SDK

My experience using the (MVP)SKD overall was pretty good, the following are some suggestion that I thinks it can help to improve the SDK (and I am pretty sure this is already included in your roadmap of future features :D)  

- Extend Big Pictures's Google Sheets api  a little in order to reduce some boilerplate 
- Support for vue and react (to attract more developers to the plaform)
- the Template creation UI works really well(/views/{ID}/edit/), on the other side as a dev user of the platform the app creation UI (/custom_app_templates/new) it is more vertical oriented(maybe more usable from a mobile device?) and sometimes it does not fit so well on a laptop or computer screen( horizontal)


## Some Issues
Maybe it is my user account but it was not possible to edit my onw View templates, the following are some error I found:
- When editing an image 
```
{"message":"server_error","type":"Pundit::NotAuthorizedError","detail":"not allowed to update? this #\u003cAppContainer id: 379, title: \"\", view_id: 259, position: nil, app_type: \"ImageApp\", app_id: 91, created_at: \"2020-04-17 01:45:02\", updated_at: \"2020-04-17 01:45:02\", comments_enabled: false, row: 2, width: 6, order_in_row: 1, show_borders: true\u003e"}
```
-  after pressing F5 when creating the view
```
Request URL: 
https://pl-big-pictures-staging.herokuapp.com/api/v1/app_containers/378
Payload 
app_container :
{
title: "<h1 class="ql-align-center">The F**ing Sheet</h1>"
row: 1
width: 6
order_in_row: 1
comments_enabled: false
show_borders: true
app: {content: "<p>This is the Fu**g Sheet</p>"}
content: "<p>This is the Fu**g Sheet</p>"
app_type: "StylizedTextApp"
}

response: 
500
{message: "server_error", type: "Pundit::NotAuthorizedError",…}
message: "server_error"
type: "Pundit::NotAuthorizedError"
detail: "not allowed to update? this #<AppContainer id: 378, title: "<h1 class=\"ql-align-center\">The F**ing Sheet</h1>", view_id: 259, position: nil, app_type: "StylizedTextApp", app_id: 188, created_at: "2020-04-17 01:42:41", updated_at: "2020-04-17 01:42:41", comments_enabled: true, row: 1, width: 6, order_in_row: 1, show_borders: true>"
```


3-> after deleting an app in the view and trying to add a new element(the editor does not delete the app at all, if f5 the removed element(in this case the app) still is there)
```
{"message":"invalid_attributes","errors":{"width":["No cabe en la fila"]}}
```




