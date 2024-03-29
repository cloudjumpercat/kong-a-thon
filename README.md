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
  - **Harmony/Friction**: Everything went really well except it's taking forever to get approved to access my private Dev Portal? I just enabled public so it was faster.

### Using Kong with plugins
-  Configure Plugin on a Service
  -  **Observation**: I decided to go here next based on the suggestion at the end of the Dev Portal page in the quickstart. I skipped API spec in the quickstart guide since I already kind of did that in the previous step.
  - **Observation**: Would a user need more guidance about where to navigate exactly for "Open a Service version."? It took me a little while to figure out where to go.
  - **Observation**: "If you don’t see the Plugins section, create an implementation first." I think this should be a requirement so users can make sure it's done right away rather than having to navigate away from what they were doing and then go back.
  - I went with Key Auth for my first plugin.
  - **Harmony**: Between the docs and the fact that the settings for the plugin were pretty much auto configured in the UI, it was really easy to set up! I'm just not sure what to do with all the parameters and additional settings that are in the doc, but that could just be my lack of tech experience. I went back into the plugin view and I think I can copy the JSON and make my edits to the params and re-upload it?
  - **Observation**: I went down a rabbit hole because as I was figuring out the key auth plugin docs, they mentioned something about Consumers, so I did some searching to find /gateway/latest/get-started/quickstart/adding-consumers/#main because I didn't think I had a Consumer. But now I can't figure out why my localhost:8001 isn't working, so I'm looking into that.
  - **Friction**: I couldn't figure out how to add a consumer because all my searches kept pulling up Gateway and then I started thinking that maybe I needed to install Gateway on top of Konnect. Angel pointed me in the right direction though. So [this is the Konnect doc for consumers](https://konnect--kongdocs.netlify.app/konnect/runtime-manager/gateway-config/), but that really doesn't seem to cover how to get to that spot in the UI or what to configure. What I was looking for was a doc that's more similar to this [Adding Consumers](https://konnect--kongdocs.netlify.app/gateway/latest/get-started/quickstart/adding-consumers/#main).
  - **Friction**: Okay, I created the consumer, so where do I put these YAML file configurations for the consumer and key that they mention in the plugin docs? The info in the [Usage](https://konnect--kongdocs.netlify.app/hub/kong-inc/key-auth/#usage) section was making me think that I have these things still left to configure in Konnect. But then I was thinking that maybe "Usage" means that this is how I can use the key auth plugin, but that didn't seem quite right because it makes sense that you'd need to associate consumers with the key auth plugin to they can authenticate to the service.
  - **Observation**: After talking to the rest of the docs team, turns out I need to use decK to do plugins with Konnect, which is why I got confused. On the decK docs, looks like I still need to install Gateway, which seems like it shouldn't be the case if I'm using Konnect, but I'm going to follow those instructions anyways.
  - **Friction**: I'm trying to do the DB-less mode for macOS, and for some reason, I can't find my kong.conf file nor can I generate the kong.yaml file (getting an error in Terminal). 
  - **Harmony/Friction**: I tried Docker instead and was having pretty good success with it until step 3 on [this section](https://docs.konghq.com/gateway/latest/install-and-run/docker/#install-kong-gateway-in-db-less-mode) because Docker would start and then exit shortly after because it wasn't recognizing the .yml file. I found this [external blog post](https://www.bswen.com/2021/11/how-to-solve-kong-docker-install-error.html), not sure if that would fix my problem.
  - Turns out I already had a Gateway configured in Konnect because I configured a runtime instance. This was kind of confusing to me because I didn't know that would create a Gateway. 
  - **Harmony**: decK install seemed to go well (I did macOS).
  - **Friction**: Now I'm stuck trying to [configure Kong Gateway](https://docs.konghq.com/deck/1.12.x/guides/getting-started/) because my localhost is running at 8000 instead of the recommended 8001 and changing it in the curl request doesn't do anything.
