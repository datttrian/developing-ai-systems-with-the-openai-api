# Developing AI Systems with the OpenAI API

## Structuring End-to-End Applications

### Formatting model response as JSON

As a librarian cataloging new books, you aim to leverage the OpenAI API
to automate the creation of a JSON file from text notes you received
from a colleague. Your task is to extract relevant information such as
book titles and authors and to do this, you use the OpenAI API to
convert the text notes, that include book titles and authors, into
structured JSON files.

In this and all the following exercises, the `openai` library has
already been loaded.

**Instructions**

- Set up your API key.
- Create a request to the Chat Completions endpoint.
- Specify that the request should use the `json_object` response format.
- Extract and print the model response.

**Answer**

```{python}

```

### Handling exceptions

You are working at a logistics company on developing an application that
uses the OpenAI API to check the shipping address of your top three
customers. The application will be used internally and you want to make
sure that other teams are presented with an easy to read message in case
of error.

To address this requirement, you decide to print a custom message in
case the users fail to provide a valid key for authentication, and use a
`try` and `except` block to handle that.

The `message` variable has already been imported.

**Instructions**

- Set up your OpenAI API key.
- Use the `try` statement to attempt making a request to the API.
- Print the response if the request succeeds.
- Use the `except` statement to handle the authentication error that may
  occur.

**Answer**

```{python}

```

### Avoiding rate limits with retry

You've created a function to run Chat Completions with a custom message
but have noticed it sometimes fails due to rate limits. You decide to
use the `@retry` decorator from the `tenacity` library to avoid errors
when possible.

**Instructions**

- Import the `tenacity` library with required functions: `retry`,
  `wait_random_exponential`, and `stop_after_attempt`.
- Set up your OpenAI API key.
- Complete the retry decorators with the parameters required to start
  retrying at an interval of 5 seconds, up to 40 seconds, and to stop
  after 4 attempts.

**Answer**

```{python}

```

### Batching messages

You are developing a fitness application to track running and cycling
training, but find out that all your customers' distances have been
measured in kilometers, and you'd like to have them also converted to
miles.

You decide to use the OpenAI API to send requests for each measurement,
but want to avoid using a for loop that would send too many requests.
You decide to send the requests in batches, specifying a `system`
message that asks to convert each of the measurements from
**kilometers** to **miles** and present the results in a **table**
containing both the original and converted measurements.

The `measurements` list (containing a list of floats) and the
`get_response()` function have already been imported.

**Instructions**

- Set up your OpenAI API key.
- Provide a system message to request a response with all measurements
  as a **table** (make sure you specify that they are in **kilometers**
  and should be converted into **miles**).
- Append one `user` message per measurement to the `messages` list.

**Answer**

```{python}

```

### Setting token limits

An e-commerce platform just hired you to improve the performance of
their customer service bot built using the OpenAI API. You've decided to
start by ensuring that the input messages do not cause any rate limit
issue by setting a limit of 100 tokens, and test it with a sample input
message.

The `tiktoken` library has been preloaded.

**Instructions**

- Set up your OpenAI API key.
- Use the `tiktoken` library to create an encoding for the
  `gpt-3.5-turbo` model.
- Check for the expected number of tokens in the input message.
- Print the response if the message passes both checks.

**Answer**

```{python}

```

## Function Calling

### Using the tools parameter

You are developing an AI application for a real estate agency and have
been asked to extract some key data from listings: house type, location,
price, number of bedrooms. Use the Chat Completions endpoint with
function calling to extract the information.

The `message_listing` message, containing the real estate listing, and
`function_definition`, containing the function to call defined as a tool
to be passed to the model, have been preloaded.

**Instructions**

- Set up your OpenAI API key.
- Add the preloaded message, `message_listing`.
- Add the function definition, `function_definition`.
- Print the response.

**Answer**

```{python}

```

### Building a function dictionary

You are working on a research project where you need to extract key
information from a collection of scientific research papers. The goal is
to create a summary of key information from the papers you are given,
that includes the title and year of publication. To compile this, you
decide to use the OpenAI API with function calling to extract the key
information.

