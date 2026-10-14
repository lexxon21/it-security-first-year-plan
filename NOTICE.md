# Notices and attribution

> **Reference work.** Fictional scenario built for a public portfolio. Not deployed in, derived from, or describing any employer environment. Not professional advice.

This file lists the third-party frameworks, identifier sets, names, and quoted material used in this repository, and the terms each comes with. Each source's terms were checked at the source on 2026-10-14 (table at the end).

The repository's own licenses cover original content only: the [MIT License](LICENSE) for the KQL queries, and [CC BY 4.0](LICENSE-docs) for the documents and data (the README's License section lists the files each covers). Third-party material stays under its owner's terms. Naming an organization, product, or framework here or anywhere in the repository does not imply affiliation with, sponsorship by, or endorsement by its owner.

## MITRE ATT&CK

- **Used:** technique and tactic IDs and names from MITRE ATT&CK Enterprise v20, in documents 08, 09, 14, and 17, ADR-006, the payroll diversion and email compromise playbook, and the headers of seven of the eight queries (q07 cites none; q01 and q06 map none and name T1078.004 only as the exposure they size). No technique descriptions are quoted.
- **Terms:** MITRE's Terms of Use license ATT&CK for research, development, and commercial use, on condition that copies reproduce MITRE's copyright designation and the license. Both follow, as published on MITRE's Terms of Use page:

  The MITRE Corporation (MITRE) hereby grants you a non-exclusive, royalty-free license to use ATT&CK® for research, development, and commercial purposes. Any copy you make for such purposes is authorized provided that you reproduce MITRE's copyright designation and this license in any such copy.

  "© 2026 The MITRE Corporation. This work is reproduced and distributed with the permission of The MITRE Corporation."

- **Trademarks:** MITRE ATT&CK and ATT&CK are registered trademarks of The MITRE Corporation.

## NIST publications

- **Used:** NIST Cybersecurity Framework (CSF) 2.0 Function, Category, and Subcategory identifiers throughout; Category descriptions paraphrased in the crosswalk (`docs/crosswalk/csf2-soc2-crosswalk.md` and `data/csf2-soc2-crosswalk.csv`); and short quotations from NIST publications, including some CSF 2.0 outcome statements, each cited where it appears. The publications cited include SP 800-61 Rev. 3, SP 800-50 Rev. 1, the SP 800-63-4 series (SP 800-63-4, 800-63A-4, 800-63B-4, and 800-63C-4), SP 800-84, SP 800-34 Rev. 1, and SP 800-55 Volumes 1 and 2; the AI Risk Management Framework (AI RMF 1.0, NIST AI 100-1), NIST AI 600-1, and the draft NIST IR 8596; the IR 8286 series; the NIST Phish Scale; and others where they are cited, such as SP 800-207, SP 800-30 Rev. 1, SP 800-40 Rev. 4, SP 800-88 Rev. 2, SP 800-161 Rev. 1, SP 800-218 and SP 800-218A, and the CSF 2.0 Quick-Start Guides.
- **Terms:** NIST states that works authored by NIST employees are not subject to copyright protection within the United States, that foreign rights are reserved, and that to the extent NIST may assert rights outside the United States, the public is granted a royalty-free, worldwide right to reprint them. NIST asks reprints to carry its recommended citation followed by "Republished courtesy of the National Institute of Standards and Technology." NIST also notes that some works it publishes were written by third parties and may be subject to copyright.
- **Credit:** the CSF 2.0 text quoted in this repository (for example in documents 10, 11, and 16) comes from National Institute of Standards and Technology (2024), The NIST Cybersecurity Framework (CSF) 2.0, NIST CSWP 29, National Institute of Standards and Technology, https://doi.org/10.6028/NIST.CSWP.29 (accessed 2026-10-13). Republished courtesy of the National Institute of Standards and Technology.

## AICPA Trust Services Criteria and SOC 2 guidance

- **Used:** identifiers from the 2017 Trust Services Criteria (with the 2022 revised points of focus), such as CC1.1 to CC9.2, A1.1 to A1.3, and C1.1 to C1.2, and the Processing Integrity and Privacy ranges named in document 10, each with an original paraphrase. AICPA's SOC 2 guide and other AICPA pages are cited and paraphrased, for example in documents 01 and 10 and in the crosswalk; the guide's Chapter 1 excerpt was read from a copy on a third-party host, as each Sources entry notes. No criteria text or point of focus is reproduced.
- **Terms:** AICPA & CIMA's Terms and Conditions state that the website's content is protected by copyright and that it may not be reproduced, modified, or used to create derivative works without written permission. The criteria appear here only by identifier, with paraphrases written for this repository.

## US government works

