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
