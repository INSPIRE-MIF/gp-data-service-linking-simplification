# INSPIRE Good Practice: <Name>
  
## Name of the GP [@jescriu + @AntoRot]

Data and Service Linking Simplification

## Description of the GP [@jescriu + @AntoRot]

The current approach for documenting data-service linking on the base of the INSPIRE requirements defined in the relevant Implementing Rules and technical guidelines foresees:
  - the documentation of data sets through metadata where, inter alia, a resource locator linking to the service(s) providing online access to the described data set (for viewing and/or downloading it) is given;
  - the documentation of services (mainly view and download services) through metadata where a link to the target spatial data set(s) of the service is given;
  - the inclusion of the extended capabilites section (extended with respect to the base standards) in the GetCapabilities document of view and download services in order to fully comply with
the INSPIRE View/Download Service metadata requirements. To this purpose, this section shall include either a reference to the INSPIRE network service metadata in a Discovery Service (scenario 1) or the capabilities for mapping INSPIRE metadata elements to the base service standard (WMS, WMTS, WFS or Atom) elements (scenario 2).

The approach descrived above has proved to be difficult to implement and understand and therefore not widely (correctly) implemented by Member States, with the consequence that the accessibility to INSPIRE data sets through view and download services (and through the INSPIRE geoportal) is low. This affects the overall usability of the INSPIRE infrastructure and the performance measured in the metadata-based monitoring and reporting.
 
This Good Practice (GP) proposes an alternative approach for documenting data-service linking in order to simplify the process, enable a greater availability of INSPIRE data sets through view and download services and consequently improve their accessibility through the INSPIRE geoportal.

This new approach is based on the following assumptions:
  - the data set metadata record shall include additional elements related to view and download services;
  - the view and download services are no longer documented in stand-alone service metadata records, but exclusively through the metadata returned by the service itself as a response to a Get View/Download Service Metadata request;
  - the metadata returned by the service no longer includes the extended capabilities section.

  
## INSPIRE component(s) [@jescriu + @AntoRot]

The INSPIRE components addressed by the GP are:

**Metadata**: the GP provides with an alternative way for describing view and download services and ensure the conformance to the INSPIRE metadata Implementing Rules for services in any cases.
  
**Network services**: specifically for view and download services, the GP affects the service metadata document removing the need for an extension of the base standard.

  
## References [@jescriu + @AntoRot]
### Normative reference

- **[ISO 19115:2005]** - EN ISO 19115:2005, *Geographic information — Metadata*
- **[ISO/TS 19139:2007]** - ISO/TS 19139:2007, *Geographic information — Metadata — XML schema implementation*
- **[IRs for NS]** - Commission Regulation (EC) No 976/2009 of 19 October 2009 implementing Directive 2007/2/EC of the European Parliament and of the Council as regards the Network Services
- **[IRs for ISDSS]** - Commission Regulation (EU) No 1089/2010 of 23 November 2010 implementing Directive 2007/2/EC of the European Parliament and of the Council as regards interoperability of spatial data sets and services
- **[INSPIRE MD TG]** - JRC. *Technical Guidance for the implementation of INSPIRE dataset and service metadata based on ISO/TS 19139:2007*.  v2.0.1 - 2017-03-02
- **[INSPIRE NS - Download Service TG]** - JRC. *Technical Guidance for the implementation of INSPIRE Download Services*. v3.1 - 2013-08-09
- **[INSPIRE NS - View Service TG]** - JRC. *Technical Guidance for the implementation of INSPIRE View Services*. v3.11 - 2013-04-04
- **[RFC 4287]** - Internet Engineering Task Force (IETF). RFC 4287, *The Atom Syndication Format*. Initial release: December 2005

