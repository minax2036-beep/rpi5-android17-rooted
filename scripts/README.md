# Project scripts

This directory is reserved for small, reviewed helper scripts for source checks, build setup, artifact checksums, and validation.

Guidelines:

- Prefer scripts that are safe to rerun.
- Explain required arguments and side effects in each script.
- Do not hard-code credentials, personal paths, or device-specific destructive commands.
- Never automate flashing until the target and recovery path are verified.
- Test scripts on the intended host OS and record the result.

No executable build or flashing scripts are provided yet.
