# Kuma/Kong Mesh State of the Docs

The purpose of this is to investigate Kong's service mesh documentation (Kuma and Kong Mesh), navigate through the workflows, learn about the technology,
and record things that were successful or trip me up. 

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
