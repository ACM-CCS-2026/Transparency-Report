# **ACM CCS 2026 Between-Cycle Transparency Report**

**Authors:** Veronique Cortier and Zhiqiang Lin  
**Last updated:** April 19, 2026  


---

## **Purpose of this document**

As the ACM CCS 2026 Program Co-Chairs, we are publishing this transparency report to document the rationale behind selected process decisions, summarize operational outcomes from the current review cycle, and record observations that may be useful to authors, reviewers, and the broader research community.

This document is intended to improve visibility into how the review process was run. It is not meant to claim that every decision was optimal, nor to preempt future community discussion. Rather, it provides concrete information that can support such discussion.

In particular, this report aims to:

* Explain notable process changes and the motivations behind them;
* Quantify, where possible, the impact of those changes on papers and authors;
* Summarize key observations from the current cycle; and
* Document lessons learned for authors and future CCS organizing teams.

---

## **Executive summary**

This report covers the following major themes from the first cycle of CCS 2026:

1. **Process changes.** We introduced or refined several parts of the submission and review workflow relative to prior CCS years, including submission metadata requirements, conflict-management procedures, desk-reject checks, ethics and open-science requirements, and AI-use guidance.

2. **Measured effects.** We report the number of papers affected by these policies, including desk rejections, conflict corrections, policy-related flags, and reviewer-process interventions.

3. **Operational insights.** We summarize end-to-end statistics for the cycle and provide observations on reviewer assignment, bidding, expertise matching, and policy enforcement.

4. **Open issues.** Some process choices worked well; others created friction or surfaced ambiguities. We summarize these issues here so they can inform future CCS planning.

**Notable findings.** Three results from this cycle stand out and may be of particular interest to the community. First, **missing or empty Open Science artifacts were by far the largest single cause of desk rejection (122 of 225 desk rejects, 54.2%)**, indicating that many authors still treat the Open Science appendix as optional rather than as a required part of the submission package. Second, **41 papers were desk-rejected for invalid or hallucinated references (18.2% of desk rejects)**, a new category of compliance issue that did not meaningfully exist in prior CCS cycles. Third, **roughly half of all submissions (598 of 1,206, or 49.6%) had at least one missing conflict of interest**; the distribution is most consistent with honest oversight rather than deliberate under-reporting, and has directly motivated a Cycle B refinement described below.
 
The final acceptance rate was **19.5% of the 981 papers in the final decision pool** (equivalently, **15.8% of the 1,206 submitted papers**, including those desk-rejected).
 

---

## **Acknowledgments**

We thank the members of the organizing committee, the track chairs, and all reviewers for their substantial effort. We also thank prior CCS chairs and steering-committee members whose advice informed many of the choices described here. This report was also inspired by the similar report published by the USENIX Security 2026 Program Co-Chairs.

---

## **1. Changes introduced in CCS 2026**

The changes described below are relative to practices from prior CCS years. Some are fully new for CCS 2026; others are refinements of existing procedures that we either made more explicit, enforced more consistently, or extended based on experience with Cycle A. Where a further refinement is planned for Cycle B, we note it in the relevant subsection.

### **1.1 Submission registration, abstract, and track requirements**

**What changed / refined.** Authors had to complete paper registration by the registration deadline and were instructed not to materially change the abstract afterward. Because registered abstracts were used for reviewer matching and automated assignment, substantial post-deadline changes could in principle trigger a desk rejection. 

**Why did we make this change?** The goal was to preserve assignment quality and fairness. If abstracts, titles, or track metadata change substantially after registration, the information used for reviewer matching may drift away from the paper actually under review.

**How it was operationalized.** Authors provided title, author information, conflicts, track information, track justification, and an abstract at registration. Although the abstract field remained editable in the system, we manually reviewed about 80 papers with noticeable abstract divergence between registration and submission and assessed whether the topic or scope had materially shifted. We did not desk reject any of these papers.

**Trade-offs.** This policy improved assignment stability, but it also required manual review and judgment. In Cycle B, the abstract field will become read-only after the paper registration deadline.

---

### **1.2 Conflict management and identity verification**

**What changed / refined.** As with other major security conferences, we strengthened conflict-of-interest management by incorporating ORCID into the submission workflow to support identity normalization and conflict detection.

**Why did we make this change?** At CCS scale, accurate conflict handling is essential for review integrity. ORCID helps reduce ambiguity caused by name variants, incomplete metadata, and inconsistent author records.

**How it was operationalized.** Authors were asked to obtain ORCID IDs as part of the author-certification flow. ORCID-linked identity information was then used alongside declared conflicts and other metadata to identify and review possible conflicts.

