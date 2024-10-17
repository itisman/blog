# How to to add subscribe links for Quantumult X?

If the VPN website has no Quantumult X subscription link, SS/SSR subscription link can be used. If V2Ray and Trojan subscription link cannot be directly imported into Quantumult X,
You need to add a resource parser, and after using the resource parser, you can easily import Quantumult X unaware nodes or subscription links.

## How do I add a resource parser?

Open the Quantumult X configuration file, find the [general] location, and add the following code:
resource_parser_url=https://raw.githubusercontent.com/KOP-XIAO/QuantumultX/master/Scripts/resource-parser.js
Alternative:
resource_parser_url=https://fastly.jsdelivr.net/gh/KOP-XIAO/QuantumultX@master/Scripts/resource-parser.js

## Reference

[https://github.com/kjfx/QuantumultX](GithubQuantumultX)
