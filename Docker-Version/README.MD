APIC-EPG-DAG-Update -DOCKER VERSION-

This example docker containter with code that may be used to capture select ACI EPG learned Endpoints and populate PANW Dynamic Address Groups. The script assumes the following information is defined:

Tenant that the EPG's reside in.
EPG Name.
Firewall VSYS that the DAG should be placed in.

Prerequisites:

Docker 

How it works:

This is a self contained docker container with the APIC to DAG script. It has a web front-end and has ACI Toolkit and Palo Networks API toolkits preloaded. The script checks the presence of the appropriate DAGs and creates or removes them as needed. The PANW DAGs are in the format "tenant--EPG" in the defined PANW vsys. An API call is made to the APIC that extracts the Learned Enpoint information and checks to see if the firewall has correct entries. If additions or deletions are needed the script creates an API call to make the appropriate changes. A firewall commit is not required unless Address Objects need to be added or removed.

How to install:

  docker pull djspears/panw:aci-v6
  
  docker run -p 2000:80 -d djspears/panw:aci-v6 /bin/bash -c "/bin/start.sh; tail -f /dev/null"

  To access:
  
  Browse to http://127.0.0.1:2000
  To access the container:
  
    find container id by executing:
 
      docker ps
    
    access container console by executing:
      
      docker exec -it <container id> bash
  
Support Policy
This template is released under an as-is, best effort, support policy. It should be seen as community supported and Palo Alto Networks will contribute our expertise as and when possible. We do not provide technical support or help in using or troubleshooting the components of the project through our normal support options such as Palo Alto Networks support teams, or ASC (Authorized Support Centers) partners and backline support options. The underlying product used by the scripts or templates are still supported, but the support is only for the product functionality and not for help in deploying or using the template or script itself. Unless explicitly tagged, all projects or work posted in our GitHub repository (at https://github.com/PaloAltoNetworks) or sites other than our official Downloads page on https://support.paloaltonetworks.com are provided under the best effort policy.
