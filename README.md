# corona123.ch

This documentation is for developers who want to provide an entry point to https://corona123.ch with prefilled data. The most common case is to display a web view or provide a link with data from a healthcare information system.

CAUTION: Be careful to only create URLs which do not exceed the limit of the used browsers.

## Prefill test form

To prefill the test form a link has to be constructed using the base URL `https://corona123.ch/corona-test-form-prefill/{organization-id}`. The organization id can be retrieved using the regular frontend `https://corona123.ch/select-organization` as the chosen organization id is written in the fragment of the URL and can be copied from there. An example of a base URL with organization id is `https://corona123.ch/corona-test-form-prefill/4b2037ca-4639-48f7-a662-501895c03d57`.

The data to prefill has to be passed as GET parameters as the following example demonstrates:

```
https://corona123.ch/corona-test-form-prefill/4b2037ca-4639-48f7-a662-501895c03d57?testDate=2021-03-04&firstName=Werner&lastName=Huber&nationality=CH&dateOfBirth=1964-10-04&gender=MALE&street=Seitenweg%2011&postalCode=8640&city=Rapperswil&canton=SG&maritalStatus=SINGLE&phone=0764561212&email=test@example.com&generalPractitioner=Dr.%20Meier&identityNumberInsurance=12412412412412&healthInsurance=Helsana&countryOfResidence=DE&worksAsMedicalStaff=false&isPregnant=true&otherSymptom=Anderes%20Symptom&startOfSymptoms=2021-03-03&otherDisease=Anderes&isSmoker=false&reasonForTest=OTHER&otherReasonForTest=AnderereGrund&expositionLand=DE&expositionCity=Berlin&otherTransportation=Rollen&isInNursingHome=true&nursingHomeName=Heim&nursingHomePhone=0552441212&contactWithPositive=false&inQuarantineBefore=true&pathOfInfection=FAMILY&otherPathOfInfection=Kein&expositionDay=2021-03-02&profession=Informatik&note=Notiz&disease=OBESITY&symptom=COUGH&symptom=CHEST_PAIN&transportation=AIR_PLANE
```

The only **required field** is `testDate` as it is currently not possible to edit this afterwards.

The following table lists all possible fields:

| Name | Label (on corona123.ch) | Type |
| --- | --- | --- |
| `firstName` | First Name | `string` |
| `lastName` | Surname | `string` |
| `nationality` | Nationality | `string` (valid ISO 3166-1 alpha-2 country code, e. g. `CH`) |
| `dateOfBirth` | Date of birth | `date` (format: YYYY-MM-DD, e. g. `2020-12-31`) |
| `gender` | Gender | `FEMALE \| MALE \| OTHER` |
| `street` | Street, house number | `string` |
| `postalCode` | Postcode | `string` |
| `city` | Place | `string` |
| `canton` | Canton | `ZH \| BE \| LU \| UR \| SZ \| OW \| NW \| GL \| ZG \| FR \| SO \| BS \| BL \| SH \| AR \| AI \| SG \| GR \| AG \| TG \| TI \| VD \| VS \| NE \| GE \| JU` |
| `maritalStatus` | Marital status | `SINGLE \| MARRIED \| WIDOWED \| SEPARATED \| DIVORCED` |
| `phone` | Mobile phone | `string` |
| `email` | E-mail | `string` |
| `generalPractitioner` | General practitioner | `string` |
| `identityNumberInsurance` | Insurance number | `string` |
| `healthInsurance` | Health insurance | `string` |
| `countryOfResidence` | Country of residence | `string` (valid ISO 3166-1 alpha-2 country code, e. g. `CH`) |
| `worksAsMedicalStaff` | Do you work in health care in direct contact with patients? | `boolean` |
| `symptom` | Which symptoms apply to you (all that apply)? | `COUGH \| CHEST_PAIN \| BREATHING_DIFFICULTIES \| SORE_THROAT \| ACUTE_RESPIRATORY_DISEASE \| ANOSMIA \| AGEUSIA \| FEVER \| CONFUSED \| GASTROINTESTINAL_SYMPTOMS` (multiple times allowed, e. g. `symptom=COUGH&symptom=SORE_THROAT`) |
| `otherSymptom` | Other symptoms | `string` |
| `startOfSymptoms` | When did the symptoms first appear? | `date` (format: YYYY-MM-DD, e. g. `2020-12-31`) |
| `disease` | Which diseases/therapies apply to you (all that apply)? | `DIABETES \| HEART_DISEASE \| IMMUNE_SUPPRESSION \| KIDNEY_DISEASE \| HYPERTENSION \| CHRONIC_RESPIRATORY_DISEASE \| CANCER \| OBESITY \| LIVER_DISEASE \| TRISOMY_21` (multiple times allowed, e. g. `disease=LIVER_DISEASE&disease=CANCER`) |
| `otherDisease` | Other disease | `string` |
| `isPregnant` | Are you pregnant or is there a chance you might be pregnant? | `boolean` |
| `isSmoker` | Smoker | `boolean` |
| `reasonForTest` | Why are you getting a COVID-19 test? | `COVID19_SYMPTOMS \| BREAKOUT_INVESTIGATION \| SWISS_COVID_APP \| OTHER` |
| `otherReasonForTest` | Other reason for testing | `string` (has only relevance if `reasonForTest` is equal to `OTHER`) |
| `expositionLand` | Have you been abroad in the last 14 days? | `string` (valid ISO 3166-1 alpha-2 country code, e. g. `DE`, `CH` indicates the person was not abroad) |
| `expositionCity` | Location where you are staying | `string` |
| `isInNursingHome` | Do you live in a retirement or care home? | `boolean` |
| `nursingHomeName` | Name of the retirement or care home | `string` |
| `nursingHomePhone` | Telephone number of the retirement or care home, format: 0XX XXX XX XX | `string` |
| `contactWithPositive` | Have you been in close contact with a lab-confirmed COVID-19 case? | `boolean` |
| `inQuarantineBefore` | Are you in quarantine? | `boolean` |
| `pathOfInfection` | In the event of a positive test result, which transmission route do you think is the most likely? | `FAMILY \| MEDICAL_STAFF \| PRIVATE_PARTY \| CLUB \| RESTAURANT \| SPONTANEOUS_GATHERING \| SCHOOL \| DEMONSTRATION \| WORK \| UNKNOWN \| OTHER` |
| `otherPathOfInfection` | Other transmission route | `string` (has only relevance if `pathOfInfection` is equal to `OTHER`) |
| `expositionDay` | When is it most likely that the infection occurred? | `date` (format: YYYY-MM-DD, e. g. `2020-12-31`) |
| `profession` | Other professional activity | `string` |
| `note` | Note | `string` |


