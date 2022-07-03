# INSPIRE Good Practice: Data-Service Linking Simplification
  
## Name of the GP

Data-Service Linking Simplification.

## Description of the GP

The current approach for linking INSPIRE data sets and its related network services on the base of the requirements established in the relevant Implementing Rules and Technical Guidelines foresees:
  - the documentation of the data sets through appropriate metadata where, inter alia, a resource locator linking to the service(s) providing online access to the described data set (for viewing and/or downloading it) shall be given, if such online access is available (otherwise, a URL pointing to a publicly available online resource providing additional information about the described data set or data set series shall be given);
  - the documentation of such network services - mainly expliciting here view and download services - through appropriate metadata where a link to the target spatial data set(s) of the service, namely coupled resource, shall be given;
  - the inclusion of an Extended Capabilites section in the Capabilities documents of Open Geospatial Consortium (OGC) view and download web services, which is added to the harmonised structure of Capabilities documents defined in the underlying OGC standards in order to fully comply with the INSPIRE View/Download Service metadata requirements. To this purpose, this section shall include either a reference to the INSPIRE network service metadata available in a Discovery Service (scenario 1) or the capabilities for providing the additional INSPIRE metadata elements which are not mapped to the base service standard (WMS, WMTS, WFS or Atom) elements (scenario 2).

The approach described above has proved to be difficult to be understood and correctly implemented by many organizations, and therefore neither homogeneously nor widely used by Member States. As a result, the accessibility of data sets through view and download services present in the INSPIRE Geoportal is insufficient. This affects the overall usability of the INSPIRE infrastructure and the performance measured through the metadata-based monitoring and reporting indicators.
 
This Good Practice (GP) proposes an alternative approach for specifying the data-service linking in order to simplify the process, reduce the effort in documenting INSPIRE metadata while enabling a greater accessibility of INSPIRE data sets through view and download services in the INSPIRE Geoportal.

When this new approach is used, the following assumptions apply:
  - the data set metadata record shall include additional elements related to view and download services;
  - there is no need for view and download services to be documented through their corresponding service metadata records. The metadata returned by the service itself, as a response to a Get View/Download Service Metadata request, is enough to provide or point to the required information;
  - as a result, the metadata returned by the OGC web services (OWS) can follow an OGC-compliant structure, no longer including the Extended Capabilities section.

  
## INSPIRE component(s)

The INSPIRE components addressed by the GP are:

**Metadata**: this GP provides with an alternative way for describing view and download services ensuring conformance to the principles of the INSPIRE metadata Implementing Rules and Technical Guidelines, which need to be amended according to it.
  
**Network services**: this GP also affects the INSPIRE network services Implementing Rules and Technical Guidelines, specifically for view and download services, since there is no longer the need to keep an extension of the base standard for the service Capabilities documents.

  
## References 
### Normative references

- **[ISO 19115:2003]** - EN ISO 19115:2003, *Geographic information — Metadata*
- **[ISO 19115:2003/Cor 1:2006]** - EN ISO 19115:2003/Cor 1:2006, *Geographic information — Metadata — Technical Corrigendum 1*
- **[ISO/TS 19139:2007]** - ISO/TS 19139:2007, *Geographic information — Metadata — XML schema implementation*
- **[ISO Metadata schemas]** - ISO Metadata schemas
- **[IR for MD]** - Commission Regulation (EC) No 1205/2008 of 3 December 2008 implementing Directive 2007/2/EC of the European Parliament and of the Council as regards metadata 
- **[IR for NS]** - Commission Regulation (EC) No 976/2009 of 19 October 2009 implementing Directive 2007/2/EC of the European Parliament and of the Council as regards the Network Services
- **[IR for ISDSS]** - Commission Regulation (EU) No 1089/2010 of 23 November 2010 implementing Directive 2007/2/EC of the European Parliament and of the Council as regards interoperability of spatial data sets and services
- **[INSPIRE MD TG]** - JRC. *Technical Guidance for the implementation of INSPIRE dataset and service metadata based on ISO/TS 19139:2007*.  v2.0.1 - 2017-03-02
- **[INSPIRE NS - Download Service TG]** - JRC. *Technical Guidance for the implementation of INSPIRE Download Services*. v3.1 - 2013-08-09
- **[INSPIRE NS - View Service TG]** - JRC. *Technical Guidance for the implementation of INSPIRE View Services*. v3.11 - 2013-04-04
- **[RFC 4287]** - Internet Engineering Task Force (IETF). RFC 4287, *The Atom Syndication Format*. Initial release: December 2005

