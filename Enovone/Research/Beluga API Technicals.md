Here are the tables with common payload properties followed by a JSON example, and then a separate list of unique attributes for each API noun.

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

#### JSON Example for Common Payload Properties

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
	  "company": "HealthCo",
	  "visitType": "weightloss"
	}
}
```

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

#### Unique Attributes for Visit Form Submission (With ID Photos)

| **Property Name**     | **Property Type**            |
|-----------------------|------------------------------|
| `pharmacyId`          | String                        |
| `masterId`            | String (unique)              |


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

#### JSON Example for Common Payload Properties

```json
{
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
  "company": "HealthCo",
  "visitType": "weightlossfollowup",
  "testToTreat": true
}
```

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

#### Unique Attributes for Lab Results Submission (Without ID Verification)

| **Property Name**     | **Property Type**            |
|-----------------------|------------------------------|
| `pharmacyId`          | String                        |
| `masterId`            | String (unique)              |
| `results`             | Array of Objects             |
| `patientPreference`   | Array of Objects (required if `testToTreat` is true) |


### 3. Image/Photo

#### Common Payload Properties

| **Property Name**     | **Property Type**            |
|-----------------------|------------------------------|
| `visitId`             | String (REQUIRED)            |

#### JSON Example for Common Payload Properties

```json
{
  "visitId": "visit123"
}
```

#### Unique Attributes for Patient Photos Submission

| **Property Name**     | **Property Type**            |
|-----------------------|------------------------------|
| `images`              | Array of Objects             |
| `mime`                | String ("image/jpeg")        |
| `data`                | String (base64 encoded)      |

#### Unique Attributes for PDF Submission

| **Property Name**     | **Property Type**            |
|-----------------------|------------------------------|
| `image`               | Object                       |
| `mime`                | String ("application/pdf")   |
| `data`                | String (base64 encoded)      |


### 4. Chat Message

#### Common Payload Properties

| **Property Name**     | **Property Type**            |
|-----------------------|------------------------------|
| `masterId`            | String (REQUIRED)            |

#### JSON Example for Common Payload Properties

```json
{
  "masterId": "master789"
}
```

#### Unique Attributes for Send Patient Chat Message

| **Property Name**     | **Property Type**            |
|-----------------------|------------------------------|
| `firstName`           | String (REQUIRED)            |
| `lastName`            | String (REQUIRED)            |
| `content`             | String (REQUIRED)            |
| `isMedia`             | Boolean                      |

#### Unique Attributes for Customer Service Message

| **Property Name**     | **Property Type**            |
|-----------------------|------------------------------|
| `content`             | String (REQUIRED)            |


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
  "apiKey": "apiKey123"
}
```

### 7. Patient Name

#### Unique Attributes for Patient Name Update

| **Property Name**     | **Property Type**            |
|-----------------------|------------------------------|
| `masterId`            | String (REQUIRED)            |
| `firstName`           | String (max length 100) (REQUIRED) |
| `lastName`            | String

 (max length 100) (REQUIRED) |

#### JSON Example for Patient Name Update

```json
{
  "masterId": "master123",
  "firstName": "Robert",
  "lastName": "Johnson"
}
```

These tables and JSON examples provide a detailed view of the payload structures for each API noun in the Shareable Beluga Skeleton API. Let me know if you need further assistance!