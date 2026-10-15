# Notices and attribution

> **Reference work.** Fictional scenario built for a public portfolio. Not deployed in, derived from, or describing any employer environment. Not professional advice.

This file lists the third-party frameworks, identifier sets, names, and quoted material used in this repository, and the terms each comes with. Each source's terms were checked at the source on 2026-10-14 (table at the end).

The repository's own licenses cover original content only: the [MIT License](LICENSE) for the KQL queries, and [CC BY 4.0](LICENSE-docs) for the documents and data (the README's License section lists the files each covers). Third-party material stays under its owner's terms. Naming an organization, product, or framework here or anywhere in the repository does not imply affiliation with, sponsorship by, or endorsement by its owner.

## MITRE ATT&CK

- **Used:** technique and tactic IDs and names from MITRE ATT&CK Enterprise v20, in documents 08, 09, 14, and 17, ADR-006, the payroll diversion and email compromise playbook, and the headers of seven of the eight queries (q07 cites none; q01 and q06 map none and name T1078.004 only as the exposure they size). Document 17 also names one ATT&CK detection strategy, by ID and name, in its prompt injection scenario (S-11). No technique descriptions are quoted.
- **Terms:** MITRE's Terms of Use license ATT&CK for research, development, and commercial use, on condition that copies reproduce MITRE's copyright designation and the license. Both follow, as published on MITRE's Terms of Use page:

  The MITRE Corporation (MITRE) hereby grants you a non-exclusive, royalty-free license to use ATT&CK® for research, development, and commercial purposes. Any copy you make for such purposes is authorized provided that you reproduce MITRE's copyright designation and this license in any such copy.

  "© 2026 The MITRE Corporation. This work is reproduced and distributed with the permission of The MITRE Corporation."

- **Trademarks:** MITRE ATT&CK and ATT&CK are registered trademarks of The MITRE Corporation.

## MITRE ATLAS

- **Used:** MITRE ATLAS is cited by name and content release only. Document 16 cites MITRE ATLAS content release 2026.09 (released 2026-09-15) in its dated framework references and its Sources, and its Appendix A names ATLAS techniques in words, such as "LLM Prompt Injection (indirect)" and "AI Supply Chain Compromise", only where a control maps cleanly to an adversary technique. The names are cited with attribution to MITRE ATLAS. No ATLAS identifier, technique description, data file, or other ATLAS content is reproduced. ATLAS publishes content releases monthly; 2026.09 was the newest release in the ATLAS data manifest on 2026-10-14.
- **Terms:** the LICENSE file in The MITRE Corporation's atlas-data repository names MITRE as the copyright holder for 2021 to 2026 and licenses the repository under the Apache License, Version 2.0 (https://www.apache.org/licenses/LICENSE-2.0). The terms view in the ATLAS website's source code carries the same Apache License 2.0 grant.
- **Discrepancy noted:** the release statement in the atlas-data README gives a copyright line for The MITRE Corporation followed by "ALL RIGHTS RESERVED." and "Approved for Public Release; Distribution Unlimited." The README statement and the LICENSE file state different terms. This repository records both, uses only the content release number and technique names, with attribution, and reproduces no ATLAS content.
- **Trademarks:** MITRE ATLAS™ is a trademark of The MITRE Corporation.

## OWASP Top 10 for LLM Applications

- **Used:** IDs and names from the OWASP Top 10 for LLM Applications 2026 (released August 2026), for example LLM01:2026 Prompt Injection and LLM08:2026 Hidden Context Exposure, cited with attribution in document 16, in its dated framework references and in Appendix A on the rows that cover its AI security controls. Document 16 also names the 2026 edition as one of the public sources behind those AI controls, attributes a few short paraphrases to it (that no reliable way to prevent prompt injection exists today, that System Prompt Leakage became Hidden Context Exposure, and that agent risks sit in a separate OWASP list), and names an informative reference that NIST lists for CSF 2.0, OWASP-LLM-Top10-v2.0-to-CSF-v2.0. No entry text is reproduced.
- **Terms:** the 2026 edition's License and Usage page states "This document is licensed under Creative Commons, CC BY-SA 4.0." and links the full license text, and the OWASP GenAI Security Project website states that, unless otherwise specified, its content is Creative Commons Attribution-ShareAlike v4.0 and provided without warranty of service or accuracy. CC BY-SA 4.0 asks for credit, a link to the license, and an indication of any changes, and applies its ShareAlike condition to adapted material.
- **Attribution:** "OWASP Top 10 for LLM Applications 2026" by the OWASP GenAI Security Project, https://genai.owasp.org/resource/owasp-genai-llm-top-10-2026/ , licensed under CC BY-SA 4.0 (https://creativecommons.org/licenses/by-sa/4.0/) and provided by OWASP without warranty. The IDs and names are used unchanged. This repository's CC BY 4.0 license does not cover them.