[ISO 19115:2003]: https://www.iso.org/standard/26020.html?browse=tc "ISO 19115:2003, Geographic information — Metadata"
[ISO 19115:2003/Cor 1:2006]: https://www.iso.org/standard/44361.html?browse=tc "ISO 19115:2003/Cor 1:2006, Geographic information — Metadata — Technical Corrigendum 1"
[ISO/TS 19139:2007]: https://www.iso.org/standard/32557.html?browse=tc "ISO/TS 19139:2007, Geographic information — Metadata — XML schema implementation"
[ISO Metadata schemas]: https://www.isotc211.org/2005/gmd "ISO Metadata schemas"
[IR for MD]: https://eur-lex.europa.eu/legal-content/EN/TXT/PDF/?uri=CELEX:02008R1205-20081224&qid=1656887526534&from=EN "Implementing Rule for Metadata (consolidated version of 24/12/2008)"
[IR for NS]: https://eur-lex.europa.eu/legal-content/EN/TXT/HTML/?uri=CELEX:02009R0976-20141231&from=EN "Implementing Rule for Network Services (consolidated version of 31/12/2014)"
[IR for ISDSS]: https://eur-lex.europa.eu/legal-content/EN/TXT/HTML/?uri=CELEX:02010R1089-20141231&from=EN "Implementing Rules for interoperability of spatial data sets and services (consolidated version of 31/12/2014)"
[INSPIRE MD TG]: https://inspire.ec.europa.eu/id/document/tg/metadata-iso19139 "Technical Guidance for the implementation of INSPIRE dataset and service metadata based on ISO/TS 19139:2007"
[INSPIRE NS - Download Service TG]: https://inspire.ec.europa.eu/documents/technical-guidance-implementation-inspire-download-services "Technical Guidance for the implementation of INSPIRE Download Services"
[INSPIRE NS - View Service TG]: https://inspire.ec.europa.eu/documents/technical-guidance-implementation-inspire-view-services-1 "Technical Guidance for the implementation of INSPIRE View Services"
[RFC 4287]: https://www.rfc-editor.org/rfc/rfc4287 "The Atom Syndication Format"

  
### Other references

An initial proposal for a simplification approach was defined with the "[Discussion Paper on possible simplification of data-service linking in INSPIRE](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/blob/main/resources/Discussion%20Paper%20on%20data-service%20linking%20v0.5.docx)" that reflected the discussions in the MIG-T and in the temporary Sub-group 2017.4 on validation and conformity testing on the topic of data-service linking.

The current work and consolidated proposals are documented in the [INSPIRE-MIF Data-Service Linking Simplification GitHub repository](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification) 
  
## Relevance & expected benefits

This GP aims at making the data-service linking process easier in order to overcome the obstacles and difficulties encountered by Member States in the implementation of the current INSPIRE requirements and consequently improve the accessibility of the INSPIRE data sets through view and download services, as well as the usability of the infrastructure through the INSPIRE Geoportal.

The expected benefits are described in the aforementioned Discussion Paper, i.e.:

- Make it easier for client application to implement discovery of and access to data sets, following the new data-centric approach which is the current trend in many geoportals (including the new INSPIRE Geoportal);
- Reduce the duplication of metadata by requiring just one metadata record per data set rather than three or more (data, view, download ,...);
- Make it easier for software developers to implement network services and metadata, by using base standards for the network services without the need to add any (undesirable) extensions.

  
## Intended Outcome

The users of the INSPIRE infrastructure can access all available data via the view and download services.
  
When using this GP, data providers are experiencing no difficulties anymore to establish downloadable and viewable data sets, because: 
  
- The requirements described in this good practice for documenting these links are easy to be implemented and understood, and therefore widely used and correctly implemented by MS.

- INSPIRE-specific extensions to existing standards that are not widely supported by existing software products. This GP makes them unnecessary from now onwards, since it allows implementer's organizations to access off-the-shelf software withouth worrying anymore about compliance to INSPIRE-specific extensions. 

