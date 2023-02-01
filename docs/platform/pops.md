---
sidebar_position: 5
---

# Global Infrastructure
--------------

ngrok runs a globally distributed collection of tunnel servers reaching around the world enabling traffic with fast, low latency communications to your applications.

### Locations {#locs}

ngrok servers are deployed in data centers around the world. The location of the data center within a given region may change without notice (e.g. the European servers may move from Frankfurt to London).

| Region Code | Location |
| --- | --- |
| ap  | Asia/Pacific (Singapore) |
| au  | Australia (Sydney) |
| eu  | Europe (Frankfurt) |
| in  | India (Mumbai) |
| jp  | Japan (Tokyo) |
| sa  | South America (São Paulo) |
| us  | United States (Ohio) |

### Usage {#usage}

If you do not explicitly pick a region when starting the ngrok agent, the agent will attempt to pick the region with the least latency, which is usually the one geographically closest to your machine.

To explicitly choose the region, add the `--region` flag or set the `region` property in your configuration file. For example, to start a tunnel in the European region:

    ngrok http --region eu 8080

Reserved domains and TCP addresses are allocated for a specific region (the US region by default). When you reserve a domain or TCP address, you must select a target region. You may not bind a domain or TCP address reserved in another region other than the one it was allocated for. Attempting to do so will yield an error and prevent your tunnel session from initializing.

### Limitations {#limits}

An ngrok agent instance may only be assigned to a single region (one-to-one association). If more are needed, then for each additional region, a separate agent would be required. For example, an agent connected to the |US| region would not be able to create an additional tunnel to the |EU| region. Multiple agent setups are permitted. 

A domain may only be reserved for a single region at a time. It is not possible to geo-balance DNS for the same tunnel name in multiple regions. As an alternative, you may use region-specific subdomains or TLDs if the need arises.

An ngrok Edge can only maintain a collection of endpoints that are within the same region.
