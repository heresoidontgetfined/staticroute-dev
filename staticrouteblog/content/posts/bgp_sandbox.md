+++
date = '2025-10-05T11:28:14-05:00'
draft = false
title = 'Claude Code Contest - What Can You Build in One Week: Bgp sandbox'
+++
> This is my entry into a contest - building something cool in one week or less. I've wanted to explore the intersection of code and network engineering more so I geared this project toward BGP daemons.

### 1: What I built:

This project is an educational tool for Border Gateway Protocol. It helps users visualize BGP route advertisements between peers. It also allows the user to interact with the BGP process by: injecting routes into the BGP process and configuring import/export policies. Users can see how these policies and advertisements effect the Peer route tables in real time. It was important to me that the application use actual BGP routing instances that peer with each other. 

The user interacts with a custom TUI build for this project (because TUIs are cool) and after selecting their run configuration a GUI is launched with the specified daemon start-states. The TUI was built using the BubbleTea framework (GO). The frontend is built using JS/React/Cytoscape and the backend is leveraging GoBGP.

### 2. How I built it in a week or less:

I started this project on the evening of Friday October 3rd, with an idea that I'd been kicking around for quite some time. I finished with a functional product that exceeded my expectations on the Sunday evening (10/5). My initial prompt:
<blockquote>
Build an educational BGP sandbox app consisting of:

1. TUI - Use: https://github.com/charmbracelet/bubbletea to create a TUI that launches the browser based frontend.
-Colorful, with options to determine how many peers are included in the launch, whether they use iBGP or eBGP, etc.

2. Frontend - Javascript:
browser-based interactive UI.
-Users see a small AS-level network w/nodes and edges.
-Users can Toggle BGP neighborships on/off between AS nodes.
-Inject prefixes from an AS.
-Apply simple BGP policy knobs (local-pref, AS-path prepend, MED, community no-export).

The graph should update to show:
-Best path selection (highlighted).
-Alternate paths (dimmed).
-Animated “packets” moving along the best path.

React + Cytoscape.js or D3.
REST or websocket connection to backend.

3. Backend - GoBGP:
Run GoBGP inside a Docker container as the routing engine.
-A lightweight Node.js/Express service runs alongside GoBGP in the same container or compose setup.
-This service exposes REST or WebSocket endpoints that the frontend can call. Use GoBGP documentation to determine functions to expose, such as:
POST /enable → enables a BGP session.
POST /disable → tears down a session.
POST /prefixes → inject a prefix into a given AS.
POST /policy → apply simple policy knobs.
GET /routes → returns the RIB for best path info for visualization.
-The service internally uses GoBGP’s gRPC API to perform these actions.
-Fully document the API

4. Containerization - Docker:

Provide a Dockerfile or docker-compose.yml that:
-Runs GoBGP.
-Runs the API service.
-Exposes the frontend via a simple dev server (e.g., Vite/React).

*This should be fully functional, no mock data. If you have questions about deployment protocols or methods feel free to ask me before deployment.
</blockquote>

Some additional prompts were used to:

* Make the TUI more decorative
* Change the configuration to ensure each "Peer" is in fact its own instance of GoBGP, rather than a single instance.
* Make sure the entire project can be spun up and down using docker.
* Add a clickable "packet" that looks like a condiment packet, which displays the NLRI being exchanged between Peers.
* Ensure import/export policies are being properly applied and can be both created and deleted by the user.

### 3. Screenshots/Demo:

[GitHub - BGP Sandbox](https://github.com/heresoidontgetfined/bgp_sandbox)

{{< video src="/images/BGP_screencap.mp4" >}}

{{< gallery >}}
![img3](/images/bgp0.png)
![img1](/images/bgp1.png)
![img2](/images/bgp2.png)
![img3](/images/bgp3.png)
![img3](/images/bgp4.png)
{{< /gallery >}}



