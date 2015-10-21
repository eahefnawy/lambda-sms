# :envelope: lambda-mailer
AWS Lambda for sending SMS through Twilio. Ready for deployment in 60 seocnds.
 
This lambda gives your browser (or any client) a backend for sending emails.

### Quick Usage

```
// install node-lambda
npm install -g node-lambda

// clone the lambda and get inside!
git clone https://github.com/eahefnawy/lambda-mailer.git
cd  lambda-mailer

// install dependencies
npm install

// create deployment files (to hold your env vars)
touch .env deploy.env event.json
```

`.env` file is used by your local machine for to test and deploy the lambda, deploy.env is used by your lambda function after deployment. So there might be some duplicate env vars.

open `.env` and fill it with your AWS credentials: (make sure you have proper IAM permissions)

```
AWS_ENVIRONMENT=dev
AWS_ACCESS_KEY_ID=your_key
AWS_SECRET_ACCESS_KEY=your_secret
AWS_SESSION_TOKEN=your_sesson token (optional)
AWS_ROLE_ARN=your_amazon_role
AWS_REGION=us-east-1
AWS_FUNCTION_NAME=your_lambda_name
AWS_HANDLER=index.handler
AWS_MODE=event
AWS_MEMORY_SIZE=128
AWS_TIMEOUT=60
AWS_DESCRIPTION=your_lambda_description
AWS_RUNTIME=nodejs
CONFIG_FILE=deploy.env

ACCOUNT_SID=XXX
AUTH_TOKEN=XXX

```

open `deploy.env` and fill it with your gmail credentials:

```
ACCOUNT_SID=XXX
AUTH_TOKEN=XXX
```

open `event.json` and fill it with the following sample event: (just change the values)

```
{
  "to": "+16515556677",
  "from": "+14506667788",
  "body": "Lambdas are cool!"
}


```
now everything is set! Let's test locally!

```
node-lambda run
```

You should get an SMS saying `Lambdas are cool!`. Now let's deploy...

```
node-lambda deploy
```
Now you can provide the previous sample event anytime to your lambda, and you should receive the same SMS.
Have fun!
