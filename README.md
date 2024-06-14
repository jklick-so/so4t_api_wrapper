# Stack Overflow for Teams API Wrapper (so4t_api_wrapper)
A Python wrapper for the Stack Overflow for Teams API

## Table of Contents
* [Requirements](https://github.com/jklick-so/so4t_tag_report?tab=readme-ov-file#requirements)
* [Setup](https://github.com/jklick-so/so4t_tag_report?tab=readme-ov-file#setup)
* [Usage](https://github.com/jklick-so/so4t_tag_report?tab=readme-ov-file#basic-usage)
* [Support, security, and legal](https://github.com/jklick-so/so4t_tag_report?tab=readme-ov-file#support-security-and-legal)

## Requirements
* A Stack Overflow for Teams instance (Basic, Business, or Enterprise)
* Python 3.9 or higher ([download](https://www.python.org/downloads/))
* Operating system: Linux, MacOS, or Windows

## Setup

[Download](https://github.com/jklick-so/so4t_api_wrapper/archive/refs/heads/main.zip) and unpack the contents of this repository

**Installing Dependencies**

* Open a terminal window (or, for Windows, a command prompt)
* Navigate to the directory where you unpacked the files
* Install the dependencies: `pip3 install -r requirements.txt`

**API Authentication**

For the Basic and Business tiers, you'll need an API token. For Enterprise, you'll need to obtain both an API key and an API token.


* For Enterprise, documentation for creating the key and token can be found within your instance, at this url: `https://[your_site]/api/docs/authentication`

Creating an access token for Enterpise can sometimes be tricky for people who haven't done it before. Here are some (hopefully) straightforward instructions:
* Go to the page where you created your API key. Take note of the "Client ID" associated with your API key.
* Go to the following URL, replacing the base URL, the `client_id`, and base URL of the `redirect_uri` with your own:
`https://YOUR.SO-ENTERPRISE.URL/oauth/dialog?client_id=111&redirect_uri=https://YOUR.SO-ENTERPRISE.URL/oauth/login_success`
* You may be prompted to login to Stack Overflow Enterprise, if you're not already. Either way, you'll be redirected to a page that simply says "Authorizing Application"
* In the URL of that page, you'll find your access token. Example: `https://YOUR.SO-ENTERPRISE.URL/oauth/login_success#access_token=YOUR_TOKEN`


* Open a terminal window (or, for Windows, a command prompt)
* Navigate to the directory where you unpacked the files
* Install the dependencies: `python3 -m pip install -r requirements.txt --trusted-host pypi.org --trusted-host pypi.python.org --trusted-host files.pythonhosted.org`

> NOTE: Depending on your installation of Python, you may need to use `python` or `py` instead of `python3` in the command above. If `python3` is not a recognized command, you can check which command to use by running `python --version` or `py --version` in your terminal and seeing which responds with the installed Python version.

**API Authentication**
To authenticate with the Stack Overflow API, you will need to generate a valid access token with write permissions.

* For Basic or Business, instructions for creating a personal access token (PAT) can be found in [this KB article](https://stackoverflow.help/en/articles/4385859-stack-overflow-for-teams-api).
* For Enterprise, follow the instructions in the KB article titled [Secure API Token Generation Using OAuth with PKCE](https://support.stackenterprise.co/support/solutions/articles/22000286119-secure-api-token-generation-using-oauth-with-pkce)

> NOTE: For Enterprise, if you'll be performing any API tasks that require posting or editing content (i.e. anything beyond just getting/reading content), you'll need to make sure to include the `write_access` scope when generating your token; otherwise, you will not be able to make the necessary updates to content via the API.

## Usage
A basic example of how to use the wrapper in an application:

```python
from so4t_api import StackClient

url = "SUBDOMAIN.stackenterprise.co"
token = "TOKEN"

stack = StackClient(url, token) # instantiate the StackClient
questions = stack.get_questions() # get all questions
export_to_json("questions", questions) # write questions to a JSON file
```

At this time, most/all the documentation for wrapper methods is documented along side the methods (i.e. in the code)

## Support, security, and legal
Disclaimer: the creator of this project works at Stack Overflow, but it is a labor of love that comes with no formal support from Stack Overflow. 

If you run into issues using the script, please [open an issue](https://github.com/jklick-so/so4t_tag_report/issues). You are also welcome to edit the script to suit your needs, steal the code, or do whatever you want with it. It is provided as-is, with no warranty or guarantee of any kind. If the creator wasn't so lazy, there would likely be an MIT license file included.

All data is handled locally on the device from which the script is run. The script does not transmit data to other parties, such as Stack Overflow. All of the API calls performed are read only, so there is no risk of editing or adding content on your Stack Overflow for Teams instance.