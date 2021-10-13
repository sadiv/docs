# Postman collection

To test and debug requests to the Green API it is recommended to use [Green API - Postman Collection](https://github.com/green-api/green-api-postman-collection)

[Postman](https://www.getpostman.com/) - a widespread tool for API testing and development. To make it easier for developers to integrate with the Green API, we have created a Postman collection with a complete set of required API.

1. [Setup](#setup): collection setup
2. [Configure](#configure): environment setup
3. [Test](#test): API methods use

## Setup {#setup}

To start, download the components below and install Postman:

- [Postman](https://www.postman.com/downloads/) application
- [Green API - Postman Collection](https://github.com/green-api/green-api-postman-collection) collection (clone the repository or download the package as a ZIP file)

After installing and running Postman, click on `Import` and select the two JSON files `collection.json` and `environment.json` from the Postman collection package on GitHub. After importing, you will see a `Green API` item in `Collections` section and you can select `Green API Developer` as` Environment`.

## Configure {#configure}

A custom Postman environment is actually a collection of  "key-value" pairs. You can create standard variables that will be then used in different requests. More on [Postman environment variables](https://learning.postman.com/docs/postman/variables-and-environments/managing-environments/).

The pre-configured `Green API Developer` environment contains the complete set of variables, referened by the collection. Some of these variables should be edited and replaced with customer values. To open the edit dialog, click the little eye button next to the environment dropdown and select `Edit`.

Set values of the two variaables `idInstance`and `apiTokenInstance`, which were got at [Before you start](before-start.md#parameters) stage.

## Test {#test}

Now you can select any API method in the collection and start sending requests. For convenience, all methods are listed in the same order as they are reviewed in [API documents](api/index.md). You can make any changes to these methods to make it easier to test them and process responses. 
