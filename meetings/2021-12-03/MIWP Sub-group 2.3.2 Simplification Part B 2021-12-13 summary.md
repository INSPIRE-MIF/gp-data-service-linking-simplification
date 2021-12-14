#### MIWP Sub-group on Action 2.3.2 - Kick-of Meeting of Part B "Remapping of the extended capabilities" 

#### Simplification of Data and Service Linking - Part B "Remapping of the extended capabilities" 

The meeting was held on-line (via WebEx) on 3rd December, 2021, 11:00 - 12:30 CET.

It was chaired by JRC and attended by experts from IT, NL, FR and DK.

#### Agenda:

0. Welcome and Approval of the agenda (JRC)
1. Possible amendments to [Part A Consolidated proposal (“Data-service linking simplification”)](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/blob/main/proposals/JRC/ds-linking-simplification-good-practice.md) (All)
2. Discussion on the Remapping of Extended Capabilities - [Based on Part A Consolidated proposal – Annex B](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/blob/main/proposals/JRC/ds-linking-simplification-good-practice.md#annex-b) (All)
3. Way forward for Part B (All).
4. AoB (All).

#### Presentations:

[Presentation (PDF)](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/blob/main/meetings/2021-12-03/20211203_MIWP_Sub-group_2.3.2_Simplification_Kick-off_Part_B.pdf)

#### Summary and main points of the discussion:

The JRC welcomed the attendees, provided an overview of the objectives of the meeting and proceed with the items scheduled in the agenda.

**Agenda Item 1 - Pending issues corresponding to [Part A Consolidated proposal (“Data-service linking simplification”)](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/blob/main/proposals/JRC/ds-linking-simplification-good-practice.md)**

The following aspects were discussed:

* **Possible amendment of Consolidated proposal for Part A** proposed in [Issue #38](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/issues/38), to solve the lack of compliance of the Coupled resource implementation as per the Consolidated proposal: 
  * As per the proposal in Issue #38 the URL of the Coupled resource should not be poining to the raw metadata, but to the #MD_DataIdentification section of the metadata. 
  * @idevisser expressed her concerns about applying this pointer to the #MD_DataIdentification as a mandatory item - by the way, already included as TG Requirement 3.6 in the Technical Guidelines on Metadata v2.0.1 (TG MD) - because it is not widely used in current metadata despite it is required by the ISO standard. Hence, she proposed to allow more frienly metadata by just recommending the use of this pointer. The INSPIRE Reference Validator is not requiring it at the moment. 
  * @AntoRot added that it would be better to avoid repeating this requirement, which is already in the TG MD, and just make reference to it in the proposal for Part A.
  * @fabiovin showed 3 different examples currently included in the TG MD to implement this pointer, but explained that it might not be useful in certain applications or clients if they do not process the #MD_DataIdentification pointer. Furthermore he clarified that if the applications / clients do process this pointer and as a result only the #MD_DataIdentification section of the metadata is retrieved. In this case, it could not be verified through the Resource Locator that the dataset metadata is the correct one - which is one of the objectives to be accomplished when applying Part A Consolidated proposal. 
  * Since there was no agreement on a consensus solution to manage the issue, the group agreed to continue the discussion in the GitHub repository.

* **Inputs sent by @heidivanparys on 2nd December**: 
  * @heidivanparys already started with the quality-check / review of Part A Consolidated proposal (Good Practice). She expressed her agreement with the previous comment from @AntoRot, and explained that the consolidated proposal should reuse the requirements already established in the technical guidelines. This could be done by expressing in this Good Practice dependencies to the requirements classesthat already exist in the TG MD. 
  * Particularly, if the present Good Practice finally proposes something not aligned with TG Requirement 3.6 discussed above, it would be better to submit a change proposal for this requirement through the governance process currently established.

**Agenda Item 2 - Discussion on the Remapping of Extended Capabilities**

An initial proposal for remapping the INSPIRE elements contained in the services metadata (Extended Capabilities), as described in Scenario 2 of the INSPIRE Network Sevices Technical Guidelines (TG NS) was discussed by the group. This draft proposal was prepared by @AntoRot and lately included in [Consolidated proposal – Annex B](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/blob/main/proposals/JRC/ds-linking-simplification-good-practice.md#annex-b). 

The objective of this discussion is to achieve a more complete simplification of data-service linking by using Scenario 2 (and thus, not requiring the provision of service matadata as metadata records offered by an external discovery service) while reallocating the service metadata elements foreseen - as per this scenario - in the Extended Capabilities of OGC WxS INSPIRE services into standard elements of their corresponding Capabilties documents. This optional approach would allow avoding their necessary provision in the Extended Capabilities of such service Capabilties documents. 

@AntoRot volunteered to further work to consolidate this proposal, clarifying the elements still pending to be remmapped (Temporal reference, Metadata point of contact, Metadata date and Supported languages) and solving any remaining doubts on it. The objective would be that Member States could optionally avoid the Extended Capabilities, or maintain it of they are willing to keep the existing implementations.

@alexanderkotsev added that this simplification is something that the SW industry is really expecting. 

@idevisser also agreed that it would be good to get rid of the Extended Capabilities, and that it should be checked if some elements were missing from this initial proposal (e.g. service metadata URL).

@idevisser and @MarieLambois agreed to collaborate with @AntoRot in further discussing this initial mapping and drafting a consolidated proposal. 

@alexanderkotsev foresaw 3 different cases for each of the elements in the Extended Capabilities: 
1. To discard the element providing an appropiate justification; 
2. To remap the element to an standard element from the default Capabilities document service response, and; 
3. To adapt a particular element from the default Capabilities document service response to avoid losing content initially included in the Extended Capabilities.

He proposed to start the discussion going through each of the the elements of the Extended Capabilities one by one, starting from the critical ones - like the conformity and the identifiers - till arriving to a consensus that could be shared with the whole Sub-group 2.3.2 and the MIG-T, and finally validated. 

Discussion on specific Extended Capabilities elements:

* **Metadata Point of contact**: 
  * @heidivanparys suggested that this element should be probably discarded, because if there is no external ISO 19139 service metadada then the metadata you have are just the information provided in the Capabilities document of the service. Therefore, in this case the point of contact would be the same as the service provider. This should be taken into account when searching for the suitable standard elements from the Capabilities document to be mapped to to the Metadata Point of contact. 
  * @MarieLambois also supported this suggestion, but mentioned that the mapping should be clear in any of the possible scenarios, Scenario 1 and Scenario 2.

* **Conformity**: 
  * @MarieLambois highlighted that there was already opened in the GitHub repository the [Issue #12](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/issues/12) for discussing on this specific element, where some XML examples were provided. 
  * @AntoRot commented that he proposed to use for the conformity the codelist published in the INSPIRE Registry (values: 'conformant', 'not conformant' and 'not evaluated'), applied to the `wms:keyword` or `wfs:keyword` elements. As a side note, this codelist in fact is not used in ISO 19139 metadata, where the conformity is declared using a boolean value. 
  * @idevisser commented that the discussion on [Issue #12](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/issues/12) was more focused on how to clearly define the specification respect to which the conformity is being declared.

#### Decisions:

1. The consolidated proposal for Part B of the Simplification work should be drafted referring, where possible, to requiments and recommmendations already existing in the current Technical Guidelines.
2. The group agreed to scope the remapping work just to OGC Web Services (OWS). 
3. Further discussion about the remapping of the Extended Capabilities will take place in the already existing [GitHub repository](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/), opening a generic issue thread to be complemented with specific issue threads to discuss on each concrete element of the Extended Capabilities. First outcomes are expected by mid January.
4. @heidivanparys will provide starting documentation regarding the quality check revision of the Consolidated proposal for for Part A of the simplification work also by mid January. 

#### Actions:

- [ ] All members of the group to achieve agreement on a consensus solution to manage [Issue #38](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/issues/38) in the dedicated GitHub repository - Deadline: 10th January 2022.
- [ ] @AntoRot will lead the opening of Issue threads to further discuss on the remapping of the Extended Capabilities in the [GitHub repository](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/). @jescriu will support him in performing this task - Deadline: 15th December 2021. 
- [ ] @idevisser and @MarieLambois will be collaborating in the remapping of the Extended Capabilities discussion in GitHub with the aim to achieve concrete agreements - Deadline: 10th January 2022.
- [ ] @jescriu will follow-up the status of the discussions and agreements in GitHub to possibly have a new meeting of this group by mid January, in time to gather feedback for the MIG-T Meeting scheduled on 20th January. This meeting would also be used to discuss on possible amendments to the Consolidated proposal for Part A of the simplification work based on the first outcomes from the quality check revision made by @heidivanparys - Deadline: 10th January 2022.

