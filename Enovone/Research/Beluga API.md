## Overview
The API documentation provides details for interacting with the Beluga Health API, including submitting patient visit forms, handling lab results, managing patient photos, PDF submissions, and communication via chat. The API supports operations in both staging and production environments and requires API keys for authentication via the `Authorization` header.

### Base URLs
- **Staging:** `https://api-staging.belugahealth.com`
- **Production:** `https://api.belugahealth.com`

### Authorization
All requests must include the following header:
```
Authorization: Bearer {API_KEY}
```

### API Endpoints

1. **Visit Form Submission (No ID photos)**
   - **Method:** POST
   - **URL:** `{base url}/visit/createNoPay`
   - **Purpose:** Create a patient visit without photo ID verification.

2. **Visit Form Submission (With ID photos)**
   - **Method:** POST
   - **URL:** `{base url}/visit/createNoPayPhotos`
   - **Purpose:** Create a patient visit with photo ID verification.

3. **Lab Results Submission (With ID verification)**
   - **Method:** POST
   - **URL:** `{base url}/lab/receiveLabResults`
   - **Purpose:** Submit lab results for a patient with ID verification.

4. **Lab Results Submission (Without ID verification)**
   - **Method:** POST
   - **URL:** `{base url}/lab/receiveLabResults`
   - **Purpose:** Submit lab results for a patient without ID verification.

5. **Patient Photos Submission**
   - **Method:** POST
   - **URL:** `{base url}/external/receivePhotos`
   - **Purpose:** Submit patient photos, including photo ID images.

6. **PDF Submission**
   - **Method:** POST
   - **URL:** `{base url}/external/receivePdf`
   - **Purpose:** Submit PDF documents related to a patient visit.

7. **Send Patient Chat Message**
   - **Method:** POST
   - **URL:** `{base url}/external/receiveChat`
   - **Purpose:** Send a chat message from a patient to the system.

8. **Customer Service Message**
   - **Method:** POST
   - **URL:** `{base url}/external/receiveCSMessage`
   - **Purpose:** Send a message from customer service to admin.

9. **Pharmacy List Search**
   - **Method:** POST
   - **URL:** `{base url}/external/pharmacies`
   - **Purpose:** Search and retrieve a list of pharmacies.

10. **Update Visit/Resend Prescription**
    - **Method:** POST
    - **URL:** `{base url}/external/updateVisit`
    - **Purpose:** Update visit data or resend a prescription.

11. **Patient Name Update**
    - **Method:** POST
    - **URL:** `{base url}/external/patientName`
    - **Purpose:** Update a patient's name in the system.

### Key Points
- All endpoints require specific request body structures.
- The system provides detailed error messages for invalid or malformed requests.
- Ensure all required fields are correctly populated to avoid errors.
- Follow specific formatting rules for data submissions, including encoding images and PDFs.

This summary covers the main functionalities and requirements of the API as described in the document. Let me know if you need further details on any specific endpoint or operation!



Here's a summary of the payloads required for each API endpoint in the Shareable Beluga Skeleton API documentation:

## API Endpoints

### 1. Visit Form Submission (No ID Photos)
**Endpoint:** `{base url}/visit/createNoPay`
- **Method:** POST
- **Payload:**
  ```json
  {
    "formObj": {
      "consentsSigned": true,
      "firstName": "String (max 100 chars)",
      "lastName": "String (max 100 chars)",
      "dob": "MM/DD/YYYY",
      "phone": "String (10 digits, US mobile)",
      "email": "String",
      "address": "String",
      "city": "String",
      "state": "String (2 chars, e.g., 'CA')",
      "zip": "String (5 digits)",
      "sex": "String ('Male', 'Female', 'Other')",
      "selfReportedMeds": "String",
      "allergies": "String",
      "medicalConditions": "String",
      "patientPreference": [
        {
          "name": "String",
          "strength": "String",
          "quantity": "String",
          "refills": "String",
          "medId": "String"
        }
      ],
      "Q1": "String",
      "A1": "String"
      // Additional Q/A pairs as needed
    },
    "patientVerified": true,
    "verificationId": "String",
    "pharmacyId": "String",
    "visitId": "String (unique)",
    "company": "String",
    "visitType": "String ('weightloss', 'weightlossfollowup', 'ED', 'PE', 'hairloss')"
  }
  ```

