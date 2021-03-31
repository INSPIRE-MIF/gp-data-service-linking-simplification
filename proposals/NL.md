# Data and Service Linking Simplification - Proposal NL

## Introduction

Country: the Netherlands

Short description: **Implementation of the requirements and recommendations as defined in the discussion paper**
This proposal implements the requirements and recommendations as described in the in the MIG-T discussed [Data and Service Linking Simplification proposal](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/blob/main/resources/Discussion%20Paper%20on%20data-service%20linking%20v0.5.docx) and the agreed [protocol code list](https://inspire.ec.europa.eu/metadata-codelist/ProtocolValue) as presented during the MIG-T. The metadata is based on [INSPIRE TG version 2.0.1](https://inspire.ec.europa.eu/id/document/tg/metadata-iso19139). In example 1 the links to the required Get View and Download Service Metadata request of a dataset utilizing the ISO 19115 CI_OnlineResource MD element used by INSPIRE Resource Locator element as proposed as in the new TG Requirement 1.8.

Supplementary to the requirement in the [Data and Service Linking Simplification proposal](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/blob/main/resources/Discussion%20Paper%20on%20data-service%20linking%20v0.5.docx) we descibed proposals for additional situations; 
2 The view (WMS) and download (WFS and ATOM) service provide more then one dataset
3 Other services are available
4 Other output formats are available

In this proposal the description element is used to distinguish between acces and endpoint.
The protocol element contains in case of an endpoint values of the iana mediatype codelist.

This aproach is implemented in the Dutch metadata profiile for several years


## Proposal body

### Details of the proposal

Supplementary  to requierement in the [Data and Service Linking Simplification proposal](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/blob/main/resources/Discussion%20Paper%20on%20data-service%20linking%20v0.5.docx) the description element with [code list values](https://inspire.ec.europa.eu/metadata-codelist/OnLineDescriptionCode) is used, to distinguish between the required response of a Get View/Download Service Metadata request of the service providing access to the data set and the direct access for downloading and/or viewing the described data set. This element and code list is required in the TG INSPIKRE TG Requirement 5.2: metadata/2.0/req/sds-invocable/access-point, its use is extended to all services in the Resource Locator element of the dataset metadata.

In case of the required response of a Get View/Download Service Metadata request, with the OnlineDescriptionCode accessPoint, the protocol element contains a value of the the agreed [protocol code list](https://inspire.ec.europa.eu/metadata-codelist/ProtocolValue)
In case of the direct access for downloading and/or viewing, with the the OnlineDescriptionCode endPoint, the protocol element contains a value of the [iana mediatype](https://docs.geostandaarden.nl/md/mdprofiel-iso19115/#codelist-mediatypes).

Assumptions;
- The application profile element with servicetype value view or download as required in the new TG Requirement 1.8 should only be used in case of INSPIRE conformant (or intended to be conformant) network services 
- The application profile element with servicetype value other should only be used in case of INSPIRE conformant (or intended to be conformant) spatial data services 

- the license on the data (public domain or CC0 etc.) applies also on the linked services, which made this data accessible


Due to the limited time we only focussed on this task, which means that the complete metadata examples are not yet available.



** 1 The required Get View and Download Service Metadata request**
This is the most simple situation, where the view (WMS) and download (WFS) service provide one dataset. These INSPIRE services are accessable via the CI_OnlineResource MD element in the dataset metadata.

The metadata record contains two links, one to the view and one to the download service.
The links have the following specifications;


1.1	This link contains the URL to the capabilities of the INSPIRE view service (WMS) containing the dataset
- The protocol element contains the value OGC:WMS and via the anchor the defenition of the protocol (http://www.opengis.net/def/serviceType/ogc/wms)
- applicationProfile element contains the value view and via the anchor the servicetype (http://inspire.ec.europa.eu/metadata-codelist/SpatialDataServiceType/view)
- The name element contains the name of the service
- The description element contains the value accesspoint, because the URL is providing the capabilities (the required response of a Get View/Download Service Metadata request of the service providing access to the data set)
	
1.2	This link contains the URL to the capabilities of the INSPIRE download service (WFS) containing the dataset
- The protocol element contains the value OGC:WFS and via the anchor the definition of the protocol. (http://www.opengis.net/def/serviceType/ogc/wfs)
- applicationProfile element contains the value download and via the servicetype ( http://inspire.ec.europa.eu/metadata-codelist/SpatialDataServiceType/download)
- The name element contains the name of the service
- The description element contains the value accesspoint, because the URL is providing the capabilities (the required response of a Get View/Download Service Metadata request of the service providing access to the data set)

1.3	This link contains the URL to the service feed of the INSPIRE download service (ATOM) containing the dataset
- The protocol element contains the value INSPIRE Atom and via the anchor the definition of the protocol.(https://tools.ietf.org/html/rfc4287)
- applicationProfile element contains the value download and via the servicetype ( http://inspire.ec.europa.eu/metadata-codelist/SpatialDataServiceType/download) 
- The name element contains the name of the service
- The description element contains the value accesspoint, because the URL is providing the the required response of a Get View/Download Service Metadata request of the service providing access to the data set

** 2 The view (WMS) and download (WFS and ATOM) service provide more then one dataset**

In this case the view (WMS) and download (WFS and ATOM) service provide more then one dataset. In the discussionpaper the recommandation is; *For cases, where a network service provides more than one data set, resource locators should also be given that contain links for the direct access for downloading and/or viewing the described data set.*  The CI_OnlineResource MD element in the metadata description of the datasets, links to the required response of a Get View/Download Service Metadata request (capabilities) as described before in 1 and to the endpoint where the described dataset is directly viewable or downloadable. The metadata record contains four links.

The supplemental links to the endpoint where the dataset is directly downloadable and viewable has the following specifications;

2.1	This link contains the URL to the described dataset in the INSPIRE view service (WMS) via a Getmap request
- The element protocol element contains the value png and in the anchor the defenition of the mediatype(https://www.iana.org/assignments/media-types/image/png), because this is the choosen output format in the request.
- applicationProfile element contains the value view and via the anchor the definition of the servicetype (http://inspire.ec.europa.eu/metadata-codelist/SpatialDataServiceType/view)
- The name element contains the name of the layer containing the described dataset
- The description element contains the value endpoint and via the anchor the definition of the URL type http://inspire.ec.europa.eu/metadata-codelist/OnLineDescriptionCode/endPoint, because the URL is directly providing data.


2.2	This link contains the URL to the described dataset in the INSPIRE download service (WFS) via a getFeature request
- The element protocol element contains the value gml and in the anchor the defenition of the mediatype(https://www.iana.org/assignments/media-types/application/gml+xml), because this is the choosen output format in the request.
- applicationProfile element contains the value download and via the anchor the definition of the servicetype (http://inspire.ec.europa.eu/metadata-codelist/SpatialDataServiceType/download)
- The name element contains the name of the featureType containing the described dataset
- The description element contains the value endpoint and via the anchor the definition of the URL type http://inspire.ec.europa.eu/metadata-codelist/OnLineDescriptionCode/endPoint, because the URL is directly providing data.

2.3	This link contains the URL to the described dataset in the INSPIRE download service (ATOM) via the dataset feed
- The element protocol element contains the value gml and in the anchor the defenition of the mediatype(https://www.iana.org/assignments/media-types/application/gml+xml), because this is the format of the choosen dataset feed.
- The applicationProfile element contains the value download and via the anchor the definition of the servicetype (http://inspire.ec.europa.eu/metadata-codelist/SpatialDataServiceType/download)
- The name element contains the name of the dataset feed containing the described dataset
- The description element contains the value endpoint and via the anchor the definition of the URL type http://inspire.ec.europa.eu/metadata-codelist/OnLineDescriptionCode/endPoint, because the URL is directly providing data.


** 3 other services are available**

In this case are beside the required view and download service as descibed in 1, additional services available. This can be any servicetype. For instance an OGC API fatures or a WFS of which it is not intended to be the INSPIRE download service. 

3.1	This link contains the URL to a WFS containing the dataset. This WFS is not intended to fulfil the INSPIRE requirements 
- The protocol element contains the value OGC:WFS and via the anchor the definition of the protocol. (http://www.opengis.net/def/serviceType/ogc/wfs)
- The applicationProfile element contains the value other and via the anchor the definition of the servicetype ( http://inspire.ec.europa.eu/metadata-codelist/SpatialDataServiceType/other) it is not (and not intended to be) an INSPIRE conformant network service
- The name element contains the name of the service
- The description element contains the value accesspoint, because the URL is providing the capabilities

3.2	This link contains the URL to a OGC API Feature containing the dataset. This OGC API Feature is not (yet) intended to fulfil the INSPIRE requirements 
- The protocol element contains the value OGC:API features and via the anchor the definition of the protocol. (http://www.opengis.net/def/interface/ogcapi-features)
- The applicationProfile element contains the value other and via the anchor the definition of the servicetype ( http://inspire.ec.europa.eu/metadata-codelist/SpatialDataServiceType/other) it is not (and not intended to be) an INSPIRE conformant network service
- The name element contains the name of the service
- The description element contains the value accesspoint, because the URL is providing the service description


** 4 other output formats are available**

In this case the service support more output formats. Additional to 1 and 2 the direct links to data in a different format is also available. This can be both an INSPIRE complient or not INSPIRE complient service (application profle download or other). It is also possible to link direct to a zip, the application profile in that case is empty.

4.1 This link contains the URL to the described dataset in the INSPIRE download service (WFS) via a getFeature request
- The element protocol element contains the value json and in the anchor the defenition of the mediatype(https://www.iana.org/assignments/media-types/application/json), because this is the choosen output format in the request.
- applicationProfile element contains the value download and via the anchor the definition of the servicetype (http://inspire.ec.europa.eu/metadata-codelist/SpatialDataServiceType/download)
- The name element contains the name of the featureType containing the described dataset
- The description element contains the value endpoint and via the anchor the definition of the URL type http://inspire.ec.europa.eu/metadata-codelist/OnLineDescriptionCode/endPoint, because the URL is directly providing data.

### Concept model


### Examples of scenarios and metadata (XML encoded)
** 1 the required Get View and Download Service Metadata request**


1.1 link to the WMS view service
```xml
<examplexml>
                  <gmd:onLine>
                  <gmd:CI_OnlineResource>
                     <gmd:linkage>
                        <gmd:URL>http://inspirelab.geonovum.nl/test/kad/wms?request=GetCapabilities&amp;service=WMS</gmd:URL>
                     </gmd:linkage>
                     <gmd:protocol>
                        <gmx:Anchor xlink:href="http://www.opengis.net/def/serviceType/ogc/wms">OGC:WMS</gmx:Anchor>
                     </gmd:protocol>
                     <gmd:applicationProfile>
                        <gmx:Anchor xlink:href="http://inspire.ec.europa.eu/metadata-codelist/SpatialDataServiceType/view">view</gmx:Anchor>
                     </gmd:applicationProfile>
                     <gmd:name>
                        <gco:CharacterString>Bestuurlijke grenzen WMS</gco:CharacterString>
                     </gmd:name>
                     <gmd:description>
                        <gmx:Anchor xlink:href="http://inspire.ec.europa.eu/metadata-codelist/OnLineDescriptionCode/accessPoint">accessPoint</gmx:Anchor>
                     </gmd:description>
                  </gmd:CI_OnlineResource>
               </gmd:onLine>
</examplexml>
```

1.2 link to the WFS download service
```xml
<examplexml>
               <gmd:onLine>
                  <gmd:CI_OnlineResource>
                     <gmd:linkage>
                        <gmd:URL>http://inspirelab.geonovum.nl/test/kad/wfs?request=GetCapabilities&amp;service=WFS</gmd:URL>
                     </gmd:linkage>
                     <gmd:protocol>
                        <gmx:Anchor xlink:href="http://www.opengis.net/def/serviceType/ogc/wfs">OGC:WFS</gmx:Anchor>
                     </gmd:protocol>
                     <gmd:applicationProfile>
                        <gmx:Anchor xlink:href="http://inspire.ec.europa.eu/metadata-codelist/SpatialDataServiceType/download">download</gmx:Anchor>
                     </gmd:applicationProfile>
                     <gmd:name>
                        <gco:CharacterString>Bestuurlijke grenzen WFS</gco:CharacterString>
                     </gmd:name>
                     <gmd:description>
                        <gmx:Anchor xlink:href="http://inspire.ec.europa.eu/metadata-codelist/OnLineDescriptionCode/accessPoint">accessPoint</gmx:Anchor>
                     </gmd:description>
                  </gmd:CI_OnlineResource>
               </gmd:onLine>
</examplexml>
```

1.3 link to the ATOM download service
```xml
<examplexml>

               <gmd:onLine>
                  <gmd:CI_OnlineResource>
                     <gmd:linkage>
                        <gmd:URL>http://inspirelab.geonovum.nl/test/atom/cbs/servicefeed.xml</gmd:URL>
                     </gmd:linkage>
                     <gmd:protocol>
                        <gmx:Anchor xlink:href="https://tools.ietf.org/html/rfc4287">INSPIRE Atom</gmx:Anchor>
                     </gmd:protocol>
                     <gmd:applicationProfile>
                        <gmx:Anchor xlink:href="http://inspire.ec.europa.eu/metadata-codelist/SpatialDataServiceType/download">Downloaddienst</gmx:Anchor>
                     </gmd:applicationProfile>
                     <gmd:name>
                        <gco:CharacterString>Wijk- en Buurtkaart 2018</gco:CharacterString>
                     </gmd:name>
                     <gmd:description>
                        <gmx:Anchor xlink:href="http://inspire.ec.europa.eu/metadata-codelist/OnLineDescriptionCode/accessPoint">accessPoint</gmx:Anchor>
                     </gmd:description>
                  </gmd:CI_OnlineResource>
               </gmd:onLine>
</examplexml>
```

** 2 The view (WMS) and download (WFS and ATOM) service provide more then one dataset**

2.1 link to the described dataset in the WMS view service
```xml
<examplexml>
<gmd:onLine>
                  <gmd:CI_OnlineResource>
                     <gmd:linkage>
                        <gmd:URL>http://inspirelab.geonovum.nl/test/rws/wms?version=1.3.0&amp;request=Getmap&amp;layers=krw_stroomgebieddistricten_rws_2018&amp;WIDTH=2000&amp;HEIGHT=2000&amp;CRS=EPSG:4258&amp;BBOX=50.7293,2.95863,53.762,7.252&amp;format=image/png</gmd:URL>
                     </gmd:linkage>
                     <gmd:protocol>
                        <gmx:Anchor xlink:href="https://www.iana.org/assignments/media-types/image/png">png</gmx:Anchor>
                     </gmd:protocol>
                     <gmd:applicationProfile>
                        <gmx:Anchor xlink:href="http://inspire.ec.europa.eu/metadata-codelist/SpatialDataServiceType/view">Raadpleegdienst</gmx:Anchor>
                     </gmd:applicationProfile>
                     <gmd:name>
                        <gco:CharacterString>krw_stroomgebieddistricten_rws_2018</gco:CharacterString>
                     </gmd:name>
                     <gmd:description>
                        <gmx:Anchor xlink:href="http://inspire.ec.europa.eu/metadata-codelist/OnLineDescriptionCode/endPoint">endPoint</gmx:Anchor>
                     </gmd:description>
                  </gmd:CI_OnlineResource>
               </gmd:onLine>
</examplexml>
```

2.2 link to the described dataset in the WFS download service
```xml
<examplexml>
              <gmd:onLine>
                  <gmd:CI_OnlineResource>
                     <gmd:linkage>
                        <gmd:URL>http://inspirelab.geonovum.nl/test/rws/wfs?request=GetFeature&amp;service=WFS&amp;version=2.0.0&amp;typeName=kaderrichtlijnwater:krw_stroomgebieddistricten_rws_2018&amp;outputFormat=text%2Fxml%3B%20subtype%3Dgml%2F3.1.1</gmd:URL>
                     </gmd:linkage>
                     <gmd:protocol>
                        <gmx:Anchor xlink:href="https://www.iana.org/assignments/media-types/application/gml+xml">gml</gmx:Anchor>
                     </gmd:protocol>
                     <gmd:applicationProfile>
                        <gmx:Anchor xlink:href="http://inspire.ec.europa.eu/metadata-codelist/SpatialDataServiceType/download">Downloaddienst</gmx:Anchor>
                     </gmd:applicationProfile>
                     <gmd:name>
                        <gco:CharacterString>kaderrichtlijnwater:krw_stroomgebieddistricten_rws_2018</gco:CharacterString>
                     </gmd:name>
                     <gmd:description>
                        <gmx:Anchor xlink:href="http://inspire.ec.europa.eu/metadata-codelist/OnLineDescriptionCode/endPoint">endPoint</gmx:Anchor>
                     </gmd:description>
                  </gmd:CI_OnlineResource>
               </gmd:onLine>
</examplexml>
```

2.3 link to the described dataset in the ATOM download service 
```xml
<examplexml>
              <gmd:onLine>
                  <gmd:CI_OnlineResource>
                     <gmd:linkage>
                        <gmd:URL>http://inspirelab.geonovum.nl/test/atom/cbs/wijkenbuurten2018.zip</gmd:URL>
                     </gmd:linkage>
                     <gmd:protocol>
                        <gmx:Anchor xlink:href="https://www.iana.org/assignments/media-types/application/gml+xml">gml</gmx:Anchor>
                     </gmd:protocol>
                     <gmd:applicationProfile>
                        <gmx:Anchor xlink:href="http://inspire.ec.europa.eu/metadata-codelist/SpatialDataServiceType/download">download</gmx:Anchor>
                     </gmd:applicationProfile>
                     <gmd:name>
                        <gco:CharacterString>Wijk- en Buurtkaart 2018</gco:CharacterString>
                     </gmd:name>
                     <gmd:description>
                        <gmx:Anchor xlink:href="http://inspire.ec.europa.eu/metadata-codelist/OnLineDescriptionCode/endPoint">endPoint</gmx:Anchor>
                     </gmd:description>
                  </gmd:CI_OnlineResource>
               </gmd:onLine>
			   </examplexml>
```

** 3 Other services are available**


3.1 link to a WFS download service, not intended to be INSPIRE complient
```xml
<examplexml>
               <gmd:onLine>
                  <gmd:CI_OnlineResource>
                     <gmd:linkage>
                        <gmd:URL>http://inspirelab.geonovum.nl/test/kad/wfs?request=GetCapabilities&amp;service=WFS</gmd:URL>
                     </gmd:linkage>
                     <gmd:protocol>
                        <gmx:Anchor xlink:href="http://www.opengis.net/def/serviceType/ogc/wfs">OGC:WFS</gmx:Anchor>
                     </gmd:protocol>
                     <gmd:applicationProfile>
                        <gmx:Anchor xlink:href="http://inspire.ec.europa.eu/metadata-codelist/SpatialDataServiceType/other">other</gmx:Anchor>
                     </gmd:applicationProfile>
                     <gmd:name>
                        <gco:CharacterString>Bestuurlijke grenzen WFS</gco:CharacterString>
                     </gmd:name>
                     <gmd:description>
                        <gmx:Anchor xlink:href="http://inspire.ec.europa.eu/metadata-codelist/OnLineDescriptionCode/accessPoint">accessPoint</gmx:Anchor>
                     </gmd:description>
                  </gmd:CI_OnlineResource>
               </gmd:onLine>
</examplexml>
```

3.2 link to a OGC API Feature, not (yet) intended to be INSPIRE complient
```xml
<examplexml>
               <gmd:onLine>
                  <gmd:CI_OnlineResource>
                     <gmd:linkage>
                        <gmd:URL>http://www.acme.com/3.0/wfs/collections?f=text%2Fhtml</gmd:URL>
                     </gmd:linkage>
                     <gmd:protocol>
                        <gmx:Anchor xlink:href="http://www.opengis.net/def/interface/ogcapi-features">OGC:API features</gmx:Anchor>
                     </gmd:protocol>
                     <gmd:applicationProfile>
                        <gmx:Anchor xlink:href="http://inspire.ec.europa.eu/metadata-codelist/SpatialDataServiceType/other">other</gmx:Anchor>
                     </gmd:applicationProfile>
                     <gmd:name>
                        <gco:CharacterString>Bestuurlijke grenzen</gco:CharacterString>
                     </gmd:name>
                     <gmd:description>
                        <gmx:Anchor xlink:href="http://inspire.ec.europa.eu/metadata-codelist/OnLineDescriptionCode/accessPoint">accessPoint</gmx:Anchor>
                     </gmd:description>
                  </gmd:CI_OnlineResource>
               </gmd:onLine>
</examplexml>
```
** 4 other output formats are available**


4.1 Direct link to the described dataset in the WFS download service, in json format
```xml
<examplexml>
              <gmd:onLine>
                  <gmd:CI_OnlineResource>
                     <gmd:linkage>
                        <gmd:URL>http://inspirelab.geonovum.nl/test/rws/wfs?request=GetFeature&amp;service=WFS&amp;version=2.0.0&amp;typeName=kaderrichtlijnwater:krw_stroomgebieddistricten_rws_2018&amp;outputFormat=json</gmd:URL>
                     </gmd:linkage>
                     <gmd:protocol>
                        <gmx:Anchor xlink:href="https://www.iana.org/assignments/media-types/application/json">json</gmx:Anchor>
                     </gmd:protocol>
                     <gmd:applicationProfile>
                        <gmx:Anchor xlink:href="http://inspire.ec.europa.eu/metadata-codelist/SpatialDataServiceType/download">Downloaddienst</gmx:Anchor>
                     </gmd:applicationProfile>
                     <gmd:name>
                        <gco:CharacterString>kaderrichtlijnwater:krw_stroomgebieddistricten_rws_2018</gco:CharacterString>
                     </gmd:name>
                     <gmd:description>
                        <gmx:Anchor xlink:href="http://inspire.ec.europa.eu/metadata-codelist/OnLineDescriptionCode/endPoint">endPoint</gmx:Anchor>
                     </gmd:description>
                  </gmd:CI_OnlineResource>
               </gmd:onLine>
			   </examplexml>
```

### Advantages/disadvantages of the proposed approach

Advantages;
- The data is direct accessible and can be downloaded in various formats via the datset metadata, without knowledge of OGC services.
- No additional tooling is needed to link the service to the dataset
- The relation between data and service is clear and easy to manage by one organizational unit
- The data is made available despite the different ways in which the services are implemented.


Use of the additional code list mediatype needed if an endpoint is included, this is not necessary for the link to the required Get View and Download Service Metadata request as described in 1

Open issue, There are different methods to link to the dataset endpoint in the ATOM;
 
- via the dataset feed, this is not really an endpoint or should we use the dataset feed instead of the service feed to fullfill the required Get View and Download Service Metadata request?
- direct to a specific datasets in a specific coordinate reference system, not yet worked out where the different available CRS can be described in the dataset metadata. This information is available in the dataset feed. An option is to add this info to the  CI_OnlineResource name element, fi, adresses in CRS EPSG 28992


### Conclusions 

This proposal is flexible and support most use cases.  It make use of existing international agreed and managed codelists  and metadata elements included in the TG INSPIRE, with the exception of the widely used protocol element.
This method is in principal implemented in the Netherlands for over 10 years and adapted and expanded inline with TG INSPIRE.
The widely used metadata catalog geoNetwork, supports this method and presents the service links together with the dataset metadata.