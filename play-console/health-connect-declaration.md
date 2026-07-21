# Health Connect declaration and reviewer notes

Use this text for the next Play Console submission. Do not reuse the prior generic rationale ("needed to export health data"). Each medical category needs its own standalone explanation.

## Declared app functionality

**Primary approved use case:** Medical care — personal access to and management of medical records.

**Additional app functionality:** Fitness and wellness record tracking through user-controlled exports.

**Core-functionality statement:**

> Health.md is a read-only health data portability and personal record management app. It lets users create portable copies of health, fitness, and FHIR medical records already stored in Android Health Connect. The user chooses the metrics, date range, output format, and destination. Exports can be readable Markdown/CSV summaries or JSON/provider-native snapshots. Health.md does not diagnose, recommend treatment, write to Health Connect, sell health data, use health data for advertising, or operate a Health.md health-data cloud.

**Why all 12 medical categories are requested:**

> The user-facing “Medical records (FHIR)” feature creates a portable personal-health-record archive. Health Connect separates that record into 12 permission categories, so each category requires read access to prevent that part of an authorized user-requested archive from being silently omitted. JSON and provider-native exports preserve the FHIR resource and source metadata supplied by Health Connect; Markdown and CSV summaries show counts by medical category. Users can deny or revoke any category, and exports of other authorized categories continue to work.

## Per-permission rationales

Paste each paragraph into the matching Play Console field.

### MedicalData-Vaccines

Permission: `READ_MEDICAL_DATA_VACCINES`

> Health.md is a read-only personal health-record export app. Read access to Vaccines lets a user-requested export include Immunization FHIR resources already stored in Health Connect, preserving vaccination history, dates, codes, status, and source details supplied in the record. Without this access, the user’s portable medical archive would omit immunization history. Data is exported only to the destination the user selects.

### MedicalData-Allergies/Intolerances

Permission: `READ_MEDICAL_DATA_ALLERGIES_INTOLERANCES`

> Health.md is a read-only personal health-record export app. Read access to Allergies/Intolerances lets a user-requested export include AllergyIntolerance FHIR resources already stored in Health Connect, preserving recorded substances, reactions, severity or status, dates, and source details. Without this access, the user’s portable medical archive would omit allergy and intolerance history. Data is exported only to the destination the user selects.

### MedicalData-Conditions

Permission: `READ_MEDICAL_DATA_CONDITIONS`

> Health.md is a read-only personal health-record export app. Read access to Conditions lets a user-requested export include Condition FHIR resources already stored in Health Connect, preserving diagnoses and problem-list history with codes, status, dates, and source details. Without this access, the user’s portable medical archive would omit condition history. Data is exported only to the destination the user selects.

### MedicalData-LaboratoryResults

Permission: `READ_MEDICAL_DATA_LABORATORY_RESULTS`

> Health.md is a read-only personal health-record export app. Read access to Laboratory Results lets a user-requested export include laboratory Observation FHIR resources already stored in Health Connect, preserving reported values, units, reference information, codes, dates, and source details. Without this access, the user’s portable medical archive would omit lab history. Data is exported only to the destination the user selects.

### MedicalData-Medications

Permission: `READ_MEDICAL_DATA_MEDICATIONS`

> Health.md is a read-only personal health-record export app. Read access to Medications lets a user-requested export include Medication, MedicationRequest, and MedicationStatement FHIR resources already stored in Health Connect, preserving medication and prescription history as provided by the source. Without this access, the user’s portable medical archive would omit medication records. Data is exported only to the destination the user selects.

### MedicalData-PersonalDetails

Permission: `READ_MEDICAL_DATA_PERSONAL_DETAILS`

> Health.md is a read-only personal health-record export app. Read access to Personal Details lets a user-requested export include Patient FHIR resources already stored in Health Connect. These records preserve the person and demographic context needed for users to identify and manage their own portable medical record. Without this access, exported resources can lose patient context. Data is exported only to the destination the user selects.

### MedicalData-PractitionerDetails