The `get_response()` function and `messages`, containing the text of the
research paper, have been preloaded. The `function_definition` variable
has also partially been filled already.

**Instructions**

- Set up your OpenAI API key.
- Define the function `'type'` parameter.
- Define the `'properties'` parameters to extract the **title** and
  **year of publication** from research papers.

**Answer**

```{python}

```

### Extracting the response

You work for a company that has just launched a new smartphone. The
marketing team has collected customer reviews from various online
platforms and wants to analyze the feedback to understand the customer
sentiment and the most talked-about features of the smartphone. To
accelerate this, you've used the OpenAI API to extract structured data
from these reviews, using function calling. You now need to write a
function to clean the output and return a dictionary of the response
from the function only.

The `get_response()` function, `messages` variable (containing the
review) and `function_definition` (containing the function to extract
sentiment and product features from reviews) have been preloaded. Notice
that both `messages` and `function_definition` can be passed as
arguments to the `get_response()` function to get the response from the
chat completions endpoint.

**Instructions**

- Set up your OpenAI API key.
- Define a function to return the dictionary containing the output data,
  as found in the response under `arguments`.
- Print the dictionary.

**Answer**

```{python}

```

### Parallel function calling

After extracting the data from customers' reviews for the marketing
team, the company you're working for asks you if there's a way to
generate a response to the customer that they can post on their review
platform. You decide to use parallel function calling to apply both
functions and generate data as well as the responses. You use a function
named `reply_to_review` and ask to return the review reply as a `reply`
property.

In this and the following two exercises in this chapter the model used
is `gpt-3.5-turbo-1106`, as other models may not support parallel
function calling.

In this exercise, the `get_response()` function, `messages` and
`function_definition` variable have been preloaded. The `messages`
already contain the user's review, and `function_definition` contains
the function asking to extract structured data.

**Instructions**

- Set up your OpenAI API key.
- Append to the function definition to return the additional message
  responding to the customer review: the function should have `name`,
  `description` and `parameters` specified, and the parameters should be
  `type` and `properties`.
- Print the response.

**Answer**

```{python}

```

### Setting a specific function

You have been given a few customer reviews to analyze, and have been
asked to extract for each one the product name, variant, and customer
sentiment. To ensure that the model extracts this specific information,
you decide to use function calling and specify the function for the
model to use. Use the Chat Completions endpoint with function calling
and `tool_choice` to extract the information.

In this exercise, the `messages` and `function_definition` have been
preloaded.

**Instructions**

- Set up your OpenAI API key.
- Add your function definition as tools.
- Set the `extract_review_info` function to be called for the response.
- Print the response.

**Answer**

```{python}

```

### Avoiding inconsistent responses

The team you were working with on the previous project is enthusiastic
about the reply generator and asks you if more reviews can be processed.
However, some reviews have been mixed up with other documents, and
you're being asked not to return responses if the text doesn't contain a
review, or relevant information. For example, the review you're
considering now doesn't contain a product name, and so there should be
no product name being returned.

In this exercise, the `get_response()` function, and `messages` and
`function_definition` variables have been preloaded. The `messages`
already contain the user's review, and `function_definition` contains
the two functions: one asking to extract structured data, and one asking
to generate a reply.

**Instructions**

- Set up your OpenAI API key.
- Modify the `messages` to ask the model **not** to assume any values
  for the responses.

**Answer**

```{python}

```

### Defining a function with external APIs

