# OpenNMS-Grafana-SSRF-XSPA-
OpenNMS Horizon ver >= 27.0.3 affected by SSRF(XSPA) 

SSRF [Server side request forgery] 
 
[Severity:High]

Assesor observed that it was possible to generate arbitrary requests from server to internal hosts and scan their ports/services.

Affected URL: https://172.23.105.203:8443/opennms/admin/endpoint/index.jsp#!/endpoints/grafana

Affected Field: Grafana URL 

Impact: 

1. Port Scanning remote Internet facing servers, intranet devices and the local web server itself. Banner grabbing is also possible in some cases.
2. Exploiting vulnerable programs running on the Intranet or on the local web server
3. Attacking internal/external web applications that are vulnerable to GET parameter based vulnerabilities (SQLi via URL, parameter manipulation etc.)
4. Fingerprinting intranet web applications using standard application default files & behavior

POC's have been shown below:

Below POC confirms that request is generated from the OpenNMS server: 

![image](https://user-images.githubusercontent.com/16098568/156047015-782d8d4d-84d3-4c07-a551-69981c9ced80.png)


Port 22 Found to be open :

![image](https://user-images.githubusercontent.com/16098568/156047063-f64d8de6-e498-4491-88b1-ffeac7e941cb.png)

Port 21 found to be closed:

![image](https://user-images.githubusercontent.com/16098568/156047088-66d1cf4d-09c4-47ad-b166-e34bc26465ce.png)

Fix: Whitelisting of Grafana ports and disabling banner information disclosure when providing random ports.


Regards

Sahil