**Cycle B refinement.** Informed by Cycle A experience (Section 2.2), for Cycle B we will introduce a proactive conflict-feedback step between the registration deadline and the submission deadline, following the practice adopted by USENIX Security. After registration, authors will receive automated feedback identifying likely missing conflicts based on publication history and co-author graphs, so that they can review and correct their declarations before the paper is submitted for review. Authors manage growing collaboration graphs over many years, and recalling every relevant conflict at submission time is genuinely difficult; giving authors an opportunity to correct honest oversights before review begins is both fairer to them and better for review integrity.

**Trade-offs.** ORCID improves identity resolution, but coverage is incomplete and manual review remains necessary, especially for overly broad or unusual conflict declarations. It also adds some burden for authors who do not already maintain ORCID records. The Cycle B feedback loop adds load on the submission system and the chairs during the registration-to-submission window, but we believe the integrity benefit justifies the cost.

---

### **1.3 Desk-reject and format-compliance checks**

**What changed / refined.** We enforced submission-compliance checks covering page limits, font size, layout, CCS format compliance, open-science requirements, and other missing required components. Clear violations were subject to desk rejection.

**Why did we make this change?** The goal was fairness and consistency. Format and page-limit rules ensure that all papers are reviewed under the same constraints and prevent unfair space advantages.

**How it was operationalized.** We combined automated and manual checks. Automated checks identified issues such as page-length and PDF-level formatting problems, while manual review handled borderline cases and requirements that could not be reliably checked automatically.

**Trade-offs.** Strict enforcement improves fairness, but borderline cases can frustrate authors and require manual effort from the chairs. Even so, predictable enforcement is preferable to ad hoc exceptions.

---

### **1.4 Ethics, open science, and artifact requirements**

**What changed / refined.** We introduced explicit ethics and open-science requirements. Papers raising potential ethical concerns had to include an `Ethical Considerations` section, and every paper had to include an `Open Science` appendix describing relevant artifacts, access methods, and any justified exceptions. For Cycle B, we will also introduce a 3-day grace period for online artifacts hosted through anonymous services, and the artifact URL will become an explicit required field in HotCRP.

**Why did we make this change?** The goal was to strengthen ethical reflection, transparency, and reproducibility. When core claims depend on code, data, models, or systems, reviewers should be able to assess those artifacts, or understand clearly why they cannot be shared. The Cycle B grace period acknowledges the practical difficulty of preparing anonymous artifact hosting by the paper deadline while preserving the underlying principle.

**How it was operationalized.** The `Ethical Considerations` section was placed after the 12-page main text and bibliography and did not count toward the page limit. The `Open Science` appendix had to describe artifacts, explain anonymous access during review, and justify any unavailable materials. It also did not count toward the page limit. Artifacts central to the paper were expected at submission time. In addition, for large artifacts that cannot feasibly be hosted anonymously (for example, datasets larger than 1 GB), authors may provide a representative subset sufficient to verify the methodology and core claims, provided that the Open Science appendix explains why the full artifact cannot be shared anonymously and how the subset preserves the integrity and representativeness of the evaluation. For artifacts that cannot reasonably be reduced (for example, large code artifacts), **starting from Cycle B**, authors should contact the PC chairs; proxy hosting may be provided in a way that preserves author anonymity.

**Trade-offs.** These requirements improve evaluability but impose extra burden on authors, especially for anonymous artifact preparation. They also apply unevenly across subareas, particularly when industrial systems, privacy, legal restrictions, or dual-use risks limit what can be shared.

---

### **1.5 AI-use guidance for authors and reviewers**

**What changed / refined.** We introduced a policy governing the use of generative AI by both authors and reviewers. Authors were permitted to use AI tools only with full human responsibility and required disclosure. Reviewers were prohibited from uploading any submission content to public AI services and were expected to keep the core intellectual work of review human-driven.

**Why did we make this change?** The policy addresses two concerns. On the author side, AI tools can produce inaccurate, fabricated, or insufficiently verified content. On the reviewer side, public AI tools create confidentiality risks and may also undermine peer review as a human intellectual process.

**How it was operationalized.** The policy was included in the CfP instructions. Authors were required to disclose AI use, with more substantive use documented in a dedicated `Generative AI Usage` section; violations such as hallucinated citations, fabricated data, or falsified results could lead to desk rejection and possible escalation. In Cycle A, **41 papers were desk-rejected specifically because of hallucinated references** (see Section 2.3). Reviewers were explicitly prohibited from uploading submissions to public AI services. Violations could result in removal from the PC and escalation to ACM.

**Trade-offs.** Enforceability of AI-use policy is fundamentally asymmetric: the policy is effective against careless use (e.g., hallucinated references) but is difficult to enforce against careful use. The 41 hallucination-based desk rejections likely represent the visible surface of a larger phenomenon. Private and self-hosted models make detection harder still. Our policy therefore emphasizes clear rules, required disclosure, and meaningful sanctions for confirmed violations, rather than relying on technical enforcement alone. We believe this is the best available approach given the current state of the art, and we expect this area to continue evolving.

