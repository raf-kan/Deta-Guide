# Deta Guide

## Quick intro:

I struggled with Azure and Docker because, frankly, I know nothing of them. With Python and some clumsy errors, I made mistakes and the Web App simply wasnt working.

Deta made the deployment so quick it took 5 lines of code in the terminal. That's it.

So heres a quick little doc to get whoever started on deploying this with ease.

---

## Step 1: Make an account with Deta

Go to [Deta](https://www.deta.sh/?ref=fastapi) to make a free account. There seems to be no difference in tiers as there is only 1. It's free and appears to have no limitations. Credit card or any sort of payment not required.

---

## Step 2: Installation

Install the Deta CLI on your computer.

- For Mac/Linux users:

        curl -fsSL https://get.deta.dev/cli.sh | sh


- For Windows:

        iwr https://get.deta.dev/cli.ps1 -useb | iex

---

## Step 3: Login

Simply type in:

    deta login

 to login. It will open up a browser window and log you in automatically

---

## Step 4: Deployment

**Change directory to where your application is located.** In the same directory, load in the requirements.txt list and/or the virtual environment.

>Eaxmple: With my experience in Python, only *main.py* (script for FastAPI), the *simple_tagger.py* (tagging "algorithm"), and finally, the requirements.txt.

In the directory, with the terminal/shell; simply enter:

    deta new

This will create the microservice, provide an endpoint, and other details.

From here, all you need is the endpoint link. You can access it through your browser or in your script through the same link.

---

## Enable public access:

To enable public access so that anyone can use the API in their browser, enter:

    deta auth disable

This makes the API public and accessible by anyone with the link

---

## Private access using API Keys:

To set an API key, we first do the opposite of enabling public access:

    deta auth enable

Followed by:

    deta auth create-api-key --name first_key --desc "api key for agent 1"

This will show something similar to:

    {
        "name": "first_key",
        "description": "api key for agent 1",
        "prefix": "randomprefix",
        "api_key": "randomprefix.supersecretrandomstring",
        "created": "2021-04-22T11:50:08Z"
    }

**Remember: Your API KEY will only show once, keep it in a memorable and safe area**

---

## Accessing Private APIs:

Simply add this key to the header of every request you make to your Micro.

    curl --request GET \
    --url https://2kzkof.deta.dev/tut \
    --header 'Content-Type: application/json' \
    --header 'X-API-Key: awEGbjqg.D1sETRFJKHWtcxSRSmofY2-akZjqFPh7j'


---
# That should be it!

If help needed, always refer to the [doc](https://docs.deta.sh/docs/home/) as these are the only few commands I have used or know of.

-- Raf