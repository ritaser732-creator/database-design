# University Admissions Database Design 🎓

Conceptual database design (**Entity-Relationship Diagram**) for a university admissions system: applicants register for study programs, receive scholarships, make payments, and are approved by the admissions office.

> Course project, B.Sc. Information Systems, University of Haifa.

## 📐 ERD

![ERD](diagrams/erd.png)

*The diagram labels are in Hebrew; the English description is below.*

## 🧱 Entities

| Entity | Key | Attributes |
|---|---|---|
| **Applicant** (מועמד) | ID number | first name, last name, email, phone, birth year, status *(accepted / rejected / pending)* |
| **Program** (חוג) | program ID | name, head of program, faculty, admission requirements *(matriculation grade)* |
| **Scholarship** (מלגה) | scholarship code | name, type *(excellence / financial aid)* |
| **Payment** (תשלום) | payment number | amount, payment date, payment method *(cash / credit)* |
| **Secretary** (מזכירה) | secretary ID | first name, last name |

## 🔗 Relationships

| Relationship | Between | Cardinality | Attributes |
|---|---|---|---|
| **Registers** (נרשם) | Applicant → Program | each applicant registers for exactly one program; a program can have many applicants | registration year |
| **Receives** (מקבל) | Applicant → Scholarship | each applicant receives at most one scholarship; a scholarship can be given to many applicants | |
| **Makes** (מבצע) | Applicant ↔ Payment | many-to-many | |
| **Approves** (מאשרת) | Secretary → Applicant | each approval is done by one secretary; a secretary approves many applicants | approval date |

## 💡 Design concepts

- Primary keys (underlined in the diagram)
- One-to-many and many-to-many relationships with crow's foot notation, including optional participation
- Relationship attributes (registration year, approval date)
- Attributes with a fixed set of allowed values (status, scholarship type, payment method)
