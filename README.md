# Sideloading-well_known_domains.dll  Microsoft Edge.

This technique leverages DLL search order hijacking by placing a malicious well_known_domains.dll in a user-writable directory that is loaded by a trusted Microsoft-signed binary—specifically, Microsoft Edge.

Steps to Reproduce:

Copy the malicious well_known_domains.dll to:

C:\Users\USERNAME\AppData\Local\Microsoft\Edge\User Data\Well Known Domains\1.x.x.x

Launch or close Microsoft Edge. The browser will attempt to load the DLL from this path, executing the payload.

Technical Details:

The folder C:\Users\USERNAME\AppData\Local\Microsoft\Edge\User Data\Well Known Domains\1.2.0.0 is user-writable.
Microsoft Edge implicitly trusts and loads the well_known_domains.dll from this location without validating its integrity or source.
This enables execution of arbitrary code under the context of a trusted Microsoft binary, which may aid in evading application control or endpoint defenses.
