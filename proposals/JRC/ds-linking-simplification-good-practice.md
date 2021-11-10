
# Data Service Linking Simplification: Good Practice guidelines

`Version: draft 1.0`
`Date: 2021-10-21`

## Table of Contents

_TO_BE_REVIEWED_

* [1. Introduction](#introduction)
* [2. Scope](#scope)
* [3. Conformance](#conformance)
* [4. Normative references](#normative-references)
* [5. Terms and definitions](#terms-and-definitions)
* [6. Acronyms](#acronyms)
* [7. Data Service Linking Simplification](#ds-linking-simplif)
    * [7.1. Main principles](#main-principles)
    * [7.2. Resources](#resources)
* [8. Requirements classes](#rcs)
    * [8.1. Requirements class: “INSPIRE-Data-set-Metadata-Resource-Locator”](#rc-ds-md-resloc)
    * [8.2. Requirements class: “INSPIRE-Network-Service-Metadata-Coupled-Resource”](#rc-ns-md-coupledres)
*  [9. Future developments](#future-dev)
* [Annex A: Examples](#annex-a)
* [Annex B: Mapping of INSPIRE elements in ExtendedCapabilities](#annex-b)

## 1. Introduction <a name="introduction"></a>

This good practice candidate is based on the collection and comparison of proposals received from the members of the temporary MIWP technical sub-group 2.3.2 on data and service linking simplification. This document leverages on the recommendations, initially described in the [Discussion Paper on possible simplification of data-service linking in INSPIRE](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/blob/main/resources/Discussion%20Paper%20on%20data-service%20linking%20v0.5.docx), and further improved by the subsequent [proposals for the simplification approach](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/tree/main/proposals) made by the members of the technical sub-group.

The reference for the metadata specification used in this proposal is the [INSPIRE MD TG]. The reference for the INSPIRE Network Service (Download and View) specifications are the [INSPIRE NS - Download Service TG] and [INSPIRE NS - View Service TG], respectively.

## 2. Scope <a name="scope"></a>

This document provides a set of opinionated interpretations and rules, that de facto standard web applications can currently support, based on the current list of Requirements and Recommendations expressed in the INSPIRE Technical Guidance (TG) documents.

## 3. Conformance <a name="conformance"></a>

The requirements classes expressed here apply to the data set and service metadata records, as well as to the service (capabilities) documents.
In particular, the data set and service metadata records shall be INSPIRE-compliant (verifiable through tests performed in the Reference Validator), should be available in the relevant national geoportal catalog (see https://inspire.ec.europa.eu/INSPIRE-in-your-Country), and consecutively harvested by the [INSPIRE Geoportal](https://inspire-geoportal.ec.europa.eu).

Furthermore, at the time of writing, the requirements expressed here for the Download Services are not applicable for specifications based on OGC APIs due to the lack of an agreed mapping for some conditional and mandatory INSPIRE metadata elements (in particular the Coupled Resource, and Unique Resource Identifier) in the [OAPIF GP] document.

## 4. Normative references <a name="normative-references"></a>

- **[ISO 19115-2:2019]** - ISO 19115-2:2019, *Geographic information — Metadata — Part 2: Extensions for acquisition and processing*
- **[ISO/TS 19139:2007]** - ISO/TS 19139:2007, *Geographic information — Metadata — XML schema implementation*
- **[IRs for NS]** - Commission Regulation (EC) No 976/2009 of 19 October 2009 implementing Directive 2007/2/EC of the European Parliament and of the Council as regards the Network Services
- **[IRs for ISDSS]** - Commission Regulation (EU) No 1089/2010 of 23 November 2010 implementing Directive 2007/2/EC of the European Parliament and of the Council as regards interoperability of spatial data sets and services
- **[INSPIRE MD TG]** - JRC. *Technical Guidance for the implementation of INSPIRE dataset and service metadata based on ISO/TS 19139:2007*.  v2.0.1 - 2017-03-02
- **[INSPIRE NS - Download Service TG]** - JRC. *Technical Guidance for the implementation of INSPIRE Download Services*. v3.1 - 2013-08-09
- **[INSPIRE NS - View Service TG]** - JRC. *Technical Guidance for the implementation of INSPIRE View Services*. v3.11 - 2013-04-04
- **[RFC 4287]** - Internet Engineering Task Force (IETF). RFC 4287, *The Atom Syndication Format*. Initial release: December 2005
- **[OAPIF GP]** - Good Practice: INSPIRE download services based on OGC API - Features

<!-- Second parts of the reference-style links, see also https://www.markdownguide.org/basic-syntax/#reference-style-links  -->
[ISO 19115-2:2019]: https://schemas.isotc211.org/schemas/19115/-2/gmi/1.0/gmi.xsd "ISO 19115-2:2019, Geographic information — Metadata — Part 2: Extensions for acquisition and processing"
[ISO/TS 19139:2007]: https://www.isotc211.org/2005/gmd/ "ISO/TS 19139:2007, Geographic information — Metadata — XML schema implementation"
[IRs for NS]: https://eur-lex.europa.eu/legal-content/EN/TXT/HTML/?uri=CELEX:02009R0976-20141231&from=EN "Implementing Rules for Network Services (consolidated version of 31/12/2014)"
[IRs for ISDSS]: https://eur-lex.europa.eu/legal-content/EN/TXT/HTML/?uri=CELEX:02010R1089-20141231&from=EN "Implementing Rules for interoperability of spatial data sets and services (consolidated version of 31/12/2014)"
[INSPIRE MD TG]: https://inspire.ec.europa.eu/id/document/tg/metadata-iso19139 "Technical Guidance for the implementation of INSPIRE dataset and service metadata based on ISO/TS 19139:2007"
[INSPIRE NS - Download Service TG]: https://inspire.ec.europa.eu/documents/technical-guidance-implementation-inspire-download-services "Technical Guidance for the implementation of INSPIRE Download Services"
[INSPIRE NS - View Service TG]: https://inspire.ec.europa.eu/documents/technical-guidance-implementation-inspire-view-services-1 "Technical Guidance for the implementation of INSPIRE View Services"
[RFC 4287]: https://www.rfc-editor.org/rfc/rfc4287 "The Atom Syndication Format"
[OAPIF GP]: https://github.com/INSPIRE-MIF/gp-ogc-api-features "Good Practice: INSPIRE download services based on OGC API - Features"

## 5. Terms and definitions <a name="terms-and-definitions"></a>

_TO_BE_REVIEWED_

For the purposes of this document, the following terms and definitions apply:

| Term | Definition | Source |
| --- | --- | --- |
| content negotiation | The practice of providing multiple representations available via the same URI | [ISO/IEC 19788](https://www.iso.org/obp/ui/#iso:std:iso-iec:19788:-7:ed-1:v1:en:sec:3.20) |
| data set | Identifiable collection of data. | [ISO 19115](https://www.iso.org/obp/ui/#iso:std:iso:19115:-2:ed-2:v1:en:sec:3.6) |
| direct access download service | Download Service which provides access to the Spatial Objects in Spatial Data Sets based upon a query | [IRs for NS] |
| encoding | Conversion of data into a series of codes. | [ISO 19118](https://www.iso.org/obp/ui/#iso:std:iso:19118:ed-2:v1:en:term:4.13) |
| encoding rule | Identifiable collection of conversion rules that define the encoding for a particular data structure. | [ISO 19118](https://www.iso.org/obp/ui/#iso:std:iso:19118:ed-2:v1:en:term:4.14) |

**NOTE** ISO and the European Commission maintain comprehensive terminological databases at the following addresses:
- [ISO Online browsing platform](https://www.iso.org/obp)
- [INSPIRE glossary](http://inspire.ec.europa.eu/glossary)

## 6. Acronyms <a name="acronyms"></a>

_TO_BE_REVIEWED_

| Abbreviation | Term |
| --- | --- |
| API | Application Programming Interface |
| GML | Geography Markup Language |
| URL | Uniform Resource Locator |
| WFS | Web Feature Service |
| WMS | Web Map Service |
| WMTS | Web Map Tile Service |

## 7. Data Service Linking Simplification <a name="ds-linking-simplif"></a>

### 7.1. Main principles <a name="main-principles"></a>

- An INSPIRE data set shall have INSPIRE View and Download services.
- The linkage between the data set and the View and Download services shall be ensured by the bidirectional relationship between the data set metadata and the service metadata.

### 7.2. Resources <a name="resources"></a>

![Diagram of Simplified linkage model](INSPIRE%20models_v1.1.jpg)

## 8. Requirements classes <a name="rcs"></a>

### 8.1. Requirements class “INSPIRE-Data-Set-Metadata-Resource-Locator” <a name="rc-ds-md-resloc"></a>

| Requirements class | http://inspire.ec.europa.eu/id/spec/ds-linking-simplification/1.0/ds-md-resource-locator |
| --- | --- |
| Target type | Data set metadata |
| Dependency | N/A |

The Resource Locator element of a data set metadata record shall point to the URL where the service can be contacted. 

Setting up the correct resource locators is important for the connection between the data sets and the services that provide access to them or for providing additional information concerning the data sets.

In particular, **TG Requirement 1.8** of [INSPIRE MD TG] expresses the obligation to provide online access, if available, to the described data set or data set series.

Furthermore, it suggests that at least two locators need to be expressed in the data set metadata: one for a View Service and one for a Download Service.

The following requirements are also an enforcement of **TG Recommendation 1.9** in [INSPIRE MD TG] for the data set metadata record.

This class requires that the Resource Locator element shall point to the set of additional information about a service resource (i.e. "Get Download/View Service Metadata" operation). 

This class requires the presence of `<gmd:protocol>` and `<gmd:applicationProfile>`, paired with the defined codelist values from the INSPIRE Registry. This would imply fulfilling this portion of the simplification described here.

The presence of additional Resource Locator elements, pointing to the data set itself (e.g. "Get Spatial Data Set" request of a Download Service), is allowed, due to the multiplicity expressed by **TG Requirement 1.8**. Consequently, these additional Resource Locator elements should avoid at least the use of the `<gmd:applicationProfile>` element specified below, in order to reduce the complexity of a machine-to-machine element recognition made by an INSPIRE software implementation such as the INSPIRE Geoportal.

### Requirement: \<gmd:URL\> element

- Within this element, the URL shall point to the response of a "Get View/Download Service Metadata" request of the service providing access to this data set (e.g. the "GetCapabilities" document in the case of an OGC:WFS service).

| **Requirement** | **/req/resource-locator-url** | 
| --- | --- |
| A | The element `URL` SHALL point to the response of a "Get View/Download Service Metadata' request. |

### Requirement: \<gmd:protocol\> element

- For this element, the INSPIRE Registry offers a set of external codelist values from the [ProtocolValue codelist](https://inspire.ec.europa.eu/metadata-codelist/ProtocolValue).
- Regarding the label of a codelist, the INSPIRE Registry specifies the text to be used, which should follow the metadata language.
- The [INSPIRE MD TG] already recommends the use of the `gmx:Anchor` element when the provided text is a term or code, instead of `gco:CharacterString`. This requirements class enforces the use of this element.
- The use of the element `gco:CharacterString` is allowed for backward compatibility with an existing Resource Locator description that might be already compliant with this simplification approach.

| **Requirement** | **/req/resource-locator-protocol** |
| --- | --- |
| A | The `protocol` element SHALL be present in the Resource Locator, encoded as either `gmx:Anchor` or `gco:CharacterString`. |
| B | The `protocol` element SHALL use the values from the [ProtocolValue codelist](https://inspire.ec.europa.eu/metadata-codelist/ProtocolValue). |
| C | If the `protocol` element is encoded as `gco:CharacterString`, it's value SHALL match the related codelist label specified in the INSPIRE registry, expressed in the metadata language where available. |

| **Recommendation** | **/rec/resource-locator-protocol** |
| --- | --- |
| A | The `protocol` element SHOULD be encoded as `gmx:Anchor`. The attribute `xlink:href` should point to a valid unique resource identifier of the ProtocolValue codelist. The text value should match the related codelist label, expressed in the metadata language where available. |

#### Example of a View Service locator with `<gmx:Anchor>` encoding
```xml
<gmd:protocol>
    <gmx:Anchor xlink:href="http://www.opengis.net/def/serviceType/ogc/wms">OGC Web Map Service</gmx:Anchor>
</gmd:protocol>
```

#### Example of a View Service locator with `<gco:CharacterString>` encoding
```xml
<gmd:protocol>
    <gco:CharacterString>OGC Web Map Service</gco:CharacterString>
</gmd:protocol>
```

_NOTE_: At the time of writing, the above examples use `eng` as metadata language, and they express the codelist `http://www.opengis.net/def/serviceType/ogc/wms` with the label "OGC Web Map Service". Please, check and use always the codelist label currently in force within the INSPIRE Registry.

### Requirement: \<gmd:applicationProfile\> element

- For this element, the INSPIRE Registry provides the values from the [SpatialDataServiceType codelist](https://inspire.ec.europa.eu/metadata-codelist/SpatialDataServiceType).
- Regarding the label of a codelist, the INSPIRE Registry specifies the text to be used, which should follow the metadata language.
- The [INSPIRE MD TG] already recommends the use of the `gmx:Anchor` element when the provided text is a term or code, instead of `gco:CharacterString`. This requirements class enforces the use of this element.
- The existence of the element `gco:CharacterString` is allowed for backward compatibility with an existing Resource Locator description that might be already compliant with this simplification.

| **Requirement** | **/req/resource-locator-application-profile** |
| --- | --- |
| A | The element `applicationProfile` SHALL be present in the Resource Locator, encoded either as `gmx:Anchor` or `gco:CharacterString`. |
| B | The element `applicationProfile` SHALL use the values from the [SpatialDataServiceType codelist](https://inspire.ec.europa.eu/metadata-codelist/SpatialDataServiceType). |
| C | If the element `applicationProfile` is encoded as `gco:characterString`, the text value SHALL match the related codelist label specified in the INSPIRE registry, expressed in the metadata language where available. |

| **Recommendation** | **/rec/resource-locator-application-profile** |
| --- | --- |
| A | The element `applicationProfile` SHOULD be encoded with `gmx:Anchor`. The attribute `xlink:href` should point to a valid unique resource identifier of the mentioned codelist. The text value should match the related codelist label, expressed in the metadata language where available. |

#### Example of a Download Service locator with `<gmx:Anchor>` encoding
```xml
<gmd:applicationProfile>
    <gmx:Anchor xlink:href="https://inspire.ec.europa.eu/metadata-codelist/SpatialDataServiceType/download">Downloaddienst</gmx:Anchor>
</gmd:applicationProfile>
```

#### Example of a Download Service locator with а `<gco:CharacterString>` encoding
```xml
<gmd:applicationProfile>
    <gco:CharacterString>Downloaddienst</gco:CharacterString>
</gmd:applicationProfile>
```

_NOTE_: At the time of writing, the above examples use `dut` as metadata language, and they express the codelist `https://inspire.ec.europa.eu/metadata-codelist/SpatialDataServiceType/download` with the label "Downloaddienst". Please, check and use always the codelist label currently in force within the INSPIRE Registry.

### Requirement: INSPIRE View Service linking

| **Requirement** | **/req/view-linkage** |
| --- | --- |
| Definition | The Resource Locator to an INSPIRE View Service SHALL point to the Service Metadata (e.g. GetCapabilities) response of the associated INSPIRE View Service. The Resource Locator SHALL include the elements `URL`, `protocol` and `applicationProfile`, properly encoded. |
| Dependency |  **/req/resource-locator-url** <br> **/req/resource-locator-protocol** <br> **/req/resource-locator-application-profile** |

See [Annex A: Examples](#annex-a) for an example of this linkage requirement.

### Requirement: INSPIRE Download Service linkage

| **Requirement** | **/req/download-linkage** |
| --- | --- |
| Definition | The Resource Locator to an INSPIRE Download Service SHALL point to the Service Metadata (e.g. GetCapabilities) response of the associated INSPIRE Download Service. The Resource Locator SHALL include the elements `URL`, `protocol` and `applicationProfile`, properly encoded. |
| Dependency |  **/req/resource-locator-url** <br> **/req/resource-locator-protocol** <br> **/req/resource-locator-application-profile** |

See [Annex A: Examples](#annex-a) for an example of this linkage requirement.


### 8.2. Requirements class “INSPIRE-Network-Service-Metadata-Coupled-Resource”  <a name="rc-ns-md-coupledres"></a>

| Requirements class | http://inspire.ec.europa.eu/id/spec/ds-linking-simplification/1.0/ns-md-coupled-resource |
| --- | --- |
| Target type | Service metadata |
| Dependency | N/A |

The Coupled Resource metadata element refers to, where relevant, the target spatial data set(s) of the described service.  
It is implemented by reference, i.e. through a URL that points to the metadata record of the data set on which the service operates. It therefore helps to link services to the relevant data sets.
This requirements class strictly follows **TG Requirement 3.6** of the [INSPIRE MD TG] for the expression of the Coupled Resource element.

Regarding the definition of a Network Service metadata, two scenarios have been identified for publishing metadata conforming to the [IRs for NS], and on the [INSPIRE MD TG]. It is up to the Member State to choose which scenario best fits their specific needs. As these scenarios are not mutually exclusive, a Member State may also choose to implement both.

**NOTE** For the ATOM implementation, the [INSPIRE NS - Download Service TG] does not offer a similar multiple scenario configuration due to the lack of mapping elements in such an implementation.

### 8.2.1 INSPIRE Network service - Scenario 1

- In Scenario 1, the INSPIRE network service metadata is available in a Discovery Service catalog and is referenced through the `<inspire_common:MetadataURL>` element within the INSPIRE ExtendedCapabilities section of such service.
- The service metadata shall define a `<srv:operatesOn>` element for every defined data set published by the service.
- The data set metadata URL may point to a Discovery Service different from the national reference catalog. This may apply especially for federated Discovery Service catalogues.

### Requirement: \<srv:operatesOn\> element

| **Requirement** | **/req/coupled-resource-operateson-locator** |
| --- | --- |
| A | The `xlink:href` attribute of each of the `srv:operatesOn` elements SHALL contain a URI pointing to the metadata record of the provided data set or data set series. |

### 8.2.2 INSPIRE Network service - Scenario 2

 - In Scenario 2, the [INSPIRE NS - Download Service TG] maps all INSPIRE metadata elements to the applicable elements in the service (i.e. ATOM feed elements or OGC Capabilities), and for OGC services, it currently relies on the ExtendedCapabilities section for the remaining elements.  [Annex B](#annex-b), which is subject to future work proposes an approach for the revision of the mapping of the INSPIRE requirements with the aim to possibly remove the Extended Capabilities section.
- The data set metadata URL may point to a Discovery Service different from the national reference catalog. This may apply especially for federated Discovery Service catalogues.

### Requirement: \<wms:MetadataURL\> and \<wfs:MetadataURL\> elements

| **Requirement** | **/req/coupled-resource-metadataurl-locator** |
| --- | --- |
| A | The URL expressed within the element `metadataURL` SHALL resolve to the metadata record of the data set or data set series, available in a Discovery Service catalog. |

## 9. Future developments <a name="future-dev"></a>

Further simplifications may be possible on a broader level about the INSPIRE implementation.

Note that often the organisation responsible for the metadata is not the same as the organisation responsible for the service operations. In "_Scenario 1_", this situation could easily lead to duplications, errors and/or lack of synchronised information. Such issues could be avoided by implementing "_Scenario 2_", whose requirements and definitions are already provided in both the [INSPIRE NS - Download Service TG] and [INSPIRE NS - View Service TG] documents. In this case, the service metadata would be no longer required (at least for the purpose of this linkage simplification), so its creation could be skipped or automated by dedicated software implementations of the INSPIRE Discovery Service.

Furthermore, the implementation of "_Scenario 2_" for Network Services could provide an opportunity for the revision of the mapping of the INSPIRE requirements, currently expressed in the Extended Capabilities section (especially the Conformance declaration) requiring the use of specialised extensions of software products. Refer to the [Annex B](#annex-b) for further details.


# Annex A: Examples <a name="annex-a"></a>

## Examples (XML encoded)
The following collection shows a series of XML snippets.
_These examples are purely informative and do not constitute a reference definition of a conformant metadata._

### Examples of Resource Locator for INSPIRE View Service

#### Resource Locator to a "Get View Service Metadata" operation - WMS GetCapabilities

```xml
<gmd:transferOptions>
  <gmd:MD_DigitalTransferOptions>
      [...]
    <gmd:onLine>
      <gmd:CI_OnlineResource>
        <gmd:linkage>
          <gmd:URL>http://.../wms?request=GetCapabilities&amp;service=WMS&amp;version=1.3.0</gmd:URL>
        </gmd:linkage>
        <gmd:protocol>
          <gmx:Anchor xlink:href="http://www.opengis.net/def/serviceType/ogc/wms">wms</gmx:Anchor>
        </gmd:protocol>
        <gmd:applicationProfile>
          <gmx:Anchor xlink:href="http://inspire.ec.europa.eu/metadata-codelist/SpatialDataServiceType/view">View Service</gmx:Anchor>
        </gmd:applicationProfile>
        <gmd:name>
          <gco:CharacterString>INSPIRE WMS</gco:CharacterString>
        </gmd:name>
      </gmd:CI_OnlineResource>
    </gmd:onLine>
      [...]
  </gmd:MD_DigitalTransferOptions>
</gmd:transferOptions>
```

#### Additional Resource Locator to an "View Service - Get Map" operation - WMS GetMap

```xml
<gmd:transferOptions>
  <gmd:MD_DigitalTransferOptions>
      [...]
    <gmd:onLine>
      <gmd:CI_OnlineResource>
        <gmd:linkage>
          <gmd:URL>http://.../wms?request=GetMap&amp;service=WMS&amp;version=1.3.0&amp;layers=1&amp;styles=default&amp;CRS=EPSG:4258&amp;format=image/png&amp;bbox=0.87,43.26,11.68,48.13&amp;width=600&amp;height=400</gmd:URL>
        </gmd:linkage>
        <gmd:protocol>
          <gmx:Anchor xlink:href="http://www.opengis.net/def/serviceType/ogc/wms">wms</gmx:Anchor>
        </gmd:protocol>
        <gmd:name>
          <gco:CharacterString>INSPIRE WMS - GetMap request</gco:CharacterString>
        </gmd:name>
      </gmd:CI_OnlineResource>
    </gmd:onLine>
      [...]
  </gmd:MD_DigitalTransferOptions>
</gmd:transferOptions>
```

### Examples of Resource Locator for INSPIRE Download Service

#### Resource Locator  a "Get Download Service Metadata" operation - ATOM topfeed

```xml
<gmd:transferOptions>
  <gmd:MD_DigitalTransferOptions>
      [...]
    <gmd:onLine>
      <gmd:CI_OnlineResource>
        <gmd:linkage>
          <gmd:URL>http://.../atom/INSPIRE_DW_dataset_2021</gmd:URL>
        </gmd:linkage>
        <gmd:protocol>
          <gmx:Anchor xlink:href="https://tools.ietf.org/html/rfc4287">ATOM Syndication Format</gmx:Anchor>
        </gmd:protocol>
        <gmd:applicationProfile>
          <gmx:Anchor xlink:href="http://inspire.ec.europa.eu/metadata-codelist/SpatialDataServiceType/download">Download Service</gmx:Anchor>
        </gmd:applicationProfile>
        <gmd:name>
          <gco:CharacterString>INSPIRE Download Service (ATOM)</gco:CharacterString>
        </gmd:name>
      </gmd:CI_OnlineResource>
    </gmd:onLine>
      [...]
  </gmd:MD_DigitalTransferOptions>
</gmd:transferOptions>
```

#### Additional Resource Locator for a "Get Spatial Data Set" - ATOM subfeed

```xml
<gmd:transferOptions>
  <gmd:MD_DigitalTransferOptions>
      [...]
    <gmd:onLine>
      <gmd:CI_OnlineResource>
        <gmd:linkage>
          <gmd:URL>http://.../atom/INSPIRE_DW_2021_Dataset.gml</gmd:URL>
        </gmd:linkage>
        <gmd:protocol>
          <gmx:Anchor xlink:href="https://tools.ietf.org/html/rfc4287">ATOM Syndication Format</gmx:Anchor>
        </gmd:protocol>
        <gmd:name>
          <gco:CharacterString>INSPIRE Download Service (ATOM)</gco:CharacterString>
        </gmd:name>
      </gmd:CI_OnlineResource>
    </gmd:onLine>
      [...]
  </gmd:MD_DigitalTransferOptions>
</gmd:transferOptions>
```

#### _TO_BE_REVIEWED_ Example of a Resource Locator of a data set metadata linking a Download Service (Get Download Service Metadata)

```xml
<gmd:transferOptions>
  <gmd:MD_DigitalTransferOptions>
      [...]
    <gmd:onLine>
      <gmd:CI_OnlineResource>
        <gmd:linkage>
          <gmd:URL>http://.../wfs?service=wfs&amp;version=2.0.0&amp;request=GetCapabilities</gmd:URL>
        </gmd:linkage>
        <gmd:protocol>
          <gmx:Anchor xlink:href="http://www.opengis.net/def/serviceType/ogc/wfs">wfs</gmx:Anchor>
        </gmd:protocol>
        <gmd:applicationProfile>
          <gmx:Anchor xlink:href="http://inspire.ec.europa.eu/metadata-codelist/SpatialDataServiceType/download">Download Service</gmx:Anchor>
        </gmd:applicationProfile>
        <gmd:name>
          <gco:CharacterString>INSPIRE Download Service (WFS)</gco:CharacterString>
        </gmd:name>
      </gmd:CI_OnlineResource>
    </gmd:onLine>
      [...]
  </gmd:MD_DigitalTransferOptions>
</gmd:transferOptions>
```

#### _TO_BE_REVIEWED_ Example of an optional definition of a Resource Locator in the dataset metadata linking directly the downloadable dataset (Get Spatial Data Set)

_Note: this example covers the WFS definition. For a WCS/SOS service, use the proper codelist for the `protocol` element_

```xml
<gmd:transferOptions>
  <gmd:MD_DigitalTransferOptions>
      [...]
    <gmd:onLine>
      <gmd:CI_OnlineResource>
        <gmd:linkage>
          <gmd:URL>http://.../wfs?service=wfs&amp;version=2.0.0&amp;request=GetFeature&amp;storedquery_id=http://inspire.ec.europa.eu/operation/download/GetSpatialDataSet&amp;DataSetIdCode=mycode&amp;DataSetIdNamespace=mynamespace&amp;CRS=EPSG:4326&amp;Language=eng</gmd:URL>
        </gmd:linkage>
        <gmd:protocol>
          <gmx:Anchor xlink:href="http://www.opengis.net/def/serviceType/ogc/wfs">wfs</gmx:Anchor>
        </gmd:protocol>
        <gmd:applicationProfile>
          <gmx:Anchor xlink:href="http://inspire.ec.europa.eu/metadata-codelist/SpatialDataServiceType/download">Download Service</gmx:Anchor>
        </gmd:applicationProfile>
        <gmd:name>
          <gco:CharacterString>INSPIRE Dataset</gco:CharacterString>
        </gmd:name>
      </gmd:CI_OnlineResource>
    </gmd:onLine>
      [...]
  </gmd:MD_DigitalTransferOptions>
</gmd:transferOptions>
```
# Annex B: Mapping of INSPIRE elements in the Extended Capabilities section <a name="annex-b"></a>

The [Discussion Paper on possible simplification of data-service linking in INSPIRE](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/blob/main/resources/Discussion%20Paper%20on%20data-service%20linking%20v0.5.docx) proposes a new mapping of the INSPIRE elements contained in the service metadata, as described in the Scenario 2 in the INSPIRE Network Service TGs, in order to remove the need for the Extended Capabilities section and thus achieve an implementation simplification.

Within the MIWP 2.3.2 action, this opportunity (subject to agreement by the sub-group) was further explored by reallocating elements from the Extended Capabilities section to the service metadata. The following tables expresses this proposed reallocation:

| Extended capabilities | Proposed action on mapping | Rationale | Applicable on Service type |
| :- | :- | :- | :- |
| inspire\_common:ResourceType          | Discard | By default = service                                     | WMS - WFS |
| inspire\_common:ResourceLocator       | Discard | Resource locator in the data set metadata                | WMS - WFS |
| inspire\_common:SpatialDataServiceType| Discard | Moved to the applicationProfile in the data set metadata | WMS - WFS |
| inspire\_common:TemporalReference     | TBD | Consider the temporalReference in the data set metadata?     | WMS - WFS |
| inspire\_common:Conformity            | Keep | Declared through the wms:keyword element                    | WMS - WFS |
| inspire\_common:MetadataPointOfContact| TBD | Consider the metadataPointOfContact in the data set metadata | WMS - WFS |
| inspire\_common:MetadataDate          | TBD | Consider the metadataDate in the data set metadata           | WMS - WFS |
| inspire\_common:SupportedLanguages    | TBD | Consider the metadataLanguage in the data set metadata       | WMS - WFS |
| inspire_dls:SpatialDataSetIdentifier/inspire_common:Code <br/> inspire_dls:SpatialDataSetIdentifier/inspire_common:Namespace | Keep | Data set identifier in the data set metadata | WFS |
