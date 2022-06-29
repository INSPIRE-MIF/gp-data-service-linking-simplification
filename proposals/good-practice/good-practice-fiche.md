# INSPIRE Good Practice: <Name>
  
## Name of the GP [@jescriu + @AntoRot]
Data and Service Linking Simplification

## Description of the GP [@jescriu + @AntoRot]
The current approach for documenting data-service linking on the base of the relevant Implementing Rules and technical guidelines foresees:
  - the documentation of data sets through metadata where a resource locator linking to the service(s) providing online access to the described data set ((for viewing and/or downloading it) is given;
  - 

  
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

  The users of the INSPIRE infrastructure can accessing all available data via the view and download services.
  
  Data providers are experiencing no difficulties anymore to establish working links for downloading and viewing data sets, because  
  
•	The requirements described in this good practice for documenting these links are easy to implement and understand and therefore widely (correctly) to implement by MS.

•	Extensions to existing standards that are not (widely) supported by existing software products are not required anymore.

• The duplication of metadata is reduced by requiring just one metadata record per data set rather than three or more (data, view, download and possibly direct access / WFS). Only the capabilities document and service feed for ATOM's are used to document the service metadata.
  
For client application it becomes easier to implement discovery of and access to data sets, which is the current trend in many geoportal (including the new INSPIRE geoportal).
  
  
## Evidence of implementation & support [@idevisser + @MarieLambois]
  
The (minor) changes in the data set metadata needed on the resource locator elements is implemented in; 
the Dutch metadata profile https://docs.geostandaarden.nl/md/mdprofiel-iso19115/ with instructions on the contents of the elements in https://docs.geostandaarden.nl/eu/INSPIRE-handreiking/#dataset-metadata. 
The validator http://validatie.geostandaarden.nl/etf-webapp/testprojects returns warnings if the requirements on data service linking are not met.
The data is available via view and download services in the Dutch Nationaal Georegister https://www.nationaalgeoregister.nl/geonetwork/srv/dut/catalog.search#/search?facet.q=category%2Finspire&resultType=details&sortBy=relevance&fast=index&_content_type=json&from=1&to=50 (selection on INSPIRE) but also for most other data https://www.nationaalgeoregister.nl/geonetwork/srv/dut/catalog.search#/search?fast=index

@Antonio The Italian metadata profile 
Italian INSPIRE or geo portal 
  
@all other profiles and portals where this is implemented?

@all
Do we have examples where the Download and view services are no longer documented in stand-alone (ISO 19119) service metadata records, but exclusively through the metadata returned by the service itself as a response to a Get Download/View Service Metadata request?


  
## Limitations [@heidivanparys]
> Describe the known limitations of the GP. This information is meant to clarify for what the GP can and cannot be used and/or which are the supported and not supported use cases. This will help understand possible adopters to understand whether the GP fits their requirements.

  
