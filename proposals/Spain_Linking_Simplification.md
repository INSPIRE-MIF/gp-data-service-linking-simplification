# Data and Service Linking Simplification - Proposal Spain

## Introduction

Country: _Spain_

Short description: Proposal to reference network service using existing metadata elements for the dataset and how you link the dataset metadata file in the GetCapabilities response of the network services. This way there is no need for using the service metadata file and the <inspire_vs:ExtendedCapabilities> element within the GetCapabilities response.

## Proposal body

### Details of the proposal
* This proposal implements the requirements and recommendations as described in the in the MIG-T discussed [Data and Service Linking Simplification proposal](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/blob/main/resources/Discussion%20Paper%20on%20data-service%20linking%20v0.5.docx) and the metadata is based on [INSPIRE TG version 2.0.1](https://inspire.ec.europa.eu/id/document/tg/metadata-iso19139).

For implementing data-service linking, in our opinion, we should be able to:

**A) Access network services through the dataset metadata file.**
This can be done in the dataset metadata file fulfilling the element <gmd:CI_OnlineResource> with the information of all the network services related to this dataset.
Below in this approach you can see an example of a dataset metadata file that can be accesible through WMS, WFS and Atom. 

**B) Linking the dataset metadata file through the network services:**

B1) If we are not using a Service metadata file
In the GetCapabilities we will complete the <MetadataURL> element linking with the dataset metadata file.
Below in this approach you can see an example for WMS, WFS and Atom. 

B2) If we are using Service metadata file
Everything would be the same as B1 but you will have to add in the <inspire_vs:ExtendedCapabilities> of the GetCapabilities response, the link to the Service dataset file. 
I haven't copied any of this in this approach because I think it is not necessary since the idea is that the extended capabilities section disappears and there will be no service metadata file anymore.


### Examples of scenarios and metadata (XML encoded)

Here below a proposal for the Administrative Units of Spain:

**A) Linking network services through the dataset metadata file (XML encoded)**

This is the dataset metadata file of the Administrative Units of Spain: https://www.ign.es/csw-inspire/srv/spa/csw?SERVICE=CSW&VERSION=2.0.2&REQUEST=GetRecordById&outputSchema=http://www.isotc211.org/2005/gmd&ElementSetName=full&ID=spaignLLM)


In the element <gmd:MD_DigitalTransferOptions> you can add all the network services related with the dataset.

WMS
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
                              <gmd:URL>https://www.ign.es/wms-inspire/unidades-administrativas?REQUEST=GetCapabilities&amp;SERVICE=WMS&amp;VERSION=1.3.0</gmd:URL>
                           </gmd:linkage>
						   <gmd:protocol>
								<gmx:Anchor xlink:href="http://www.opengis.net/def/serviceType/ogc/wms">OGC Web Map Service</gmx:Anchor>
						   </gmd:protocol>
							<gmd:applicationProfile>
								<gmx:Anchor xlink:href="https://inspire.ec.europa.eu/metadata-codelist/SpatialDataServiceType/view">WMS</gmx:Anchor>
							</gmd:applicationProfile>
                           <gmd:name>
                              <gco:CharacterString>Servicio de visualización (WMS) de Unidades administrativas de España</gco:CharacterString>
                           </gmd:name>
							<gmd:description>
								<gmx:Anchor xlink:href="https://inspire.ec.europa.eu/metadata-codelist/OnLineDescriptionCode/accessPoint">URL de acceso al WMS de Unidades Administrativas de España</gmx:Anchor>
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

WFS

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
                              <gmd:URL>https://www.ign.es/wfs-inspire/unidades-administrativas?REQUEST=GetCapabilities&amp;SERVICE=WFS&amp;VERSION=2.0.0</gmd:URL>
                           </gmd:linkage>
						   <gmd:protocol>
								<gmx:Anchor xlink:href="http://www.opengis.net/def/serviceType/ogc/wfs">OGC Web Feature Service</gmx:Anchor>
							</gmd:protocol>
							<gmd:applicationProfile>
									<gmx:Anchor xlink:href="https://inspire.ec.europa.eu/metadata-codelist/SpatialDataServiceType/download">Servicio de descarga WFS</gmx:Anchor>
							</gmd:applicationProfile>
							<gmd:name>
                              <gco:CharacterString>Servicio de descarga (WFS) de Unidades administrativas de España</gco:CharacterString>
                           </gmd:name>
							<gmd:description>
								<gmx:Anchor xlink:href="https://inspire.ec.europa.eu/metadata-codelist/OnLineDescriptionCode/accessPoint">URL de acceso</gmx:Anchor>
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
Atom
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
                              <gmd:URL>https://www.ign.es/atom/ds.es.xml</gmd:URL>
                           </gmd:linkage>
						    <gmd:protocol>
								<gmx:Anchor xlink:href="https://tools.ietf.org/html/rfc4287">ATOM Syndication Format</gmx:Anchor>
							</gmd:protocol>
							<gmd:applicationProfile>
									<gmx:Anchor xlink:href="https://inspire.ec.europa.eu/metadata-codelist/SpatialDataServiceType/download">Servicio de descarga Atom</gmx:Anchor>
							</gmd:applicationProfile>
                           <gmd:name>
                              <gco:CharacterString>Servicio de descarga (ATOM Feed) de Unidades administrativas de España</gco:CharacterString>
                           </gmd:name>
                          <gmd:description>
								<gmx:Anchor xlink:href="https://inspire.ec.europa.eu/metadata-codelist/OnLineDescriptionCode/accessPoint">URL de acceso</gmx:Anchor>
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

