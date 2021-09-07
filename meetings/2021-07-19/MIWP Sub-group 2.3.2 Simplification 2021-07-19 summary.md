### Fourth meeting of MIWP Sub-group 2.3.2

### Simplification of Data and Service Linking 

The meeting was held on July 19, 2021, 15:00 - 16:30 CEST (via WebEx).

The meeting was chaired by JRC and attended by experts from AT, CZ, DK, ES, FR, IT and NL.

The JRC gave a presentation during which the meeting participants were invited to discuss particular issues related to the proposed approach for simplification of data and service linking.

#### Discussion:

IT agreed on the use of the anchor element, suggested that the check (for the purpose of validation) should be done only on the URI, not on the label. JRC suggested to require to protocol (and anchor) as mandatory element, IT agreed. FR agreed on the anchor, but suggested to make it a strong recommendation instead of mandatory, as there might be cases not included in the codelist. NL suggested to make it mandatory, but with good management of the protocol codelist, so that it can be updated quickly. This applies just to the protocol, without version. IT brought up the issue to extend the codelist in order to cover all types of services foreseen by INSPIRE, as described in the [GitHub issue](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/issues/8). NL suggested that we should focus on services used for INSPIRE. FR suggested to make the protocol mandatory only in case of links to INSPIRE network services (download and view).

AT mentioned several ideas:

- use of the ApplicationProfile for the conformity statement, i.e. to say if it is a correct INSPIRE download/view service;
- use of the Protocol for the type of service (download, view);
- use of the Function element.

FR agreed on the use of the ApplicationProfile to identify the link to view or download service and the use of GetCapabilites as the link. NL agreed to include direct links to the data and to use the ApplicationProfile for the conformity statement of the service. IT agreed to use GetCapabilites as the link, but disagreed on the implicit declaration of the conformity of the service, they believe that the use of the ApplicationProfile for this purpose is too limited and that it should be used to declare the type of service. NL asked for the reason of the disagreement, IT replied that they have many services non-conformant to INSPIRE specification and the use of ApplicationProfile only for conformant services would limit the availability of many datasets, furthermore this element should be dedicated only to the type of service. AT commented that if we do not use ApplicationProfile for the conformity statement, we can use a keyword within getCapabilities and considering that we have the mandatory protocol value, then the ApplicationProfile is not needed at all. IT replied that indeed within the past work of the Action 2019.2 on simplification they had this suggestion. IT added that in the future the scope of this element may be extended for other (than view or download) types of services. For example it is currently used in IT to identify direct download type with the value "other". JRC suggested to continue the discussion in the [Issue #17](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/issues/17), and anticipated that they are working on a proposal dedicated to this issue that they are going to share.

FR commented that the discussion about the Name element goes beyond the INSPIRE elements. AT asked if the Name is free text or anchor, JRC replied that it is free text. NL mentioned that the Name element has been mandatory for years in the NL and they observed a lot of metadata errors because metadata editors are not aware of the layer name, therefore they do not recommend it.

IT commented that the Description element should be used to distinguish between getCapabilities and other operations, such as getMap or getFeature, but it depends on the decision on the URL. IT proposed to use Access Point for getCapabilities and Endpoint for getMap or getFeature. NL suggested that if we decide on getCapabilities or comparable URL to make it recommended. JRC mentioned that there are a lot of API-based services, such as OGC API - Features, where there is no getCapabilities and it would be good to be able to apply the same simplification approach to these services. IT commented that the new features, such as the OGC API, are one of the reasons for their proposal to extend the protocol codelist, and also not to use ApplicationProfile only for conformant services.

IT mentioned that Extended Capabilities should be dismissed, so that the data and service providers can use pure OGC standards. The only reason to keep the Extended Capabilities is the conformity statement, but it should apply only to INSPIRE network services. FR was strongly against keeping Extended Capabilities,  the only necessary thing is the link back to the dataset metadata, but it can be provided in the metadata URL and it should be mandatory. NL agreed with this point of view. FR added that the conformity statement can be solved using keywords and Application Profile. FR added that the keyword can be linked to a vocabulary, an INSPIRE vocabulary would declare conformity. IT mentioned that there is a vocabulary for the degree of conformity in the INSPIRE registry.

JRC re-iterated that the mandate of the subgroup is to reach an agreement on the consolidated approach, so please be be flexible and think of the possible solutions compatible with all the members.

