#!/bin/bash

# Transaction Level Contract

## Overview

This document explains the purpose of the transaction level contract between participating Network Participants (NPs) and outlines the standard terms & conditions for network participants.

The codified digital contract includes:

*   A set of configurable terms defined by the seller.
*   A set of static terms defined by the Buyer Network Participant (BNP).
*   A reference to these static terms will be included in every online transaction between two participants.
*   Reference clauses to guide participants in drafting their static terms for the codified digital contract can be found [here](https://docs.google.com/document/d/1hKImxDwZ-LUd1ln0D61KhhuQ9-Rqrzt2/edit#heading=h.9z4gdnelcvjh).  
## Proposed Flow

Static terms will be version-controlled in a [GitHub repository](https://github.com/ONDC-Official/static-terms).

1.  **Version Control:** All static terms will start with version 1.0.0, and subsequent changes will increment the version number.

2.  **NP Submission:**
    *   The NP creates a Pull Request (PR) for their static terms.
    *   ONDC will merge this PR and share the link with the NP.

3.  **Branching Strategy:**
    *   The NP forks the repository.
    *   The NP creates a branch under the appropriate version using the following naming convention: `<NP name>_role` (e.g., "Pincode_BNP", "Magicpin_BNP").
    *   The NP merges their static terms into this branch.
    *   The NP creates a PR for these changes.

4.  **Publication:** Static terms can be published by the NP on multiple channels (e.g., their website, ONDC portal).

## Communication & Acceptance of Static Terms

### Communication by BNP

The BNP will send the following additional information as part of the `/search` API call:

1.  **Current Static Terms Link:** The link to the current static terms with the version number. For the very first set of static terms, this will be a blank link.

2.  **New Static Terms Link:** The link to the new static terms with the version number, if any. For the very first set of static terms, this will be the link to the static terms in GitHub.

3.  **Effective Date:** The effective date for the new static terms.

**Communication Timeline:**

*   Information in (1) above will be sent in `/search` for the full catalog for 24 hours after the new version of the static terms is published.
*   24 hours prior to the expiry of the effective date in (1) above, the BNP resends the information in (1) above.
*   If the BNP wants to change the effective date, they can update the effective date in (1) above and repeat steps (2) & (3) above.
*   If the BNP wants to change their static terms, they need to resubmit their PR with a new version number.
*   It is recommended that the BNP provide at least 15 days' advance notice when changing their static terms.

### Acceptance by SNP

The Seller Network Participant (SNP) must indicate their acceptance of the static terms:

*   **Acceptance:** If the SNP accepts the static terms in `/search` above, they need to send `accept="Y"` in `/on_search`.
*   **Rejection:** If the SNP does not accept the static terms in `/search` above, they need to send `accept="N"` in `/on_search`.
*   **Consequences of Rejection:** If the SNP does not accept the static terms for a BNP, they should stop responding with their catalog for the corresponding BNP from the effective date.
*   **BNP Action:** If the SNP does not accept the static terms but continues to send their catalog, the BNP may, at their discretion, choose to delist the sellers for this SNP.

Static terms agreed upon between the BNP and SNP will be included as part of `/confirm` and `/on_confirm` API calls.