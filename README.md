<picture><source media="(prefers-color-scheme: dark)" srcset="https://nextwork.ai/static/nextwork-logo-paper.svg" /><img src="https://nextwork.ai/static/nextwork-logo-leather.svg" alt="NextWork" width="300" /></picture>

# Save User Info with a Lex Chatbot

**Project Link:** [View Project](https://nextwork.ai/projects/19e304aa-a759-5670-97ff-e3e1c45436eb)

**Author:** Maria Jasmin Ahorro

---

## Introducing Today's Project!

### ✍️ What are we here to do today?

In this project, I will demonstrate how to capture and carry over user information across chatbot intents using context tags in Amazon Lex, specifically saving a user's date of birth and reusing it to streamline follow-up balance inquiries. I'm doing this project to learn how to build smarter, more context-aware conversational user experiences that eliminate repetitive questions and make chatbots feel more natural and efficient.

### ✍️ What are we doing in this step?

In this step, I will scroll down to the Contexts panel on the CheckBalance intent page, choose New context tag, name the new context contextCheckBalance, and set its timeout to 5 turns or 90 seconds because we need to save the user's verified details (like their date of birth) as an output context so that subsequent intents can securely access and reuse this information without making the user repeat themselves.

### ✍️ What are we doing in this step?

In this step, I will save the user's birthday from the CheckBalance intent because we need to create an output context tag named contextCheckBalance so that subsequent follow-up intents can capture and reuse the user's verified details without requiring them to repeat their information.

### What is Amazon Lex?

Amazon Lex is a fully managed artificial intelligence service with advanced natural language models designed for building conversational interfaces into any application. It is useful because it allows developers to quickly build, test, and deploy text and voice chatbots that can understand user intent, maintain conversation context across multiple turns, and securely connect with backend services like AWS Lambda without requiring complex natural language processing infrastructure from scratch.

### How I used Amazon Lex in this project

In today's project, I used Amazon Lex to build conversational intent workflows with context carryover and session management, configuring output and input context tags (contextCheckBalance) to securely pass verified user attributes like dates of birth across intents (CheckBalance and FollowupCheckBalance) and seamlessly streamline multi-turn account balance inquiries without repetitive authentication.

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was how cleanly Amazon Lex's context carryover handles the session state behind the scenes, automatically passing the verified date of birth from the CheckBalance intent into the FollowupCheckBalance intent without requiring any extra backend database storage or complex session management!

### This project took me...

This project took me 20 minute to complete, successfully setting up context tags and the FollowupCheckBalance intent in Amazon Lex!

### ❤️ Thanks for doing this project!

I chose to do this project today because I wanted to master advanced Amazon Lex concepts like context carryover and session management to build smarter, more intuitive chatbots that remember user details across turns. Something that would make learning with NextWork even better is having even more hands-on real-world scenarios where multiple chatbots integrate with external APIs and databases!

## Context Tags

Context tags are markers used in Amazon Lex to store and check for specific information across different parts of a conversation, helping save the user from having to repeat details like their date of birth or account type between different intents.

There are two types of context tags:

Output context tag: Tells the chatbot to remember specific details after an intent is successfully completed (such as saving the user's date of birth or account type), so that other parts of the conversation can reuse this stored information later.

Input context tag: Checks if specific stored details are already available before a new intent can activate (such as verifying that the user's date of birth is already saved), allowing follow-up questions to be answered without making the user repeat themselves.

I created a context tag called contextCheckBalance. This context tag was created in the intent CheckBalance. This tag stores information about the user's verified details, specifically their date of birth, so that subsequent follow-up intents can securely access and reuse it without making the user repeat themselves.

### ✍️ What are we doing in this step?

In this step, I will configure the dateOfBirth slot's default value to #contextCheckBalance.dateOfBirth and enable the fulfillment Lambda code hook under Advanced options because we need to automatically pull and reuse the user's saved birthdate from the contextCheckBalance output context without asking them to type it in again, while ensuring random bank balances are still successfully generated and returned by our backend Lambda function.

![Context Tags](https://nextwork.ai/overjoyed_magenta_proud_yak/uploads/19e304aa-a759-5670-97ff-e3e1c45436eb_97dc2351)

## FollowUpCheckBalance

I created a new intent called FollowupCheckBalance. The purpose of this intent is to handle subsequent account balance inquiries (such as asking about other accounts) without requiring the user to re-authenticate or repeat their date of birth, leveraging the saved context carryover to deliver a smooth, efficient conversational experience.

### ✍️ What are we doing in this step?

In this step, I will expand the dateOfBirth slot in the FollowupCheckBalance intent, open Advanced options, enter #contextCheckBalance.dateOfBirth into the Default values panel, and enable the fulfillment Lambda code hook under Advanced options because we need the chatbot to automatically pull and reuse the user's verified date of birth from our saved context tag without asking them to type it in again, while ensuring our backend Lambda function can still dynamically process requests and return bank balances.

This intent is connected to the previous intent I made, CheckBalance, because it utilizes the contextCheckBalance output context tag to carry over the user's verified date of birth, allowing the chatbot to seamlessly handle follow-up account balance inquiries without making the user re-authenticate or repeat their information.

![FollowUpCheckBalance](https://nextwork.ai/overjoyed_magenta_proud_yak/uploads/19e304aa-a759-5670-97ff-e3e1c45436eb_12345678)

## Input Context Tag

I created an input context, contextCheckBalance, that acts as a prerequisite gatekeeper for the FollowupCheckBalance intent, ensuring that the chatbot checks for the user's previously saved verification details (such as their date of birth) before allowing follow-up account balance inquiries to proceed.

![Input Context Tag](https://nextwork.ai/overjoyed_magenta_proud_yak/uploads/19e304aa-a759-5670-97ff-e3e1c45436eb_c4fc89af)

## The final result!

To see the context tags and followup intent in action, I typed "check my balance", selected my account (amex), provided my date of birth (12/12/1992), received my initial balance, and then immediately asked "What about my checking account?" without re-entering my birthday.

If I had gone straight to trying to trigger FollowUpCheckBalance without setting up any context, the chatbot would have failed to recognize the request or asked for my date of birth from scratch because the input context requirement (contextCheckBalance) wouldn't be met and the saved verification data wouldn't exist yet!

![The final result!](https://nextwork.ai/overjoyed_magenta_proud_yak/uploads/19e304aa-a759-5670-97ff-e3e1c45436eb_505be5b8)
