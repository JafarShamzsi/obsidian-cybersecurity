# CompTIA Security+ (SY0-601) Study Guide

Welcome to my Security+ certification study notes. This index serves as the central hub for all study materials, concepts, and practice resources.

## Study Activity Tracker

```githubcalendar
calendar: Study Sessions
color: green
```

## Exam Domains

|Domain|Weight|Link|
|---|---|---|
|1. Threats, Attacks and Vulnerabilities|24%|[[1-Threats-Attacks-Vulnerabilities/README]]|
|2. Architecture and Design|21%|[[2-Architecture-Design/README]]|
|3. Implementation|25%|[[3-Implementation/README]]|
|4. Operations and Incident Response|16%|[[4-Operations-Incident-Response/README]]|
|5. Governance, Risk and Compliance|14%|[[5-Governance-Risk-Compliance/README]]|

## Study Progress

- [ ] Complete domain 1 review
- [ ] Complete domain 2 review
- [ ] Complete domain 3 review
- [ ] Complete domain 4 review
- [ ] Complete domain 5 review
- [ ] Take practice exam 1
- [ ] Review weak areas
- [ ] Take practice exam 2
- [ ] Final review

## Quick Links

- [[Glossary|Security+ Terminology]]
- [[Practice-Questions/README|Practice Questions]]
- [[Labs/README|Hands-on Labs]]
- [[Study Schedule]]
- [[Exam Tips]]

## Key Concepts

- [[CIA Triad]]
- [[Authentication Factors]]
- [[Network Security]]
- [[Cryptography Basics]]
- [[Incident Response Process]]
- [[Risk Management]]

## Resources

- Official CompTIA Resources
    - [CompTIA Security+ Exam Objectives](https://www.comptia.org/training/resources/exam-objectives)
    - CompTIA Security+ Study Guide (Book)
- Online Courses
    - Professor Messer's Security+ Videos
    - Jason Dion's Udemy Course
- Practice Tests
    - ExamCompass
    - Jason Dion's Practice Exams

## Recent Notes

```dataview
LIST
FROM "Security+"
SORT file.mtime DESC
LIMIT 5
```

## Focus Areas

```dataview
LIST
FROM #exam-essential
SORT file.mtime DESC
```

## Red Team Specific Notes

```dataview
LIST
FROM #red-team
SORT file.mtime DESC
```

## Study Metrics

```dataview
TABLE 
  dateformat(file.ctime, "yyyy-MM-dd") as "Date",
  time-studied as "Time",
  topics as "Topics Covered"
FROM "Security+/Daily-Study"
SORT file.ctime DESC
LIMIT 7
```

---

Last updated: [[{{date:YYYY-MM-DD}}]]

#security+ #certification #study-guide