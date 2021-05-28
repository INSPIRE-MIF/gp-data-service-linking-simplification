### Third meeting of MIWP Sub-group 2.3.2

### Simplification of Data and Service Linking 

The meeting was held on May 11, 2021, 10:00 - 11:30 CEST (via WebEx).

The meeting was chaired by JRC and attended by experts from AT, CZ, DE, DK, ES, FR, LT, NL, PL, SE and SK.

#### Agenda: 

1. Welcome (JRC) 
2. Recap of the process, status of work (JRC)
3. Proposal for the consolidated approach (JRC) 
4. Discussion (All) 
5. Next steps (JRC, All)
6. AOB (All) 

#### Discussion:

DE asked (via chat) if the service metadata are needed to calculate the NSi4 indicators, JRC confirmed.

AT asked what the conformity statement indicates, if there are no extended capabilities anymore. They asked about the INSPIRE conformity of pure WMS/WFS if there is no INSPIRE extension.

AT commented that we should keep the service metadata not so much for the Network Data Services, but for the Spatial Data Services, because in this case there is no clear link from the dataset to the service. SE agreed to keep service metadata for Spatial Data Services, but for Network Data Services it would be better to avoid them.

AT commented that if we keep service metadata and there are no extended capabilities, how can we link from service to service metadata. JRC replied that a possible solution could be to automatically generate service metadata from the service.

NL proposed the *implicit conformity declaration*, i.e. to use the application profile element with INSPIRE codelist values for INSPIRE conformant services only. FR agreed on this idea. DE commented that this solution would need to be well documented, so that it is well understood.

FR commented that if we count the same service multiple times, because it is linked in several dataset metadata - it is OK from the indicator point of view.

JRC mentioned the [issue described by IT on GitHub](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/issues/8) to extend the protocol codelist with two new values. SE commented that the protocol value pointing to an information page would be useful, currently in SE it is called 'http information'.

SE asked how to point to specific layers in the linkage to a service. NL commented that they use 'name' elements to point to specific layers, but this causes a lot of errors (due to misspelled names, etc.), and it would be better to include this information in the request. SE would expect to have a standard way to achieve this using the OGC `getCapabilites` request.

NL mentioned that `getCapabilities` is always information, so if we agree on its mandatory presence in the Resource Locator, then the `function` element can be avoided. They asked to keep the INSPIRE requirements as simple as possible. JRC highlighted one disadvantage on this approach: with several locators it needs iteration to discover and distinguish the mandatory element.

AT suggested to be careful not to make the proposed approach too complicated, as - often - the data set providers / metadata creators are not the same as the service providers. If the former are required to have too much information about the service, it may lead to problems and inconsistencies.

AT asked how to differentiate between as-is and harmonized data sets. JRC replied that there is a sub-group that should deal with this issue, and that the *implicit conformity declaration* is a possible solution.

JRC suggested the following issues to be further discussed on GitHub:

- implicit conformity declaration,
- protocol codelist extension,
- avoiding the `function` element as information.

JRC to develop a showcase implementation of the proposed approach. AT suggested to contact the Geonetwork community. NL is already doing this, JRC is also closely cooperating with the Geonetwork community. NL offered to develop an independent showcase implementation in parallel.

DE mentioned that the extended capabilities contain a lot of useful information, so if we get rid of it and put everything into data set metadata - it would not be simplification. NL commented that in case of differences between information contained in the extended capabilities and ISO elements, it is unclear which is correct, moreover, there is no standard for extended capabilities. They pointed that the extended capabilities can still be provided, but they are not required according the proposal.

JRC mentioned the example of the OGC API features where they wanted to avoid INSPIRE specific extensions (although the documentation allows for that). They mapped the different INSPIRE requirements to the open API standards.

JRC commented on extended capabilities:

- possible conflict between extended capabilities and ISO elements, 
- almost zero client support for extended capabilities, 
- a possible solution could be an optional/conditional requirement class, i.e. the extended capabilities could be used only under specific conditions.

#### Actions:

Discussion to continue in the [Issues section](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/issues) of the GitHub space.

JRC to adapt the [proposal for the consolidated approach](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/blob/main/proposals/JRC/Consolidated_proposal.md) according to the outcome of the discussion.

JRC and NL to start developing showcase implementations of the proposed approach.

The fourth meeting will be held on June 9 at 10:00.

