# Create HubDB Table Row and Publish Table (POST)

A serverless function that creates a [HubDB](https://developers.hubspot.com/docs/cms/features/hubdb) table row based on request body data, and publishes the HubDB table so this data is live. This endpoint accepts a POST request with some data, that is used in the function.

## Hitting the endpoint

The endpoint is executed with the POST request method, and requires sending JSON data in the request body:

```
POST /_hcms/api/create-hubdb-row-publish-table
{
    "name": "Brian",
    "amount": 100
}
```

In vanilla JavaScript, this might look like:

```
var data = {
    "name": "Will",
    "amount": 50
};

fetch("/_hcms/api/create-hubdb-row-publish-table", {
    method: "POST",
    body: JSON.stringify(data),
    headers: {
      'Content-Type': 'application/json'
    },
}).then(res => {
    console.log(res);
});
```

These values are then used in the function to create a HubDB table row with the submitted information.

## Configuration

This function relies on:

1. Creating a [secret](https://developers.hubspot.com/docs/cms/features/serverless-functions#secrets) named `API_KEY` with the HubSpot API key for the destination account.
2. Creating a HubDB table with the name `donations` that contains the columns: `name` (text), `amount` (number).

## Example use cases:

- Collect user submitted info to display on a page
