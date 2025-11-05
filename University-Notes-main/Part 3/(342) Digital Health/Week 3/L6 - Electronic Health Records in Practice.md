
case studies and data systems


- analyse example EMR data, to explore how structured medical data can be organised and retrieved
- identify key principles for the successful implementation of EHR systems
- Illustrate these principles using real-world examples of well-implemented and poorly implemented EHR systems


## A real example: MIMIC

(Medical information Mart for intensive care)

MIMIC is an example of EMR data derived data, it is not a EHR or EMR. it is a static archived data from a single setting 

a database comprising de-indentification health-related data from patients who were admitted to the critical care units of the Beth Israel Deaconess Medical Centre (Boston, MA)



![[Pasted image 20251023141021.png]]
Relational databases - JOINS

- JOINs combine data from two or more tables into a single dataset. Records are matched based on a given condition
- some people find JOINs more intuitive, while others find joining tables on multiple WHERE conditions more intuitive

• JOIN returns all rows that match the ON condition.
• The JOIN condition doesn’t have to be an equality – it can be any condition you want
• JOIN is also called INNER JOIN
`
```SQL
SELECT *
FROM patients
JOIN medications ON patients.patient_id = medications.patient_id; 
```


two tables:
d_icd_dignoses & diagnoses_icd

in d_icd_diagnosis: gives ICD code to text translation with the following data fields; **icd_code, icd_version, long_title**
in diagnosis_icd that contains diagnosis codes assigned to patient during hospital admissions with the following data fields: **subject_id, hadm_id, seq_num, icd_code, icd_version**



write a query to find the three most common diagnoses and return the icd code, long title, and number of diagnoses for each


```SQL
SELECT
d.icd_code,
d.long_title,
COUNT(*) as count
FROM d_icd_diagnoses as di
JOIN diagnoses_id as d
	ON d.icd_code = di.icd_code
GROUP BY d.icd_code, di.long_title
ORDER BY count DESC
LIMIT 3;
```

overview of data structure - MIMIC

- MIMIC-IV adopts a relational structure with predefined relationships stored across tables and columns
- data are grouped into distinct modules: core, hosp, and icu
- core: tracks patients, who, where
- icu: tracks ICU, clinical information system
- hosp: tracks hospital level information sourced from hospital EMR


## EHR systems

-  a system where the appliance or software allows to store, intermediate, export, import, convert, edit, or view personal electronic health data that belongs to the priority categories of personal electronic health data
	- data includes patient summaries, electronic prescriptions, electronic dispensations, medical imaging studies and related imaging reports, medical test results, discharge reports
 state EHR system should offer the following basic functions

**Health Information** and Data It should store and provide access to health information of patients.
**Replicate the Workflow** It should be able to work in-sync with the original workflow of the healthcare organization.
**Efficient Interaction** It should be able to work effectively, saving time of care providers by keeping things concise.
**Clinical Decision Support (CDS)** It should support provision of reminders, prompts, and alerts.
**Patient Support** It should empower patients to access their health information, enabling them to be involved in their own healthcare.
**Messaging and Data Processing Capability** It should enable exchange of data in
known/standard formats for interoperability of healthcare applications.
**Administrative Tools** It should provide administrative tools, such as scheduling systems, for improving efficiency of clinical practices. 22 / 32


EHR example: OpenEMR

- open source electronic medical record and practice management system
- ONC certified - meets US healthcare standards for electronic health record
• Patient Demographics
• Patient Scheduling
• Electronic Medical Records
• Prescriptions
• Medical Billing
• Clinical Decision Rules
• Patient Portal
• Reports
• Multilanguage Support
• Security

In this lecture we covered:

• How electronic health record (EHR) data is structured and used in real-world clinical
settings using MIMIC-IV as a case study

• The role of SQL JOINs and database relationships in extracting meaningful clinical
information

• Key features and design considerations of effective EHR systems

• Lessons from real-world EHR implementations - understanding why some succeed
and others fail

• The importance of interoperability, usability, and stakeholder involvement in
EHR adoption