### 2. Visit Form Submission (With ID Photos)
**Endpoint:** `{base url}/visit/createNoPayPhotos`
- **Method:** POST
- **Payload:**
  ```json
  {
    "formObj": {
      "consentsSigned": true,
      "firstName": "String (max 100 chars)",
      "lastName": "String (max 100 chars)",
      "dob": "MM/DD/YYYY",
      "phone": "String (10 digits, US mobile)",
      "email": "String",
      "address": "String",
      "city": "String",
      "state": "String (2 chars, e.g., 'CA')",
      "zip": "String (5 digits)",
      "sex": "String ('Male', 'Female', 'Other')",
      "selfReportedMeds": "String",
      "allergies": "String",
      "medicalConditions": "String",
      "patientPreference": [
        {
          "name": "String",
          "strength": "String",
          "quantity": "String",
          "refills": "String",
          "medId": "String"
        }
      ],
      "Q1": "String",
      "A1": "String"
      // Additional Q/A pairs as needed
    },
    "pharmacyId": "String",
    "masterId": "String (unique)",
    "company": "String",
    "visitType": "String ('weightloss', 'weightlossfollowup', 'ED', 'PE', 'hairloss')"
  }
  ```

### 3. Lab Results Submission (With ID Verification)
**Endpoint:** `{base url}/lab/receiveLabResults`
- **Method:** POST
- **Payload:**
  ```json
  {
    "formObj": {
      "consentsSigned": true,
      "firstName": "String (max 100 chars)",
      "lastName": "String (max 100 chars)",
      "dob": "MM/DD/YYYY",
      "phone": "String (10 digits)",
      "email": "String",
      "address": "String",
      "city": "String",
      "state": "String (2 chars)",
      "zip": "String (5 digits)",
      "sex": "String ('Male', 'Female', 'Other')",
      "selfReportedMeds": "String",
      "allergies": "String",
      "medicalConditions": "String",
      "testToTreat": true,
      "results": [
        {
          "screeningDate": "MM/DD/YYYY",
          "testName": "String",
          "testResult": "String",
          "testResultUnits": "String ('N/A' if not applicable)",
          "refRange": "String ('N/A' if not applicable)",
          "statusIndicator": "String ('H', 'L', 'N', 'N/A')",
          "reportDate": "MM/DD/YYYY",
          "sampleSource": "String ('URINE', 'BLOOD', etc.)"
        }
      ],
      "patientPreference": [
        {
          "name": "String ('N/A' if not applicable)",
          "strength": "String ('N/A' if not applicable)",
          "refills": "String ('N/A' if not applicable)",
          "quantity": "String ('N/A' if not applicable)",
          "medId": "String ('N/A' if not applicable)"
        }
      ],
      "Q1": "String",
      "A1": "String"
      // Additional Q/A pairs as needed
    },
    "patientVerified": true,
    "verificationId": "String",
    "pharmacyId": "String",
    "masterId": "String (unique)",
    "company": "String",
    "visitType": "String ('weightloss', 'weightlossfollowup', 'ED', 'PE', 'hairloss')"
  }
  ```

