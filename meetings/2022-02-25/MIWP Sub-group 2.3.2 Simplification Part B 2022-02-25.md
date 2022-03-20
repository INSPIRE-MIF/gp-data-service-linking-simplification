#### MIWP Sub-group on Action 2.3.2 - Part B "Remapping of the extended capabilities" 2nd Meeting

#### Simplification of Data and Service Linking - Part B "Remapping of the extended capabilities" 

The meeting was held on-line (via WebEx) on 25nd February, 2022, 14:00 - 15:30 CET.

It was chaired by JRC and attended by experts from IT, NL, FR and DK.

#### Agenda:

1. Introduction and planning.
2. Discussion on [issues](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/issues)
   * Part A – Pending issues: [Issue #38](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/issues/38) (Coupled resource implementation is not compliant)
   * Part B - Extended Capabilities elements remapping:
     * [Issue #39](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/issues/39) (Conformity)
     * [Issue #40](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/issues/40) (Temporal Reference)
     * [Issue #41](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/issues/41) (Metadata Point of Contact)
     * [Issue #42](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/issues/42) (Metadata Date)
     * [Issue #43](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/issues/43) (Supported languages)
     * Others issues not discussed (if any)
3. Consolidated proposal – Quality checking.
   * [Issue #44](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/issues/44) (Figure in 7.2 Resources)
   * [Issue #45](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/issues/45) (Duplicate requirements / reorganisation requirements classes)
   * [Issue #46](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/issues/46) (Keyword mapping for keywords from thesauri (WFS))
   * [Issue #47](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/issues/47) (Spatial data service category)
4. Way forward and Next steps.

#### Presentations:

[Presentation (PDF)](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/blob/main/meetings/2022-02-25/20220225_Action_2.3.2_Simplification_Part_B_2nd_Meeting.pdf)

#### Summary and main points of the discussion:

**Agenda Item 1 - Introduction and planning** 

The JRC welcomed the attendees, provided an overview to the objectives of the meeting and introduced the planning proposed to continue the activititives of the sub-group for the remapping of the elements of the Extended Capabilities (See Slide 4 of the presentation).
Afterwards, the rest of items scheduled in the agenda were covered.

**Agenda Item 2 - Discussion on issues**

   * Part A – Pending issues: [Issue #38](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/issues/38) (Coupled resource implementation is not compliant)
     * As per the request in this issue, the URL of the Coupled resource should be pointing to the #MD_DataIdentification section of the metadata, and not to the raw metadata iself, in order to keep compliance to ISO 19119, and also to TG Requirement 3.6 of the [INSPIRE Technical Guidelines on Metadata v2.1.0](TG Requirement 3.6) (TG MD).
     * Given the different existing implementations, @idevisser asked to relax this requirement, by keeping the linkage to the #MD_DataIdentification section of the metadata as an optional feature (i.e. pointing to the URL of the metadata, with or without the  additional #MD_DataIdentification pointer). 
     * @heidivanparys commented that she would aldo agree to relax TG Requirement 3.6 despite slightly deviating from ISO 19119, and proposed to add an explanatory note on this aspect in the final consolidated proposal.
     * All the other attendees agreed with both on this approach.
   * Part B - Extended Capabilities elements remapping:
     * [Issue #39](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/issues/39) (Conformity)
       * jescriu proposed to select [the proposal from @LauraAlemany](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/issues/39#issuecomment-1022169849), further elaborated on top of the initial proposals made by @AntoRot and @ @heidivanparys, based on adding a specific set of ordered keywords for declaring each of the Regulations and the conformity value corresponding to it, in that order.
       * @AntoRot agreed that it was a good proposal, but mentioned the possibility of making it more simple and user friendly, by considering as the 'conformant' value as default when the keyword agreed for declaring a specific Regulation is present, that is avoiding to additionally add a second keyword stating the conformity value.
       * Both, @MarieLambois and @idevisser commented that this apporach would be better, due to the fact that relying on the order of keywords is not safe when processing XML-kind files.
       * Based on the mentioned inputs, all attendees agreed to finally take this simplified and user friendly approach, as @MarieLambois already proposed in [this post](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/issues/39#issuecomment-1050622445).
     * [Issue #40](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/issues/40) (Temporal Reference)
     
     * [Issue #41](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/issues/41) (Metadata Point of Contact)
     
     * [Issue #42](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/issues/42) (Metadata Date)
     
     * [Issue #43](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/issues/43) (Supported languages)
     
     * Others issues not discussed (if any)
       * No addtional issues were discussed.

**Agenda Item 3 - Consolidated proposal – Quality checking**

Unfortunately, there was no time for review the proposals made by @heidivanparys (till the date of the meeting) for revising the quality of the consolidated proposals for Part A and Part B of the data-service linking simplification work (See Slide 7 of the presentation).  

**Agenda Item 4 - Way forward and Next steps**

The JRC presented a proposal to organise the way forward on Part A and Part B of the data-service linking simplification work, based on the planning already presented under Point 1 of the agenda (See Slides 8 and 9 of the presentation). 

#### Decisions:

1. Based on the good progress achieved during the meeting, the participants agreed with the planning proposed.
2. 

#### Actions:

- [ ] xxx.