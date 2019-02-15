---
title: Create a Voice API application
description: The application stores security and configuration information for your interaction with the API.
navigation_weight: 3
---

# Create a Voice API Application

Every number programmability service application that you build must be associated with a Nexmo Voice Application.

> **Note**: To avoid confusion, `Application` in the Number Programmability documentation refers to the Nexmo Voice Application. The application you are building will be referred to as `application`.

A Nexmo Voice Application stores configuration information such as details of the programmable numbers and webhook callback URLs that your application uses.

You can create Nexmo Voice Applications by any of the following methods:

* Using the [Nexmo Developer Dashboard](https://dashboard.nexmo.com/voice/create-application).
* Using the [Nexmo CLI](/tools).
* Programmatically, using the [Nexmo Application API](/api/application). 

## Using the Nexmo CLI

In this example, we'll create a Voice Application using the Nexmo CLI:

1. If you don't already have one, [create a Nexmo account](https://dashboard.nexmo.com/sign-up).

2. Use [npm](https://www.npmjs.com/) to install and setup the Nexmo CLI, using the API key and secret from your [Nexmo Developer Dashboard](https://dashboard.nexmo.com/getting-started-guide):

    ```sh
    $ npm install nexmo-cli -g
    $ nexmo setup <api_key> <api_secret>
    ```
3. Execute the following command in your application directory:

    ```sh
    $ nexmo app:create "NumberProgrammabilityApp" http://example.com/webhooks/answer http://example.com/webhooks/event  --keyfile private.key
    ```
    The two URLs you provide refer to the webhook endpoints that your application will expose to Nexmo's servers:
    * The first is the webhook that Nexmo's APIs will make a request to when a call is received on your VBC programmable number.
    * The second is where Nexmo's APIs will post details about events that your application might be interested in - such as a call being answered or terminated.

    You can change them when you know the exact endpoints, so leave them as `http://example.com` for now.

    The above command also stores your private key in the file named `private.key` in the directory that you executed the command in.

    Make a note of the `application_id` that this command creates. You can also find this in your [Nexmo Developer Dashboard](https://dashboard.nexmo.com/voice/your-applications).

The next step is to [link your VBC programmable numbers](/vonage-business-cloud/number-programmability/guides/link-vbc-numbers) to this application.
