# corona123.ch

This documentation is for developers who want to provide an entry point to https://corona123.ch with prefilled data. The most common case is to display a web view or provide a link with data from a healthcare information system.

CAUTION: Be careful to only create URLs which do not exceed the limit of the used browsers.

## Prefill test form

To prefill the test form a link has to be constructed using the base URL `https://corona123.ch/corona-test-form-prefill/{organization-id}`. The organization id can be retrieved using the regular frontend `https://corona123.ch/select-organization` as the chosen organization id is written in the fragment of the URL and can be copied from there. An example of a base URL with organization id is `https://corona123.ch/corona-test-form-prefill/4b2037ca-4639-48f7-a662-501895c03d57`.

The data to prefill has to be passed as GET parameters as the following example demonstrates:

```
https://corona123.ch/corona-test-form-prefill/52511093-03b5-4fce-9356-be41aa58cb9c?testDate=2021-03-04&firstName=Werner&lastName=Huber&nationality=CH&dateOfBirth=1964-10-04&gender=MALE&street=Seitenweg%2011&postalCode=8640&city=Rapperswil&canton=SG&maritalStatus=SINGLE&phone=0764561212&email=test@example.com&generalPractitioner=Dr.%20Meier&identityNumberInsurance=12412412412412&healthInsurance=Helsana&countryOfResidence=DE&worksAsMedicalStaff=false&isPregnant=true&otherSymptom=Anderes%20Symptom&startOfSymptoms=2021-03-03&otherDisease=Anderes&isSmoker=false&reasonForTest=OTHER&otherReasonForTest=AnderereGrund&expositionLand=DE&expositionCity=Berlin&otherTransportation=Rollen&isInNursingHome=true&nursingHomeName=Heim&nursingHomePhone=0552441212&contactWithPositive=false&inQuarantineBefore=true&pathOfInfection=FAMILY&otherPathOfInfection=Kein&expositionDay=2021-03-02&profession=Informatik&note=Notiz&disease=OBESITY&symptom=COUGH&symptom=CHEST_PAIN&transportation=AIR_PLANE
```

The only **required field** is `testDate` as it is currently not possible to edit this afterwards.

The following table lists all fields:



## Prefill vaccination form