For the element <gmd:protocol> you can select diferent options for the <gmx:Anchor> in the following link: 
https://inspire.ec.europa.eu/metadata-codelist/ProtocolValue/ 

			  
**B) Linking the dataset metadata file through the GetCapabilities response of the network services (XML encoded)**

The proposal have to link the datasets through the network services without using the extended capabilities and the service metadata file.
You can publish several datasets in one service using layers in the case of a WMS, using Feature types in the case of a WFS or using different entries in Atom.

WMS
https://www.ign.es/wms-inspire/unidades-administrativas?REQUEST=GetCapabilities&SERVICE=WMS&VERSION=1.3.0 

```xml

<WMS_Capabilities (…)>
…
	<Capability>
		<Layer>
			<Layer queryable="1">
				<Name>AU.AdministrativeBoundary</Name>
				…
				<Identifier authority="IGN">bdlje_limites_adm</Identifier>
				<MetadataURL type="ISO19115:2003">
					<Format>text/plain</Format>
					<OnlineResource xlink:type="simple" xlink:href="https://www.ign.es/csw-inspire/srv/spa/csw?SERVICE=CSW&VERSION=2.0.2&REQUEST=GetRecordById&outputSchema=http://www.isotc211.org/2005/gmd&ElementSetName=full&ID=spaignLLM"/>
				</MetadataURL>
			</Layer>
			<Layer queryable="1">
				<Name>AU.AdministrativeUnit</Name>
				…
				<Identifier authority="IGN">bdlje_unidades_adm</Identifier>
				<MetadataURL type="ISO19115:2003">
					<Format>text/plain</Format>
					<OnlineResource xlink:type="simple" xlink:href="https://www.ign.es/csw-inspire/srv/spa/csw?SERVICE=CSW&VERSION=2.0.2&REQUEST=GetRecordById&outputSchema=http://www.isotc211.org/2005/gmd&ElementSetName=full&ID=spaignLLM"/>
				</MetadataURL>
			</Layer>
		</Layer>
	</Capability>
</WMS_Capabilities>

```

WFS
https://www.ign.es/wfs-inspire/unidades-administrativas?REQUEST=GetCapabilities&SERVICE=WFS&VERSION=2.0.0

```xml

<WFS_Capabilities (…)>
…
	<FeatureTypeList>
		<FeatureType>
			<Name xmlns:au="http://inspire.ec.europa.eu/schemas/au/4.0">au:AdministrativeBoundary</Name>
			…
			<MetadataURL xlink:href="https://www.ign.es/csw-inspire/srv/spa/csw?SERVICE=CSW&VERSION=2.0.2&REQUEST=GetRecordById&outputSchema=http://www.isotc211.org/2005/gmd&ElementSetName=full&ID=spaignLLM"/>
		</FeatureType>
		<FeatureType>			
			…			
		</FeatureType>		
	</FeatureTypeList>
	…
</WFS_Capabilities>

```

Atom
https://www.ign.es/atom/ds.es.xml

```xml

<feed xmlns="http://www.w3.org/2005/Atom" xmlns:georss="http://www.georss.org/georss" xmlns:inspire_dls="http://inspire.ec.europa.eu/schemas/inspire_dls/1.0" xml:lang="es">
	<id>https://www.ign.es/atom/ds.es.xml</id>

	<!--  Every dataset has an entry with its own metadata file  -->
	<entry>
		<title>Base de Datos de Límites Jurisdiccionales de España</title>
		<inspire_dls:spatial_dataset_identifier_code>BDLJE</inspire_dls:spatial_dataset_identifier_code>
		<inspire_dls:spatial_dataset_identifier_namespace>IGN</inspire_dls:spatial_dataset_identifier_namespace>
		<link href="https://www.ign.es/csw-inspire/srv/spa/csw?SERVICE=CSW&VERSION=2.0.2&REQUEST=GetRecordById&outputSchema=http://www.isotc211.org/2005/gmd&ElementSetName=full&ID=spaignLLM" rel="describedby" type="application/xml"/>
		<!--  Link to "Dataset Feed" for this specific dataset of the administrative units -->
		<link rel="alternate" href="https://www.ign.es/atom/dataset_feeds/lin_lim_mun.es.xml" type="application/atom+xml" hreflang="es" title="Fuente con la información de descarga del conjunto de datos"/>
		...
	</entry>
	<entry>
	...
	</entry>
	<entry>
	...
	</entry>
</feed>

```

### Advantages/disadvantages of the proposed approach

Advantages:
- There is no need to use de service metadata file and the <inspire_vs:ExtendedCapabilities> element within the GetCapabilities response
- The relation between data and service is clear and easy to manage.
- Similar to what is already used in many countries.
- It uses the existing codelists and metadata elements included in the TG INSPIRE

Disadvantages:

### Conclusions 


