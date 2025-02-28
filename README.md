### Automated Grading and Plagiarism Detection System(Use Case Diagram)

#### Overview

This document provides a description of the use case diagram for the Automated Grading and Plagiarism Detection System. The diagram outlines the interactions between different actors and the system, detailing the processes of assignment submission, grading, and feedback, as well as plagiarism detection.

#### Key Components

Actors:

###### Professor

Sets grading criteria and deadlines.

Reviews student submissions.

Provides feedback and assigns grades.

###### Student

Submits assignments.

Views grades and feedback.

Requests assistance if needed.

###### Plagiarism Detection Service

Checks for plagiarism in submitted assignments.

###### LMS System

Syncs final grades with the Learning Management System.

##### Regulatory Body

Audits grades to ensure compliance with academic policies.

#### Use Cases:

###### 1. Set Deadline & Criteria (Professor)

- The professor defines assignment deadlines and grading parameters.

##### 2. Submit Assignment (Student)

- The student submits an assignment to the system.

- Extends: Allow Resubmission (if enabled by the professor).

##### 3. Run and Grade Code (System)

- The system compiles and executes the student's code.

- Includes: Plagiarism Check.

##### 4. Plagiarism Check (Plagiarism Detection Service)

- Compares the submission with existing online and past submissions.

##### 5. Store Grade & Feedback (System)

- The system stores grades and feedback for students.

- Includes: Sync with LMS.

##### 6. View Grades & Feedback (Student)

- The student accesses their assignment results.

##### 7. Sync with LMS (LMS System)

- The system updates the LMS with the final grades.

###### 8. Audit Grades (Regulatory Body)

- Ensures that grading policies are followed correctly.

###### 9. Request Assistance (Student)

- Students can request help from professors or system support.

- Extends:

- FAQ Access (for immediate answers).

- Follow-Up Reminder (if the response time exceeds a threshold).

#### Relationships:

- Includes: Some use cases require additional processes (e.g., plagiarism detection and LMS synchronization).

- Extends: Additional functionalities trigger under specific conditions (e.g., FAQ access when students request assistance).

#### Conclusion

The Automated Grading and Plagiarism Detection System streamlines assignment evaluation, ensures academic integrity, and integrates with existing LMS platforms for efficient grade management. The system also provides support mechanisms for students seeking help, enhancing the overall learning experience.

For further improvements, future iterations can integrate AI-based code quality analysis and adaptive grading techniques.


### Automated Grading and Plagiarism Detection System (IOD for combination of above Iod nd use case diagram)

#### Overview

This Interaction Overview Diagram (IOD) represents the workflow for automated grading and plagiarism detection, integrating elements from the assignment submission process and the use case diagram.

#### Key Processes:

#### Assignment Submission

Students push code to GitHub.

The professor retrieves and reviews the code.

If errors exist, manual testing determines grading.

#### Automated Grading & Plagiarism Check

Code is processed through an automated system.

Plagiarism detection is performed.

Results are stored and synchronized with the LMS.

#### Feedback & Auditing

Students receive grades and feedback.

Professors audit grades if necessary.

#### Student Assistance

Students can request help.

FAQ and reminders assist in resolving queries.

#### Actors:

- Student: Submits assignments, views grades, and requests assistance.

- Professor: Reviews submissions, audits grades, and sets criteria.

- Automated System: Grades assignments and detects plagiarism.

- LMS & Plagiarism Service: Stores grades and ensures integrity.

- Regulatory Body: Audits grading compliance.

This diagram streamlines the grading process, integrating automation and manual review while ensuring academic integrity.





































### Iod for University SWE Course Assignment

#### Overview

This document provides a description of the University Software Engineering (SWE) Course Assignment Workflow as depicted in the workflow diagram. The diagram illustrates the process a student follows to submit a programming assignment, the role of the professor in grading, and the possible outcomes of the submission.

#### Key Actions

Student Submission - The student submits the programming assignment.

Professor Review - The professor reviews the submission.

Automated and Manual Grading - The grading process includes automated and manual testing.

#### Participants

Student: Submits the assignment to a GitHub repository.

Professor: Reviews and grades the assignment.

Automated Grading System: Evaluates the submission based on predefined tests.

#### Workflow Description

###### Student Submission

The student pushes their code to a GitHub repository.

The professor is notified about the submission.

###### Grading Process

The professor receives the submission and runs an automated grading system.

The system evaluates the assignment based on:

- Compilation success

- Functional correctness

- Code quality

The system checks for similarities with previous submissions and online resources to detect plagiarism.

##### Review & Testing

The professor clones the repository and manually reviews the code in VSCode.

If the code works correctly, it is considered successful.

If the code has errors, manual testing is marked as failed.

###### Feedback & Results

The system generates a final report with grades and feedback.

The professor may provide additional comments or suggestions.

The final grades and feedback are sent to the student via email or updated on GitHub.

If no submission is made, the student receives a zero grade.

#### Possible Outcomes

Successful Submission: Code passes automated grading and manual review.

Failed Submission: Code contains errors and does not pass testing.

No Submission: The student does not submit the assignment and receives a zero grade.

#### Conclusion

This workflow ensures an efficient process for handling programming assignments in a university setting. It incorporates automated grading for efficiency, manual review for accuracy, and feedback mechanisms to help students improve their coding skills.