- **Used:** publications and pages of CISA (including the Zero Trust Maturity Model Version 2.0, the phishing-resistant MFA fact sheet, the SCuBA baselines and ScubaGear, and the Tabletop Exercise Packages, whose structure the tabletop template borrows); the FBI's Internet Crime Complaint Center (IC3), including its public service announcements and the 2025 Internet Crime Report; the IRS (Publication 3112); USCIS and DHS (Form I-9 and the E-Verify memorandum of understanding for employer agents); and the CFPB. Regulations as published in the eCFR, including the FTC Safeguards Rule (16 CFR Part 314), the HIPAA business associate notification rule (45 CFR 164.410), and 8 CFR 274a.2; Federal Register records; and, through GovInfo, sections of the United States Code (15 U.S.C. 1681a and 1681b) and a federal appeals court opinion. Short quotations are attributed where they appear.
- **Terms:** under 17 U.S.C. 105, "Copyright protection under this title is not available for any work of the United States Government." Publications issued jointly with non-federal partners are not treated here as U.S. government works: CISA's #StopRansomware Guide (CISA, MS-ISAC, NSA, and FBI) is paraphrased, and the short passages quoted from it are attributed where they appear. No seal or logo of any agency is used.

## State statutes, regulations, and court opinions

- **Used:** statutes, regulations, and court opinions of California (the California Consumer Privacy Act, the California Privacy Protection Agency's regulations, and an Attorney General release), Colorado, Connecticut, Delaware, Florida, Illinois (read through the Illinois Supreme Court's opinion), New York, Texas, and Washington, cited by section and paraphrased in documents 08, 10, and 16 and elsewhere where cited, with short quotations attributed where they appear. They are read as questions for counsel, not as legal advice (document 10).

## Nacha

- **Used:** Nacha is named as the body that sets the ACH network's operating rules, and documents 08, 10, and 11 cite and paraphrase public pages on nacha.org about third-party roles, the rules compliance audit, data security requirements, and fraud monitoring. The Nacha Operating Rules themselves are referenced, never reproduced.
- **Terms:** Nacha's 2026 Terms of Use for its Operating Rules online resource state "© 2026 Nacha® All rights reserved" and require Nacha's prior written permission to reproduce, publish, or include the publication in derivative works.

## IETF RFCs

- **Used:** RFC 9989 (DMARC, May 2026) and RFC 7505 (the null MX record), cited in documents 06 and 15 and paraphrased. DNS record values such as DMARC policy tags appear as technical identifiers. No RFC text is reproduced beyond titles.
- **Terms:** the IETF Trust Legal Provisions (Corrected TLP 5.0, effective March 25, 2015) govern use of RFC text. Section 3.c allows anyone to copy and distribute RFCs in full and without modification, and to copy unmodified portions when each portion is clearly attributed to the IETF and identifies the RFC, keeping the RFC's legends, legal notices, and indications of authorship when a substantial portion is reproduced.

## BIMI Group

- **Used:** BIMI is named in document 06 as an optional benefit once a domain is at DMARC enforcement, and the BIMI Group's FAQ for senders is paraphrased for its definition of enforcement (p=quarantine or p=reject). No specification text is reproduced.
- **Terms:** the BIMI Group's site carries the notice "AuthIndicators Working Group, all rights reserved" and states no separate license for its content.

## Microsoft

- **Products:** the plan uses Microsoft products as Fabrikam's platform. Microsoft and the names of the Microsoft products and services referred to in this repository are trademarks of the Microsoft group of companies. Microsoft's trademark guidelines ask third parties to refer to its products truthfully and accurately and not to imply affiliation with or endorsement by Microsoft; this repository implies neither.
- **Quoted material:** the documents, and comments in the queries, cite Microsoft Learn and other Microsoft pages, and some documents quote short passages from them. Each quotation is cited to its page in the file that uses it, and the Markdown documents give the date each page was checked. That content is Microsoft's and is not covered by this repository's licenses. Microsoft Learn's Terms of Use (updated 2025-05-12) say that certain documentation may carry explicit license terms, which control where they conflict with those terms, and Microsoft publishes the source of many Learn pages in public MicrosoftDocs repositories under their own licenses: for example, [MicrosoftDocs/entra-docs](https://github.com/MicrosoftDocs/entra-docs) carries the MIT License, and [MicrosoftDocs/azure-docs](https://github.com/MicrosoftDocs/azure-docs) carries a CC BY 4.0 LICENSE file and an MIT LICENSE-CODE file. Where such a license covers a quoted page, its terms apply to the quoted text.
- **Fabrikam:** Fabrikam is one of the fictional company names used in Microsoft's documentation and learning material; an archived Microsoft TechNet Wiki page lists it as "Fabrikam, Inc.". Fabrikam, Inc. (fictional) is a fictional organization used for this plan. It is not affiliated with Microsoft and does not describe any real organization.

## CIS Microsoft 365 Foundations Benchmark

- **Used:** the CIS Microsoft 365 Foundations Benchmark v7.0.0 is named in document 06 as a second opinion on settings in Phase 4. No benchmark text or recommendation numbers are included, and the plan describes Fabrikam's settings as informed by the benchmark, never as compliant with it.
- **Terms:** CIS's Terms of Use for Non-Member CIS Products license non-member Benchmark PDFs under CC BY-NC-SA 4.0 and bar, among other things, posting the products on a website, creating derivative works based directly on them, and claiming a level of compliance or consistency with them.

## ITIL

- ITIL® is a registered trademark of PeopleCert. Document 13 uses ITIL practice names as shared vocabulary only, reproduces no ITIL content, and implies no endorsement.

