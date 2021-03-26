# Data and Service Linking Simplification - Proposal FRA

## Introduction

Country: _France_

Short description: _Proposal to reference network service using existing metadata elements and Anchor mechanism, while allowing old approach in parallel (service metadata).

## Proposal body

### Details of the proposal
For simple cases, when the dataset is served by a known service:
Reference the service access point (download and view). Several services can be referenced. Other services can be references as well, identification of INSPIRE network services would be made using Anchor pointing to codelists. 

For more complex use cases (for example if the data producer does not know the URL of the final service) the "old" approach using service metadata would still be available. The Geoportal would check "new" linking first and if no success it would check the "old" one (searching for a corresponding service metadata). 

### Examples of scenarios and metadata (XML encoded)

The proposal would be to reference the network services like this: 

```xml
<gmd:MD_Metadata …
…
	<gmd:distributionInfo>
		<gmd:MD_Distribution>
…
			<gmd:transferOptions>
				<gmd:MD_DigitalTransferOptions>
					<gmd:onLine>
						<gmd:CI_OnlineResource>
							<gmd:linkage>
								<gmd:URL>http://xxx.xxx.xxx/atom.xml</gmd:URL>
							 </gmd:linkage>
							 <gmd:protocol>
									<gmx:Anchor xlink:href="http://tools.ietf.org/html/rfc5023">ATOM Syndication Format</gmx:Anchor>
							 </gmd:protocol>
							 <gmd:applicationProfile>
								 <gmx:Anchor xlink:href="http://inspire.ec.europa.eu/metadata-codelist/SpatialDataServiceType/download ">Download Service</gmx:Anchor>
							 </gmd:applicationProfile>
							<gmd:description>
								 <gmx:Anchor xlink:href="http://inspire.ec.europa.eu/metadatacodelist/OnLineDescriptionCode/accessPoint">Access Point</gmx:Anchor>
							 </gmd:description>
						</gmd:CI_OnlineResource>
				</gmd:onLine>
			</gmd:MD_DigitalTransferOptions>
		</gmd:transferOptions>
	</gmd:MD_Distribution>
</gmd:distributionInfo>
…
</gmd:MD_Metadata>
```

The code list used would be:
https://inspire.ec.europa.eu/metadata-codelist/OnLineDescriptionCode for the _description_ element;

https://inspire.ec.europa.eu/metadata-codelist/SpatialDataServiceType for the _applicationProfile_ element;

For the _protocol_ element the list would be:
| Identifier  | Value |
|--|--|
|http://www.opengis.net/def/serviceType/ogc/csw| OGC Catalogue Service for the Web|
|http://www.opengis.net/def/serviceType/ogc/sos| OGC Sensor Observation Service|
|http://www.opengis.net/def/serviceType/ogc/wcs| OGC Web Coverage Service|
|http://www.opengis.net/def/serviceType/ogc/wfs| OGC Web Feature Service|
|http://www.opengis.net/def/serviceType/ogc/wms| OGC Web Map Service|
|http://www.opengis.net/def/serviceType/ogc/wmts| OGC Web Map Tile Service|
|http://tools.ietf.org/html/rfc5023|ATOM Syndication Format|


### Advantages/disadvantages of the proposed approach
Close to what is already used in many countries. Usage of Anchors allow a free text in the element (especially useful for those who are alredy using the same element for something else). 

### Conclusions 


