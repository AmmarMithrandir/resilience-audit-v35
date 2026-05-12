# resilience-audit-v35
A technical post-mortem on deploying sandboxed security tools (ScoutSuite) within a degraded Rocky Linux environment.
I. Abstract: The Cinderblock Impasse
A documentation of "Systemic Resolve" during a critical firmware transition. This case study explores the friction between rigid laboratory parameters and real-world repository corruption (VS Code GPG key mismatches and broken dependency paths).

II. Technical Audit & Conflict Resolution
The Environment: Rocky Linux 01 (Virtual Node).

The Incident: Repository drift in /etc/yum.repos.d/ preventing the installation of python3-virtualenv.

The Solution (The Sandbox Model): 1.  Metadata Purge: Executed dnf clean all to bypass corrupted GPG keys.
2.  Environment Isolation: Forced the creation of a clean venv at /home/rocky/scoutsuite to satisfy strict administrative proctoring.
3.  Dependency Injection: Manual activation of the bin/activate gate to install ScoutSuite via pip within the sandbox, preventing "Global System Stains."

III. Key Commands for Reproducibility
Bash
# Establishing the Technical Anchor
python3 -m venv /home/rocky/scoutsuite
source /home/rocky/scoutsuite/bin/activate
pip install scoutsuite
scoutsuite --help
