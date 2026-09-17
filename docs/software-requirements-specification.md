# CVision AI
## Software Requirements Specification

**Version:** 0.1  
**Status:** Draft

---

## 1. Introduction

### 1.1 Purpose
    CVision AI is an AI-powered system designed to help job candidates evaluate how well their professional profile matches the requirements of a specific job opportunity.

    The system aims to reduce the time and uncertainty involved in manually comparing a resume against a job description by identifying relevant strengths, missing or partially satisfied requirements, and areas for professional improvement.

    Rather than providing only a compatibility score, CVision AI aims to produce an explainable assessment supported by evidence extracted from both the candidate's resume and the job description.

### 1.2 Scope
    The initial version of CVision AI will focus on individual job candidates who want to evaluate their resume against a specific job opportunity.

    The system will accept one resume in PDF format and one job description as input. It will analyze both sources to identify relevant qualifications, strengths, missing or partially satisfied requirements, and evidence supporting the assessment.

    The system will generate an explainable compatibility assessment intended to help candidates understand how their current professional profile aligns with the requirements stated in the job description.

    #### In Scope

    - Upload and validation of one resume in PDF format.
    - Input of one job description as plain text provided by the user.
    - Extraction of relevant information from the resume.
    - Identification of relevant requirements from the job description.
    - Comparison between the candidate profile and job requirements.
    - Identification of strengths, gaps, and partially satisfied requirements.
    - Generation of an explainable compatibility score.
    - Evidence supporting relevant analysis results.
    - Recommendations based on identified gaps.

    #### Out of Scope for the MVP

    - Analysis or ranking of multiple candidates.
    - Recruiter-specific workflows.
    - DOCX and other resume formats.
    - User accounts and authentication.
    - Integration with external recruitment platforms or Applicant Tracking Systems (ATS).
    - Automatic job applications.
    - Interview simulation.
    - Native mobile applications.
    - Automatic extraction of job descriptions from external URLs.
    - Job description file uploads.

### 1.3 Definitions and Terminology

        Candidate 
        The individual whose resume is being evaluated against a job description.

        Resume (CV) 
        A document containing information about a candidate's professional experience, education, skills, projects, and other relevant qualifications.

        Job Description (JD) 
        The text describing a job opportunity, including its responsibilities, qualifications, skills, experience, and other requirements.

        Job Requirement
        A qualification, skill, experience, or condition requested or preferred in the job description.

        Strength 
        A candidate qualification supported by evidence in the resume that is relevant to a requirement in the job description.

        Gap
        A job requirement for which sufficient supporting evidence cannot be identified in the candidate's resume.

        Partial Match 
        A job requirement that is supported by some evidence in the resume but is not fully satisfied based on the available information.

        Evidence
        Information extracted from the resume or job description that supports an analysis result.

        Match Score
        A numerical representation of the degree of alignment between the candidate's documented profile and the requirements identified in the job description.

        MVP (Minimum Viable Product)
        The smallest functional version of CVision AI that delivers the core candidate-to-job analysis.

## 2. Functional Requirements

 ### FR-001 — Resume Upload

The system shall allow the candidate to upload one resume in PDF format for analysis.

### FR-002 — Job Description Input

The system shall allow the candidate to provide one job description as plain text for analysis.

### FR-003 — Resume Validation

The system shall validate the uploaded resume before processing and reject files that are invalid, unsupported, corrupted, or otherwise not processable.

### FR-004 — Resume Text Extraction

The system shall extract processable textual content from the uploaded resume.

### FR-005 — Candidate Information Extraction

The system shall identify relevant candidate information from the resume, including skills, professional experience, education, and other qualifications relevant to the job analysis.

### FR-006 — Job Requirement Extraction

The system shall identify relevant requirements from the job description, including skills, experience, education, and other stated qualifications.

### FR-007 — Requirement Matching

The system shall compare the candidate's documented qualifications against the identified job requirements.

### FR-008 — Match Classification

The system shall classify relevant job requirements according to the degree of supporting evidence found in the resume, including matched, partially matched, and unsupported requirements.

### FR-009 — Evidence Generation

The system shall provide evidence from the resume and job description to support relevant matching results.

### FR-010 — Compatibility Score

The system shall generate an explainable compatibility score representing the degree of alignment between the candidate's documented profile and the identified job requirements.

### FR-011 — Strength and Gap Identification

The system shall identify relevant candidate strengths and gaps with respect to the analyzed job description.

### FR-012 — Candidate Recommendations

The system shall provide recommendations based on identified gaps and partially satisfied requirements without representing unsupported qualifications as facts.

### FR-013 — Error Handling

The system shall provide understandable error information when an analysis cannot be completed without causing the application to terminate unexpectedly.

---

## 3. Non-Functional Requirements

### NFR-001 — Performance

Under normal operating conditions, the system should complete a single candidate-job analysis within a defined acceptable response-time target.

### NFR-002 — Reliability

Invalid or unsupported input shall not cause the application to terminate unexpectedly.

### NFR-003 — Privacy

Resume content and extracted candidate information shall not be exposed to unauthorized users or publicly accessible by default.

### NFR-004 — Security

The system shall validate untrusted user input before processing and shall apply appropriate safeguards when handling uploaded documents.

### NFR-005 — Maintainability

The system shall be organized into modular components with clearly defined responsibilities to support testing, modification, and extension.

### NFR-006 — Testability

Core processing and matching components shall be designed so that their expected behavior can be verified through automated tests.

### NFR-007 — Usability

Analysis results and error messages shall be presented in language understandable to the intended user without requiring technical knowledge of the underlying AI system.

### NFR-008 — Explainability

Relevant matching results shall be traceable to supporting information from the resume, the job description, or explicitly identified system inference.

### NFR-009 — Extensibility

The system architecture shall allow additional input formats, analysis capabilities, and user workflows to be introduced without requiring a complete redesign of the core analysis pipeline.

