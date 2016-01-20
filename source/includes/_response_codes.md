# Response Codes

<aside class="notice">This error section is stored in a separate file in `includes/_errors.md`. Slate allows you to optionally separate out your docs into many files...just save them to the `includes` folder and add them to the top of your `index.md`'s frontmatter. Files are included in the order listed.</aside>

The Vin65 Market Services API uses the following error codes:

Code       | Message               | Description
---------- | --------------------- | -----------
200        | ok                    | The request completed normally
201        | created               | The resource was created
204        | no content            | The request did not return any content. Normally used during a successful update
401        | unauthorized          | Your authentication credentials are incorrect or your authorization token is invalid
404        | not found             | The specified resource could not be found
500        | internal server error | We had a problem with our server
