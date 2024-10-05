## Definitions

### Wearable Data

Wearable Data is a phrase with many meanings to different audiences. Wearable Data can also be a misnomer; not all data is derived from a wearable device. 

Wearable's are a branch of the Internet of Things (IoT) and as such, you may find Wearable Data being provided by things like a mattress, cycling equipment, and even the weight scales. Things you don't really wear, but describe physical wear on the user. 

Wearable Data should be defined as any data that is provided by an application or device (Provider) that describes a physical attribute or action gathered from its measurements.

### Providers

Providers are, in a way, the wearable itself.  When you put on your Fitbit or Garmin watch in the morning, you're putting on that Provider. When you jump on your Peloton bike for a workout, your "wearable" is now Peloton.

## Access to Data

Most Providers grant some type of API access to third party developers to the Wearable Data they aggregate. There are lots of Providers out there today; creating a fragmentation in the marketplace on how to access and gather this data. This has given way to plenty of companies offering a unified API to access that data. 

### Provider Integrations

Providers typically offer access through on device SDK and/or OAuth API. 

On device SDK means just that, you must have an application on the device itself that asks for access to the given Wearable Data. Any data gathered must be gathered by the on device application first.

OAuth API allows an application to gain access to the Provider's gathered data without access to the device. Any data gathered must be gathered first by the Provider.

### Vital
Vital, https://www.tryvital.com/, is one of the aforementioned unified API providers. 

They split access into two different groups: Vital SDK and Vital Link.

Without an on device application, we could get access to the following:

- Abbot
- Beurer
- Dexcom
- Fitbit
- Garmin
- Google Fit
- Hammerhead
- iHealth
- My Fitness Pal
- Omron
- Oura
- Peloton
- Renpho
- Wahoo
- Withings
- Zwift

With an application on device, we could get access to the following:
- Apple HealthKit
- Android Health Connect


