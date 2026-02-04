# Lab 1 Report

## Task 1 — SSH Commit Signature Verification

### 1.1 Commit Signing Benefits

Commit signing verifies the author's identity using cryptographic signatures (GPG/SSH keys). It ensures:

1. Authenticity – Confirms the commit truly came from the claimed author.
2. Integrity – Guarantees the code hasn’t been altered after signing.
3. Non-repudiation – Authors cannot deny their contributions.

This prevents spoofed commits, enforces traceability, and is crucial in secure workflows (e.g., Linux kernel, regulated industries). Platforms like GitHub mark signed commits as "Verified."

### 1.2 SSH Key Setup Evidence

Configured `gpg.format` to `ssh` and linked my public key.

```
$ git config --list | grep -E "(signingkey|gpgsign|gpg.format)"
user.signingkey=/home/thallars/.ssh/id_ed25519.pub
commit.gpgsign=true
gpg.format=ssh
```

### 1.3 Commit Signing in DevOps workflows

In DevOps workflows where multiple team members collaborate on code, commit signing establishes trust and accountability. It prevents unauthorized changes, ensures code provenance, and is particularly crucial for compliance requirements in regulated industries. When automated deployments trigger from commits, knowing the commit source is authentic prevents malicious code injection.

### 1.4 Verified Commit Evidence

![](verified_commit.png)

## Task 2 — PR Template & Checklist

### 2.1 PR Template Evidence

![](pr_template.png)

![](template_location.png)

### 2.1 PR Template Benefits

PR templates improve collaboration by:

1. Standardization - Ensures all PRs contain necessary information

2. Efficiency - Reduces back-and-forth questions between developers and reviewers

3. Completeness - Checklist ensures common quality gates are addressed

4. Consistency - Creates predictable PR structure across the team

## Challenges

1. Initially had Authentication Key set-up on GitHub and tried to use it for signing, while separate keys are needed for authentication and signing.
