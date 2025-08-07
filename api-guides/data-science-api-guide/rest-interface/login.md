# Login

`POST insightmaker/ds/login`

#### Body

`{"username": username, "password": password}`

* **Username**: The Active Directory username.
* **Password**: InsightMaker DS API Token as configured in Control Hub.

#### Response

API authorisation token. This token should be added to all other requests as an Authorisation header with the value “Bearer xxxx”, where xxxx is the token value.
