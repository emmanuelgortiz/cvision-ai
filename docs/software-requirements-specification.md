# CVision AI
## Software Requirements Specification

**Version:** 0.1  
**Status:** Draft  
**Product Mode:** Candidate Mode  
**Initial Language:** English  

---

## 1. Introduction

### 1.1 Purpose

CVision AI is an AI-assisted system designed to help job candidates evaluate how well their documented professional profile aligns with the requirements of a specific job opportunity.

The system aims to reduce the time and uncertainty involved in manually comparing a resume against a job description by identifying relevant strengths, partially satisfied requirements, unsupported requirements, and areas for professional improvement.

CVision AI shall produce an explainable assessment supported by evidence extracted from the candidate's resume and the job description.

The system shall not treat the absence of evidence in a resume as proof that the candidate does not possess a qualification.

---

### 1.2 Scope

The initial version of CVision AI focuses on individual job candidates who want to evaluate one resume against one specific job opportunity.

The MVP accepts:

- One resume in PDF format.
- One job description provided as plain text.

The MVP analyzes:

- Skills.
- Professional experience.
- Education.
- Work authorization or eligibility when explicitly stated.

The system produces:

- Matched requirements.
- Partial matches.
- Requirements for which no supporting evidence was found.
- Requirements that cannot be reliably evaluated.
- Supporting evidence.
- Candidate strengths.
- Relevant gaps.
- Recommendations.
- An explainable compatibility score.

#### In Scope

- Upload and validation of one resume in PDF format.
- Processing of PDFs containing extractable text.
- Acceptance of partially processable PDFs when sufficient text remains available.
- Warning the user when parts of a PDF could not be processed.
- Input of one job description as plain text.
- Extraction of relevant candidate information.
- Extraction of relevant job requirements.
- Comparison between candidate evidence and job requirements.
- Classification of requirement-level matches.
- Evidence-backed analysis.
- Explainable compatibility scoring.
- Candidate-oriented recommendations.
- Understandable error handling.
- Initial support for English-language resumes and job descriptions.
- Local CLI-based interaction for the first implementation.

#### Out of Scope for the MVP

- OCR for image-only or scanned resumes.
- DOCX or other resume formats.
- Analysis or ranking of multiple candidates.
- Recruiter-specific workflows.
- User accounts or authentication.
- Persistent candidate databases.
- Integration with Applicant Tracking Systems.
- Automatic job applications.
- Automatic extraction of job descriptions from URLs.
- Job description file uploads.
- Native mobile applications.
- Multilingual analysis.
- Automatic storage of personal candidate information.
- Cloud deployment requirements.
- External LLM or AI API dependency as a mandatory MVP requirement.

---

### 1.3 Definitions and Terminology

**Candidate**  
The individual whose resume is being evaluated against a job description.

**Resume (CV)**  
A document containing information about a candidate's professional experience, education, skills, projects, and other relevant qualifications.

**Job Description (JD)**  
Text describing a job opportunity, including responsibilities, qualifications, skills, experience, and other requirements.

**Job Requirement**  
A skill, qualification, experience level, education requirement, work-authorization condition, or other explicitly stated condition associated with the job.

**Evidence**  
Information contained in the resume or job description that supports an analysis result.

**Match**  
A job requirement for which the resume contains sufficient supporting evidence to reasonably conclude that the documented candidate profile satisfies the requirement.

**Partial Match**  
A job requirement for which relevant supporting evidence exists, but the available evidence is insufficient to conclude that the requirement is fully satisfied.

**No Evidence**  
A job requirement for which no relevant supporting evidence can be identified in the resume.

No Evidence shall not be interpreted as proof that the candidate does not possess the corresponding qualification.

**Not Evaluable**  
A job requirement for which the system cannot make a reliable assessment from the available information.

**Strength**  
A relevant candidate qualification supported by evidence in the resume and aligned with one or more job requirements.

**Gap**  
A job requirement that is not sufficiently supported by the available resume evidence.

A gap describes the relationship between the documented resume and the job requirement, not necessarily the candidate's actual abilities.

**Compatibility Score**  
A numerical representation of the degree of documented alignment between the resume and the evaluated job requirements.

The compatibility score shall not represent:

- Probability of receiving an interview.
- Probability of being hired.
- Overall candidate quality.
- Personal suitability for the job.

**MVP (Minimum Viable Product)**  
The smallest functional version of CVision AI that delivers the core candidate-to-job analysis.

---

## 2. Functional Requirements

### FR-001 — Resume Input

The system shall allow the candidate to provide one resume in PDF format for analysis.

### FR-002 — Job Description Input

The system shall allow the candidate to provide one job description as plain text.

### FR-003 — Resume Validation

The system shall validate the uploaded resume before analysis.

The system shall reject a resume when:

- The file is not a supported PDF.
- The file cannot be opened.
- The file is encrypted or otherwise inaccessible.
- No extractable textual content can be obtained.

### FR-004 — Partial PDF Processing

If some PDF pages contain extractable text and other pages cannot be processed, the system may continue the analysis using the available content.

The system shall clearly indicate that the analysis was performed using incomplete document content.

