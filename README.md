# fmOAuth

[![Join the chat at https://gitter.im/frudens-com/fmoauth](https://badges.gitter.im/frudens-com/fmoauth.svg)](https://gitter.im/frudens-com/fmoauth?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

fmOAuth is a solution for accessing APIs such as Google and Microsoft from FileMaker, and it consists only of scripts.

NOTE: I think that it is better to implement it as "2-legged OAuth" or "2LO" than to call the API from FileMaker client.

[Using OAuth 2.0 for Server to Server Applications](https://developers.google.com/identity/protocols/OAuth2ServiceAccount)

# Usage

## Google Cloud Platform

* Log in to GCP with Gsuite's Google Account.
* Create a Project and set the OAuth consent screen.
* Create OAuth 2.0 client ID.
* `Client ID`, `Client secret` in FileMaker.

## FileMaker(fmOAuth.fmp12)

* Open `fmOAuth.fmp12`.
* Click the `RELOGIN` button.
* Re-login ( account:`admin` | password:`admin` )
* Open the `Script Workspace`.
* Open the script ( `0498.Get myApp ( kind )` ) and enter Client ID, Client secret, scope etc.

## FileMaker(mysolution.fmp12)

* Open `mysolution.fmp12 `.
* Open the `Script Workspace`.
* Run the script `0013.get refreshToken and Gmail getProfile`

## Demo

* This video is a demo that calls getProfile of Gmail API.

[![demo](https://user-images.githubusercontent.com/31458364/46595590-12ccdb80-cb14-11e8-96b2-2f484fe4c3ae.png)](https://www.youtube.com/watch?v=TH_XAoOtnr4)

# Release History

## v0.0.4

### Bug Fixes:

* Fixed the script.
* Deleted unnecessary layouts, scripts and custom functions.

## v0.0.3

### Bug Fixes:

* Update the Google Client ID of fmOAuth set in fmoauth.fmp12
* Fix UI of fmoauth.fmp12

# Author

frudens Inc. <https://frudens.com>

# License

This software is distributed under the
[Apache License, Version 2.0](http://www.apache.org/licenses/LICENSE-2.0),
see LICENSE.txt for more information.
