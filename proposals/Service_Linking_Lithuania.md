# Data and Service Linking Simplification

## Introduction

Country: _Lithuania_

Short description: We use Geonetwork software for metadata creation and datasets and services linking.

## Proposal body

### Details of the proposal
_Firstly, we create metadata for a data set and services, and only then we do publishing of the services. We do so because we insert the dataset and view the service metadata URL to the WMS Getcapabilities.
Our dataset metadata contains Unique resource identifiers (e.g Theme abbreviation (BU), view service layer name (BU.Building), and Codespace (LT.GC.GRPK)) and these elements are provided in the WMS Getcapabilities and ATOM feed as Identifiers for dataset metadata and network service linking._


### Examples of scenarios and metadata (XML encoded)
_OnlineResource description of the downloadable file in the dataset metadata_

```xml
<gmd:transferOptions>
<gmd:MD_DigitalTransferOptions>
<gmd:onLine>
<gmd:CI_OnlineResource>
<gmd:linkage>
<gmd:URL>https://inspire-geoportal.lt/resources/atom/bu/data/BU_INSPIRE2.zip</gmd:URL>
</gmd:linkage>
<gmd:protocol>
<gco:CharacterString>WWW:DOWNLOAD-1.0-http--download</gco:CharacterString>
</gmd:protocol>
<gmd:applicationProfile>
<gco:CharacterString>INSPIRE-ATOM</gco:CharacterString>
</gmd:applicationProfile>
<gmd:name>
<gco:CharacterString>INSPIRE Dataset for Buildings Theme</gco:CharacterString>
</gmd:name>
<gmd:description>
<gco:CharacterString>INSPIRE Dataset for Buildings Theme in ETRS89 - GML file</gco:CharacterString>
</gmd:description>
<gmd:function>
<gmd:CI_OnLineFunctionCode codeList="http://standards.iso.org/iso/19139/resources/gmxCodelists.xml#CI_OnLineFunctionCode" codeListValue="download"/>
</gmd:function>
</gmd:CI_OnlineResource>
</gmd:onLine>
<gmd:onLine>
```

_OnlineResource description of WMS service in the View Service metadata_

```xml
<gmd:CI_OnlineResource>
<gmd:linkage>
<gmd:URL>https://www.inspire-geoportal.lt/geoserver/bu/wms?service=WMS&version=1.3.0&request=GetCapabilities</gmd:URL>
</gmd:linkage>
<gmd:protocol>
<gco:CharacterString>OGC:WMS-1.3.0-http-get-capabilities</gco:CharacterString>
</gmd:protocol>
<gmd:applicationProfile>
<gco:CharacterString>INSPIRE-VIEW</gco:CharacterString>
</gmd:applicationProfile>
<gmd:name>
<gco:CharacterString>BU.Building</gco:CharacterString>
</gmd:name>
<gmd:description>
<gco:CharacterString>Building</gco:CharacterString>
</gmd:description>
<gmd:function>
<gmd:CI_OnLineFunctionCode codeList="http://standards.iso.org/iso/19139/resources/gmxCodelists.xml#CI_OnLineFunctionCode" codeListValue="information"/>
</gmd:function>
</gmd:CI_OnlineResource>
```

_OnlineResource description of ATOM in the Download Service metadata_

```xml
<gmd:transferOptions>
<gmd:MD_DigitalTransferOptions>
<gmd:onLine>
<gmd:CI_OnlineResource>
<gmd:linkage>
<gmd:URL>https://www.inspire-geoportal.lt/geonetwork/srv/eng/atom.predefined.service?uuid=328ff8ef-c6ce-4a41-a096-2630de752298</gmd:URL>
</gmd:linkage>
<gmd:protocol>
<gco:CharacterString>INSPIRE Atom</gco:CharacterString>
</gmd:protocol>
<gmd:applicationProfile>
<gco:CharacterString>INSPIRE-ATOM</gco:CharacterString>
</gmd:applicationProfile>
</gmd:CI_OnlineResource>
</gmd:onLine>
</gmd:MD_DigitalTransferOptions>
</gmd:transferOptions>
```
_WMS Getcapabilities description_