## Prefill vaccination form

The link construction is very similar to the one of the test form but uses
another base link: `https://corona123.ch/corona-vaccine-form-prefill/{organization-id}`.

A complete example is the following:

```
https://corona123.ch/corona-vaccine-form-prefill/4b2037ca-4639-48f7-a662-501895c03d57?firstName=Werner&lastName=Huber&nationality=CH&dateOfBirth=1964-10-04&gender=MALE&street=Seitenweg%2011&postalCode=8640&city=Rapperswil&canton=SG&maritalStatus=SINGLE&phone=0764561212&email=test@example.com&generalPractitioner=Dr.%20Meier&identityNumberInsurance=12412412412412&healthInsurance=Helsana&countryOfResidence=DE&worksAsMedicalStaff=false&&hasContactWithVulnerablePeople=false&livesInACommunityFacility=false&isPregnant=false&hasAllergies=false&hasCurrentlyColdSymptoms=false&takesAnticoagulants=false&hadCovidInTheLast90Days=false&hadCovidVaccination=false&isCurrentlyBreastfeeding=false&wantsVaccinationCertificate=true&disease=LIVER_DISEASE&disease=CANCER
```

The following table lists all possible fields:

| Name | Label (on corona123.ch) | Type |
| --- | --- | --- |
| `firstName` | First Name | `string` |
| `lastName` | Surname | `string` |
| `nationality` | Nationality | `string` (valid ISO 3166-1 alpha-2 country code, e. g. `CH`) |
| `dateOfBirth` | Date of birth | `date` (format: YYYY-MM-DD, e. g. `2020-12-31`) |
| `gender` | Gender | `FEMALE \| MALE \| OTHER` |
| `street` | Street, house number | `string` |
| `postalCode` | Postcode | `string` |
| `city` | Place | `string` |
| `canton` | Canton | `ZH \| BE \| LU \| UR \| SZ \| OW \| NW \| GL \| ZG \| FR \| SO \| BS \| BL \| SH \| AR \| AI \| SG \| GR \| AG \| TG \| TI \| VD \| VS \| NE \| GE \| JU` |
| `maritalStatus` | Marital status | `SINGLE \| MARRIED \| WIDOWED \| SEPARATED \| DIVORCED` |
| `phone` | Mobile phone | `string` |
| `email` | E-mail | `string` |
| `generalPractitioner` | General practitioner | `string` |
| `okpInsured` | Are you OKP insured (in Switzerland)? | `boolean` |
| `identityNumberInsurance` | Insurance number | `string` |
| `healthInsurance` | Health insurance | `string` |
| `countryOfResidence` | Country of residence | `string` (valid ISO 3166-1 alpha-2 country code, e. g. `CH`) |
| `worksAsMedicalStaff` | Do you work in health care in direct contact with patients? | `boolean` |
| `isPregnant` | Are you pregnant or is there a chance you might be pregnant? | `boolean` |
| `hasContactWithVulnerablePeople` | Do you live in the same household with someone who is particularly at risk of becoming seriously ill? | `boolean` |
| `livesInACommunityFacility` | Do you live in one of the following communal facilities for adults: shelter or facility for people with disabilities, psychosomatic or psychiatric clinic, asylum shelter, homeless shelter or detention centre or similar? | `boolean` |
| `hasAllergies` | In the past, have you experienced severe allergic reactions to drugs or vaccines? | `boolean` |
| `hasCurrentlyColdSymptoms` | Are you currently experiencing cold symptoms (temperature, feeling poorly, sore throat, cough, body aches) or changes in taste/smell? | `boolean` |
| `takesAnticoagulants` | Are you taking anti-coagulants ('blood thinners')? | `boolean` |
| `hadCovidInTheLast90Days` | Have you been diagnosed with COVID-19 in the past 90 days? | `boolean` |
| `hadCovidVaccination` | Have you already had a COVID-19 vaccine? | `boolean` |
| `isCurrentlyBreastfeeding` | Are you currently breastfeeding? | `boolean` |
| `wantsVaccinationCertificate` | Do you want the vaccination to be entered in your electronic vaccination card (meineimpfungen.ch/myCOVIDvac.ch)? If you do not yet have an electronic vaccination card, this will be created for you during the registration process. All information on the electronic vaccination card can be found at [myCOVIDvac.ch](https://www.myCOVIDvac.ch). | `boolean` |
| `disease` | Which diseases/therapies apply to you (all that apply)? | `DIABETES \| HEART_DISEASE \| IMMUNE_SUPPRESSION \| KIDNEY_DISEASE \| HYPERTENSION \| CHRONIC_RESPIRATORY_DISEASE \| CANCER \| OBESITY \| LIVER_DISEASE \| TRISOMY_21` (multiple times allowed, e. g. `disease=LIVER_DISEASE&disease=CANCER`) |