---

### **1.6 Reviewer assignment, calibration, and discussion procedures**

**What changed / refined.** We adopted a more structured assignment workflow combining declared expertise, representative publications, AI-assisted matching, reviewer bidding, and chair oversight. Track chairs were actively involved in final assignments and conflict handling.

**Why did we make this change?** The goal was to improve review quality, broaden expertise coverage, and reduce reviewer-assignment mismatches. Publication-based expertise and AI-assisted matching provided stronger initial signals than topic labels alone, reviewer bidding further refined those matches, and chair oversight helped balance loads, resolve conflicts, and handle edge cases.

**How it was operationalized.** Each PC member completed an onboarding form, including representative papers. Using these materials and paper abstracts, we generated about 20 AI-matched candidate papers per PC member for bidding; the exact number of papers was calibrated for each track. Final assignments were then reviewed and adjusted by track chairs. When a track chair had a conflict on a paper, the Program Co-Chairs handled that case.

**Trade-offs.** This workflow improved assignment quality but added complexity. AI matching and bidding scale well, but manual intervention remained necessary for interdisciplinary papers, imperfect metadata, and conflict cases.

---

## **2. Measurable impact of process changes**

This section reports the observed impact of the policy and workflow choices described above. Where relevant, we report both absolute counts and percentages.

### **2.1 Submission registration and metadata requirements**

* Registrations with no final paper submission: **287**
* Final submitted papers entering compliance screening: **1,206**
* Papers with noticeable abstract divergence reviewed manually: **~80**
* Papers desk-rejected for abstract divergence alone: **0**

---

### **2.2 Conflict-management procedures**

* Papers with at least one missing conflict detected by automated or manual checks: **598** (49.6% of 1,206 submitted papers)
* Papers with more than `N` missed conflicts:

| Missed Conflicts Threshold (N) | # Papers with > N Missed Conflicts |
| :---: | :---: |
| 14 | 1 |
| 13 | 3 |
| 12 | 3 |
| 11 | 4 |
| 10 | 11 |
| 9 | 15 |
| 8 | 20 |
| 7 | 34 |
| 6 | 58 |
| 5 | 94 |
| 4 | 157 |
| 3 | 243 |
| 2 | 387 |
| 1 | 598 |

**Comments.** Roughly half of all CCS 2026 submissions had at least one missing conflict of interest, with a small but non-trivial tail of papers missing ten or more. This pattern is most consistent with honest oversight rather than deliberate under-reporting: in a field where authors accumulate collaborators across many years, many institutions, and many projects, recalling every relevant conflict at submission time is genuinely difficult. Authors are not, on the whole, gaming the conflict system; they are making ordinary memory mistakes at scale.

This observation directly motivated the Cycle B refinement described in Section 1.2: we will provide authors with automated feedback on likely missing conflicts between the registration and submission deadlines, so that they can proactively review and correct their declarations before review begins. Identity normalization through ORCID, automated conflict assistance, and targeted manual review together appear to be the right toolkit for a venue at CCS scale, and we expect continued refinement along this direction.

---

### **2.3 Desk rejections**
 
* Desk rejections total: **225** (219 caught at initial screening plus 6 caught later during review when author-introduced deanonymization became apparent)

#### **Desk-reject reasons, overall**
 
**Note:** categories overlap; a single paper may be counted under multiple reasons. Counts and percentages are relative to the 225 desk-rejected papers. Anonymity violations occurred at both stages: 13 were identified at initial screening, and 6 additional cases surfaced during review/discussion when content in the submission made author identity apparent.
 
| Reason | Count | % of Desk Rejects |
| :---- | :---: | :---: |
| Missing Open Science (including Empty Artifact) | 122 | 54.2% |
| Format Violations | 59 | 26.2% |
| Hallucinated References | 41 | 18.2% |
| Double-Blind / Anonymity Violation | 19 | 8.4% |
| Missing Ethics | 13 | 5.8% |
| Out of Scope | 1 | 0.4% |
| Already Published | 1 | 0.4% |
 
#### **Overlap analysis**
 
Number of flagged reasons per desk-rejected paper (categories, not raw tags; empty-artifact + missing-open-science counted once):
 
| # of Reasons | Papers | % of Desk Rejects |
| :---: | :---: | :---: |
| 1 | 199 | 88.4% |
| 2 | 22 | 9.8% |
| 3 | 3 | 1.3% |
| 4 | 1 | 0.4% |
 
All desk-rejected papers were flagged for at least one reason.
 
