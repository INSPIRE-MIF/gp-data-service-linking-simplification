### Second meeting of MIWP Sub-group 2.3.2

### Simplification of Data and Service Linking 

The meeting was held on April 8, 2021, 14:00 - 15:30 CEST (via WebEx).

The meeting was chaired by JRC and attended by experts from AT, CZ, DE, DK, EL, ES, FR, LT, NL, PL, SE and SK.

#### Agenda: 

1. Welcome (JRC) 
2. Tour de table (New members)
3. Recap of the process, status of work (JRC)
4. Proposals for approaches (NL, FR, LT, AT, PL, others) 
5. Preliminary findings (JRC)
6. Discussion (All) 
7. Next steps (JRC, All)
8. AOB (All) 

#### Discussion:

NL presented their proposal. ES asked about linkages element in dataset metadata, discussed the use of endpoints versus access points.

JRC pointed the use of the IANA media types, as the media types register is also available in the INSPIRE Registry. IANA had been found to be limited in terms of geospatial media types. This issue needs clarification in the final Good Practice. 

AT mentioned the need of a clear definition of endpoint and access point. For example, in the NL proposal, *getCapabilities* service is an access point, while *getMap*, *getFeature* are endpoints, but it is not always used this way across different communities.

AT pointed the use of description field for anchors. In AT the description field is used for other purposes such as distinguishing between harmonized and as-is data. NL are using separate datasets for this purpose. SE mentioned that in the FR proposal the anchor in the description element allows for the use of free text, which may block its use for other purposes. In SE it is sometimes used to include information about license and formats of the individual online resources. In NL, *href* is the machine readable part and text content is the human readable part of the same item, so both parts should correspond to each other. In FR, *href* is the required part, while text content is used to state that it is, for example, an access point, but it can also include additional information, such as harmonized/as-is dataset.

SK pointed the misuse of the protocol element that should not be used for the media type or the type of service, as it may create confusion; the protocol should be used for http get or post, for example. NL, SE commented that the protocol is often used across Member States for information such as WFS, WMS, etc. for pragmatic reasons.

SK asked about the case when the service that provides multiple media types, such as GML and JSON. NL replied that their proposal suggests linkage to *getCapabilities* as the required simple case. Support for other, more complex cases presented are optional.

FR presented their proposal. They are mostly using access points, not endpoints, as they mostly have relatively big datasets. The proposed approach is focused on simple cases, for more complex cases they suggest to keep the service metadata.

AT suggested to use the Issues section of the GitHub space to continue the discussion on specific issues.

ES asked about removing of the service metadata and extended capabilities. JRC confirmed that both points are the main idea of the simplification in order to remove duplication and the need for software extensions, among others.

#### Actions:

Discussion to continue in the [Issues section](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/issues) of the GitHub space.

JRC to prepare a proposal for the consolidated approach by the end of the month of April.

The third meeting will be held on April 11 at 10:00.

