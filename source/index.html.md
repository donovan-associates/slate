---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

toc_footers:
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: false
---

# Introduction

This is a basic RESTFUL API for office staff members to save their timesheets.

# Timesheets

## Get timesheets for a user
```shell
curl "http://example.com/timesheets?uid=1&date=2018-01-01"
```

> The above command returns an array of standard JSONAPI objects like this:

```json
[{
  "data": {
    "id": 1,
    "type": "timesheet",
    "attributes": {
      "added_at": "2018-01-01",
      "amount_complete": 0,
      "item": "/2",
      "job": "332211",
      "minutes": 10,
      "notes": "another random note",
      "task": "Drafting",
      "user_uid": "1"
    }
  }
}, {
  "data": {
    "id": 2,
    "type": "timesheet",
    "attributes": {
      "added_at": "2018-01-01",
      "amount_complete": 0,
      "item": "/1",
      "job": "112233",
      "minutes": 10,
      "notes": "random note",
      "task": "Drafting",
      "user_uid": "1"
    }
  }
}]
```

This endpoint retrieves all timesheets on a date by a user.

### HTTP Request

`GET http://example.com/timesheets`

### Query Parameters

Parameter | Description
--------- | -----------
uid | The user id you want to retrieve timesheets for
date | The date the timesheets were added in iso8601 format

<aside class="info">
No authentication has been setup as yet.
</aside>

## Create / update a timesheet

```shell
curl "http://example.com/timesheets"
```

> The above command returns a JSONAPI object like this:

```json
{
  "data": {
    "id": 2,
    "type": "timesheet",
    "attributes": {
      "added_at": "2018-01-01",
      "amount_complete": 0,
      "item": "/1",
      "job": "112233",
      "minutes": 10,
      "notes": "random note",
      "task": "Drafting",
      "user_uid": "1"
    }
  }
}
```

This endpoint will create a timesheet, or update an existing one. If it finds a timesheet that matches the same date, job, item, task and user then it will update it, otherwise it will create a new timesheet.

### HTTP Request

`POST http://example.com/timesheets`

### URL Parameters
        added_at: '02/07/2018',
        amount_complete: 0,
        item: '/2',
        job: '332211',
        entered_time: '10',
        notes: 'another random note',
        task: 'Drafting',
        user_uid: '2',

Parameter | Description
--------- | -----------
added_at | The date the timesheet is for in iso8601 format
amount_complete | Percentage as an integer between 0 and 100
item | Item identifier
job | The job identifier
entered_time | The time worked. Can be any one of `52`, `52m`, `1:52`, `1h 52m`
notes | Notes explaining the work done for this task
task | A string representing the task performed
user_uid | The id for the staff member