## News and industry sources

- **Vendor research.** Verizon's 2026 Data Breach Investigations Report and Microsoft's 2025 and 2026 Digital Defense Reports are cited for statistics, which documents such as 09, 16, and 17 report with attribution.
- **Mailbox providers.** The large mailbox providers' published sender guidelines are paraphrased in document 06, with a short quotation attributed where it appears.
- **A public incident.** The December 2021 ransomware attack on a workforce management provider's private cloud is described in one neutral sentence in documents 14 and 17 and ADR-006. The affected company is named only in the titles of the news articles cited in their Sources sections.
- **Audit commentary.** Document 10 and the crosswalk cite a large audit firm's summary of the 2022 revisions to the Trust Services Criteria points of focus, and document 10 cites a CPA firm's article on bridge letters. Both are paraphrased and labeled secondary in the Sources sections.
- **A community mirror.** The SMTP AUTH date comes from a community mirror of Microsoft 365 Message Center posts, labeled secondary wherever it is cited.
- **Other names.** OWASP appears only within the name of an informative reference that NIST lists for CSF 2.0 (document 16).

## Other sources and names

- Every document in `docs/` lists its sources in a Sources section, with publisher, URL, date checked, and a quality label for each external source. Short quotations are attributed where they appear. Third-party content remains its owners' and is not covered by this repository's licenses.
- All other product names, company names, and marks belong to their respective owners and are used only to identify them.
- This repository is not affiliated with, sponsored by, or endorsed by any organization it names, and Fabrikam, Inc. (fictional) does not describe any real organization.

## Terms checked for this notice

| Title | Publisher | URL | Date checked | Quality |
|---|---|---|---|---|
| Terms of Use (ATT&CK license, copyright designation, and trademark notice) | MITRE | https://attack.mitre.org/resources/legal-and-branding/terms-of-use/ | 2026-10-14 | Primary |
| Copyright, Fair Use, and Licensing Statements for SRD, Data, Software, and Technical Series Publications (updated June 24, 2025) | NIST | https://www.nist.gov/open/copyright-fair-use-and-licensing-statements-srd-data-software-and-technical-series-publications | 2026-10-14 | Primary |
| Copyright Law of the United States, Chapter 1, section 105 (United States Government works) | U.S. Copyright Office | https://www.copyright.gov/title17/92chap1.html | 2026-10-14 | Primary |
| Terms & Conditions (Version 4), section 2 | AICPA & CIMA | https://www.aicpa-cima.com/help/terms-and-conditions | 2026-10-14 | Primary |
| Nacha Operating Rules Online Resource Terms of Use (2026) | Nacha | https://www.nacha.org/system/files/2026-05/2026_NORO_Terms_of_Use.pdf | 2026-10-14 | Primary |
| License information (current TLP) | IETF Trust | https://trustee.ietf.org/license-info | 2026-10-14 | Primary |
| Corrected Trust Legal Provisions 5.0 (effective March 25, 2015), section 3.c | IETF Trust | https://trustee.ietf.org/documents/trust-legal-provisions/tlp-5/ | 2026-10-14 | Primary |
| FAQs for Senders and ESPs (site notice and enforcement definition) | BIMI Group | https://bimigroup.org/faqs-for-senders-esps/ | 2026-10-14 | Primary |
| Trademark and Brand Guidelines | Microsoft | https://www.microsoft.com/en-us/legal/intellectualproperty/trademarks | 2026-10-14 | Primary |
| Terms of Use, Microsoft Learn (updated 2025-05-12) | Microsoft | https://learn.microsoft.com/en-us/legal/termsofuse | 2026-10-14 | Primary |
| MicrosoftDocs/entra-docs repository (LICENSE: MIT) | Microsoft, on GitHub | https://github.com/MicrosoftDocs/entra-docs | 2026-10-14 | Primary |
| MicrosoftDocs/azure-docs repository (LICENSE: CC BY 4.0; LICENSE-CODE: MIT) | Microsoft, on GitHub | https://github.com/MicrosoftDocs/azure-docs | 2026-10-14 | Primary |
| List of fictional companies used in Microsoft material (archived community wiki page) | Microsoft Learn archive | https://learn.microsoft.com/en-us/archive/technet-wiki/1117.list-of-fictional-companies-used-in-microsoft-material | 2026-10-14 | Secondary |
| Terms of Use for Non-Member CIS Products | Center for Internet Security | https://www.cisecurity.org/terms-of-use-for-non-member-cis-products | 2026-10-14 | Primary |
| Acknowledgements (PeopleCert registered trademarks) | PeopleCert | https://www.peoplecert.org/acknowledgements | 2026-10-14 | Primary |
| Attribution 4.0 International legal code (the text in LICENSE-docs) | Creative Commons | https://creativecommons.org/licenses/by/4.0/legalcode.txt | 2026-10-14 | Primary |
| MIT License template (the text in LICENSE) | GitHub, choosealicense.com | https://github.com/github/choosealicense.com/blob/gh-pages/_licenses/mit.txt | 2026-10-14 | Primary |