Unprocessed pages shall not be treated as negative evidence about the candidate.

### FR-005 — Resume Text Extraction

The system shall extract processable textual content from the resume.

### FR-006 — Candidate Information Extraction

The system shall identify relevant candidate information, including:

- Skills.
- Professional experience.
- Education.
- Work authorization or eligibility when explicitly documented.

### FR-007 — Job Requirement Extraction

The system shall identify relevant job requirements, including:

- Required or preferred skills.
- Experience requirements.
- Education requirements.
- Work authorization or eligibility requirements when stated.

### FR-008 — Requirement Matching

The system shall compare identified job requirements against evidence found in the resume.

### FR-009 — Match Classification

The system shall classify each evaluated requirement as one of:

- Match.
- Partial Match.
- No Evidence.
- Not Evaluable.

### FR-010 — Evidence Association

For relevant analysis results, the system shall associate the conclusion with supporting evidence from the resume and/or job description.

### FR-011 — Provenance

When technically available, the system shall preserve sufficient source information to determine where relevant evidence originated.

### FR-012 — Strength Identification

The system shall identify relevant candidate strengths supported by resume evidence.

### FR-013 — Gap Identification

The system shall identify requirements that are partially supported, unsupported, or not evaluable from the available resume evidence.

### FR-014 — Compatibility Score

The system shall generate a compatibility score representing documented alignment between the candidate profile and the evaluated job requirements.

The score shall be explainable through the underlying requirement-level analysis.

### FR-015 — Recommendations

The system shall provide candidate-oriented recommendations based on:

- Partial matches.
- Requirements with insufficient evidence.
- Relevant weaknesses in how qualifications are demonstrated.

Recommendations shall not instruct the candidate to claim qualifications that are not supported by their actual experience.

### FR-016 — Unsupported Inference Protection

The system shall not present unsupported assumptions about a candidate as confirmed facts.

### FR-017 — Insufficient Information Handling

The system shall indicate when insufficient information prevents a reliable assessment of a requirement.

### FR-018 — Error Handling

The system shall provide understandable error messages when processing cannot be completed.

A processing failure shall not cause the application to terminate unexpectedly when the error can be handled safely.

### FR-019 — Language Handling

The MVP shall support English-language resumes and job descriptions.

When the system determines that the input cannot be reliably processed under the supported language scope, it shall inform the user rather than silently presenting the analysis as fully reliable.

---

## 3. Non-Functional Requirements

### NFR-001 — Explainability

Relevant analysis results shall be traceable to supporting evidence or explicitly identified as uncertain or not evaluable.

### NFR-002 — Reliability

Invalid, unsupported, or partially processable input shall be handled without causing uncontrolled application failure.

### NFR-003 — Privacy

Resume content and extracted candidate information shall not be publicly exposed by default.

The initial implementation shall prioritize local processing.

### NFR-004 — Data Minimization

The MVP shall avoid persistent storage of personal candidate information unless storage becomes necessary for an explicitly introduced feature.

### NFR-005 — Security

User-provided files and text shall be treated as untrusted input and validated before processing.

### NFR-006 — Maintainability

The system shall be organized into components with clearly defined responsibilities.

### NFR-007 — Testability

Core validation, extraction, matching, and scoring behavior shall be designed so that it can be verified through automated tests.

### NFR-008 — Extensibility

The architecture should allow future capabilities such as OCR, APIs, alternative document formats, recruiter workflows, and additional analysis methods without requiring a complete rewrite of the core domain logic.

### NFR-009 — Interface Independence

Core analysis logic shall not depend directly on the CLI interface.

### NFR-010 — Usability

Results and error messages shall be understandable to a job candidate without requiring knowledge of the underlying AI or implementation details.

### NFR-011 — Performance

The system shall provide acceptable response time for interactive analysis of one resume and one job description.

A numerical performance target shall be established after implementation measurements provide evidence for a realistic threshold.

### NFR-012 — Reproducibility

Given the same supported input and deterministic processing configuration, deterministic components of the system should produce consistent results.

---

## 4. Use Cases

### UC-001 — Provide Resume

**Primary Actor:** Candidate

**Goal:**  
Provide a resume for analysis.

**Preconditions:**

- The application is available.
- The candidate has access to a resume file.

**Main Flow:**

1. The candidate selects one PDF resume.
2. The system receives the document.
3. The system validates the PDF.
4. The system determines whether extractable textual content is available.
5. The system accepts the resume for analysis.

**Alternative / Error Flows:**

- Unsupported file format → reject input.
- Corrupted PDF → reject input.
- Encrypted or inaccessible PDF → reject input.
- No extractable text → reject input and explain that OCR is not supported in the MVP.
- Partial text extraction → continue with a warning if sufficient content remains.

**Postconditions:**

- A processable resume is available for analysis, or the user has received an understandable error.

---

### UC-002 — Provide Job Description

**Primary Actor:** Candidate

**Goal:**  
Provide the target job description.

**Preconditions:**

- The application is available.

**Main Flow:**

1. The candidate provides the job description as plain text.
2. The system validates that usable content exists.
3. The system accepts the text for analysis.

