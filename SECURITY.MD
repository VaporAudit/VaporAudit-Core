# **SECURITY.md: VaporAudit Proprietary Architecture and Fail-Dead Protocol**

## **1\. Security Mission and Fail-Dead Philosophy**

VaporAudit operates under a singular mandate: **Infrastructure Sovereignty**. In a landscape where state-level actors and advanced persistent threats (APTs) exercise Ring \-1 (hypervisor) and Ring \-2 (SMM) interdiction, traditional security postures are obsolete. Our architecture is built upon the "Zero Policy" doctrine. We do not rely on administrative promises or software-defined boundaries. Instead, we enforce protection through pure physics. Protecting sovereign data is a mechanical requirement, not a configuration preference.

The core of our posture is the **"Fail-Dead"** mandate. Traditional "Fail-Safe" models prioritize availability and graceful degradation, but in high-threat environments, software abstractions are inherently fallible and subject to compromise. "Fail-Dead" dictates that at the first detection of a sovereignty breach, the system must prioritize data destruction over availability. If data cannot be mathematically and physically verified as sovereign, it must cease to exist. This philosophy governs every layer of the VaporAudit stack, ensuring that protection is a matter of physical law, not trust.

**Proprietary Notice: The core VaporAudit architecture is proprietary and operates under a Fail-Dead mandate. Zero Policy. Pure Physics. Verified Certainty.**

This mission necessitates a total rejection of the "Shared Responsibility Model" in favor of a doctrine that assumes the host is actively adversarial.

## **2\. The Hostile Memory Environment (HME) Doctrine**

VaporAudit assumes the **Hostile Memory Environment (HME)**. We posit that the host operating system, the hypervisor, and the network fabric are compromised or susceptible to external coercion. In an HME, cleartext execution in RAM is the primary liability. Data is vulnerable to **"Silent Observer"** attacks (e.g., memory bus snooping and micro-architectural side-channels like Spectre/Meltdown) and **"Teleportation"** attacks (unauthorized live migration to non-sovereign jurisdictions while software dashboards continue to report a safe region).

To navigate the HME, we utilize the **Texture Map Protocol** to distinguish between verified sovereignty and inherent liability.

### **Standard Cloud Assumptions vs. VaporAudit HME Realities**

