# Linux Mobile Environment Recovery & Configuration

## Project Description
A practical systems administration and support log detailing how I diagnosed, debugged, and restored a broken mobile Linux workspace. This project highlights root-cause analysis, package manager troubleshooting, and permission control in restricted environments.

---

## Tools and Technologies Used
* **Hardware:** Tecno Spark 7 Mobile Device
* **Operating Environment:** Android Linux Terminal (Termux with `proot-distro` / Ubuntu distribution)
* **Version Control & Hosting:** Git & GitHub (`benji-infosec`)
* **Core Utilities & Package Managers:** `apt` package manager (`apt clean`, `apt update --fix-missing`), shell scripting, and file storage permission controls (`termux-setup-storage`)

---

## The Problem
While setting up my mobile development workspace, I ran into frustrating package installation blocks (`E: Unable to locate package`) and permission errors. Every time I tried updating the software repositories or accessing internal device storage to run my scripts, the terminal threw errors and blocked my setup workflow.

---

## How I Diagnosed It
1. **Checked the Symptoms:** Ran standard update commands (`apt update`), which kept timing out or throwing broken mirror errors. Script executions failed with `Permission Denied` because the container couldn't properly reach the shared storage paths.
2. **Inspected Configs:** Looked into `/etc/apt/sources.list` and tested network connections to see if the issue was a dead mirror or local routing.
3. **Found the Root Cause:** The mobile container's internal storage links had broken, and local package caches were left messy from previous interrupted syncs.

---

## Step-by-Step Implementation
1. **Cache Clean & Mirror Refresh:**
   * Cleared out broken lists:
     ```bash
     apt clean
     ```
   * Forced a clean repository index update:
     ```bash
     apt update --fix-missing
     ```
2. **Storage Binding Reconfiguration:**
   * Re-linked internal storage access for the terminal environment:
     ```bash
     termux-setup-storage
     ```
   * Checked and corrected read/write execution permissions across project folders.
3. **Verification & Testing:**
   * Reinstalled my developer tools and verified that everything installed smoothly without errors. Tested cloning repos and running a local server to confirm it was fully operational.

---

## What I Learned
* Gained deeper hands-on experience handling package dependency conflicts using the `apt` package manager.
* Mastered internal storage path linking and permission boundaries within containerized Linux environments (Termux / proot).
* Strengthened my technical documentation skills by breaking down complex debugging steps into clear, reproducible instructions.

---

## Result
Got my entire mobile Linux workspace running smoothly again with zero data loss. This whole process helped sharpen my practical debugging and permissions management skills inside restricted Linux environments.
