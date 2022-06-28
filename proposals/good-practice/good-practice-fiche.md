# INSPIRE Good Practice: <Name>
  
## Name of the GP [@jescriu + @AntoRot]
> Name of the proposed good practice.

## Description of the GP [@jescriu + @AntoRot]
> Provide a short description of the proposed GP.

  
## INSPIRE component(s) [@jescriu + @AntoRot]
> Describe the INSPIRE component(s) addressed by the GP (data, metadata, network services, data sharing, monitoring & reporting, registers, …)

  
## References [@jescriu + @AntoRot]
### Normative reference
> Provide a normative reference to the detailed description, documentation or specification describing the GP.

  
### Other references
> Provide other references, e.g. to papers, presentations etc.

  
## Relevance & expected benefits [@AntoRot + @jescriu]
> Describe why the GP was developed. In the description, please explain whether the GP 
> •	aims at meeting (some of) the INSPIRE requirements  AND/OR
> •	goes beyond the requirements of the IRs and TGs in order to improve the usability / usefulness of the infrastructure (including INSPIRE extensions) AND/OR
> •	is using INSPIRE data or services to perform a certain task
> and what the expected benefits are for INSPIRE implementers, users or other stakeholders.
> A full text description of the problem addressed by the GP may also be provided. It can be any length but is likely to be no more than a few sentences. 

  
## Intended Outcome [@idevisser + @MarieLambois]

  The users of the INSPIRE infrastructure can accessing the data via the view and download services.

Data providers are experiencing no difficulties anymore to implement the good practice requirements and recommendations, because  
•	extensions to existing standards that are not (widely) supported by existing software products are not required anymore.

•	It becomes easy  to establish working links for downloading and viewing data sets for all MS, e.g. because the requirements described in this good practice for documenting these links are easy to implement and understand and therefore widely (correctly) to implement by MS;

•	There is no duplication between the metadata required for services in the Metadata and the Network Services IRs. The duplication of metadata is reduced by requiring just one metadata record per data set rather than three or more (data, view, download and possibly direct access / WFS);

Make it easier for client application to implement discovery of and access to data sets, which is the current trend in many geoportal (including the new INSPIRE geoportal).
  
A simplified approach for data-service linking INSPIRE metadata aim at supporting (at least) the following user stories:
•	As a user, I want to be able to search relevant data sets using a discovery service (via a geoportal) based on at least the search criteria defined in Art. 11(2) of the Directive. .
•	As a user, once I have discovered a data set in the discovery service, I want to be able to find in the metadata sufficient information to directly access the service metadata of the download/view service(s) that provide access to the selected/discovered data.
•	As a user, once I have discovered a data set in the discovery service, I want to be able to find in the metadata sufficient information to directly download/view the selected/discovered data.
  
The proposed approach aims at implementing these requirements in the simplest possible way.


  
## Evidence of implementation & support [@idevisser + @MarieLambois]
> Where relevant, provide evidence that the solution 
> •	has been put into practice, ideally in more than one context (more than one domain / tool / country), 
> •	has received broader support, by referring to online discussion or documentation of the activity in an appropriate publicly available resource (e.g. GitHub, Thematic Clusters platform),
> •	has been endorsed by a standardization body, and/or
> •	has a well-defined governance structure and/or sustainability plan.

  
## Limitations [@heidivanparys]
> Describe the known limitations of the GP. This information is meant to clarify for what the GP can and cannot be used and/or which are the supported and not supported use cases. This will help understand possible adopters to understand whether the GP fits their requirements.

  