- The duplication of metadata information is reduced. Only one metadata record is required per data set, avoiding the need for documenting additional service metadata records (view, download and possibly direct access / WFS). Only the Capabilities document and service feed for ATOM's are used to document the service metadata, removing possible inconsistencies.

- The amount of metadata in the INSPIRE Geoportal and the national geoportals could be reduced, making search easier and reducing the size of information to be stored and indexed.
  
- For client applications, it becomes easier to implement discovery of and access to data sets. This helps implementers to focus on INSPIRE specificity following a data-centric approach, rather than devoting excesive time to documenting the resources, mainly services, and configuring them properly.
  
  
## Evidence of implementation & support
  
The (minor) changes in the data set metadata needed on the resource locator elements is implemented in:
  
The Dutch metadata profile https://docs.geostandaarden.nl/md/mdprofiel-iso19115/ with instructions on the contents of the elements in https://docs.geostandaarden.nl/eu/INSPIRE-handreiking/#dataset-metadata. 
  
The validator http://validatie.geostandaarden.nl/etf-webapp/testprojects returns warnings if the requirements on data service linking are not met.
  
The data is available via view and download services in the Dutch Nationaal Georegister https://www.nationaalgeoregister.nl/geonetwork/srv/dut/catalog.search#/search?facet.q=category%2Finspire&resultType=details&sortBy=relevance&fast=index&_content_type=json&from=1&to=50 (selection on INSPIRE) but also for most other data https://www.nationaalgeoregister.nl/geonetwork/srv/dut/catalog.search#/search?fast=index

The [Italian metadata profile](https://agid.github.io/geodocs/rndt-lg/2.0.1/), aligned to the INSPIRE TGs 2.0, already includes the additional elements in the data sets metadata records for the documentation of the information about the services providing online access to the described data sets.
  
The national profile has extended the scope of those metadata elements by also including direct access for downloading the data set (e.g. a URL providing a zip file) or a web page (with additional information about the data set, as per in the metadata TG Requirement 1.8). Consequently, the [Protocol Value register](https://inspire.ec.europa.eu/metadata-codelist/ProtocolValue) has been extended at [national level](https://registry.geodati.gov.it/metadata-codelist/ProtocolValue) to include the related items. That means in the metadata records additional online resources besides the view and download services can be documented.
  
Some examples of data sets metadata records including the additional information for view and download services and coming from the national catalogue:
https://geodati.gov.it/RNDT/rest/document?id=r_liguri%3AD.1179
  
https://geodati.gov.it/RNDT/rest/document?id=r_basili:-1a8220d0:1507f878817:-6181

https://geodati.gov.it/RNDT/rest/document?id=ispra_rm%3A0029CNATHB_DT

https://geodati.gov.it/RNDT/rest/document?id=ispra_rm%3A0016_WFD_RBD_DT

The same approach is also defined in the [French metadata national Guidelines](http://cnig.gouv.fr/wp-content/uploads/2019/12/Guide-de-saisie-des-%C3%A9l%C3%A9ments-de-m%C3%A9tadonn%C3%A9es-INSPIRE-v2.0-1.pdf) and implemented into the [French catalog](https://www.geocatalogue.fr/).
  
@all other profiles and portals where this is implemented?

@all
Do we have examples where the Download and view services are no longer documented in stand-alone (ISO 19119) service metadata records, but exclusively through the metadata returned by the service itself as a response to a Get Download/View Service Metadata request?

## Limitations

This GP is not applicable for services based on the [OGC API family of standards](https://ogcapi.ogc.org/). This is because a mapping between the INSPIRE metadata elements and the [OpenAPI Specification]([url](https://spec.openapis.org/oas/latest.html)) has not yet been agreed. See also the [Technical guidelines for setting up an INSPIRE Download service based on the OGC API-Features standard](https://github.com/INSPIRE-MIF/gp-ogc-api-features/blob/master/spec/oapif-inspire-download.md)
  
Complying with this GP and also providing metadata for services in the discovery service will result in the duplication of certain INSPIRE metadata elements, which can lead to inconsistencies if the metadata elements are not kept in sync by means of automated processes.