Permission: `READ_MEDICAL_DATA_PRACTITIONER_DETAILS`

> Health.md is a read-only personal health-record export app. Read access to Practitioner Details lets a user-requested export include Practitioner and PractitionerRole FHIR resources referenced by visits, results, medications, and procedures. This preserves care-provider context in the user’s portable archive. Without this access, those references can lack useful provider details. Data is exported only to the destination the user selects.

### MedicalData-Pregnancy

Permission: `READ_MEDICAL_DATA_PREGNANCY`

> Health.md is a read-only personal health-record export app. Read access to Pregnancy lets a user-requested export include pregnancy-related FHIR resources already stored in Health Connect. This allows a user who has this data to preserve pregnancy status and history with the rest of their personal medical archive. Without this access, that record category would be omitted. Data is exported only to the destination the user selects.

### MedicalData-Procedures

Permission: `READ_MEDICAL_DATA_PROCEDURES`

> Health.md is a read-only personal health-record export app. Read access to Procedures lets a user-requested export include Procedure FHIR resources already stored in Health Connect, preserving procedure history, codes, dates, status, and source details. Without this access, the user’s portable medical archive would omit performed procedures. Data is exported only to the destination the user selects.

### MedicalData-SocialHistory

Permission: `READ_MEDICAL_DATA_SOCIAL_HISTORY`

> Health.md is a read-only personal health-record export app. Read access to Social History lets a user-requested export include social-history FHIR observations already stored in Health Connect, preserving lifestyle and clinical context recorded by the source without interpreting or changing it. Without this access, that context would be omitted from the user’s portable archive. Data is exported only to the destination the user selects.

### MedicalData-Visits

Permission: `READ_MEDICAL_DATA_VISITS`

> Health.md is a read-only personal health-record export app. Read access to Visits lets a user-requested export include Encounter FHIR resources already stored in Health Connect, preserving care-visit history and its dates, status, location, practitioner, and source references when supplied. Without this access, the user’s portable medical archive would omit encounter history. Data is exported only to the destination the user selects.

### MedicalData-VitalSigns

Permission: `READ_MEDICAL_DATA_VITAL_SIGNS`

> Health.md is a read-only personal health-record export app. Read access to Medical Vital Signs lets a user-requested export include clinical vital-sign Observation FHIR resources already stored in Health Connect. These are part of the user’s medical record and are distinct from consumer sensor measurements. Without this access, the archive would omit clinical vital-sign history. Data is exported only to the destination the user selects.

## Reviewer instructions

No account or credentials are required.

1. Launch Health.md.
2. The first page identifies the app as a Health Connect fitness and medical-record export tool.
3. Continue to **Your Health, Your Data**.
4. Tap **Why each permission is requested** to see a separate purpose and user benefit for every requested medical category.
5. Return and tap the Health Connect permission button. Any category may be denied; the rest of the app remains usable.
6. Select a folder with Android’s system folder picker and complete onboarding.
7. On the Export tab, open metric selection and find **Medical Records → Medical records (FHIR)**. Its description lists all 12 supported medical categories.
8. Select a date range, format, and destination, then tap Export. The app reads authorized records only to create that requested export.

## Submission checklist

- Upload a build containing the expanded rationale screen and corrected Medical Records metric label.
- Replace the old store listing with `play-console/listing/en-US/full-description.txt` and `short-description.txt`.
- Ensure every Health Connect permission in the uploaded AAB manifest is also selected in the Play Console declaration.
- Paste each medical rationale above into its matching field; do not submit one bulk explanation for all 12.
- Add the reviewer instructions above to App access/review notes and attach a short screen recording of that exact flow if the form allows it.
- Keep the public privacy policy synchronized with the listing and in-app disclosure, including the 12 medical categories, destination handling, retention/deletion, and revocation controls.

## Official guidance

- Google Play Android Health Permissions guidance: https://support.google.com/googleplay/android-developer/answer/12991134
- Publish a Health Connect app: https://developer.android.com/health-and-fitness/health-connect/publish