```xml
<WMS_Capabilities xmlns:inspire_vs="http://inspire.ec.europa.eu/schemas/inspire_vs/1.0" xmlns:inspire_common="http://inspire.ec.europa.eu/schemas/common/1.0" xmlns="http://www.opengis.net/wms" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" version="1.3.0" updateSequence="2252" xsi:schemaLocation="http://www.opengis.net/wms https://www.inspire-geoportal.lt/geoserver/schemas/wms/1.3.0/capabilities_1_3_0.xsd http://inspire.ec.europa.eu/schemas/inspire_vs/1.0 http://inspire.ec.europa.eu/schemas/inspire_vs/1.0/inspire_vs.xsd">

...
<Identifier authority="LT.GC.GRPK">BU.Building</Identifier>
<MetadataURL type="ISO19115:2003">
<Format>text/plain</Format>
<OnlineResource xlink:type="simple" xlink:href="https://www.inspire-geoportal.lt/geonetwork/srv/eng/csw?service=CSW&request=GetRecordById&version=2.0.2&outputSchema=http://www.isotc211.org/2005/gmd&elementSetName=full&id=3722b45f-5fa0-4f60-8c6f-c27f69619b1e"/>
</MetadataURL>
...
</WMS_Capabilities>
```


_ATOM feed description_

```xml
<feed xmlns="http://www.w3.org/2005/Atom" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://www.w3.org/2005/Atom http://inspire-geoportal.ec.europa.eu/schemas/inspire/atom/1.0/atom.xsd" xml:lang="en">
  <title>Annex III. INSPIRE ATOM Download Service (predefined datasets) for Buildings Theme</title>
 
...
 <entry>
    <inspire_dls:spatial_dataset_identifier_code xmlns:inspire_dls="http://inspire.ec.europa.eu/schemas/inspire_dls/1.0">BU</inspire_dls:spatial_dataset_identifier_code>
    <inspire_dls:spatial_dataset_identifier_namespace xmlns:inspire_dls="http://inspire.ec.europa.eu/schemas/inspire_dls/1.0">LT.GC.GRPK</inspire_dls:spatial_dataset_identifier_namespace>
    <category term="http://www.opengis.net/def/crs/EPSG/0/unknown" label="Unknown" />
    <author>
      <name>SE GIS-Centras</name>
      <email>info@gis-centras.lt</email>
    </author>
    <id>https://www.inspire-geoportal.lt:/geonetwork/srv/atom/describe/dataset?spatial_dataset_identifier_code=BU&amp;spatial_dataset_identifier_namespace=LT.GC.GRPK&amp;language=en</id>
    <link rel="describedby" type="application/xml" href="https://www.inspire-geoportal.lt:/geonetwork/srv/eng/csw?service=CSW&amp;version=2.0.2&amp;request=GetRecordById&amp;outputschema=http://www.isotc211.org/2005/gmd&amp;elementSetName=full&amp;id=3722b45f-5fa0-4f60-8c6f-c27f69619b1e" />
    <link type="application/atom+xml" rel="alternate" hreflang="en" title="INSPIRE Dataset ATOM feed: Annex III. INSPIRE Dataset for Buildings Theme" href="https://www.inspire-geoportal.lt:/geonetwork/srv/atom/describe/dataset?spatial_dataset_identifier_code=BU&amp;spatial_dataset_identifier_namespace=LT.GC.GRPK&amp;language=en" />
    <rights>otherRestrictions.</rights>
    <summary>INSPIRE dataset for Buildings theme represents information about buildings located in the territory of Lithuania. The objects are shown at a scale of 50:25 000 through the view service.</summary>
    <title>Annex III. INSPIRE Dataset for Buildings Theme</title>
    <updated>2021-04-08T09:00:04Z</updated>
    <georss:polygon xmlns:georss="http://www.georss.org/georss">53.84835 20.59123 56.45108 20.59123 56.45108 26.83282 53.84835 26.83282 53.84835 20.59123</georss:polygon>
  </entry>
</feed>
```
### Advantages/disadvantages of the proposed approach
_In Geonetork INSPIRE extension can be installed, it allows configure download and view services corresponding to INSPIRE requirements. This facilitates the process of creating metadata and the process of linking services and datasets._

### Conclusions 
_text here_