### 4. Lab Results Submission (Without ID Verification)
**Endpoint:** `{base url}/lab/receiveLabResults`
- **Method:** POST
- **Payload:**
  ```json
  {
    "formObj": {
      "consentsSigned": true,
      "firstName": "String (max 100 chars)",
      "lastName": "String (max 100 chars)",
      "dob": "MM/DD/YYYY",
      "phone": "String (10 digits)",
      "email": "String",
      "address": "String",
      "city": "String",
      "state": "String (2 chars)",
      "zip": "String (5 digits)",
      "sex": "String ('Male', 'Female', 'Other')",
      "selfReportedMeds": "String",
      "allergies": "String",
      "medicalConditions": "String",
      "testToTreat": true,
      "results": [
        {
          "screeningDate": "MM/DD/YYYY",
          "testName": "String",
          "testResult": "String",
          "testResultUnits": "String ('N/A' if not applicable)",
          "refRange": "String ('N/A' if not applicable)",
          "statusIndicator": "String ('H', 'L', 'N', 'N/A')",
          "reportDate": "MM/DD/YYYY",
          "sampleSource": "String ('URINE', 'BLOOD', etc.)"
        }
      ],
      "patientPreference": [
        {
          "name": "String ('N/A' if not applicable)",
          "strength": "String ('N/A' if not applicable)",
          "refills": "String ('N/A' if not applicable)",
          "quantity": "String ('N/A' if not applicable)",
          "medId": "String ('N/A' if not applicable)"
        }
      ],
      "Q1": "String",
      "A1": "String"
      // Additional Q/A pairs as needed
    },
    "pharmacyId": "String",
    "masterId": "String (unique)",
    "company": "String",
    "visitType": "String ('weightloss', 'weightlossfollowup', 'ED', 'PE', 'hairloss')"
  }
  ```

### 5. Patient Photos Submission
**Endpoint:** `{base url}/external/receivePhotos`
- **Method:** POST
- **Payload:**
  ```json
  {
    "visitId": "String (REQUIRED)",
    "images": [
      {
        "mime": "image/jpeg",
        "data": "String (base64 encoded)"
      }
      // Additional image objects as needed
    ]
  }
  ```

### 6. PDF Submission
**Endpoint:** `{base url}/external/receivePdf`
- **Method:** POST
- **Payload:**
  ```json
  {
    "visitId": "String (REQUIRED)",
    "image": {
      "mime": "application/pdf",
      "data": "String (base64 encoded)"
    }
  }
  ```

### 7. Send Patient Chat Message
**Endpoint:** `{base url}/external/receiveChat`
- **Method:** POST
- **Payload:**
  ```json
  {
    "firstName": "String (REQUIRED)",
    "lastName": "String (REQUIRED)",
    "content": "String (REQUIRED)",
    "isMedia": false,
    "masterId": "String (REQUIRED)"
  }
  ```

### 8. Customer Service Message
**Endpoint:** `{base url}/external/receiveCSMessage`
- **Method:** POST
- **Payload:**
  ```json
  {
    "content": "String (REQUIRED)",
    "masterId": "String (REQUIRED)"
  }
  ```

### 9. Pharmacy List Search
**Endpoint:** `{base url}/external/pharmacies`
- **Method:** POST
- **Payload:**
  ```json
  {
    "name": "String (REQUIRED
```


Here is a breakdown of the common and unique payload properties for each REST API noun based on the Shareable Beluga Skeleton API documentation:

## Properties

Sure! Below are the tables for each API noun, followed by an example JSON object for each.

### 1. Visit

#### Common Payload Properties

| **Property Name**     | **Property Type**            |
|-----------------------|------------------------------|
| `firstName`           | String (max 100 chars)       |
| `lastName`            | String (max 100 chars)       |
| `dob`                 | String (MM/DD/YYYY)          |
| `phone`               | String (10 digits, US mobile)|
| `email`               | String                        |
| `address`             | String                        |
| `city`                | String                        |
| `state`               | String (2 chars)             |
| `zip`                 | String (5 digits)            |
| `sex`                 | String ('Male', 'Female', 'Other') |
| `selfReportedMeds`    | String                        |
| `allergies`           | String                        |
| `medicalConditions`   | String                        |
| `company`             | String                        |
| `visitType`           | String ('weightloss', 'weightlossfollowup', 'ED', 'PE', 'hairloss') |

#### Unique Attributes for Visit Form Submission (No ID Photos)

| **Property Name**     | **Property Type**            |
|-----------------------|------------------------------|
| `patientVerified`     | Boolean                      |
| `verificationId`      | String                        |
| `pharmacyId`          | String                        |
| `visitId`             | String (unique)              |
| `patientPreference`   | Array of Objects             |
| `Q1`, `A1`            | String                        |
| `Q[n]`, `A[n]`        | String                        |

