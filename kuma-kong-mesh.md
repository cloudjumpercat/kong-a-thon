# Kuma/Kong Mesh State of the Docs

The purpose of this is to investigate Kong's service mesh documentation (Kuma and Kong Mesh), navigate through the workflows, learn about the technology,
and record things that were successful or trip me up. 

_Note:_ Make a column in the IA rework for persona?

## Initial research

- Started by first researching "what is a service mesh" to learn about the tech. First (non-ad) article was this: https://linkerd.io/what-is-a-service-mesh/
  - "platform level" = control plane, "application level" = data plane?
  - article was pretty helpful about understanding how it worked, especially the "what Linkerd does" part.
- I'm also a visual learner, so I looked at "what is a service mesh" images

## Kuma docs

- **Friction:** The ["What is Service Mesh"](https://kuma.io/docs/1.8.x/introduction/what-is-a-service-mesh/) topic was a bit more confusing and wordy than the
  Linkerd one. But I appreciated the additional info about CP vs DP, that's something that confused me about where the service mesh operates. 
- [How Kuma works](https://kuma.io/docs/1.8.x/introduction/how-kuma-works/#dependencies) seems a bit disorganized since it talks more about services meshes in general, but this was super helpful: "An architecture made of sidecar proxies deployed next to our services 
(the data-planes, or DPs), and a control plane (CP) controlling those DPs, is called Service Mesh."
- Had to look up what Envoy was since there weren't any links to it.
- **Harmony:** I like the simplicity of the three step install process for each install type.
- I ran through the Docker install topic (because I don't have k8s yet). Everything worked at first and I liked the wizard in the GUI, although it was more pictures than explaining the options. The [README](https://github.com/kumahq/kuma-counter-demo/blob/master/README.md) was kind of confusing, I didn't know I had to install redis because that wasn't mentioned and at first I couldn't get the server to work (needed two Terminal windows). I also had to move to the correct demo-app folder to get the prefix=app/ command to work. Also, never told me to install kumactl. I eventually quit at the `kumactl generate dataplane-token --name=redis > kuma-token-redis` phase because it looks like it was looking for the wrong port and I wasn't sure how to progress from there. So that stopped the whole "get it running" process, so I don't have a working Kuma instance.
  - Also, is it kind of weird that to get the GUI Kuma up and runnning, you still need the CLI? 
  - Maybe an opportunity for a default ports page?
- **Friction:** It feels like this (and the other install topics) have a lot of steps that assume knowlege of things (ex. how to pull Docker images, what kind of deployment you want, how to install K8s dependencies, etc.). I'm not sure if it's fair or not to assume that kind of knowledge.
- The "Explore....demo app" pages seem to just rehash what was in the README, but more details and better. Can we just direct to those instead because the README was pretty confusing?
- For metric visualization, we mention Prometheus and Grafana. Should/can we also mention Gateway (or Konnect) as a place to view those metrics? 
- The "Overview" page in the Explore section feels like it's repeating info from the Intro section. Or at least the first part did.
- I'm a bit confused how the gateways, DPs, ingress, and egress all fit together. I'd like that to be described in the beginning and part of a diagram.
- Inspect API docs are more like "how to debug Kuma", I think
- "Requirements" page should be moved up to an "Intro" or "Getting Started" section, or something like that.
- Topics in the "Policies" section should probably be moved to more specific sections like "Observability" or "Security" etc.
  - For those, we should call out that they need to understand the basic policy concepts before configuring specific policies.

## Kong Mesh docs

- **Friction:** The "Enterprise" section isn't necessary. Mesh is only enterprise. Since "Plan and Deploy" only contains a License page, that also leads me to believe there are no "free" features at all. All you could do is install Mesh.
- Mesh is lacking a proper "What is Kong Mesh" type overview content
- In the "Getting Started" section, we link to Kuma get started docs, so that's something that could be shared. 
- **Friction:** I find it weird that there's so many "see the Kuma docs for more info" links. As a customer, I'd just want to use Kuma then since that seems to have better doc support (and is free).
- **Friction:** I had this issue with Kuma, too. There's the dp, cp, kumactl, etc. and we're just told "download what you need". I have no idea which of those I need because 1. those instructions come later in the docs and are not linked to in the install docs and 2. those concepts aren't explained well. Maybe it's just me because I don't have experience with this tech. I just pulled everything but Prometheus to test the Docker install steps.
- So to install Kong Mesh, I actually need to install Kuma images? There are no separate Kong Mesh images? Is the Kong Mesh license the only thing that differentiates between Kuma and Kong Mesh?
- **Harmony:** Docker install and run instructions did work. I was able to look at my mesh in the GUI.
- Why have an Egress? Is that just to have another layer of abstraction?
- Got an error when I tried to install the demo-app
- CA stuff could probably be grouped in a "Security" section? Or would this be zero-trust?

## IA thoughts

- Introduction
  - What is service mesh?
  - What is Kuma?
  - Release notes
  - Compatiblity
  - Stages of software availability
  - Default ports (https://kuma.io/docs/1.8.x/networking/networking/#kuma-cp-ports)  
- Getting Started
  - Install
  - Deploy
  - Observe (https://kuma.io/docs/1.8.x/explore/observability/#demo-setup)
- Observability
  - Grafana
  - Datadog
  - Prometheus
  - Control plane metrics
  - Multi-zone?
- Multi-cluster service discovery
- Zero trust communication
- Reference
  - CLI
