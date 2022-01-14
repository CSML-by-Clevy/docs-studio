---
description: How to configure an Amazon Alexa skill with CSML Studio
---

# Installation

## Step 1: Initial setup in the Alexa Console

To create an Amazon Alexa skill, you will first need to create a free developer account on [https://developer.amazon.com/alexa](https://developer.amazon.com/alexa), then visit the [Alexa Skills Kit (ASK) console](https://developer.amazon.com/alexa/console) and click on Create Skill.

![](<../../.gitbook/assets/image (39).png>)

In the next section, give your skill a name and select the default language. This can be changed later! Under **Choose a model to add to your skill**, select **Custom**, and under **Choose a method to host your skill's backend resources**, select **Provision your own**, then click on **Create Skill** at the top.

![](<../../.gitbook/assets/image (40).png>)

In the next screen, select **Start from scratch**. Alexa will then build your skill.

![](<../../.gitbook/assets/image (41).png>)

## Step 2: Connecting your skill with CSML Studio

Once the skill is built, you will need to connect it with CSML Studio. This step is actually very easy. First, find [the list of all your skills in the Alexa Skills Kit console](https://developer.amazon.com/alexa/console/ask) and copy the Skill ID of your skill:

![](<../../.gitbook/assets/image (42).png>)

Then, in CSML Studio, create a new Alexa channel for your bot under **Channels > Amazon Alexa** and set the name and ID of your skill. You will also need to copy the **HTTPS Endpoint URL** to configure the Skill in the ASK console later. You can then save for now!

![](<../../.gitbook/assets/image (44).png>)

To finalize the configuration, in the ASK Console, visit your skill's **Build tab > Endpoint**. By default, AWS Lambda ARN is selected: select **HTTPS** instead and under **Default Region**, paste your HTTPS Endpoint URL from CSML Studio and select the SSL Certificate option "_My development endpoint is a sub-domain of a domain that has a wildcard certificate from a certificate authority_", then click on **Save Endpoints**.

![](<../../.gitbook/assets/image (45).png>)

Your skill is now correctly configured with CSML Studio!