#### JSON Example for Visit Form Submission (No ID Photos)

```json
{
  "formObj": {
    "firstName": "John",
    "lastName": "Doe",
    "dob": "01/01/1980",
    "phone": "5551234567",
    "email": "john.doe@example.com",
    "address": "123 Elm Street",
    "city": "Springfield",
    "state": "CA",
    "zip": "90210",
    "sex": "Male",
    "selfReportedMeds": "None",
    "allergies": "Peanuts",
    "medicalConditions": "Hypertension",
    "patientPreference": [
      {
        "name": "Medication A",
        "strength": "50mg",
        "quantity": "30",
        "refills": "2",
        "medId": "12345"
      }
    ],
    "Q1": "Have you traveled recently?",
    "A1": "No"
  },
  "patientVerified": true,
  "verificationId": "abc123",
  "pharmacyId": "pharmacy123",
  "visitId": "visit123",
  "company": "HealthCo",
  "visitType": "weightloss"
}
```

### 2. Lab Results

#### Common Payload Properties

| **Property Name**     | **Property Type**            |
|-----------------------|------------------------------|
| `firstName`           | String (max 100 chars)       |
| `lastName`            | String (max 100 chars)       |
| `dob`                 | String (MM/DD/YYYY)          |
| `phone`               | String (10 digits)           |
| `email`               | String                        |
| `address`             | String                        |
| `city`                | String                        |
| `state`               | String (2 chars)             |
| `zip`                 | String (5 digits)            |
| `sex`                 | String ('Male', 'Female', 'Other') |
| `selfReportedMeds`    | String                        |
| `allergies`           | String                        |
| `medicalConditions`   | String                        |
| `company`             | String                        |
| `visitType`           | String ('weightloss', 'weightlossfollowup', 'ED', 'PE', 'hairloss') |
| `testToTreat`         | Boolean                      |

#### Unique Attributes for Lab Results Submission (With ID Verification)

| **Property Name**     | **Property Type**            |
|-----------------------|------------------------------|
| `patientVerified`     | Boolean                      |
| `verificationId`      | String                        |
| `pharmacyId`          | String                        |
| `masterId`            | String (unique)              |
| `results`             | Array of Objects             |
| `patientPreference`   | Array of Objects (required if `testToTreat` is true) |
| `Q1`, `A1`            | String                        |
| `Q[n]`, `A[n]`        | String                        |

#### JSON Example for Lab Results Submission (With ID Verification)

```json
{
  "formObj": {
    "firstName": "Jane",
    "lastName": "Doe",
    "dob": "02/02/1985",
    "phone": "5559876543",
    "email": "jane.doe@example.com",
    "address": "456 Oak Avenue",
    "city": "Somewhere",
    "state": "NY",
    "zip": "10001",
    "sex": "Female",
    "selfReportedMeds": "Aspirin",
    "allergies": "None",
    "medicalConditions": "Diabetes",
    "testToTreat": true,
    "results": [
      {
        "screeningDate": "01/15/2024",
        "testName": "Blood Sugar",
        "testResult": "120",
        "testResultUnits": "mg/dL",
        "refRange": "70-110",
        "statusIndicator": "H",
        "reportDate": "01/16/2024",
        "sampleSource": "BLOOD"
      }
    ],
    "patientPreference": [
      {
        "name": "Insulin",
        "strength": "100 units",
        "refills": "1",
        "quantity": "1",
        "medId": "67890"
      }
    ],
    "Q1": "Do you exercise regularly?",
    "A1": "Yes"
  },
  "patientVerified": true,
  "verificationId": "def456",
  "pharmacyId": "pharmacy456",
  "masterId": "master456",
  "company": "HealthCo",
  "visitType": "weightlossfollowup"
}
```

### 3. Image/Photo

#### Common Payload Properties

| **Property Name**     | **Property Type**            |
|-----------------------|------------------------------|
| `visitId`             | String (REQUIRED)            |

