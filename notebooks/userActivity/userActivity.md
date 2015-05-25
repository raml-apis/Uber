---
site: https://anypoint.mulesoft.com/apiplatform/popular/admin/#/organizations/52560d3f-c37a-409d-9887-79e0a9a9ecff/dashboard/apis/19622/versions/20942/portal/pages/34516/edit
apiNotebookVersion: 1.1.67
title: User activity
---

```javascript
load('https://github.com/chaijs/chai/releases/download/1.9.0/chai.js')
```

See http://chaijs.com/guide/styles/ for assertion styles

```javascript
assert = chai.assert
```

```javascript
useSandbox = window.confirm('Use Uber Sandbox?')
apiMode = useSandbox ? 'sandbox-api' : 'api'
```

```javascript
API.createClient('client', '#REF_TAG_DEFENITION_Uber user activity:',
{ 
  baseUriParameters: {  
    apiMode : apiMode
  } 
});
```

```javascript
clientId = prompt("Please, enter your Client ID")
clientSecret = prompt("Please, enter your Client Secret")
```

```javascript
API.authenticate(client,"oauth_2_0",{
  clientId: clientId,
  clientSecret: clientSecret
})
```

The User Activity endpoint returns a limited amount of data about a user's lifetime activity with Uber. The response will include pickup and dropoff times, the city the trips took place in, the distance of past requests, and information about which products were requested.

The history array in the response will have a maximum length based on the limit parameter. The response value count may exceed limit, therefore subsequent API requests may be necessary.

```javascript
historyResponse = client.history.get({
  "offset": "0",
  "limit": "5"
})
```

```javascript
assert.equal( historyResponse.status, 200 )
```