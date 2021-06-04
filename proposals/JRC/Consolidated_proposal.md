# Data and Service Linking Simplification - Consolidated Proposal

## Introduction

Author: EC JRC based on input from INSPIRE MIWP sub-group 2.3.2.

Short description:
This is a consolidated proposal, based on the collection and comparison of proposals received from the contributing Member State representatives (NL, FR, ES, LT) of the sub-group.

This proposal implements the requirements and recommendations as initially described in the [Discussion Paper on possible simplification of data-service linking in INSPIRE](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/blob/main/resources/Discussion%20Paper%20on%20data-service%20linking%20v0.5.docx) and further improved by the subsequent [proposals for the simplification approach](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/tree/main/proposals) made by the members of the sub-group.
The reference for the metadata specification used in this proposal is the [INSPIRE Technical Guidance document version 2.0.1](https://inspire.ec.europa.eu/id/document/tg/metadata-iso19139). 

## Proposal

#### Data set metadata

The proposed approach for data set metadata is aligned with the Discussion Paper. Data sets are documented in metadata as currently described in the Technical Guidance documents, with minor modifications for the provision of data-service linkage. In the metadata for each data set, resource locator elements are provided for at least one view and one download service (mandatory), pointing to an "INSPIRE Get Download/View Service Metadata" request.

#### Service metadata

The proposed approach recommends to keep the service metadata as currently described in the Technical Guidance documents. This requirement is due to the need of the provision of conformity indicators as described in the [COMMISSION IMPLEMENTING DECISION (EU) 2019/1372](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=uriserv:OJ.L_.2019.220.01.0001.01.ENG&toc=OJ:L:2019:220:FULL) as regards Monitoring and Reporting.

#### Applicable codelists

##### Protocol
- For this element, the central INSPIRE Registry already offers a series of external codelist values from the register: https://inspire.ec.europa.eu/metadata-codelist/ProtocolValue
- Regarding the labels, the central INSPIRE Registry specifies quite long text for the OGC services. On the other hand, the OGC vocabularies specify quite essential labels. For instance, the preferred label for the codelist value `http://www.opengis.net/def/serviceType/ogc/wfs` is `wfs`. The proposal suggest to use the extensive format for ATOM (ie. `ATOM Syndication Format`) and a compact but expressive format `OGC:***` (e.g. `OGC:WFS`, `OGC:WMTS`) for the relative services.

##### ApplicationProfile
- For this element, use a codelist value (eg. `download`, `view`, etc) coming from the `Spatial data service type` metadata codelist: https://inspire.ec.europa.eu/metadata-codelist/SpatialDataServiceType
- By using the above mentioned codelist values coming from the central INSPIRE Registry, it would imply that the described ResourceLocator URL would refer to an INSPIRE Spatial Data Service, fulfilling all the applicable Technical Guidelines requirements.

##### Function
- For this element, use the predefined ISO 19139 schema codelist `<gmd:CI_OnLineFunctionCode>`

#### Use of the `gmd:function` element to distinguish the INSPIRE operations

In order to express the expected INSPIRE operation (and relative response), the `gmd:function` element shall be used. The available ISO 19139 codelist offers two values useful for this purpose: `information` and `download`.

In the current MD TG (v2.0) the Recommendation 5.4 suggest the use of 'information' regarding access point of an Invocable SDS.

To describe the linkage of a INSPIRE Get View/Download Service Metadata (eg. `GetCapabilities`) request, it shall be expressed with:
```xml
<gmd:function>
    <gmd:CI_OnLineFunctionCode codeList="http://standards.iso.org/iso/19139/resources/gmxCodelists.xml#CI_OnLineFunctionCode" codeListValue="information" />
</gmd:function>
```
To describe the linkage of a INSPIRE Get Map / Get Spatial Data Set (eg. `GetMap` or `GetFeature`) request, it shall be expressed with:
```xml
<gmd:function>
    <gmd:CI_OnLineFunctionCode codeList="http://standards.iso.org/iso/19139/resources/gmxCodelists.xml#CI_OnLineFunctionCode" codeListValue="download" />
</gmd:function>
```

#### View Services

In addition to the well-known elements already expressed in the TG requirements (ie. `gmd:linkage/gmd:URL`, `gmd:name`), the Resource Locator element shall contain the INSPIRE definition of a View service, through a `gmd:applicationProfile` element:

```xml
<gmd:applicationProfile>
    <gmx:Anchor xlink:href="http://inspire.ec.europa.eu/metadata-codelist/SpatialDataServiceType/view">view</gmx:Anchor>
</gmd:applicationProfile>
```

Then, the `gmd:protocol` must be specified based on the relative OGC specification of the service.

For a WMS service:

```xml
<gmd:protocol>
    <gmx:Anchor xlink:href="http://www.opengis.net/def/serviceType/ogc/wms">OGC:WMS</gmx:Anchor>
</gmd:protocol>
```

In case of a WMTS service, a specific value from another OGC vocabulary can be used (http://defs.opengis.net/vocprez/object?uri=http%3A//www.opengis.net/def/standards-baseline)

```xml
<gmd:protocol>
    <gmx:Anchor xlink:href="http://www.opengis.net/def/serviceType/ogc/wmts">OGC:WMTS</gmx:Anchor>
</gmd:protocol>
```

Finally, the Resource Locator shall contain the `gmd:function` definition (described before [here](#use-of-the-gmdfunction-element-to-distinguish-the-inspire-operations)).

#### Download services

In addition to the well-known elements already expressed in the TG requirements (ie. `gmd:linkage/gmd:URL`, `gmd:name`), the Resource Locator element shall contain the INSPIRE definition of a Download service, through a `gmd:applicationProfile` element:

```xml
<gmd:applicationProfile>
    <gmx:Anchor xlink:href="http://inspire.ec.europa.eu/metadata-codelist/SpatialDataServiceType/download">download</gmx:Anchor>
</gmd:applicationProfile>
```
Then, for the implementation of a Dowload service the Technical Guidance offers different options, expressed here:

##### ATOM feed

```xml
<gmd:protocol>
    <gmx:Anchor xlink:href="https://tools.ietf.org/html/rfc4287">ATOM Syndication Format</gmx:Anchor>
</gmd:protocol>
```

##### OGC service (WFS, WCS, SOS)

```xml
<gmd:protocol>
    <gmx:Anchor xlink:href="http://www.opengis.net/def/serviceType/ogc/wfs">OGC:WFS</gmx:Anchor>
</gmd:protocol>
```

```xml
<gmd:protocol>
    <gmx:Anchor xlink:href="http://www.opengis.net/def/serviceType/ogc/sos">OGC:SOS</gmx:Anchor>
</gmd:protocol>
```

```xml
<gmd:protocol>
    <gmx:Anchor xlink:href="http://www.opengis.net/def/serviceType/ogc/wcs">OGC:WCS</gmx:Anchor>
</gmd:protocol>
```

Finally, the Resource Locator shall contain the `gmd:function` definition (described before [here](#use-of-the-gmdfunction-element-to-distinguish-the-inspire-operations)).

##### Download services based on OGC APIs (OGC SensorThings API, OGC API - Features)

For the OGC API - Features, a codelist to be used for the `gmd:protocol` element is defined as `http://www.opengis.net/def/interface/ogcapi-features`

For the OGC SensorThings API, a valid codelist value is defined as `http://www.opengis.net/def/serviceType/ogc/sta`.

## Examples (XML encoded)

#### View - WM(T)S - Get View Service Metadata

_Note: for the definition of a WMTS service, use the proper codelist defined before inside the `protocol` element_

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
          <gmx:Anchor xlink:href="http://www.opengis.net/def/serviceType/ogc/wms">OGC:WMS</gmx:Anchor>
        </gmd:protocol>
        <gmd:applicationProfile>
          <gmx:Anchor xlink:href="http://inspire.ec.europa.eu/metadata-codelist/SpatialDataServiceType/view">view</gmx:Anchor>
        </gmd:applicationProfile>
        <gmd:name>
          <gco:CharacterString>INSPIRE WMS</gco:CharacterString>
        </gmd:name>
        <gmd:function>
          <gmd:CI_OnLineFunctionCode codeList="http://standards.iso.org/iso/19139/resources/gmxCodelists.xml#CI_OnLineFunctionCode" codeListValue="information" />
        </gmd:function>
      </gmd:CI_OnlineResource>
    </gmd:onLine>
      [...]
  </gmd:MD_DigitalTransferOptions>
</gmd:transferOptions>
```

#### View - WM(T)S - Get Map

_Note: for the definition of a WMTS service, use the proper codelist defined before inside the `protocol` element_

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
          <gmx:Anchor xlink:href="http://www.opengis.net/def/serviceType/ogc/wms">OGC:WMS</gmx:Anchor>
        </gmd:protocol>
        <gmd:applicationProfile>
          <gmx:Anchor xlink:href="http://inspire.ec.europa.eu/metadata-codelist/SpatialDataServiceType/view">view</gmx:Anchor>
        </gmd:applicationProfile>
        <gmd:name>
          <gco:CharacterString>INSPIRE WMS</gco:CharacterString>
        </gmd:name>
        <gmd:function>
          <gmd:CI_OnLineFunctionCode codeList="http://standards.iso.org/iso/19139/resources/gmxCodelists.xml#CI_OnLineFunctionCode" codeListValue="download" />
        </gmd:function>
      </gmd:CI_OnlineResource>
    </gmd:onLine>
      [...]
  </gmd:MD_DigitalTransferOptions>
</gmd:transferOptions>
```

#### Download - ATOM feed - Get Download Service Metadata

```xml
<gmd:transferOptions>
  <gmd:MD_DigitalTransferOptions>
      [...]
    <gmd:onLine>
      <gmd:CI_OnlineResource>
        <gmd:linkage>
          <gmd:URL>http://.../atom/INSPIRE_DW_2021</gmd:URL>
        </gmd:linkage>
        <gmd:protocol>
          <gmx:Anchor xlink:href="https://tools.ietf.org/html/rfc4287">ATOM Syndication Format</gmx:Anchor>
        </gmd:protocol>
        <gmd:applicationProfile>
          <gmx:Anchor xlink:href="http://inspire.ec.europa.eu/metadata-codelist/SpatialDataServiceType/download">download</gmx:Anchor>
        </gmd:applicationProfile>
        <gmd:name>
          <gco:CharacterString>INSPIRE Download Service (ATOM)</gco:CharacterString>
        </gmd:name>
        <gmd:function>
          <gmd:CI_OnLineFunctionCode codeList="http://standards.iso.org/iso/19139/resources/gmxCodelists.xml#CI_OnLineFunctionCode" codeListValue="information" />
        </gmd:function>
      </gmd:CI_OnlineResource>
    </gmd:onLine>
      [...]
  </gmd:MD_DigitalTransferOptions>
</gmd:transferOptions>
```

#### Download - ATOM feed - Get Spatial Data Set (subfeed)

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
        <gmd:applicationProfile>
          <gmx:Anchor xlink:href="http://inspire.ec.europa.eu/metadata-codelist/SpatialDataServiceType/download">download</gmx:Anchor>
        </gmd:applicationProfile>
        <gmd:name>
          <gco:CharacterString>INSPIRE Download Service (ATOM)</gco:CharacterString>
        </gmd:name>
        <gmd:function>
          <gmd:CI_OnLineFunctionCode codeList="http://standards.iso.org/iso/19139/resources/gmxCodelists.xml#CI_OnLineFunctionCode" codeListValue="download" />
        </gmd:function>
      </gmd:CI_OnlineResource>
    </gmd:onLine>
      [...]
  </gmd:MD_DigitalTransferOptions>
</gmd:transferOptions>
```

#### Download - OGC service - Get Download Service Metadata

_Note: this example covers the WFS definition. For a WCS/SOS service, use the proper codelist defined before inside the `protocol` element_

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
          <gmx:Anchor xlink:href="http://www.opengis.net/def/serviceType/ogc/wfs">OGC:WFS</gmx:Anchor>
        </gmd:protocol>
        <gmd:applicationProfile>
          <gmx:Anchor xlink:href="http://inspire.ec.europa.eu/metadata-codelist/SpatialDataServiceType/download">download</gmx:Anchor>
        </gmd:applicationProfile>
        <gmd:name>
          <gco:CharacterString>INSPIRE Download Service (WFS)</gco:CharacterString>
        </gmd:name>
        <gmd:function>
          <gmd:CI_OnLineFunctionCode codeList="http://standards.iso.org/iso/19139/resources/gmxCodelists.xml#CI_OnLineFunctionCode" codeListValue="information" />
        </gmd:function>
      </gmd:CI_OnlineResource>
    </gmd:onLine>
      [...]
  </gmd:MD_DigitalTransferOptions>
</gmd:transferOptions>
```

#### Download - OGC service - Get Spatial Data Set

_Note: this example covers the WFS definition. For a WCS/SOS service, use the proper codelist defined before inside the `protocol` element_

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
          <gmx:Anchor xlink:href="http://www.opengis.net/def/serviceType/ogc/wfs">OGC:WFS</gmx:Anchor>
        </gmd:protocol>
        <gmd:applicationProfile>
          <gmx:Anchor xlink:href="http://inspire.ec.europa.eu/metadata-codelist/SpatialDataServiceType/download">download</gmx:Anchor>
        </gmd:applicationProfile>
        <gmd:name>
          <gco:CharacterString>INSPIRE Download Service (WFS)</gco:CharacterString>
        </gmd:name>
        <gmd:function>
          <gmd:CI_OnLineFunctionCode codeList="http://standards.iso.org/iso/19139/resources/gmxCodelists.xml#CI_OnLineFunctionCode" codeListValue="download" />
        </gmd:function>
      </gmd:CI_OnlineResource>
    </gmd:onLine>
      [...]
  </gmd:MD_DigitalTransferOptions>
</gmd:transferOptions>
```

### Advantages/disadvantages of the proposed approach

#### Advantages on the use of `gmd:function` element

With this approach, the proposal would use all the available elements under `<gmd:CI_OnlineResource>`. The `function` element uses the predefined ISO 19139 codelist, that offers two useful values (described [here](#use-of-the-gmdfunction-element-to-distinguish-the-inspire-operations)). In this manner, the proposal would keep the `gmd:description` free for current (or future) uses. In the current Metadata TG (v2.0) the TG Requirement 5.2 `metadata/2.0/req/sds-invocable/access-point` requires the `gmd:description` element to point to the value `accessPoint` of the code list `OnLineDescriptionCode`.

### Conclusions

