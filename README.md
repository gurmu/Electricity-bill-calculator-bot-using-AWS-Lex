# Electricity-bill-calculator-bot-using-AWS-Lex

I am always fascinated with the technology behind AWS Lex and Alexa. Amazon Lex is a service for building conversational interfaces into any application using voice and text. Amazon Lex provides the advanced deep learning functionalities of automatic speech recognition (ASR) for converting speech to text, and natural language understanding (NLU) to recognize the intent of the text, to enable you to build applications with highly engaging user experiences and lifelike conversational interactions. In this post, I will explain how you can develop AWS Lex chatbot and integrated it with Slake. We will implement the app from scratch


Lesson Goals
It is very easy to calculate the electricity bill and tariff for electrical engineering students and professionals but, it makes confusion for non-technical people that concern about their electric charges from the electricity service providers. In this lesson, you will be able to easily develop a chatbot that can calculate your electricity bill.
Prerequests
Sign in to the AWS Management Console, and open the Amazon Lex console at https://console.aws.amazon.com/lex/
Sign in to the Slack API Console at http://api.slack.com
ANATOMY OF A CHATBOT
We want the process for using a ChatBot to be simple for the end user; it should be like a conversation. I want to know something, so I ask in natural language and hopefully get a sensible reply.

This is where we rely on Lex. Lex allows us to configure Intents, which are actions we would like our bot to take. These can be a simple static reply, or a more complex function which needs to call out for fulfillment, e.g., to a Lambda. These intents can have Slots, which are pieces of information from the conversation, which are necessary (or optional) to fulfill the request. In this example, we need to know what country the user is asking about.

ARCHITECTURE OF A CHATBOT
title

Intent: Think of this as a key of conversation; an action that the user wants to perform, with the minimum information needed.for this project we create three intent:

greeting

electricitybill

close

Utterances: Speech or text phrases that trigger the intent. It is the flexibility and variation of spoken language in the real world, there will often be many different ways to express the same request.

Calculate the total energy bill?

I want to know my estimate on electricity consumption?

can you start electric bill estimation?

Hi bot
thanks
Slots: This represents a piece of data needed for the chatbot to fulfill the user’s intent.It is list of values that Amazon Lex uses to train the machine learning model to recognize values for a slot. Since we are dealing with number i created three slot:

dataone(for power)
datatwo( for number of days)
datathree( for cost per unit electricity)
Prompt: This is a question the chatbot will ask the user when requesting user input to match a given slot. When the bot can not match a slot from the triggered utterance, it will use the associated prompt to ask for input from the user.

Tell me about your daily power consumption(watts)?
For how many days your appliances consume power?
How much is the cost per unit electricity?
Fulfillment: When the chatbot has all the slot values (if any), then it proceeds with the logic in the fulfillment section. This is where an AWS lambda function can be used if you need some business logic. If that is not the case, then a simple text response will suffice. i create lambda function:
