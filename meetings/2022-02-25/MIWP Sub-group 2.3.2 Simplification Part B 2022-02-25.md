#### MIWP Sub-group on Action 2.3.2 'Simplification of Data and Service Linking'

####  - Part B "Remapping of the extended capabilities", 2nd meeting

The meeting was held on-line (via WebEx) on 25th February, 2022, 14:00 - 15:30 CET.

It was chaired by the JRC and attended by experts from IT, NL, FR and DK.

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

The JRC welcomed the attendees, provided an overview to the objectives of the meeting and introduced the proposed plan to continue the activities of the sub-group for the remapping of the elements of the Extended Capabilities (See Slide 4 of the presentation).
Afterwards, the rest of items scheduled in the agenda were covered.

**Agenda Item 2 - Discussion on issues**

   * Part A – Pending issues: [Issue #38](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/issues/38) (Coupled resource implementation is not compliant)
     * As per the request in this issue, the URL of the Coupled resource should be pointing to the `#MD_DataIdentification` section of the metadata, and not to the raw metadata iself, in order to keep compliance to ISO 19119, and also to TG Requirement 3.6 of the [INSPIRE Technical Guidelines on Metadata v2.1.0](https://github.com/INSPIRE-MIF/technical-guidelines/blob/2022.1/metadata/metadata-iso19139/metadata-iso19139.adoc#4124-linking-to-provided-data-sets-using-coupled-resource) (TG MD).
     * Given the different existing implementations, @idevisser (NL) asked to relax this requirement, by keeping the linkage to the `#MD_DataIdentification` section of the metadata as an optional feature (i.e. pointing to the URL of the metadata, with or without the  additional `#MD_DataIdentification` pointer). 
     * @heidivanparys (DK) commented that she would aldo agree to relax TG Requirement 3.6 despite slightly deviating from ISO 19119, and proposed to add an explanatory note on this aspect in the final consolidated proposal.
     * All the other attendees agreed with both on this approach.
   * Part B - Extended Capabilities elements remapping:
     * [Issue #39](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/issues/39) (Conformity)
       * jescriu proposed to select [the proposal from @LauraAlemany (ES)](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/issues/39#issuecomment-1022169849), further elaborated on top of the initial proposals made by @AntoRot (IT) and @heidivanparys (DK), based on adding a specific set of ordered keywords for declaring each of the Regulations and the conformity value corresponding to it, in that order.
       * @AntoRot (IT) agreed that it was a good proposal, but mentioned the possibility of making it more simple and user friendly, by considering as the 'conformant' value as default when the keyword agreed for declaring a specific Regulation is present, that is avoiding to additionally add a second keyword stating the conformity value.
       * Both, @MarieLambois (FR) and @idevisser (NL) commented that this apporach would be better, due to the fact that relying on the order of keywords is not safe when processing XML-kind files.
       * Based on the mentioned inputs, all attendees agreed to finally take this simplified and user friendly approach, as @MarieLambois (FR) already proposed in [this post](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/issues/39#issuecomment-1050622445).
     * [Issue #40](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/issues/40) (Temporal Reference)
       * @AntoRot (IT) explained and proposed his [initial proposal](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/issues/40#issue-1097580058) based on the publication date of the dataset served by the service, further clarified in [this post](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/issues/40#issuecomment-1021637467).
       * On the other hand, @idevisser (NL) proposed to simplify and adopt a solution based on the revision date of the service, as explained in [this post](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/issues/40#issuecomment-1025631157), more concretely using only the `UPDATESEQUENCE` value of the OWS service Capabilities (optional in OWS) and the `atom:updated` element for ATOM services, while mapping its value to both elements of the Extended Capabilities, the Temporal reference and to the Metadata date (i.e. taking an approach aligned to her proposal on [Issue #42](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/issues/42)).
       * @MarieLambois (FR) suggested to take any of the previous proposals, either the one from @AntoRot (IT) or the one from @idevisser (NL).
       * @jescriu (JRC) mentioned that, if possible, it would be better to choose a solution which could support descentralized scenarios, where the service is managed by a different organization than the one creating or maintaining the dataset.
       * Due to the (initial) disagreement and the links to [Issue #42](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/issues/42), the attendees proposed to discuss first the latter.
       * Based on such discussion and subsequent agreement (see below), it was decided to map both elements of the Extended Capabilities, the Temporal reference and to the Metadata date, following the criteria stated in [Issue #42](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/issues/42).
     * [Issue #42](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/issues/42) (Metadata Date)
       * The use of `UPDATESEQUENCE` value of the OWS service Capabilities and the `atom:updated` element for ATOM services, was discussed. 
       * It was highlighted that `UPDATESEQUENCE` is optional in OWS and, if provided, it can be just an integer or a string representing a timestamp in ISO 8601:2004 format. Hence, there is a need to check if an standardised date format might be used / expected or required.
       * Additionally, support in different service publication software available in the market is not assured. At the moment there is only evidence that MapServer supports it for WMS.
       * Based on the previous discussion, it was agreed to adopt a solution based on the following prioritised criteria:
         * A. if an `atom:updated` date value (in case of ATOM) or an `UPDATESEQUENCE` date value is present, take this value as Metadata Date (Only in the case an standardised date format might be used and retrieved - See below checks required with ISO / OGC).
         * B. Failing A, check the dataset metadata for the existence of the following dates:
            * B1. If a date of type 'publication' is present, take this value as Metadata Date.
            * B2. Failing B1: If a date of type 'revision' is present, take this value as Metadata Date.
            * B3. Failing B2: Otherwise, take the date of type 'creation' as value of the Metadata Date.
       * @heidivanparys (DK) will check with ISO / OGC about the possibility to use an standardised date format for `UPDATESEQUENCE`.
     * [Issue #41](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/issues/41) (Metadata Point of Contact)
       * All attendees directly agreed to take the [proposal posted by @heidivanparys (DK)](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/issues/41#issuecomment-1021278214).
       * A note will be added to the consolidated proposal, clarifying that in cases where external ISO 19139 service metadada will not exist (i.e. only the Capabilities document of the service will), the metadata point of contact would be considered the same as the service provider.     
     * [Issue #43](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/issues/43) (Supported languages)
       * jescriu reminded about the possibility to obtain the suported languages automatically (see [related post](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/issues/43#issuecomment-1022528187)) by requesting the service in all the possible different languages and analysing its responses. But this functionality could only be probably added to the new INSPIRE Geoportal and the implications in service performance could not be negligible.
       * @AntoRot (IT) totally agree on this approach. He also reminded the possibility of mapping (1) the DefaultLanguage element to the dataset metadata language and (2) the SupportedLanguage to the locale element (PT_locale) values - in case of having multilingual dataset metadata, as he suggested in [this post](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/issues/43#issuecomment-1022105139). About this proposal, @AntoRot (IT) mentioned that he noticed a potential issue on the validation of multilingual metadata (using the locale element) when the record contains Anchor encodings. He will open an issue in the INSPIRE Reference Validator helpdesk.
       * @MarieLambois (FR) considered this last proposal quite complex. Additionally, she stated that this solution will not work for France, because they are offering multilingual dataset metadata but not service Capabilities documents in different languages (because of limited resources to maintain them).
       * @idevisser (NL) reminded the [lastest proposal from @AntoRot (IT)](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/issues/43#issuecomment-1050773537) added to the dicussion thread. On it:
         * 1. in case of one language (DefaultLanguage), use the dataset metadata language; 
         * 2. in case of further supported languages, in case of WFS or Atom, use the attribute xml:lang for the two elements affected (title and abstract), and;
         * 3. in case of further supported languages, in case of WMS, keep the possibility to include the (optional) ExtendedCapabilities section, including the SupportedLanguages elements.
       * Finally, the attendees agreed on taking this last approach, but giving aproximately 1 week to further discuss about it in the related issue thread ([Issue #43](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/issues/43))
     * Others issues not discussed (if any)
       * No additional issues were discussed.

**Agenda Item 3 - Consolidated proposal – Quality checking**

Unfortunately, there was no time for review the proposals made by @heidivanparys (DK) (till the date of the meeting) for revising the quality of the consolidated proposals for Part A and Part B of the data-service linking simplification work (See Slide 7 of the presentation).  

**Agenda Item 4 - Way forward and Next steps**

The JRC presented a proposal to organise the way forward on Part A and Part B of the data-service linking simplification work, based on the planning already presented under Point 1 of the agenda (See Slides 8 and 9 of the presentation). 

#### Decisions:

1. Based on the good progress achieved during the meeting, the participants agreed with the planning proposed.
2. Agreement on each of the issues discussed was reached. The specific agreements on the mapping of each of the elements in the Extended Capabilities have been traced among the summary provided for the Agenda Item 2.

#### Actions:

- [ ] @heidivanparys (DK) to check with ISO / OGC about the possibility to use a standardised date format for `UPDATESEQUENCE`.
- [ ] @AntoRot (IT) to open an issue in the INSPIRE Reference Validator helpdesk, warning about the potential issue on the validation of multilingual metadata when Anchor encodings are used within the metadata record.
- [ ] All to summarize the specific agreements reached for each of the issue threads discussed, while closing them. 
- [ ] All to collaboratively draft the consolidated proposal for Part B (Remapping of the Extended Capabilities), including the description of the necessary TG/IR changes, based on the mentioned agreements and according the planning agreed by the group. 
- [ ] @jescriu (JRC) to organize this work (for the last two previous actions), by making a proposal to distribute the related tasks between the attendees of this meeting.
- [ ] All to start processing the quality checking of the consolidated proposals based on the proposals provided by @heidivanparys (DK) through GitHub and/or email. @jescriu (JRC) and @heidivanparys (DK) will coordinate a way forward for this work item.
- [ ] Submission of the consolidated proposal (integrating Part A and Part B) for the data-service linking simplification as a candidated INSPIRE Good Practice.