[ISO 19115:2005]: https://www.isotc211.org/2005/gmd "ISO 19115:2005, Geographic information — Metadata"
[ISO/TS 19139:2007]: https://www.isotc211.org/2005/gmd/ "ISO/TS 19139:2007, Geographic information — Metadata — XML schema implementation"
[IRs for NS]: https://eur-lex.europa.eu/legal-content/EN/TXT/HTML/?uri=CELEX:02009R0976-20141231&from=EN "Implementing Rules for Network Services (consolidated version of 31/12/2014)"
[IRs for ISDSS]: https://eur-lex.europa.eu/legal-content/EN/TXT/HTML/?uri=CELEX:02010R1089-20141231&from=EN "Implementing Rules for interoperability of spatial data sets and services (consolidated version of 31/12/2014)"
[INSPIRE MD TG]: https://inspire.ec.europa.eu/id/document/tg/metadata-iso19139 "Technical Guidance for the implementation of INSPIRE dataset and service metadata based on ISO/TS 19139:2007"
[INSPIRE NS - Download Service TG]: https://inspire.ec.europa.eu/documents/technical-guidance-implementation-inspire-download-services "Technical Guidance for the implementation of INSPIRE Download Services"
[INSPIRE NS - View Service TG]: https://inspire.ec.europa.eu/documents/technical-guidance-implementation-inspire-view-services-1 "Technical Guidance for the implementation of INSPIRE View Services"
[RFC 4287]: https://www.rfc-editor.org/rfc/rfc4287 "The Atom Syndication Format"

  
### Other references

An initial proposal for a simplification approach was defined with the "[Discussion Paper on possible simplification of data-service linking in INSPIRE](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/blob/main/resources/Discussion%20Paper%20on%20data-service%20linking%20v0.5.docx)" that reflected the discussions in the MIG-T and in the temporary sub-group 2017.4 on validation and conformity testing on the topic of data-service linking.

  
## Relevance & expected benefits [@AntoRot + @jescriu]

The GP aims at making the data-service linking process easier in order to overcome the obstacles and difficulties encountered by Member States in the implementation of the current INSPIRE requirements and consequently improve the accessibility and the usability of the INSPIRE data sets through view and download services and in general of the infrastructure through the INSPIRE geoportal.

The expected benefits are described in the aforementioned Discussion Paper, i.e.:

  - Make it easier for client application to implement discovery of and access to data sets, following the new data-centric approach which is the current trend in many geoportal (including the new INSPIRE geoportal);
  - Reduce the duplication of metadata by requiring just one metadata record per data set rather than three or more (data, view, download ,...);
  - Make it easier for software developers to implement network services and metadata, by using base standards for the network services without any need to add extensions.

  
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

The [Italian metadata profile](https://agid.github.io/geodocs/rndt-lg/2.0.1/), aligned to the INSPIRE TGs 2.0, already includes the additional elements in the data sets metadata records for the documentation of the information about the services providing online access to the described data sets.

The national profile has extended the scope of those metadata elements by also including direct access for downloading the data set (e.g. a URL providing a zip file) or a web page (with additional information about the data set, as per in the metadata TG Requirement 1.8). Consequently, the [Protocol Value register](https://inspire.ec.europa.eu/metadata-codelist/ProtocolValue) has been extended at [national level](https://registry.geodati.gov.it/metadata-codelist/ProtocolValue) to include the related items. That means in the metadata records additional online resources besides the view and download services can be documented.
  
Some examples of data sets metadata records including the additional information for view and download services and coming from the national catalogue:
https://geodati.gov.it/RNDT/rest/document?id=r_liguri%3AD.1179
  
https://geodati.gov.it/RNDT/rest/document?id=r_basili:-1a8220d0:1507f878817:-6181

https://geodati.gov.it/RNDT/rest/document?id=ispra_rm%3A0029CNATHB_DT

https://geodati.gov.it/RNDT/rest/document?id=ispra_rm%3A0016_WFD_RBD_DT
  
@all other profiles and portals where this is implemented?

@all
Do we have examples where the Download and view services are no longer documented in stand-alone (ISO 19119) service metadata records, but exclusively through the metadata returned by the service itself as a response to a Get Download/View Service Metadata request?


  
## Limitations [@heidivanparys]
> Describe the known limitations of the GP. This information is meant to clarify for what the GP can and cannot be used and/or which are the supported and not supported use cases. This will help understand possible adopters to understand whether the GP fits their requirements.

  