#### Unique Attributes for Patient Photos Submission

| **Property Name**     | **Property Type**            |
|-----------------------|------------------------------|
| `images`              | Array of Objects             |
| `mime`                | String ("image/jpeg")        |
| `data`                | String (base64 encoded)      |

#### JSON Example for Patient Photos Submission

```json
{
  "visitId": "visit123",
  "images": [
    {
      "mime": "image/jpeg",
      "data": "/9j/4AAQSkZJRgABAQEAAAAAAAD/2wBDAA..."
    }
  ]
}
```

#### Unique Attributes for PDF Submission

| **Property Name**     | **Property Type**            |
|-----------------------|------------------------------|
| `image`               | Object                       |
| `mime`                | String ("application/pdf")   |
| `data`                | String (base64 encoded)      |

#### JSON Example for PDF Submission

```json
{
  "visitId": "visit123",
  "image": {
    "mime": "application/pdf",
    "data": "JVBERi0xLjQKJcTl8uXrp/Og0MTGCjQgMCBvYmoK..."
  }
}
```

### 4. Chat Message

#### Common Payload Properties

| **Property Name**     | **Property Type**            |
|-----------------------|------------------------------|
| `masterId`            | String (REQUIRED)            |

#### Unique Attributes for Send Patient Chat Message

| **Property Name**     | **Property Type**            |
|-----------------------|------------------------------|
| `firstName`           | String (REQUIRED)            |
| `lastName`            | String (REQUIRED)            |
| `content`             | String (REQUIRED)            |
| `isMedia`             | Boolean                      |

#### JSON Example for Send Patient Chat Message

```json
{
  "firstName": "Alice",
  "lastName": "Smith",
  "content": "Hello, I have a question about my prescription.",
  "isMedia": false,
  "masterId": "master789"
}
```

#### Unique Attributes for Customer Service Message

| **Property Name**     | **Property Type**            |
|-----------------------|------------------------------|
| `content`             | String (REQUIRED)            |

#### JSON Example for Customer Service Message

```json
{
  "content": "Customer requested assistance with account setup.",
  "masterId": "master789"
}
```

### 5. Pharmacy

#### Unique Attributes for Pharmacy List Search

| **Property Name**     | **Property Type**            |
|-----------------------|------------------------------|
| `name`                | String (REQUIRED)            |
| `city`                | String                        |
| `state`               | String ("XX")                |
| `zip`                 | String ("XXXXX")             |

#### JSON Example for Pharmacy List Search

```json
{
  "name": "Main Street Pharmacy",
  "city": "New York",
  "state": "NY",
  "zip": "10001"
}
```

### 6. Visit Update/Resend Prescription

#### Unique Attributes

| **Property Name**     | **Property Type**            |
|-----------------------|------------------------------|
| `patientPreference`   | Array of Objects             |
| `name`                | String (REQUIRED)            |
| `strength`            | String (REQUIRED)            |
| `refills`             | String (REQUIRED)            |
| `quantity`            | String (REQUIRED)            |
| `medId`               | String (REQUIRED)            |
| `pharmacyId`          | String (REQUIRED)            |
| `apiKey`              | String (REQUIRED)            |

#### JSON Example for Visit Update/Resend Prescription

```json
{
  "patientPreference": [
    {
      "name": "Medication B",
      "strength": "10mg",
      "refills": "3",
      "quantity": "60",
      "medId": "11223"
    }
  ],
  "pharmacyId": "pharmacy123",
  "masterId": "master123",
  "apiKey": "apiKey123"
}
```

### 7. Patient Name

#### Unique Attributes for Patient Name Update

| **Property Name**     | **Property Type**            |
|-----------------------|------------------------------|
| `masterId`            | String (REQUIRED)            |
| `firstName`           | String (max length 100) (REQUIRED) |
| `lastName`            | String (max length 100) (REQUIRED) |

#### JSON Example for Patient Name Update

```json
{
  "masterId": "master123",
  "firstName": "Robert",
  "lastName": "Johnson"
}
```

