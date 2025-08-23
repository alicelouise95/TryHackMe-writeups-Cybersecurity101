### **TryHackMe: Cyber Security 101**

**Room:** `Digital Forensics Fundamentals`  
**Status:** Completed  
**Date:** 2025-08-22

----------

### **Goal**

To understand the fundamentals of digital forensics, including its processes, types, tools, and methods of evidence acquisition and analysis, with a focus on Windows systems and practical approaches such as imaging, metadata analysis, and forensic tool usage.

---------

### **Key Topics Covered**
### 1. Introduction to Digital Forensics

Digital forensics applies investigative methods to cyber crimes, which are criminal activities conducted on or through digital devices. The field involves analyzing devices such as computers, USBs, cameras, or mobile phones to uncover evidence that can be used in legal proceedings. My notes emphasized that the process must be careful and precise, ensuring no tampering occurs and all findings can stand up in court.

----------

### 2. NIST Process for Digital Forensics

The National Institute of Standards and Technology (NIST) defines a four-phase process for digital forensics:

1.  **Collection** – Identifying and gathering devices and data at a crime scene while ensuring original data integrity. Documentation of items collected is essential.
    
2.  **Examination** – Filtering large volumes of data to extract relevant information. For example, narrowing down media files by date or selecting data tied to a specific user account.
    
3.  **Analysis** – Correlating multiple pieces of evidence to reconstruct activities and establish timelines. This is where investigators piece together events relevant to the case.
    
4.  **Reporting** – Preparing a comprehensive report with methods, findings, and executive summaries. The report must be accessible to both technical investigators and non-technical stakeholders like management or law enforcement.
    

I found the step-by-step structure helpful in understanding how evidence moves from raw data to actionable legal material.

----------

### 3. Types of Digital Forensics

Different forms of digital forensics focus on distinct areas of investigation:

-   **Computer forensics** – Investigating desktops and laptops, the most common devices in crimes.
    
-   **Mobile forensics** – Extracting data such as texts, call records, and GPS locations from mobile devices.
    
-   **Network forensics** – Examining traffic logs and network activity across infrastructures.
    
-   **Database forensics** – Investigating unauthorized modifications or data theft from databases.
    
-   **Cloud forensics** – Handling evidence from cloud storage, which can be difficult due to limited direct access.
    
-   **Email forensics** – Investigating phishing or fraudulent campaigns via email evidence.
    

This categorization clarified how broad digital forensics is and showed that each branch demands specialized methods.

----------

### 4. Evidence Acquisition Principles

Collecting evidence securely is critical. My notes highlighted three important principles:

-   **Proper Authorization** – Investigators must have legal approval before collecting data, ensuring compliance with law and admissibility in court.
    
-   **Chain of Custody** – Maintaining a documented record of evidence handling, including details such as collection time, storage location, and every person who accessed it. This ensures accountability and prevents disputes over integrity.
    
-   **Use of Write Blockers** – Write blockers prevent changes when accessing suspect drives, such as unintentional timestamp alterations, preserving the original state of evidence.
    

These practices reinforced the importance of both technical and procedural safeguards in digital investigations.

----------

### 5. Windows Evidence Acquisition

Since Windows is a common target in investigations, my notes stressed the importance of collecting both:

-   **Disk Images** – Bit-by-bit copies of all non-volatile storage data (e.g., documents, browsing history).
    
-   **Memory Images** – Copies of volatile data in RAM, such as running processes, open files, and network connections. Because this data disappears when the system is powered off, it must be acquired first.
    

I found it useful to distinguish between volatile and non-volatile evidence, as this clarified why memory imaging is often prioritized.

----------

### 6. Forensic Tools

Several key tools were noted for disk and memory imaging, as well as analysis:

-   **FTK Imager** – A user-friendly tool for creating and analyzing disk images.
    
-   **Autopsy** – An open-source platform for disk image analysis, supporting keyword searches, deleted file recovery, and metadata checks.
    
-   **DumpIt** – A command-line tool for capturing Windows memory images.
    
-   **Volatility** – A versatile open-source framework for analyzing memory images with plugins across multiple operating systems.
    

My notes reflected the importance of choosing the right tool depending on the type of evidence and stage of the investigation.

----------

### 7. Photo EXIF Data

EXIF (Exchangeable Image File Format) metadata is embedded in images by cameras and smartphones. It can include:

-   Camera model
    
-   Date and time of capture
    
-   Photo settings (shutter speed, ISO, aperture, etc.)
    
-   GPS coordinates (when enabled)
    

This information can reveal not just the content of an image, but also contextual details such as the exact location and time it was taken. A tool highlighted in my notes was **ExifTool**, which can read and write this metadata from the command line.

----------

## What I Learned

-   Digital forensics follows a structured four-phase process (Collection, Examination, Analysis, Reporting).
    
-   Multiple branches of forensics exist, each focusing on different evidence sources (computers, networks, mobiles, etc.).
    
-   Evidence acquisition requires legal authorization, strict documentation (chain of custody), and protective tools like write blockers.
    
-   Windows investigations require both disk and memory imaging, with memory prioritized due to volatility.
    
-   Tools such as FTK Imager, Autopsy, DumpIt, and Volatility are essential for evidence acquisition and analysis.
    
-   EXIF metadata in photos can provide valuable contextual evidence such as time, device, and location.