## CVE identifiers

- **Used:** one CVE identifier, CVE-2025-32711, in document 16, which cites the NIST National Vulnerability Database and Microsoft Security Response Center pages for it. No CVE record text is reproduced.
- **Terms:** the CVE Program's Terms of Use license CVE for reproduction and distribution, on condition that copies reproduce MITRE's copyright designation and the license. The license follows, as published in the source of the CVE website's Terms of Use page (the live page, https://www.cve.org/Legal/TermsOfUse , renders in the browser, so the checking tool read its source):

  CVE Usage: MITRE hereby grants you a perpetual, worldwide, non-exclusive, no-charge, royalty-free, irrevocable copyright license to reproduce, prepare derivative works of, publicly display, publicly perform, sublicense, and distribute Common Vulnerabilities and Exposures (CVE™). Any copy you make for such purposes is authorized provided that you reproduce MITRE's copyright designation and this license in any such copy.

  The page refers to MITRE's copyright designation without giving its wording. This repository cites the one identifier and reproduces no CVE record content.

## NIST publications

- **Used:** NIST Cybersecurity Framework (CSF) 2.0 Function, Category, and Subcategory identifiers throughout; Category descriptions paraphrased in the crosswalk (`docs/crosswalk/csf2-soc2-crosswalk.md` and `data/csf2-soc2-crosswalk.csv`); and short quotations from NIST publications, including some CSF 2.0 outcome statements, each cited where it appears. The publications cited include SP 800-61 Rev. 3, SP 800-50 Rev. 1, the SP 800-63-4 series (SP 800-63-4, 800-63A-4, 800-63B-4, and 800-63C-4), SP 800-84, SP 800-34 Rev. 1, and SP 800-55 Volumes 1 and 2; the AI Risk Management Framework (AI RMF 1.0, NIST AI 100-1), NIST AI 600-1, and the draft NIST IR 8596; the IR 8286 series; the NIST Phish Scale; and others where they are cited, such as SP 800-207, SP 800-30 Rev. 1, SP 800-40 Rev. 4, SP 800-88 Rev. 2, SP 800-161 Rev. 1, SP 800-218 and SP 800-218A, and the CSF 2.0 Quick-Start Guides.
- **Terms:** NIST states that works authored by NIST employees are not subject to copyright protection within the United States, that foreign rights are reserved, and that to the extent NIST may assert rights outside the United States, the public is granted a royalty-free, worldwide right to reprint them. NIST asks reprints to carry its recommended citation followed by "Republished courtesy of the National Institute of Standards and Technology." NIST also notes that some works it publishes were written by third parties and may be subject to copyright.
- **Credit:** the CSF 2.0 text quoted in this repository (for example in documents 10, 11, and 16) comes from National Institute of Standards and Technology (2024), The NIST Cybersecurity Framework (CSF) 2.0, NIST CSWP 29, National Institute of Standards and Technology, https://doi.org/10.6028/NIST.CSWP.29 (accessed 2026-10-13). Republished courtesy of the National Institute of Standards and Technology.

## AICPA Trust Services Criteria and SOC 2 guidance

- **Used:** identifiers from the 2017 Trust Services Criteria (with the 2022 revised points of focus), such as CC1.1 to CC9.2, A1.1 to A1.3, and C1.1 to C1.2, and the Processing Integrity and Privacy ranges named in document 10, each with an original paraphrase. AICPA's SOC 2 guide and other AICPA pages are cited and paraphrased, for example in documents 01 and 10 and in the crosswalk; the guide's Chapter 1 excerpt was read from a copy on a third-party host, as each Sources entry notes. No criteria text or point of focus is reproduced.
- **Terms:** AICPA & CIMA's Terms and Conditions state that the website's content is protected by copyright and that it may not be reproduced, modified, or used to create derivative works without written permission. The criteria appear here only by identifier, with paraphrases written for this repository.

## US government works

