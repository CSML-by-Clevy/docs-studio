# Custom Code Execution

When used together with custom "serverless" function runtimes \(cloud-based such as [AWS Lambda](https://aws.amazon.com/fr/lambda/features/), [Azure Functions](https://azure.microsoft.com/fr-fr/services/functions/), [Google Cloud Functions](https://cloud.google.com/functions/docs/)\), or on-premise with [FnProject](https://fnproject.io/), [OpenFaas](https://docs.openfaas.com/) or [OpenWhisk](https://openwhisk.apache.org/)\), the CSML interpreter is able to automatically handle the execution of any payload, any code, in any language.

With CSML Functions, you can integrate your own business logic, on your own servers, in your language of choice. When using the [CSML Studio](https://studio.csml.dev/auth/register), the heavy setup is already done for you, which means that you can import functions in java, python, nodejs, go... without any additional setup, simply by uploading your code and calling the function in your CSML script.

CSML Studio also comes with [many ready-to-use integrations](https://www.csml.dev/integrations.html) that are installable in one-click.

```cpp
findweather:
  say "Let me query the weather in {{location}} for you..."
  use Fn("weatherchannel", location = location) as weather
  say "It will be {{weather.temperature}}°C tomorrow."
```

