# Let's Encrypt Certificate Manager
### About
The Let's Encrypt Certificate Manager obtains a free (SAN) SSL Certificate from the [Let's Encrypt CA](https://letsencrypt.org/) and adds it to Rancher's certificate store. Once the certificate is created it is scheduled for auto-renewal 14-days before expiration. The renewed certificate is propagated to all applicable load balancer services.
     
### Usage
 1. Accept the terms of service.
 2. Select the API version to use. The Sandbox API should be used for testing purposes.
 3. Fill in your email address.
 4. Enter the name for storing the certificate in Rancher. If you specify the name of an existing resource it will be overwritten with a renewed certificate.
 4. Enter one or more domain names. The first domain will be used as the Common Name property of the certificate.
 5. Select the DNS provider which manages the DNS zone(s) for all specified domains.
 5. Fill in the required credentials for the chosen DNS provider.  

If you want your certificate to be automatically renewed leave the service running. Otherwise you may remove the service once the certificate has appeared in Rancher's certificate store.
   
Certificate and private key can be accessed by arbitrary services by mounting the container volume `/etc/letsencrypt`.
    
### Suggestions & issue reports
Please submit suggestions or any issues you find to the [rancher-letsencrypt](https://github.com/janeczku/rancher-letsencrypt) GitHub repo.