**Comments.** Two findings in this table deserve emphasis. First, **Open Science compliance was the dominant desk-reject cause**: 122 of 225 desk-rejected papers (54.2%) were flagged for missing or empty Open Science material. This is the first cycle in which CCS enforced Open Science requirements at desk-rejection strength, and the result suggests that a substantial fraction of authors still approach the Open Science appendix as administrative boilerplate rather than as a required, reviewable component of the submission. The Cycle B refinements in Section 1.4 (explicit artifact URL field, 3-day grace period for anonymous hosting, optional proxy hosting for large artifacts) are aimed at reducing logistical friction without weakening the principle.
 
Second, **41 papers (18.2% of desk rejects) were rejected for invalid or hallucinated references**, a category that did not meaningfully exist in prior CCS cycles. We expect this category to matter more, not less, in future cycles, and we will continue to track and report it.
 
Most desk-rejected papers were flagged for a single reason (88.4%), but a non-trivial minority involved multiple issues, suggesting that compliance and quality-control problems sometimes co-occurred.
 
---
 
## **3. End-to-end statistics for the current cycle**
 
### **3.1 Submission flow**
 
| Category | Count |
| :---- | ----: |
| Registrations | 1,493 |
| Registrations that did not convert to submission | 287 |
| Final submitted papers | 1,206 |
| Desk rejections at initial screening | 219 |
| Desk rejections during review (author-caused deanonymization) | 6 |
| Papers included in the final decision pool | 981 |
 
**Comments.** Three flow numbers are worth commenting on. First, 287 of 1,493 registrations (19.2%) did not convert to a final submission. This is a substantial share, and likely reflects a mix of strategic registrations, projects that did not reach submission-ready quality, and authors who revised their readiness estimate during the registration-to-submission window. Future chairs sizing reviewer capacity should expect a similar conversion gap and plan accordingly. Second, anonymity breaches occurred at two stages of the process: 13 cases were caught at initial screening, and 6 additional cases were caught during review/discussion when the content of the submission inadvertently revealed author identity (some were in the artifacts); in both instances the deanonymization was author-caused rather than reviewer-caused, and the papers were handled as desk rejections. This brings the total desk-reject count across both stages to 225 (see Section 2.3). Third, after all desk rejections are accounted for, **981 papers remained in the final decision pool**; this is the denominator we use for the primary acceptance-rate figure below.
 
### **3.2 Decision outcomes**
 
| Outcome | Count |
| :---- | ----: |
| Round 1 rejects | 516 |
| Round 2 rejects | 274 |
| Minor Revision | 66 |
| Shepherding | 47 |
| Straight accepts | 78 |
| **Final accepts** | **191** |
 
**Acceptance rate:** **19.5%** of the 981 papers in the final decision pool (equivalently, **15.8%** of the 1,206 submitted papers, including those desk-rejected).
 
---
 
## **4. Lessons learned and next steps**
 
This cycle showed that, at CCS scale, many consequential submission problems arise not from the technical ideas themselves, but from integrity and compliance issues surrounding the submission package. In practice, titles, abstracts, track information, conflicts, artifacts, appendices, formatting, anonymization, and references all affected whether a paper could enter review smoothly. **The main lesson for authors is therefore to treat submission as a complete and verified package rather than focusing only on the 12-page paper**. Registration metadata should be entered carefully and should reflect the final framing of the paper, since these fields are used operationally for reviewer assignment and conflict handling. Likewise, open-science materials, ethical disclosures where applicable, anonymous artifact access, and reference verification should be prepared as core parts of the submission rather than as last-minute administrative tasks. The experience with missed conflicts, incomplete artifacts, format violations, anonymization mistakes, and invalid or hallucinated references all point to the same conclusion: **many avoidable problems can be reduced if authors treat compliance, anonymity, and verification as first-class responsibilities throughout the entire submission process, including discussion-phase communication**.
 
These observations have informed several refinements planned for Cycle B. We will make registration metadata expectations firmer, with the abstract field becoming read-only after the registration deadline. We will require artifact URLs as an explicit field in HotCRP, introduce a 3-day grace period for anonymously hosted online artifacts, and add a proactive conflict-feedback step between registration and submission so that authors can correct likely missing conflicts before review begins. The Open Science, Ethical Considerations, and format-compliance requirements from Cycle A will remain in effect. The goal of these changes is not to make the process more burdensome, but to make conference requirements clearer, more visible, and better aligned with actual review operations.
 
At the same time, this cycle also highlighted the limits of policy language alone. Some recurring sources of friction, such as post-registration metadata changes, artifact availability, anonymous hosting logistics, and borderline formatting cases, still required substantial manual judgment. Going forward, a key question is which requirements should be enforced more directly by the submission system and which should remain subject to chair discretion. Our experience suggests that clear and objective requirements should be enforced as early and automatically as possible, while limited flexibility should remain for exceptional cases where practical constraints, rather than non-compliance, are the main issue.