You are developing a flight simulation application and have been asked
to develop a system that provides specific information about airports
mentioned in users' requests. You decide to use the OpenAI API to
convert the user request into airport codes, and then call the
[AviationAPI](https://docs.aviationapi.com/) to return the information
requested. As the first step in your coding project, you configure the
function to pass to the `tools` parameter in the Chat Completions
endpoint.

In this exercise, the `get_airport_info()` and `get_response()`
functions have been preloaded. The `get_airport_info()` function uses
the `AviationAPI` and takes as input one airport code, returning the
response with the requested airport information.

**Instructions**

- Set up your OpenAI API key.
- Define the function to pass to tools: that should include the function
  `'name'` for the function, a `'description'` specifying that a
  matching airport code should be returned, and `'parameters'` and
  `'result'` details.

**Answer**

```{python}

```

### Calling an external API

Now that you have a clearly structured function definition, you move on
to improving your endpoint request. You use the Chat Completions
endpoint and pass a `system` message to ensure that the AI assistant is
aware that it is in the aviation space and that it needs to extract the
corresponding airport code based on the user input.

In this exercise, the `get_airport_info()` function has been preloaded.
The `get_airport_info()` function uses the `AviationAPI` and takes as
input one airport code, returning the response with the requested
airport information. The `print_response()` function has also been
preloaded to print the output.

**Instructions**

- Set up your OpenAI API key.
- Call the Chat Completions endpoint and ensure the `system` is provided
  with instructions on how to handle the prompt.

**Answer**

```{python}

```

### Handling the response with external API calls

To better connect your flight simulation application to other systems,
you'd like to add some checks to make sure that the model has found an
appropriate answer. First you check that the response has been produced
via `tool_calls`. If that is the case, you check that the function used
to produce the result was `get_airport_info`. If so, you load the
airport code extracted from the user's prompt, and call the
`get_airport_info()` function with the code as argument. Finally, if
that produces a response, you return the response.

In this exercise, the `response`, the `json` library, and
`get_airport_info()` function have been preloaded.

**Instructions**

- Check that the response has been produced via `tool_calls`.
- Extract the function if the previous check passed.

**Answer**

```{python}

```

## Best Practices for Production Applications

### Moderation API

You are developing a chatbot that provides educational content to learn
languages. You'd like to make sure that users don't post inappropriate
content to your API, and decide to use the moderation API to check
users' prompts before generating the response.

**Instructions**

- Set up your OpenAI API key.
- Use the moderation API to check the user message for inappropriate
  content within `categories`.
- Print the response.

**Answer**

```{python}

```

### Adding guardrails

You are developing a chatbot that provides advice for tourists visiting
Rome. You've been asked to keep the topics limited to only covering
questions about **food and drink, attractions, history and things to do
around the city**. For any other topic, the chatbot should apologize and
say 'Apologies, but I am not allowed to discuss this topic.'.

**Instructions**

- Set up your OpenAI API key.
- Write a `user` message with the `user_request` given, and a `system`
  message to tell the model to assess the question first: if it is
  allowed, provide a reply, otherwise provide the message: 'Apologies,
  but I am not allowed to discuss this topic.'.
- Print the response.

**Answer**

```{python}

```

### Adversarial testing

You are developing a chatbot designed to assist users with personal
finance management. The chatbot should be able to handle a variety of
finance-related queries, from budgeting advice to investment
suggestions. You have one example where a user is planning to go on
vacation, and is budgeting for the trip.

As the chatbot is only designed to respond to personal finance
questions, you want to ensure that it is robust and can handle
unexpected or adversarial inputs without failing or providing incorrect
information, so you decide to test it by asking the model to ignore all
financial advice and suggest ways to spend the budget instead of saving
it.

**Instructions**

- Set up your OpenAI API key.
- Test the chatbot with an adversarial input that asks to **spend** the
  **\$800** instead.

**Answer**

```{python}

```

### Including end-user IDs

You are developing a content moderation tool for a social media company
that uses the OpenAI API to assess their content. To ensure the safety
and compliance of the tool, you need to incorporate user identification
in your API requests, so that investigations can be performed in case
malicious content is found.

The `uuid` library has been preloaded. A `message` has also been
preloaded containing text from a social media post.

**Instructions**

- Set up your OpenAI API key.
- Use the `uuid` library with `uuid4()` to generate a unique ID.
- Pass the unique ID to the chat completions endpoint to identify the
  user.

**Answer**

```{python}

```