| Feature | Standard Cloud Assumption | VaporAudit HME Reality |
| :---- | :---- | :---- |
| **Infrastructure State** | Benevolent/Neutral | **Hostile (Ring \-1/Ring \-2 Interdiction)** |
| **Memory Security** | Isolated by Hypervisor | **Insecure (Quarantined State XXXX)** |
| **Data Residency** | Software "Region IDs" (Mutable) | \*\*Physics-Verified (Alibi Routing |
| **VM Migration** | "Live Migration" (Optimization) | **Banned (Teleportation Attack Vector XXXX)** |
| **Integrity Check** | Periodic Software Logs | \*\*Thermodynamic Lie Detector (Active Sonar |
| **Encryption State** | Software-Managed Keys | \*\*Hardware-Rooted (PSP-Managed Keys |

The remedy for HME is hardware-rooted cryptographic identity. By pinning our infrastructure to **AMD SEV-SNP (gdccs-g2)**, we ensure that memory encryption keys are managed exclusively by the on-die **Platform Security Processor (PSP)** and are never exposed to the hostile host.

## **3\. Core Enforcement Mechanisms: The Kinetic Defense**

"The Shield" is VaporAudit’s unified Kinetic Defense, comprising three interlocking mechanisms that enforce sovereignty through immutable constants and mechanical locks.

### **I. Hardware Pinning**

The **Master Auditor** engine serves as a binary gatekeeper for the sovereignty stack. It parses all Infrastructure-as-Code (IaC) definitions (Terraform) prior to instantiation. The Auditor enforces a strict mandate: if the `confidential_instance_config` is not correctly nested or if the `machine_type` deviates from **AMD SEV-SNP (gdccs-g2)** on Google Distributed Cloud Connected Secure platforms, the Auditor rejects the definition **in toto**. There are no warnings; non-compliant infrastructure is physically prevented from deploying.

### **II. Physics-Based Attestation (Alibi Routing)**

To eliminate the risk of "Teleportation Attacks," VaporAudit rejects all software-defined location metadata. We employ **Alibi Routing**, utilizing the speed of light in fiber (**200 km/ms**) as an immutable constant. The system calculates the physical distance to trusted **Alibi Nodes** (including the **US Naval Observatory**) by measuring Round-Trip Time (RTT). By calculating the intersection of three RTT radii, the system defines a **"Feasible Region."** If triangulation places the host outside of the continental United States, the system recognizes a sovereignty breach and triggers a Fail-Dead response.

### **III. The Legal Interlock Protocol**

The **Sanitization Interceptor** acts as a mechanical firewall for anti-spoliation compliance (FRCP 37(e)). When a `Litigation_Hold` state is active in the Single Source of Truth (SSOT), it becomes an **Immutable State** that overrides all administrative privileges. Any attempt to delete data—whether by a user, a rogue root admin, or an automated process—is intercepted and blocked. The system returns the hard-coded `PRESERVATION_LOCK_ACTIVE` error, ensuring mechanical compliance that cannot be bypassed by software reconfiguration.

## **4\. Integrity Verification via Micro-Code Sentry**

VaporAudit maintains **"Thermodynamic Integrity"** via the **Micro-Code Sentry**, a "Thermodynamic Lie Detector" that utilizes "Active Sonar" to detect sub-millisecond intrusions. We assume that any observation of a system (such as hypervisor introspection) consumes physical resources and creates detectable **"Friction"** or **"Time Dilation"** in the execution of the code.

### **The Micro-Code Sentry Loop**

The Sentry executes a deterministic monitoring loop with real-time scheduling priority (`SCHED_FIFO`):

1. **Start Timestamp:** Captures initial hardware cycles via the `_rdtsc` intrinsic.  
2. **Deterministic Workload:** Executes a fold operation (summing integers **0 to 1000**) sized to fit entirely within the **L1 Cache** to eliminate memory latency jitter.  
3. **End Timestamp:** Captures final hardware cycles.  
4. **Z-Score Calculation:** Compares the delta against a calibrated "Gold Master" baseline.

### **Analysis of the 3-Sigma Threshold**

The system enforces a **"3-Sigma"** threshold. A Z-Score **\> 3.0** constitutes a **"Thermodynamic Violation."** This statistical deviation provides probabilistic proof of an **"Energy Shadow"** created by an external observer (e.g., a hypervisor context-switching to snapshot memory). This detection of physical friction serves as the definitive trigger for Cryptographic Suicide.

## **5\. The Hermetic Panic: Cryptographic Suicide and Immediate Termination**

Upon detection of a Thermodynamic Violation, the system enters a **"Hermetic Panic."** This is the irreversible transition to a Fail-Dead state designed to win the race against the **"Snapshot Gap"**—the 1,000 to 20,000 cycle latency required for a hypervisor to execute a `VMEXIT` and lock memory.

### **Cryptographic Suicide**

The system invokes `trigger_cryptographic_suicide()`, utilizing the `ptr::write_volatile` intrinsic.

* **Anti-Forensic Wipe:** Standard writes can be optimized away by compilers via **Dead Store Elimination (DSE)**. The `volatile` qualifier forces the compiler to physically emit the store instruction to the hardware.  
* **The 0xFF Pattern:** Sensitive memory locations and session keys are overwritten with a high-entropy **0xFF** pattern, scorching the volatile memory and preventing forensic recovery through "Cold Boot" attacks.

### **Immediate Termination**

Following the wipe, the system executes `process::abort()`. Unlike a standard "Panic" or shutdown, an `abort` bypasses the language runtime's stack unwinding. By skipping destructors and "drop" traits, VaporAudit eliminates the **"Temporal Gap"** (5–50ms) that a compromised hypervisor could use to "hook" the shutdown process. The guest wins the OODA loop against the hypervisor's `VMEXIT` loop, ensuring the process ceases to exist before it can be captured.

## **6\. Vulnerability Disclosure and VDR Access Protocol**

VaporAudit engages with authorized security researchers and auditors under **"Sovereign Handshake"** protocols. Due to the proprietary and sensitive nature of the architecture, all disclosures must occur within the Virtual Data Room (VDR).

### **Reporting Directive**

All architectural reviews, findings, or disclosures must be submitted through the VDR. Unauthorized public disclosure of VaporAudit's proprietary architecture is a violation of our Zero-Liability doctrine.

**Access the VDR at: [https://sites.google.com/vaporaudit.us/vaporaudit/home](https://sites.google.com/vaporaudit.us/vaporaudit/home)**

### **Architectural Review Requests**

Requests for review are granted only under the **Sovereign Handshake**, utilizing **Shamir’s Secret Sharing** (M-of-N authorization) for access. VaporAudit is committed to verified certainty through pure physics, where data protection is not a matter of trust, but of physical law.

