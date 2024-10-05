---
ticket: https://www.notion.so/New-ordering-for-patient-facing-dna-Traits-17c6fb6cf18746d9b29c5c554f21bfb8
priority: P1
---

## Status
Blocked: Cannot create new branches


## Description

Right now when user views their snapshot, they see the dna traits ordered from High to Low, but the doctors would like certain traits to show up at the beginning of the list if the trait is high or medium and they consider it "foundational"

## Tasks

- [x] Add a new field to the Traits table for "foundational" boolean ✅ 2024-07-08
- [x] When getting the traits to show to the patient, take all the foundational traits that have a medium or high status (not low) put those at the beginning of the list. ✅ 2024-07-12
- [x] After that the remaining traits should be ordered high to low as usual. If there is a foundational ✅ 2024-07-12
- [x] Trait thats low, it will just be included in the second as if its not foundational. ✅ 2024-07-12

