# Errors
The Timesheet API returns back a valid JSONAPI error object. Nearly all of the time the error will be a validation error when creating or updating a timesheet. An example of this is provided.

```json
{
  "errors": [{
    "status": 422,
    "source": {
      "pointer": "/data/attributes/added_at"
    },
    "detail": "Added at can't be blank"
  }, {
    "status": 422,
    "source": {
      "pointer": "/data/attributes/amount_complete"
    },
    "detail": "Amount complete can't be blank"
  }, {
    "status": 422,
    "source": {
      "pointer": "/data/attributes/item"
    },
    "detail": "Item can't be blank"
  }]
}
```

Error Code | Meaning
---------- | -------
422 | There was a problem with the data you provided. Check the error response
