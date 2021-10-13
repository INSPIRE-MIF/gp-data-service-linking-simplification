
# Data Service Linking Simplification: Best Practice guidelines

`Version: draft 1.0`
`Date: 2021-10-13`

## Table of Contents

_TO_BE_REVIEW_

* [1. Introduction](#introduction)
* [2. Scope](#scope)
* [3. Conformance](#conformance)
* [4. Normative references](#normative-references)
* [5. Terms and definitions](#terms-and-definitions)
* [6. Symbols and abbreviated terms](#symbols-and-abbreviated-terms)
* [7. Data Service Linking Simplification](#ds-linking-simplif)
    * [7.1. Main principles](#main-principles)
    * [7.2. From the definition to the data](#def-to-data)
    * [7.3. From the data to the definition](#data-to-def)
* [8. Conformance classes](#ccs)
    * [8.1. Conformance class: “INSPIRE-Data-set-Metadata-Resource-Locator”](#cc-ds-md-resloc)
    * [8.2. Conformance class: “INSPIRE-Network-Service-Metadata-Coupled-Resource”](#cc-ns-md-coupledres)
*  [9. Future developments](#future-dev)
* [Annex A: Examples](#annex-a)

## 1. Introduction <a name="introduction"></a>

_TO_BE_REVIEW_

This is the best practice document, originated from a consolidated proposal based on the collection and comparison of all the proposals received from the contributing Member State representatives of the MIWP 2.3.2 technical sub-group.

This document implements the recommendations and best-practice actions as initially described in the [Discussion Paper on possible simplification of data-service linking in INSPIRE](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/blob/main/resources/Discussion%20Paper%20on%20data-service%20linking%20v0.5.docx) and further improved by the subsequent proposals [proposals for the simplification approach](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/tree/main/proposals) made by the members of the technical sub-group.

The reference for the metadata specification used in this proposal is the [INSPIRE MD TG]. The reference for the INSPIRE Network Service (Download and View) specifications are the [INSPIRE NS - Download Service TG] and [INSPIRE NS - View Service TG].

## 2. Scope <a name="scope"></a>

_TO_BE_REVIEW_

The scope of this document is to provide a well-defined series of opinionated interpretations and rules (that de facto standard web applications can currently support), based on the current list of Requirements and Recommendations expressed in the INSPIRE Technical Guidance documents.

## 3. Conformance <a name="conformance"></a>

_TO_BE_REVIEW_

The recommendations expressed here apply to the data set and service metadata records, as well as to the service (capabilities) documents.
In particular, the data set and service metadata records must be INSPIRE-compliant (through the Reference Validator), should be available in the relevant national geoportal catalog (see https://inspire.ec.europa.eu/INSPIRE-in-your-Country), and they should be harvested by the [INSPIRE Geoportal](https://inspire-geoportal.ec.europa.eu).

## 4. Normative references <a name="normative-references"></a>

_TO_BE_REVIEW_

- **[ISO 19115-2:2019](https://schemas.isotc211.org/schemas/19115/-2/gmi/1.0/gmi.xsd)** - ISO 19115-2:2019, *Geographic information — Metadata — Part 2: Extensions for acquisition and processing*
- **[ISO/TS 19139:2007](https://www.isotc211.org/2005/gmd/)** - ISO/TS 19139:2007, *Geographic information — Metadata — XML schema implementation*
- **[IRs for NS]** - Commission Regulation (EC) No 976/2009 of 19 October 2009 implementing Directive 2007/2/EC of the European Parliament and of the Council as regards the Network Services
- **[IRs for ISDSS]** - Commission Regulation (EU) No 1089/2010 of 23 November 2010 implementing Directive 2007/2/EC of the European Parliament and of the Council as regards interoperability of spatial data sets and services
- **[INSPIRE MD TG]** - JRC. *Technical Guidance for the implementation of INSPIRE dataset and service metadata based on ISO/TS 19139:2007*.  v2.0.1 - 2017-03-02
- **[INSPIRE NS - Download Service TG]** - JRC. *Technical Guidance for the implementation of INSPIRE View Services*. v3.1 - 2013-08-09
- **[INSPIRE NS - View Service TG]** - JRC. *Technical Guidance for the implementation of INSPIRE Download Services*. v3.11 - 2013-04-04
- **[RFC 4287]** - Internet Engineering Task Force (IETF). RFC 4287, *The Atom Syndication Format*. Initial release: December 2005
- **[RFC 7231]** - Internet Engineering Task Force (IETF). RFC 7231, *Hypertext Transfer Protocol (HTTP/1.1): Semantics and Content*. June 2014
- **[OGC API - Features - 1]** - OGC API - Features - Part 1: Core<sup> 2</sup>
- **[OGC API - Features - 2]** - OGC API - Features - Part 2: Coordinate Reference Systems by Reference
- **[OpenAPI 3.0]** - OpenAPI Initiative (OAI). *OpenAPI Specification*. The latest patch version at the time of publication of this document was 3.0.3, published in February 2020.


<sup>2 </sup> The standard is also published as [ISO 19168-1:2020, Geographic information — Geospatial API for features — Part 1: Core](https://www.iso.org/standard/32586.html). Note that a [draft version 1.0.1](http://docs.opengeospatial.org/DRAFTS/17-069r4.html) is available, see the included issues on https://github.com/opengeospatial/ogcapi-features/milestone/4?closed=1.

<!-- Second parts of the reference-style links, see also https://www.markdownguide.org/basic-syntax/#reference-style-links  -->
[IRs for NS]: https://eur-lex.europa.eu/legal-content/EN/TXT/HTML/?uri=CELEX:02009R0976-20141231&from=EN "Implementing Rules for Network Services (consolidated version of 31/12/2014)"
[IRs for ISDSS]: https://eur-lex.europa.eu/legal-content/EN/TXT/HTML/?uri=CELEX:02010R1089-20141231&from=EN "Implementing Rules for interoperability of spatial data sets and services (consolidated version of 31/12/2014)"
[INSPIRE MD TG]: https://inspire.ec.europa.eu/id/document/tg/metadata-iso19139
[INSPIRE NS - Download Service TG]: https://inspire.ec.europa.eu/documents/technical-guidance-implementation-inspire-download-services
[INSPIRE NS - View Service TG]: https://inspire.ec.europa.eu/documents/technical-guidance-implementation-inspire-view-services-1
[OGC API - Features - 1]: http://docs.opengeospatial.org/is/17-069r3/17-069r3.html "OGC API - Features - Part 1: Core"
[OGC API - Features - 2]: http://docs.opengeospatial.org/is/18-058/18-058.html "OGC API - Features - Part 2: Coordinate Reference Systems by Reference"
[OpenAPI 3.0]: http://spec.openapis.org/oas/v3.0.3 "OpenAPI Specification 3.0"
[RFC 4287]: https://www.rfc-editor.org/rfc/rfc4287 "The Atom Syndication Format"
[RFC 7231]: https://www.rfc-editor.org/rfc/rfc7231 "HTTP/1.1: Semantics and Content"

## 5. Terms and definitions <a name="terms-and-definitions"></a>

_TO_BE_REVIEW_

For the purposes of this document, the following terms and definitions apply:

| Term | Definition | Source |
| --- | --- | --- |
| content negotiation | The practice of providing multiple representations available via the same URI | [ISO/IEC 19788](https://www.iso.org/obp/ui/#iso:std:iso-iec:19788:-7:ed-1:v1:en:sec:3.20) |
| data set | Identifiable collection of data. | [ISO 19115](https://www.iso.org/obp/ui/#iso:std:iso:19115:-2:ed-2:v1:en:sec:3.6) |
| direct access download service | Download Service which provides access to the Spatial Objects in Spatial Data Sets based upon a query | \[[IRs for NS]\] |
| encoding | Conversion of data into a series of codes. | [ISO 19118](https://www.iso.org/obp/ui/#iso:std:iso:19118:ed-2:v1:en:term:4.13) |
| encoding rule | Identifiable collection of conversion rules that define the encoding for a particular data structure. | [ISO 19118](https://www.iso.org/obp/ui/#iso:std:iso:19118:ed-2:v1:en:term:4.14) |
| feature | Abstraction of real world phenomena. **NOTE** The concept of a `feature` is synonymous to a `spatial object` in INSPIRE | [OGC API - Features - 1](http://docs.opengeospatial.org/is/17-069r3/17-069r3.html#_feature) |
| feature collection | A set of features from a data set. | [OGC API - Features - 1](http://docs.opengeospatial.org/is/17-069r3/17-069r3.html#_feature_collection) |
| feature type | **NOTE** The concept of a `feature type` is synonymous to a `spatial object type` in INSPIRE | [INSPIRE](https://inspire.ec.europa.eu/glossary/SpatialObject) |
| pre-defined data set download service | Service that enables copies of spatial data sets, or parts of such sets, to be downloaded. | \[[IRs for NS]\] |


**NOTE** ISO and the European Commission maintain comprehensive terminological databases at the following addresses:
- [ISO Online browsing platform](https://www.iso.org/obp)
- [INSPIRE glossary](http://inspire.ec.europa.eu/glossary)

## 6. Symbols and abbreviated terms <a name="symbols-and-abbreviated-terms"></a>

_TO_BE_REVIEW_

| Abbreviation | Term |
| --- | --- |
| API | Application Programming Interface |
| GML | Geography Markup Language |
| OAPIF | OGC API - Features |
| URL | Uniform Resource Locator |
| WFS | Web Feature Service |
| WMS | Web Map Service |
| WMTS | Web Map Tile Service |

## 7. Data Service Linking Simplification <a name="ds-linking-simplif"></a>

### 7.1. Main principles <a name="main-principles"></a>

- A data set shall point to the INSPIRE Network Services, such as Download and View Service.
- The linkage shall be ensured by the bidirectional relationship between the data set metadata and the service metadata.

### 7.2. Resources <a name="resources"></a>

_Insert here diagrams and figures to illustrate the link relation to be used._

![Diagram A](figures/diagramA.png)

![Diagram B](figures/diagramB.png)

## 8. Conformance classes <a name="ccs"></a>

### 8.1. Conformance class: “INSPIRE-Data-set-Metadata-Resource-Locator”  <a name="cc-ds-md-resloc"></a>

| Conformance class | http://inspire.ec.europa.eu/id/spec/ds-linking-simplification/1.0/ds-md-resource-locator |
| --- | --- |
| Target type | Data set metadata |
| Dependency | N/A |

The Resource Locator of a metadata record shall point users to the location (URL) where the service can be contacted. 

Setting up the correct resource locators is important for the connection between the data and the services that provide access to them or for providing additional information concerning the resource.

In particular, the **TG Requirement 1.8** in [INSPIRE MD TG] express the obligation of providing online access, if available, to the described data set or data set series.

Furthermore, it suggests that at least two locators need to be expressed in the metadata: one for a Download Service, one for a View Service.

The following requirements are also an enforcement of **TG Recommendation 1.9** in [INSPIRE MD TG] for the metadata record.

This conformance class requires that the ResourceLocator element shall point to the set of additional information about a service resource (ie. "Get Download/View Service Metadata" operation).

This conformance class requires the presence of `<gmd:protocol>` and `<gmd:applicationProfile>`: by using these two elements, paired with the defined codelist from the central INSPIRE Registry, it would imply that you are fulfilling this portion of the simplification described here.

The presence of additional ResourceLocator elements, pointing to the data itself (eg. "Get Spatial Data Set" request of a Download Service), is permitted, due to the multiplicity expressed by the **TG Requirement 1.8**. Consequently, these additional ResourceLocator elements should avoid at least the use of the `<gmd:applicationProfile>` element, specified below, in order to reduce the complexity of a machine-to-machine element recognition made by an INSPIRE software implementation (eg. INSPIRE Geoportal).

### Requirement: \<gmd:URL\> element

- Within this element, the URL shall point to the response of a "Get View/Download Service Metadata" request of the service providing access to this data set (eg. the "GetCapabilities" document in case of a OGC:WFS service).

| **Requirement** | **/req/resource-locator-url** |
| --- | --- |
| A | The element `URL` SHALL point to the response of a "Get View/Download Service Metadata' request. |

### Requirement: \<gmd:protocol\> element

- For this element, the central INSPIRE Registry offers a series of external codelist values from the register: https://inspire.ec.europa.eu/metadata-codelist/ProtocolValue
- Regarding the label of a codelist, the central INSPIRE Registry specifies the text to be use, and this should follow the metadata language.
- The [INSPIRE MD TG] already recommends the use of element `gmx:Anchor` when the provided text is a term or code, instead of `gco:CharacterString`. This conformance class enforces the use of this element.
- The existence of element `gco:CharacterString` is permitted only for backward compatibility with an existing ResourceLocator description that might be already compliant with this simplification.

| **Requirement** | **/req/resource-locator-protocol** |
| --- | --- |
| A | The element `protocol` SHALL be present in the Resource Locator. |
| B | The element `protocol` SHALL use the values from the following codelist: `https://inspire.ec.europa.eu/metadata-codelist/ProtocolValue`. |
| C | The element `protocol` SHOULD be encoded with `gmx:Anchor`. The attribute `xlink:href` should point to a valid unique resource identifier of the mentioned codelist. The text value should match the related codelist label, expressed in the metadata language. |
| D | The element `protocol` MAY be encoded with `gco:CharacterString`. The text value SHALL match the related codelist label, expressed in the metadata language. |

#### Example of a View Service locator with `<gmx:Anchor>` encoding
```xml
<gmd:protocol>
    <gmx:Anchor xlink:href="http://www.opengis.net/def/serviceType/ogc/wms">wms</gmx:Anchor>
</gmd:protocol>
```

#### Example of a View Service locator with `<gco:CharacterString>` encoding
```xml
<gmd:protocol>
    <gco:CharacterString>wms</gco:CharacterString>
</gmd:protocol>
```

### Requirement: \<gmd:applicationProfile\> element

- For this element, the central INSPIRE Registry offers the codelist values from the register: https://inspire.ec.europa.eu/metadata-codelist/SpatialDataServiceType
- Regarding the label of a codelist, the central INSPIRE Registry specifies the text to be use, and this should follow the metadata language.
- The [INSPIRE MD TG] already recommends the use of element `gmx:Anchor` when the provided text is a term or code, instead of `gco:CharacterString`. This conformance class enforces the use of this element.
- The existence of element `gco:CharacterString` is permitted only for backward compatibility with an existing ResourceLocator description that might be already compliant with this simplification.

| **Requirement** | **/req/resource-locator-application-profile** |
| --- | --- |
| A | The element `applicationProfile` SHALL be present in the Resource Locator. |
| B | The element `applicationProfile` SHALL use the values from the following codelist: `https://inspire.ec.europa.eu/metadata-codelist/SpatialDataServiceType`. |
| C | The element `applicationProfile` SHOULD be encoded with `gmx:Anchor`. The attribute `xlink:href` should point to a valid unique resource identifier of the mentioned codelist. The text value should match the related codelist label, expressed in the metadata language. |
| D | The element `applicationProfile` MAY be encoded with `gco:characterString`. The text value SHALL match the related codelist label, expressed in the metadata language. |

#### Example of a Download Service locator with `<gmx:Anchor>` encoding
```xml
<gmd:applicationProfile>
    <gmx:Anchor xlink:href="https://inspire.ec.europa.eu/metadata-codelist/SpatialDataServiceType/download">Downloaddienst</gmx:Anchor>
</gmd:applicationProfile>
```

#### Example of a Download Service locator with `<gco:CharacterString>` encoding
```xml
<gmd:applicationProfile>
    <gco:CharacterString>Downloaddienst</gco:CharacterString>
</gmd:applicationProfile>
```

### Requirement: INSPIRE Download Service linkage

| **Requirement** | **/req/download-linkage** |
| --- | --- |
| Definition | The ResourceLocator to an INSPIRE Download Service SHALL point to the Service Metadata (eg. GetCapabilities) response of the associated INSPIRE Download Service. The Resource Locator SHALL present the elements `URL`, `protocol` and `applicationProfile`, properly encoded. |
| Dependency |  **/req/resource-locator-url** <br> **/req/resource-locator-protocol**<br> **/req/resource-locator-application-profile** |

For an example of this linkage requirement, see [Annex A: Examples](#annex-a)

### Requirement: INSPIRE View Service linkage

| **Requirement** | **/req/view-linkage** |
| --- | --- |
| Definition |The ResourceLocator to an INSPIRE View Service SHALL point to the Service Metadata (eg. GetCapabilities) response of the associated INSPIRE View Service. The Resource Locator SHALL present the elements `URL`, `protocol` and `applicationProfile`, properly encoded. |
| Dependency |  **/req/resource-locator-url** <br> **/req/resource-locator-protocol**<br> **/req/resource-locator-application-profile** |

For an example of this linkage expression, see [Annex A: Examples](#annex-a)

### 8.2. Conformance class: “INSPIRE-Network-Service-Metadata-Coupled-Resource”  <a name="cc-ns-md-coupledres"></a>

| Conformance class | http://inspire.ec.europa.eu/id/spec/ds-linking-simplification/1.0/ns-md-coupled-resource |
| --- | --- |
| Target type | Service metadata |
| Dependency | N/A |

The CoupledResource metadata element refers to, where relevant, the target spatial data set(s) of the described service.  
It is implemented by reference, i.e. through a URL that points to the metadata record of the data on  
which the service operates. It helps therefore linking services to the relevant datasets.
This conformance class strictly follows the **TG Requirement 3.6** of the [INSPIRE MD TG] for the expression of the CoupledResource element.

Regarding the definition of a Network Service metadata, two scenarios have been identified for publishing metadata conforming to the [IRs for NS], and on the [INSPIRE MD TG]. It is up to the Member  
State to choose which scenario best fits its needs. As these scenarios are not mutually exclusive, a  
Member State may choose to implement both.

**NOTE** For the ATOM implementation, the [INSPIRE NS - Download Service TG] doesn't offers a similar multiple scenario configuration, due to the lack of mapping elements in such implementation.

### 8.2.1 INSPIRE Network service - Scenario 1

- With the implementation of the Scenario 1, the INSPIRE network service metadata is available in a Discovery Service catalog and it is referenced through the `<inspire_common:MetadataURL>` element within the extended INSPIRE capabilities of such service.
- The service metadata shall define a `<srv:operatesOn>` element for every defined data set published by the service.
- The data set metadata URL may point to a Discovery Service different from the national reference catalog. This may apply especially for federated Discovery Service catalogues.

### Requirement: \<srv:operatesOn\> element

| **Requirement** | **/req/coupled-resource-operateson-locator** |
| --- | --- |
| A | The `xlink:href` attribute of each of the `srv:operatesOn` elements SHALL contain a URI pointing to the metadata record of the provided data set or data set series. |

### 8.2.2 INSPIRE Network service - Scenario 2

 - With the implementation of the Scenario 2, the [INSPIRE NS - Download Service TG] maps all INSPIRE metadata elements to the OGC capabilities elements, where applicable, and it relies on the ExtendedCapabilities section for the remaining elements.
- The data set metadata URL may point to a Discovery Service different from the national reference catalog. This may apply especially for federated Discovery Service catalogues.

### Requirement: \<wms:MetadataURL\> and \<wfs:MetadataURL\> elements

| **Requirement** | **/req/coupled-resource-metadataurl-locator** |
| --- | --- |
| A | The URL expressed within the element `metadataURL` SHALL resolve to the metadata record of the data set or data set series, available in a Discovery Service catalog. |

## 9. Future developments <a name="future-dev"></a>

Within this document, the series of recommendations imply the possibility of further simplifications, on a broader level about the INSPIRE implementation.
Note that often the person or organization responsible for the metadata is not the same as the responsible for the service operations. This can lead to duplication, errors and/or outdated set of information.
For instance, the more direct connection expressed with these recommendations could suggest the implementation of a [Scenario 2], which requirements and definitions are already provided in both the [INSPIRE NS - Download Service TG] and [INSPIRE NS - View Service TG] documents.
In this case, the service metadata is no longer required (at least, for this linkage simplification purpose) and so its creation can be skipped, or automated by dedicated features of a software implementation of the INSPIRE Discovery Service.
Furthermore, the implementation of the above mentioned [Scenario 2] for Network Service could offer the opportunity of a revision of the mapping of the INSPIRE requirements, currently expressed in the Extended Capabilities section, since the current lack of support of that vendor section in some (especially commercial) software implementation of OGC service.

# Annex A: Examples <a name="inspire-examples"></a>

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

#### _TO_BE_REVIEW_ Example of a Resource Locator of a data set metadata linking a Download Service (Get Download Service Metadata)

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

#### _TO_BE_REVIEW_ Example of an optional definition of a Resource Locator in the dataset metadata linking directly the downloadable dataset (Get Spatial Data Set)

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
