# fmOAuth

fmOAuth is a solution for accessing APIs such as Google and Microsoft from FileMaker, and it consists only of scripts.

NOTE: I think that it is better to implement it as "2-legged OAuth" or "2LO" than to call the API from FileMaker client.

[Using OAuth 2.0 for Server to Server Applications](https://developers.google.com/identity/protocols/OAuth2ServiceAccount)

# Intro

* Add the `fmoauth.fmp12` file to your solution` External Data Sources`.
* Create a test script for your solution.
* Specify the script in the `fmoauth.fmp12` file in the` Perform Script` of the script step and set the arguments as well.
* Get the result of API with `Get (ScriptResult)` of script step.
* NOTE: FileMaker 16 or higher is required.

## Demo

* This is a demonstration to insert FileMaker records into Google Spreadsheet.

[![demo](https://user-images.githubusercontent.com/31458364/46208019-4b2a2800-c364-11e8-81b0-6928983ed90e.png)](https://www.youtube.com/watch?v=EKo8YYYbWkQ)

# Usage Example (I recommend you to look the sample file.)

## Add the External Data Sources.

* Add the `fmoauth.fmp12` file to your solution` External Data Sources`.

![usage1](https://user-images.githubusercontent.com/31458364/46208032-5d0bcb00-c364-11e8-8e5d-e17be76e7a0b.png)

## Create a script like the one below.

```
Set Variable [$param1; Value:JSONSetElement ( "" ; [ "scopeList" ; "https://mail.google.com/" ; JSONString ] )]

Perform Script ["0307.Get Refresh Token Google ( appId ; secret ; redirect ; scopeList )"  from file: "fmoauth"; Parameter: $param1]

Set Variable [$$refreshToken; Value:JSONGetElement ( Get ( ScriptResult ) ; "refresh_token" )]

Set Variable [$param2; Value:JSONSetElement ( "" ; [ "refresh_token" ; $$refreshToken ; JSONString ] )]

Perform Script ["0354.Gmail getProfile /gmail/v1/users/me/profile"  from file: "fmoauth"; Parameter: $param2]

Show Custom Dialog ["result"; Get ( ScriptResult )]
```

![usage2](https://user-images.githubusercontent.com/31458364/46208049-6bf27d80-c364-11e8-8cf7-c4edea501ea1.png)

## Run the script.

* I called the following API.
* [https://developers.google.com/gmail/api/v1/reference/users/getProfile](https://developers.google.com/gmail/api/v1/reference/users/getProfile)

![usage3](https://user-images.githubusercontent.com/31458364/46208062-744ab880-c364-11e8-8842-8a4c477130bd.png)

# Release History

## v0.0.3

### Bug Fixes:

* Update the Google Client ID of fmOAuth set in fmoauth.fmp12
* Fix UI of fmoauth.fmp12
* I deleted the development repository of fmoauth.fmp12, so I created it again from DDR ...

# Author

frudens Inc. <https://frudens.com>

# License

This software is distributed under the
[Apache License, Version 2.0](http://www.apache.org/licenses/LICENSE-2.0),
see LICENSE.txt for more information.