**Alternative / Error Flows:**

- Empty or unusable input → reject input and explain the problem.

**Postconditions:**

- A processable job description is available.

---

### UC-003 — Analyze Candidate-Job Alignment

**Primary Actor:** Candidate

**Goal:**  
Evaluate documented alignment between the resume and job requirements.

**Preconditions:**

- A valid resume is available.
- A valid job description is available.

**Main Flow:**

1. The system extracts relevant resume information.
2. The system extracts relevant job requirements.
3. The system evaluates each supported requirement category.
4. The system associates available evidence.
5. The system classifies each evaluated requirement.
6. The system determines relevant strengths and gaps.
7. The system calculates the compatibility score.
8. The system produces recommendations.
9. The system prepares an explainable result.

**Alternative / Error Flows:**

- Insufficient resume evidence → affected requirements may be classified as No Evidence or Not Evaluable.
- Insufficient job-description information → affected requirements may be marked Not Evaluable.
- Partial PDF extraction → analysis continues with an explicit limitation warning.
- Processing failure → incomplete output shall not be presented as a fully valid analysis.

**Postconditions:**

- An analysis result exists or the user receives an explanation of why a reliable analysis could not be completed.

---

### UC-004 — Review Analysis Results

**Primary Actor:** Candidate

**Goal:**  
Understand how the documented candidate profile aligns with the selected job opportunity.

**Preconditions:**

- Analysis has completed successfully or with explicitly reported limitations.

**Main Flow:**

1. The candidate reviews the compatibility score.
2. The candidate reviews matched requirements.
3. The candidate reviews partial matches.
4. The candidate reviews requirements with no identified evidence.
5. The candidate reviews requirements marked Not Evaluable.
6. The candidate reviews supporting evidence.
7. The candidate reviews recommendations.
8. The candidate reviews any processing limitations or warnings.

**Postconditions:**

- The candidate can understand both the analysis conclusions and the evidence or uncertainty supporting them.

---

### UC-005 — Handle Invalid Input

**Primary Actor:** Candidate

**Goal:**  
Receive clear feedback when unsupported or unusable input is provided.

**Main Flow:**

1. The system detects invalid or unsupported input.
2. Processing of that input is stopped.
3. The system provides an understandable explanation.
4. The application remains available for another attempt.

**Postconditions:**

- Invalid input has not been interpreted as valid candidate data.
- The application remains operational.

---

## 5. Acceptance Criteria

The MVP shall be considered functionally acceptable when the following conditions are satisfied.

### AC-001 — Valid Resume

Given a valid text-based PDF resume, when the candidate provides the document, then CVision AI shall extract usable textual content.

### AC-002 — Invalid Resume Format

Given an unsupported file format, when the candidate attempts to provide it as a resume, then the system shall reject it with an understandable message.

### AC-003 — Image-Only Resume

Given a PDF containing no extractable text, when the system attempts to process it, then the PDF shall be rejected and the user shall be informed that OCR is outside the MVP.

### AC-004 — Partially Processable Resume

Given a PDF containing both processable and non-processable pages, when sufficient text remains available, then the system may continue the analysis and shall display a limitation warning.

### AC-005 — Job Description

Given non-empty supported English job-description text, the system shall accept the content for analysis.

### AC-006 — Requirement Extraction

Given a supported job description containing relevant skills, experience, education, or work-authorization requirements, the system shall identify applicable requirements for evaluation.

### AC-007 — Match Classification

For each evaluated requirement, the system shall produce one supported classification:

- Match.
- Partial Match.
- No Evidence.
- Not Evaluable.

### AC-008 — Evidence

Relevant Match and Partial Match conclusions shall include supporting evidence when such evidence is available.

### AC-009 — No Evidence Semantics

When no evidence for a requirement is identified in the resume, the system shall not state that the candidate definitively lacks the corresponding qualification.

### AC-010 — Unsupported Claims

The system shall not present unsupported candidate qualifications as confirmed facts.

### AC-011 — Explainable Score

The compatibility score shall be traceable to the evaluated requirements and shall not be presented as a probability of being interviewed or hired.

### AC-012 — Recommendations

Recommendations shall relate to identified gaps, partial matches, or insufficiently demonstrated qualifications and shall not encourage fabrication of experience.

### AC-013 — Error Resilience

Expected invalid-input conditions shall not cause uncontrolled application termination.

### AC-014 — Privacy

The initial MVP shall not require persistent storage of real candidate resume content to perform a single local analysis.

### AC-015 — Core / Interface Separation

Core analysis behavior shall be usable independently of the CLI implementation.

---

## 6. MVP Limitations

The initial MVP intentionally accepts the following limitations:

- PDF resumes only.
- Extractable-text PDFs only.
- OCR is not supported.
- English language only.
- Single candidate analysis only.
- Single job description only.
- Local CLI interaction.
- No persistent candidate database.
- No recruiter ranking.
- No job-board scraping.
- No guaranteed analysis of information that is absent, ambiguous, or inaccessible.
- No claim that the compatibility score predicts hiring outcomes.

These limitations may be revisited in future versions based on product needs and evaluation results.