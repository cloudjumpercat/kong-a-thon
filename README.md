# kong-a-thon
Hacking on Kong

(inspired by https://github.com/rspurgeon/kong-a-thon)

## Goals
The overall goal is to learn how to use some of Kong's products by trying them out, sort of like a usability test. Because I am a technical writer, my focus will be mainly on trying to use Kong's documentation to learn how to use the products.

These are the more specific steps I will be following:
- Getting Started (quickstart)
- Getting Started (comprehensive)
- Using Kong with plugins
  - Key Authentication
  - JWT Authentication
  - Rate Limiting

## Background
I am a technical writer with four years of experirence in the software industry, so I have some technical knowledge. I'd say I'm very much a novice when it comes to API technology as my background is in MDM software. I learn best by doing and like to use a combination of documentation and videos to figure out how something works. 

## Experience
### Quickstart with Konnect
- My first stop is the [Konnect Cloud](https://docs.konghq.com/konnect/) documentation (I knew this documentation existed, so I have the advantage of not having to Google it). 
  - **Harmony**: Registration process went great!
  - **Friction**: Just realized that there's another iteration of the Konnect docs here: https://docs.konghq.com/konnect-platform/ This is kind of confusing because they contain similar, but not the same, content. I didn't notice it because it's lower in the list of docs in the Docs tab.
- Configuring the Runtime
  - **Harmony**: No issues downloading Docker or jq. 
  - **Observation**: "Set up a New Runtime Instance" step 2, what if I don't have a runtime group already configured? Or will you always have the "default" one configured? 
  - **Observation**: "Once the script has finished running, the runtime instances table will include a new entry for your instance and the tag in the Sync Status column should say Connected." Mine says "In sync".
- Configuring a Service
  - **Friction**: Step 5 says to click "Create", but all I had was "Save" and it didn't redirect me to the new Service. (this was a bug that resolved itself)
  - **Observation**: The "Create a Service version" section is written in a way that implies you are already on the Service overview page. If this section was separated, it could possibly be reused if we wrote it like you were just in Konnect after a login, not necessarily like you had just finished the previous workflow. Do customers do the whole quickstart in one go or would they log out and come back to it? 
- Implement and Test a Service
  - **Observation**: The 6 Advanced Fields section only had five fields and Tags didn't have any default tags (unless no tags = the default).
  - **Friction**: I got an error when I tried to create the implementation because I didn't realize there were naming restrictions (ex. no spaces in my case) for the Name field.
  - **Friction**: I tried viewing the localhost, but it wasn't working. Docker says Kong Gateway is running, so I have to Google to figure out what's going wrong. I had to restart the container in Docker. For some reason, it was saying the localhost was already assigned but then the problem went away on its own.
- Set Up and Access Dev Portal
  - 