- **Used:** publications and pages of CISA (including the Zero Trust Maturity Model Version 2.0, the phishing-resistant MFA fact sheet, the SCuBA baselines and ScubaGear, and the Tabletop Exercise Packages, whose structure the tabletop template borrows); the FBI's Internet Crime Complaint Center (IC3), including its public service announcements and the 2025 Internet Crime Report; the IRS (Publication 3112); USCIS and DHS (Form I-9 and the E-Verify memorandum of understanding for employer agents); and the CFPB. Regulations as published in the eCFR, including the FTC Safeguards Rule (16 CFR Part 314), the HIPAA business associate notification rule (45 CFR 164.410), and 8 CFR 274a.2; Federal Register records; and, through GovInfo, sections of the United States Code (15 U.S.C. 1681a and 1681b) and a federal appeals court opinion. Short quotations are attributed where they appear.
- **Terms:** under 17 U.S.C. 105, "Copyright protection under this title is not available for any work of the United States Government." Publications issued jointly with non-federal partners are not treated here as U.S. government works. CISA's #StopRansomware Guide (CISA, MS-ISAC, NSA, and FBI) is paraphrased, and the short passages quoted from it are attributed where they appear. The same applies to the joint AI security guidance that document 16 cites, issued by CISA, the NSA, or the FBI with partner agencies of other governments: AI Data Security (May 2025), Deploying AI Systems Securely (April 2024), the Guidelines for Secure AI System Development (November 2023), Careful Adoption of Agentic AI Services (May 2026), and the Five Eyes Cyber Security Agencies Statement (June 2026). They are paraphrased, and the short passages quoted from two of them are attributed where they appear. No seal or logo of any agency is used.

## State and local laws, regulations, and court opinions

- **Used:** statutes, regulations, and court opinions of California (the California Consumer Privacy Act, the California Privacy Protection Agency's regulations, and an Attorney General release), Colorado, Connecticut, Delaware, Florida, Illinois (read through the Illinois Supreme Court's opinion), New York, Texas, and Washington, cited by section and paraphrased in documents 08, 10, and 16 and elsewhere where cited, with short quotations attributed where they appear. Document 16 also paraphrases New York City's Local Law 144 of 2021, on automated employment decision tools, from the page of the city's Department of Consumer and Worker Protection. They are read as questions for counsel, not as legal advice (document 10).

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

## Other sources and names

- Every document in `docs/` lists its sources in a Sources section, with publisher, URL, date checked, and a quality label for each external source. Short quotations are attributed where they appear. Third-party content remains its owners' and is not covered by this repository's licenses.
- All other product names, company names, and marks belong to their respective owners and are used only to identify them.
- This repository is not affiliated with, sponsored by, or endorsed by any organization it names, and Fabrikam, Inc. (fictional) does not describe any real organization.

## Terms checked for this notice

| Title | Publisher | URL | Date checked | Quality |
|---|---|---|---|---|
| Terms of Use (ATT&CK license, copyright designation, and trademark notice) | MITRE | https://attack.mitre.org/resources/legal-and-branding/terms-of-use/ | 2026-10-14 | Primary |
| atlas-data LICENSE (Apache License, Version 2.0, and copyright line) | The MITRE Corporation, on GitHub | https://raw.githubusercontent.com/mitre-atlas/atlas-data/main/LICENSE | 2026-10-14 | Primary |
| atlas-data README (release statement with "ALL RIGHTS RESERVED"; monthly content releases) | The MITRE Corporation, on GitHub | https://raw.githubusercontent.com/mitre-atlas/atlas-data/main/README.md | 2026-10-14 | Primary |
| ATLAS data manifest (content release 2026.09, release date 2026-09-15) | The MITRE Corporation, on GitHub | https://raw.githubusercontent.com/mitre-atlas/atlas-data/main/dist/manifest.yaml | 2026-10-14 | Primary |
| ATLAS website terms view (TermsView.vue, the source of the site's terms page, which the checking tool could not load directly) | The MITRE Corporation, on GitHub | https://raw.githubusercontent.com/mitre-atlas/atlas-website/main/src/views/TermsView.vue | 2026-10-14 | Primary |
| D3FEND Terms of Use (MITRE ATLAS trademark statement) | The MITRE Corporation | https://next.d3fend.mitre.org/tou | 2026-10-14 | Primary |
| OWASP GenAI LLM Top 10 2026 (resource page and site footer license notice; PDF "OWASP Top 10 for LLM Applications 2026", License and Usage, page 2) | OWASP GenAI Security Project | https://genai.owasp.org/resource/owasp-genai-llm-top-10-2026/ | 2026-10-14 | Primary |
| Attribution-ShareAlike 4.0 International legal code, section 3 | Creative Commons | https://creativecommons.org/licenses/by-sa/4.0/legalcode.en | 2026-10-14 | Primary |
| CVE website Terms of Use page source (TermsOfUse.vue on the default branch, "CVE Usage" license; the live page at https://www.cve.org/Legal/TermsOfUse renders in the browser) | CVE Program, on GitHub | https://raw.githubusercontent.com/CVEProject/cve-website/dev/src/views/Legal/TermsOfUse.vue | 2026-10-14 | Primary |
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
