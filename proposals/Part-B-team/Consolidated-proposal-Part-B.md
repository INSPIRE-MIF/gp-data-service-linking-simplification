# Data Service Linking Simplification - Part B: Remapping of the Extended Capabilities

`Version: draft 1.0`
`Date: 2022-03-21`

## Table of Contents

_TO_BE_REVISED_

* [1. Introduction](#introduction)
* [2. Scope](#scope)
* [3. Mapping of INSPIRE elements in ExtendedCapabilities](#mapping-extended-capabilities)
  * [3.1. Resource type](#resource-type)
  * [3.2. Resource locator](#resource-locator)
  * [3.3. Spatial data service type](#spatial-data-service-type)
  * [3.4. Temporal reference](#temporal-reference)
  * [3.5. Conformity](#conformity)
  * [3.6. Metadata point of contact](#metadata-point-of-contact)
  * [3.7. Metadata date](#metadata-date)
  * [3.8. Supported languages](#supported-languages)
  * [3.9 INSPIRE Spatial data set identifier](#inspire-data-set-identifier)
  

## 1. Introduction <a name="introduction"></a>

This part follows-up the proposal given in the [**Annex B**](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/blob/main/proposals/JRC/ds-linking-simplification-good-practice.md#annex-b-mapping-of-inspire-elements-in-the-extended-capabilities-section-) in the Good Practice guidelines by providing the details and the agreed version of the new mapping of INSPIRE service metadata elements to the available elements in the GetCapabilities document of the OGC base standard services (WMS, WFS) and Atom feed in order to remove the need for the Extended Capabilities section and thus achieve a more complete implementation simplification.

Currently, the INSPIRE metadata elements that cannot be mapped to available elements in the GetCapabilities document of the OGC base standard services are implemented as Extended Capabilities. In case of Atom, only some of the mandatory INSPIRE Metadata elements for the Download service have been mapped to the Atom feed files. The current mapping between INSPIRE metadata elements and ISO 19128 WMS elements is provided in the Table 3 in [INSPIRE NS - View Service TG](https://inspire.ec.europa.eu/documents/technical-guidance-implementation-inspire-view-services-1), whereas the mapping of INSPIRE Metadata elements to Atom and to ISO 19142 WFS is provided in the Table 17 (page 38) and Table 19 (page 66) in [INSPIRE NS - Download Service TG](https://inspire.ec.europa.eu/documents/technical-guidance-implementation-inspire-download-services), respectively.

As outlined in the [Discussion Paper on possible simplification of data-service linking in INSPIRE](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/blob/main/resources/Discussion%20Paper%20on%20data-service%20linking%20v0.5.docx), the aim of the proposed mapping in this document is to remove the requirements to document view and download services in stand-alone (ISO 19119/ISO TS 19139) service metadata records and to exclusively document those network services through the metadata returned by the service itself as a response to a Get Download/View Service Metadata request.

## 2. Scope <a name="scope"></a>

This part provides a set of rules for the mapping of INSPIRE metadata elements with a new allocation in the GetCapabilities document in the OGC base standard services and the Atom feed.

## 3. Mapping of INSPIRE elements in ExtendedCapabilities <a name="mapping-extended-capabilities"></a>

The Table below provides a summary of the new mapping of INSPIRE metadata elements, previously mapped with elements in the Extended Capabilities section. 

| INSPIRE metadata elements | New allocation | Applicable on Service type |
| :- | :- | :- |
| Resource Type          | No element mapped | WMS - WFS - Atom |
| Resource Locator       | No element mapped| WMS - WFS - Atom |
| Spatial Data Service Type| `gmd:applicationProfile` element (in data set metadata record) | WMS - WFS - Atom |
| Temporal Reference     | `updateSequence` attribute in the `WMS_Capabilities`/`WFS_Capabilities` root element. Otherwise, `gmd:citation/gmd:CI_Citation/gmd:date/gmd:CI_Date/gmd:date` element in the data set metadata record, with one of the following prioritised  date types:- _publication_, - _revision_ or - _creation_ | WMS - WFS |
|                        | `feed/updated` element in the Atom feed. Otherwise, `gmd:citation/gmd:CI_Citation/gmd:date/gmd:CI_Date/gmd:date` element in the data set metadata record, with one of the following prioritised  date types: - _publication_, - _revision_ or - _creation_ | Atom |
| Conformity            | `wms:Keyword` element for each specification against the service is conformant, included within an specific `wms:KeyworList` group. | WMS |
|                       | `ows:Keyword` element for each specification against the service is conformant, included within an specific `ows:Keywords` group including an `ows:Type` element of type URI. | WFS |
|                       |  `atom:category` element for each specification against which the service is conformant. | Atom |
| Metadata Point of Contact| `WMS_Capabilities/Service/ContactInformation/ContactPersonPrimary/ContactOrganization` and `WMS_Capabilities/Service/ContactInformation/ContactElectronicMailAddress` elements in GetCapabilities | WMS |
|                          | `WFS_Capabilities/ows:ServiceProvider/ows:ProviderName` and `WFS_Capabilities/ows:ServiceProvider/ows:ServiceContact/ows:ContactInfo/ows:Address/ows:ElectronicMailAddress` elements in GetCapabilities | WFS |
|                          | `<feed><author><name>` and `<feed><author><email>` elements | Atom |
| Metadata Date     | `updateSequence` parameter in the `WMS_Capabilities`/`WFS_Capabilities`root element. Otherwise, `gmd:citation/gmd:CI_Citation/gmd:date/gmd:CI_Date/gmd:date` element in the data set metadata record, with one of the following prioritised  date types:- _publication_, - _revision_ or - _creation_ | WMS - WFS |
|                        | `<updated>` element in the Atom feed. Otherwise, `gmd:citation/gmd:CI_Citation/gmd:date/gmd:CI_Date/gmd:date` element in the data set metadata record, with one of the following prioritised  date types: - _publication_, - _revision_ or - _creation_ | Atom|
| Metadata Language    | `gmd:MD_Metadata/gmd:language/gmd:LanguageCode` element in the data set metadata record for default language. `xml:lang` attribute for supported languages    | WMS - WFS - Atom |


Below, for each mapping element, the following information is provided: 
- the current mapping present in [INSPIRE NS - View Service TG](https://inspire.ec.europa.eu/documents/technical-guidance-implementation-inspire-view-services-1) and [INSPIRE NS - Download Service TG](https://inspire.ec.europa.eu/documents/technical-guidance-implementation-inspire-download-services);
- proposed mapping and rationale;
- detailed mapping description; and
- changes to the current INSPIRE framework.

### 3.1. Resource type <a name="resource-type"></a>

Currently, the mapping of the resource type element to OWS service capabilities and Atom feed is as follows: 

| INSPIRE metadata elements | Elements of OWS service capabilities / Atom feed | Applicable on Service type |
| :- | :- | :- |
| Resource Type          | `inspire_common:ResourceType` (ExtendedCapabilities) | WMS - WFS |
| Resource Type          | not mapped | Atom |

#### Proposed mapping and rationale

As proposed in the [Discussion Paper on possible simplification of data-service linking in INSPIRE](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/blob/main/resources/Discussion%20Paper%20on%20data-service%20linking%20v0.5.docx), if service metadata is available only through the given service, the resource type is implicit.

#### Detailed mapping description

No element is identified in the GetCapabilities document for the mapping with the resource type element.

#### Changes to the current INSPIRE framework

Integrate the TG Requirement 3.1 in [metadata TG](https://github.com/INSPIRE-MIF/technical-guidelines/blob/2022.1/metadata/metadata-iso19139/metadata-iso19139.adoc) with the following statement:

_In case of view and download services, when the service metadata is provided as response to a Get Download/View Service Metadata request, then the resource type is implicit and shall not be documented_.

Integrate the Implementation Requirement 11 in [View Services TG] with the following statement:

_In case the service metadata is provided as response to a Get Download/View Service Metadata request, then the resource type is implicit and shall not be documented_.

### 3.2. Resource locator <a name="resource-locator"></a>

Currently, the mapping of the resource locator element to OWS service capabilities and Atom feed is as follows: 

| INSPIRE metadata elements | Elements of OWS service capabilities / Atom feed | Applicable on Service type |
| :- | :- | :- |
| Resource Locator          | `inspire_common:ResourceLocator` (ExtendedCapabilities) | WMS - WFS |
| Resource Locator          | Feed level link in the top Atom feed `/feed/link[@rel="self"]` | Atom |

#### Proposed mapping and rationale

As proposed in the [Discussion Paper on possible simplification of data-service linking in INSPIRE](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/blob/main/resources/Discussion%20Paper%20on%20data-service%20linking%20v0.5.docx), if service metadata is available only through the given service, the resource locator is implicit; furthermore, more detailed information is available in the operations metadata of the service.

#### Detailed mapping description

No element is identified in the GetCapabilities document for the mapping with the resource locator element.

#### Changes to the current INSPIRE framework

TBD

### 3.3. Spatial data service type <a name="spatial-data-service-type"></a>

Currently, the mapping of the spatial data service type element to OWS service capabilities and Atom feed is as follows:

| INSPIRE metadata elements | Elements of OWS service capabilities / Atom feed | Applicable on Service type |
| :- | :- | :- |
| Spatial Data Service Type          | `inspire_common:SpatialDataServiceType` (ExtendedCapabilities) | WMS - WFS |
| Spatial Data Service Type          | not mapped | Atom |


#### Proposed mapping and rationale

The spatial data service type will be provided by providing the application profile element on the resource locator in the data set metadata record pointing to the response of a "Get View/Download Service Metadata" request of the service providing access to that data set.

#### Detailed mapping description

The [requirements](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/blob/main/proposals/JRC/ds-linking-simplification-good-practice.md#requirement-gmdapplicationprofile-element) to meet for the implementation of the mapping are already defined in the Good Practice guidelines.

For WMS, the value to be used for the encoding of the applicationProfile element is "view" (URI: http://inspire.ec.europa.eu/metadata-codelist/SpatialDataServiceType/view).

For WFS and ATOM, the value to be used for the encoding of the applicationProfile element is "download" (URI: http://inspire.ec.europa.eu/metadata-codelist/SpatialDataServiceType/download).

#### Changes to the current INSPIRE framework

TBD

### 3.4. Temporal reference <a name="temporal-reference"></a>

Currently, the mapping of the temporal reference element to OWS service capabilities and Atom feed is as follows:

| INSPIRE metadata elements | Elements of OWS service capabilities / Atom feed | Applicable on Service type |
| :- | :- | :- |
| Temporal Reference          | `inspire_common:TemporalReference` (ExtendedCapabilities) | WMS - WFS |
| Temporal Reference          | not mapped | Atom |

#### Proposed mapping and rationale

Temporal reference[^note_temporal_reference_19139] will be mapped to

- The optional `updateSequence` attribute in case of a WXS if in this attribute a timestamp value[^note_format_updatesequence] is present;
- The mandatory `<updated>` in case of an Atom[^note_format_updated].

[^note_temporal_reference_19139]: In a ISO/TS 19139 metadata record, Temporal reference is mapped to `MD_Metadata.identificationInfo > MD_DataIdentification.citation > CI_Citation.date > CI_Date.date` element, see also [metadata TG](https://github.com/INSPIRE-MIF/technical-guidelines/blob/2022.1/metadata/metadata-iso19139/metadata-iso19139.adoc).

[^note_format_updatesequence]: The extended ISO 8601:2000 format, ccyy-mm-ddThh:mm:ss.sssZ whereby the precision may be reduced by omitting least-significant digits, e.g. 2022-01-26 or 2022-01-26T09:30Z, shall be used according to the [WMS specification](http://portal.opengeospatial.org/files/?artifact_id=14416). No reference to or description of the precise ISO 8601 format to be used, extended or basic, is present in the [OWS specification](https://portal.ogc.org/files/?artifact_id=20040).

[^note_format_updated]: The `updated` element shall be a timestamp including a time component, see also [The "atom:updated" Element](https://datatracker.ietf.org/doc/html/rfc4287#section-4.2.15) and [Date Constructs](https://datatracker.ietf.org/doc/html/rfc4287#section-3.3).

If in the optional `updateSequence` attribute a timestamp value is not present (WXS), the Metadata Date is mapped to the Temporal reference of the dataset metadata[^note_temporal_reference_19139]:

1. If a date of type `publication` is present, take this value as Temporal Reference; or
2. If a date of type `revision` is present, take this value as Temporal Reference;
3. Otherwise, take the date of type `creation` as value of the Temporal Reference.

For a WXS, this means that the last update of the service metadata is assumed to be the same as the publication, revision or creation date of the data set. For Atom, this means that the last update of the service metadata is assumed equal to the update date of the service.

The same mapping is also used to derive the [Metadata date](#metadata-date) of the service.

The reasoning behind is that:
- The metadata in the capabilities is part of the service, so the update date of the metadata and the service are the same;
- The `updateSequence` attribute is optional in WXS, a fallback scenario is needed if this attribute is not present;
- In the case of deriving the Temporale Reference of the service from the dataset metadata, a strong connection between the administrator of the dataset metadata and the administrator of the service is needed.

#### Detailed mapping description

For **WMS 1.3**, the related [XML schema](http://schemas.opengis.net/wms/1.3.0/capabilities_1_3_0.xsd) snippet is:

```xml
<element name="WMS_Capabilities">
<annotation>
   <documentation>
        A WMS_Capabilities document is returned in response to a GetCapabilities request made on a WMS.
   </documentation>
</annotation>
<complexType>
   <sequence>
      <element ref="wms:Service"/>
      <element ref="wms:Capability"/>
   </sequence>
   <attribute name="version" type="string" fixed="1.3.0"/>
   <attribute name="updateSequence" type="string"/>
</complexType>
</element>
```

So it would look like this in a GetCapabilities response:

```xml
<WMS_Capabilities
  xmlns="http://www.opengis.net/wms"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  version="1.3.0"
  updatesequence="2022-01-26"
  xsi:schemaLocation="http://www.opengis.net/wms http://schemas.opengis.net/wms/1.3.0/capabilities_1_3_0.xsd>
  <!-- ... -->
</WMS_Capabilities>
```

For **WFS 2.0**, using [OWS 1.1 schemas](http://www.opengis.net/ows/1.1), the related XML schema snippet is:

```xml
<complexType name="CapabilitiesBaseType">
   <annotation>
      <documentation>XML encoded GetCapabilities operation response.
      </documentation>
   </annotation>
   <sequence>
      <element ref="ows:ServiceIdentification" minOccurs="0"/>
      <element ref="ows:ServiceProvider" minOccurs="0"/>
      <element ref="ows:OperationsMetadata" minOccurs="0"/>
   </sequence>
   <attribute name="version" type="ows:VersionType" use="required"/>
   <attribute name="updateSequence" type="ows:UpdateSequenceType"
use="optional">
      <annotation>
         <documentation>Service metadata document version, having
values that are "increased" whenever any change is made in service
metadata document. Values are selected by each server, and are always
opaque to clients. When not supported by server, server shall not
return this attribute. </documentation>
         </annotation>
    </attribute>
</complexType>
```

So it would look like this in a GetCapabilities response:


```xml
<WFS_Capabilities xmlns="http://www.opengis.net/wfs/2.0" 
    xmlns:ows="http://www.opengis.net/ows/1.1" 
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" version="2.0.0" 
    xsi:schemaLocation="http://www.opengis.net/wfs/2.0 http://schemas.opengis.net/wfs/2.0/wfs.xsd"
    updateSequence="2022-01-26">
    <ows:ServiceIdentification>
    <!-- ... -->
    </ows:ServiceIdentification>
</WFS_Capabilities>
```

For an **ATOM feed**:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<feed xmlns="http://www.w3.org/2005/Atom" xmlns:georss="http://www.georss.org/georss" xmlns:inspire_dls="http://inspire.ec.europa.eu/schemas/inspire_dls/1.0" xml:lang="nl">
<updated>2022-01-26T00:00:00Z</updated>
```

#### Changes to the current INSPIRE framework


### 3.5. Conformity <a name="conformity"></a>

_@jescriu_

#### Proposed mapping and rationale


#### Detailed mapping description


#### Changes to the current INSPIRE framework


### 3.6. Metadata point of contact <a name="metadata-point-of-contact"></a>

Currently, the mapping of the metadata point of contact element to OWS service capabilities and Atom feed is as follows:

| INSPIRE metadata elements | Elements of OWS service capabilities / Atom feed | Applicable on Service type |
| :- | :- | :- |
| Metadata Point of Contact          | `inspire_common:MetadataPointOfContact` (ExtendedCapabilities) | WMS - WFS |
| Metadata Point of Contact          | not mapped | Atom |

#### Proposed mapping and rationale

Metadata Point Of Contact [^note_metadata_poc_19139] will be mapped to the contact information for the service. This means that the Metadata Point Of Contact is assumed to be the same as the Responsible Organisation.
[^note_metadata_poc_19139]: In a ISO/TS 19139 metadata record, Metadata Point Of Contact is mapped to `gmd:MD_metadata/gmd:contact/gmd:CI_ResponsibleParty`, see also [metadata TG](https://github.com/INSPIRE-MIF/technical-guidelines/blob/2022.1/metadata/metadata-iso19139/metadata-iso19139.adoc).


#### Detailed mapping description

For WMS 1.3 [XML schema](http://schemas.opengis.net/wms/1.3.0/capabilities_1_3_0.xsd):
Metadata Point of Contact - organisation name: `WMS_Capabilities/Service/ContactInformation/ContactPersonPrimary/ContactOrganization`
Metadata Point of Contact - e-mail: `WMS_Capabilities/Service/ContactInformation/ContactElectronicMailAddress`

```xml
  <ContactInformation>
    <ContactPersonPrimary>
      <ContactOrganization>organisation name</ContactOrganization>
    </ContactPersonPrimary>
    <ContactElectronicMailAddress>contact@myorg.eu</ContactElectronicMailAddress>
  </ContactInformation>
```

For WFS 2.0, that uses the [OWS 1.1 schemas](http://www.opengis.net/ows/1.1) (see also http://docs.opengeospatial.org/is/09-025r2/09-025r2.html#23):
Metadata Point of Contact - organisation name: `WFS_Capabilities/ows:ServiceProvider/ows:ProviderName`
Metadata Point of Contact - e-mail: `WFS_Capabilities/ows:ServiceProvider/ows:ServiceContact/ows:ContactInfo/ows:Address/ows:ElectronicMailAddress`

```xml
<ows:ServiceProvider>
	<ows:ProviderName>organisation name</ows:ProviderName>
	<ows:ServiceContact>
		<ows:ContactInfo>
			<ows:Address>
				<ows:ElectronicMailAddress>contact@myorg.eu</ows:ElectronicMailAddress>
			</ows:Address>
		</ows:ContactInfo>
	</ows:ServiceContact>
</ows:ServiceProvider>
```

For An ATOM feed
Metadata Point of Contact - organisation name: `feed/author/name`
Metadata Point of Contact - e-mail: `feed/author/email`

```xml
<author> <name>organisation name</name> <email>contact@myorg.eu</email> </author>
```

#### Changes to the current INSPIRE framework

Note to be added to the Service Technical Guidelines:
**Note**: In cases where external ISO 19139 service metadada will not exist (i.e. only the Capabilities document of the service will), the metadata point of contact would be considered the same as the service provider.

### 3.7. Metadata date <a name="metadata-date"></a>

Currently, the mapping of the metadata date element to OWS service capabilities and Atom feed is as follows:

| INSPIRE metadata elements | Elements of OWS service capabilities / Atom feed | Applicable on Service type |
| :- | :- | :- |
| Metadata Date          | `inspire_common:MetadataDate` (ExtendedCapabilities) | WMS - WFS |
| Metadata Date          | Feed level link in the top Atom feed `/feed/updated` | Atom |

#### Proposed mapping and rationale

Metadata Date [^note_metadata_data_19139] will be mapped to
[^note_metadata_data_19139]: In a ISO/TS 19139 metadata record, Metadata Date is mapped to `MD_metadata.dateStamp` element, see also [metadata TG](https://github.com/INSPIRE-MIF/technical-guidelines/blob/2022.1/metadata/metadata-iso19139/metadata-iso19139.adoc).

- The optional `updateSequence` attribute in case of a WXS if in this attribute a timestamp value[^note_format_updatesequence] is present;
- The mandatory `<updated>` in case of an Atom[^note_format_updated].

Otherwise, if the optional `updateSequence` attribute is not present (WXS), the Metadata Date is mapped to the Temporal reference[^note_temporal_reference_19139] of the dataset metadata.

- If a date of type 'publication' is present, take this value as Metadata Date;
- If a date of type 'revision' is present, take this value as Metadata Date;
- Otherwise, take the date of type 'creation' as value of the Metadata Date.

For a WXS, this means that the last update of the service metadata is assumed to be the same as the publication, revision or creation date of the data set. For Atom, this means that the last update of the service metadata is assumed equal to the update date of the service.

The same elements are also used to derive the Temporal reference of the service.

The reasoning behind is that:
- The metadata in the capabilities is part of the service, so the update date of the metadata and the service are the same.
- The `updateSequence` attribute is optional in WXS, a fallback scenario is needed if this attribute is not present.
- In the case of deriving the Metadata date of the service from the dataset metadata, a strong connection between the administrator of the dataset metadata and the administrator of the service is needed.

#### Detailed mapping description

See the detailed mapping for [Temporal](#temporal-reference).

#### Changes to the current INSPIRE framework


### 3.8. Supported languages <a name="supported-languages"></a>

Currently, the mapping of the metadata language to OWS service capabilities and Atom feed is as follows:

| INSPIRE metadata elements | Elements of OWS service capabilities / Atom feed | Applicable on Service type |
| :- | :- | :- |
| Metadata Language          | `inspire_common:SupportedLanguages` (ExtendedCapabilities) | WMS - WFS |
| Metadata Language          | Feed level link in the top Atom feed `/feed/link[@rel="self"]/@hreflang` | Atom |

#### Proposed mapping and rationale

The default language will be set to the data set metadata default language.

The other supported language (if any) will be mapped to the `xml:lang` attributes for WFS and ATOM and the SupportedLanguages element of the INSPIRE GetCapabilities extension.

#### Detailed mapping description

For multiple language support:

```xml
 <ows:ServiceIdentification>
      <ows:Title xml:lang="en">My WFS</ows:Title>
      <ows:Title xml:lang="da">Min WFS</ows:Title>
      <ows:Abstract xml:lang="en">My abstract</ows:Abstract>
      <ows:Abstract xml:lang="da">Min abstrakt</ows:Abstract>
      <ows:Keywords>
        <ows:Keyword xml:lang="en">My keyword</ows:Keyword>
        <ows:Keyword xml:lang="da">Mit emneord</ows:Keyword>
      </ows:Keywords>
      <ows:ServiceType>WFS</ows:ServiceType>
      <ows:ServiceTypeVersion>2.0.2</ows:ServiceTypeVersion>
      <ows:ServiceTypeVersion>2.0.1</ows:ServiceTypeVersion>
      <ows:ServiceTypeVersion>2.0.0</ows:ServiceTypeVersion>
      <ows:ServiceTypeVersion>1.1.0</ows:ServiceTypeVersion>
      <ows:ServiceTypeVersion>1.0.0</ows:ServiceTypeVersion>
      <ows:Fees>NONE</ows:Fees>
      <ows:AccessConstraints>NONE</ows:AccessConstraints>
   </ows:ServiceIdentification>
```

#### Changes to the current INSPIRE framework

In the Download Service Technical Guidelines, add the following requirement:
**Requirement**: If the service supports several languages and if there is no Extended Capabilities, the xml:lang attribute shall be used to define the language used.
(insert the example above)

### 3.9 INSPIRE Spatial data set identifier <a name="inspire-data-set-identifier"></a>

_@AntoRot_ + _@ALL_

#### Proposed mapping and rationale


#### Detailed mapping description


#### Changes to the current INSPIRE framework

