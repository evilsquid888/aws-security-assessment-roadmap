# 🔴 AWS Security Assessment Roadmap

A structured path from zero to professional-grade AWS security assessments. Built for pentesters, auditors, and security engineers.

> **Assessment-first mindset:** At every phase, practice writing findings. Even while learning foundations, document misconfigurations you discover as if they were real assessment findings — with evidence, risk rating, and remediation. This habit separates good assessors from great ones.

> 💡 **Interactive version:** Open [`index.html`](./index.html) in your browser for the full interactive experience with expandable phases, tabs, and clickable links.

---

## 📋 Table of Contents

- [Phase 1: Foundations (Weeks 1–4)](#phase-1-foundations-weeks-14)
- [Phase 2: IAM & Access Control (Weeks 5–8)](#phase-2-iam--access-control-weeks-58)
- [Phase 3: Assessment Tooling (Weeks 9–13)](#phase-3-assessment-tooling-weeks-913)
- [Phase 4: Attack Techniques (Weeks 14–19)](#phase-4-attack-techniques-weeks-1419)
- [Phase 5: Compliance & Frameworks (Weeks 20–23)](#phase-5-compliance--frameworks-weeks-2023)
- [Phase 6: Advanced & Specialization (Weeks 24–30+)](#phase-6-advanced--specialization-weeks-2430)
- [Suggested Weekly Habit](#-suggested-weekly-habit)
- [Hands-On Labs](#-hands-on-labs)
- [Certification Path](#-certification-path)

---

## Phase 1: Foundations (Weeks 1–4)

> Build your AWS & security baseline before touching assessment tools.

### AWS Core Services Deep Dive

IAM (policies, roles, trust policies, permission boundaries), VPC (subnets, NACLs, security groups, flow logs), S3 (bucket policies, ACLs, block public access), EC2 (metadata service v1/v2, user data, instance profiles), Lambda, RDS, KMS, CloudTrail, CloudWatch.

📖 [IAM Documentation](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html) · 📖 [VPC Security Guide](https://docs.aws.amazon.com/vpc/latest/userguide/security.html) · 📖 [S3 Security Best Practices](https://docs.aws.amazon.com/AmazonS3/latest/userguide/security-best-practices.html) · 📖 [EC2 Instance Metadata](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-metadata.html)

### Shared Responsibility Model

Understand exactly what AWS secures vs. what you secure. This is the foundation of every assessment finding you'll write.

📖 [AWS Shared Responsibility Model](https://aws.amazon.com/compliance/shared-responsibility-model/) · 📖 [Security Pillar Whitepaper](https://docs.aws.amazon.com/wellarchitected/latest/security-pillar/welcome.html)

### AWS CLI & SDK Proficiency

Master `aws configure`, profiles, `assume-role`, STS tokens. You'll live in the CLI during assessments. Practice: enumerate IAM users, list S3 buckets, describe security groups programmatically.

📖 [AWS CLI User Guide](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-welcome.html) · ⚙ [Boto3 Docs (Python SDK)](https://boto3.amazonaws.com/v1/documentation/api/latest/index.html) · 📖 [AWS STS Reference](https://docs.aws.amazon.com/STS/latest/APIReference/welcome.html)

### Networking & Identity Fundamentals

DNS (Route 53), load balancers, CloudFront, WAF basics. Understand how traffic flows through an AWS environment from ingress to workload.

📖 [AWS Networking Fundamentals](https://aws.amazon.com/getting-started/aws-networking-essentials/) · 📖 [Route 53 Developer Guide](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/Welcome.html) · 📖 [AWS WAF Documentation](https://docs.aws.amazon.com/waf/latest/developerguide/waf-chapter.html)

**Key Resources:** [AWS Certified Cloud Practitioner](https://aws.amazon.com/certification/certified-cloud-practitioner/) · [AWS Well-Architected Framework — Security Pillar](https://docs.aws.amazon.com/wellarchitected/latest/security-pillar/welcome.html) · [Stephane Maarek's AWS courses (Udemy)](https://www.udemy.com/user/stephane-maarek/)

---

## Phase 2: IAM & Access Control (Weeks 5–8)

> IAM misconfigurations are the #1 finding in AWS assessments. Go deep.

### IAM Policy Language Mastery

JSON policy structure, Effect/Action/Resource/Condition blocks. Understand NotAction vs Deny, wildcard abuse, policy evaluation logic (explicit deny > allow > implicit deny).

📖 [IAM Policy Reference](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies.html) · 📖 [Policy Evaluation Logic](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_evaluation-logic.html) · ⚙ [IAM Policy Simulator](https://policysim.aws.amazon.com/)

### Privilege Escalation Paths

Study Rhino Security Labs' 21+ IAM privesc techniques: `iam:CreatePolicyVersion`, `iam:AttachUserPolicy`, `iam:PutRolePolicy`, `sts:AssumeRole` chains, Lambda + IAM combos, PassRole abuse.

📖 [Rhino Security — IAM Privesc Methods](https://rhinosecuritylabs.com/aws/aws-privilege-escalation-methods-mitigation/) · ⚙ [PMapper — Privesc Graph Tool](https://github.com/nccgroup/PMapper) · ⚙ [Cloudsplaining](https://github.com/salesforce/cloudsplaining)

### Cross-Account Access & Federation

Role trust policies, external ID confusion, SAML/OIDC federation misconfigs, AWS Organizations SCPs. Assess if cross-account roles are overly permissive.

📖 [Cross-Account Access Guide](https://docs.aws.amazon.com/IAM/latest/UserGuide/tutorial_cross-account-with-roles.html) · 📖 [SCP Best Practices](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_scps.html) · 📖 [Confused Deputy Problem](https://docs.aws.amazon.com/IAM/latest/UserGuide/confused-deputy.html)

### Assessment Practice

Use IAM Access Analyzer, policy simulator, Cloudsplaining, Parliament, and PMapper to map and visualize privilege escalation graphs.

⚙ [IAM Access Analyzer](https://docs.aws.amazon.com/IAM/latest/UserGuide/what-is-access-analyzer.html) · ⚙ [Parliament — IAM Linter](https://github.com/duo-labs/parliament) · ⚙ [PMapper](https://github.com/nccgroup/PMapper) · ⚙ [Cloudsplaining](https://github.com/salesforce/cloudsplaining)

**Key Resources:** [Rhino Security Labs — AWS IAM Privilege Escalation](https://rhinosecuritylabs.com/aws/aws-privilege-escalation-methods-mitigation/) · [PMapper by NCC Group](https://github.com/nccgroup/PMapper) · [AWS IAM Access Analyzer documentation](https://docs.aws.amazon.com/IAM/latest/UserGuide/what-is-access-analyzer.html)

---

## Phase 3: Assessment Tooling (Weeks 9–13)

> Learn the tools that make up a professional AWS security assessment toolkit.

### Automated Scanners

Prowler (CIS benchmarks, PCI-DSS, HIPAA checks — run this first on every engagement). ScoutSuite (multi-cloud, great reporting). AWS Security Hub + Config Rules. Steampipe (SQL queries against AWS APIs).

⚙ [Prowler](https://github.com/prowler-cloud/prowler) · ⚙ [ScoutSuite](https://github.com/nccgroup/ScoutSuite) · ⚙ [Steampipe AWS Plugin](https://hub.steampipe.io/plugins/turbot/aws) · 📖 [AWS Security Hub](https://docs.aws.amazon.com/securityhub/latest/userguide/what-is-securityhub.html)

### Offensive / Red Team Tools

Pacu (AWS exploitation framework — practice every module). CloudFox (find attack paths). Enumerate-IAM (brute-force permissions). WeirdAAL. aws_consoler (convert keys to console access).

⚙ [Pacu](https://github.com/RhinoSecurityLabs/pacu) · ⚙ [CloudFox](https://github.com/BishopFox/cloudfox) · ⚙ [Enumerate-IAM](https://github.com/andresriancho/enumerate-iam) · ⚙ [WeirdAAL](https://github.com/carnal0wnage/weirdAAL)

### Reconnaissance & OSINT

Cloud_enum, S3Scanner, bucket-finder, MicroBurst concepts adapted for AWS, Shodan/Censys for exposed AWS assets, certificate transparency logs for subdomain discovery.

⚙ [cloud_enum](https://github.com/initstring/cloud_enum) · ⚙ [S3Scanner](https://github.com/sa7mon/S3Scanner) · ⚙ [Shodan](https://www.shodan.io/) · ⚙ [crt.sh (Cert Transparency)](https://crt.sh/)

### Custom Scripting

Write your own boto3 scripts for: enumerating all public resources, finding over-permissive security groups, checking encryption-at-rest across services, auditing CloudTrail gaps.

📖 [Boto3 Documentation](https://boto3.amazonaws.com/v1/documentation/api/latest/index.html) · ⚙ [AWS Security Automation Examples](https://github.com/awslabs/aws-security-automation) · 📖 [Prowler Custom Checks Guide](https://docs.prowler.com/projects/prowler-open-source/en/latest/)

**Key Resources:** [Prowler](https://github.com/prowler-cloud/prowler) · [Pacu by Rhino Security](https://github.com/RhinoSecurityLabs/pacu) · [CloudFox by BishopFox](https://github.com/BishopFox/cloudfox) · [Steampipe + AWS plugin](https://hub.steampipe.io/plugins/turbot/aws)

---

## Phase 4: Attack Techniques (Weeks 14–19)

> Understand real-world attack chains to assess like an attacker, not a checkbox auditor.

### Initial Access Vectors

Exposed credentials (GitHub leaks, .env files, EC2 metadata SSRF), public S3 buckets, misconfigured API Gateways, Lambda function URL abuse, Cognito misconfigs, overly permissive resource policies.

📖 [AWS Threat Technique Catalog — Initial Access](https://aws-samples.github.io/threat-technique-catalog-for-aws/Techniques/) · 📖 [Hacking The Cloud — Initial Access](https://hackingthe.cloud/aws/general-knowledge/intro_metadata_service/) · ⚙ [CloudGoat Scenarios](https://github.com/RhinoSecurityLabs/cloudgoat) · ⚙ [TruffleHog (Credential Scanner)](https://github.com/trufflesecurity/trufflehog)

### Post-Exploitation & Lateral Movement

Credential harvesting from metadata service, SSM parameter store, Secrets Manager. Role chaining through assume-role. Lambda pivot to VPC resources. ECS/EKS container escape scenarios.

📖 [AWS TTC — Lateral Movement](https://aws-samples.github.io/threat-technique-catalog-for-aws/matrix.html) · 📖 [Hacking The Cloud — Post Exploitation](https://hackingthe.cloud/aws/post_exploitation/intro/) · 📖 [MITRE ATT&CK — Cloud Lateral Movement](https://attack.mitre.org/tactics/TA0008/) · ⚙ [Pacu Post-Exploitation Modules](https://github.com/RhinoSecurityLabs/pacu/wiki)

### Persistence Mechanisms

Backdoor IAM users/roles, malicious Lambda layers, modified AMIs, EventBridge rules for callback, cross-account persistence, STS session token abuse.

📖 [AWS TTC — Persistence](https://aws-samples.github.io/threat-technique-catalog-for-aws/Techniques/) · 📖 [Hacking The Cloud — Persistence](https://hackingthe.cloud/aws/post_exploitation/intro/) · 📖 [MITRE ATT&CK — Cloud Persistence](https://attack.mitre.org/tactics/TA0003/) · 📖 [Daniel Grzelak — AWS Persistence Talk](https://www.youtube.com/watch?v=pSHHiQ3aYtE)

### Data Exfiltration Paths

S3 replication to attacker account, RDS snapshot sharing, EBS snapshot copy, DNS exfil via Route 53, VPC endpoint abuse, CloudFormation export values.

📖 [AWS TTC — Collection & Impact](https://aws-samples.github.io/threat-technique-catalog-for-aws/matrix.html) · 📖 [MITRE ATT&CK — Cloud Exfiltration](https://attack.mitre.org/tactics/TA0010/) · 📖 [Hacking The Cloud](https://hackingthe.cloud/) · ⚙ [Dufflebag — EBS Snapshot Scanner](https://github.com/BishopFox/dufflebag)

**Key Resources:** [AWS Threat Technique Catalog (TTC)](https://aws-samples.github.io/threat-technique-catalog-for-aws/) · [MITRE ATT&CK Cloud Matrix](https://attack.mitre.org/matrices/enterprise/cloud/) · [Hacking The Cloud](https://hackingthe.cloud/) · [CloudGoat by Rhino Security](https://github.com/RhinoSecurityLabs/cloudgoat) · [Flaws.cloud](http://flaws.cloud/)

---

## Phase 5: Compliance & Frameworks (Weeks 20–23)

> Map your findings to frameworks that clients and organizations care about.

### CIS AWS Foundations Benchmark

The gold standard for AWS assessments. Know every control across IAM, logging, monitoring, and networking sections. Prowler maps directly to CIS — understand what each check means.

📖 [CIS AWS Benchmark](https://www.cisecurity.org/benchmark/amazon_web_services) · ⚙ [Prowler CIS Checks](https://docs.prowler.com/projects/prowler-open-source/en/latest/) · ⚙ [CIS Controls Navigator](https://www.cisecurity.org/controls/cis-controls-navigator)

### AWS-Specific Compliance

SOC 2 control mapping to AWS services, PCI-DSS in AWS (cardholder data environments), HIPAA (PHI handling in S3/RDS/DynamoDB), FedRAMP (GovCloud considerations).

📖 [AWS Compliance Programs](https://aws.amazon.com/compliance/programs/) · ⚙ [AWS Artifact (Compliance Reports)](https://aws.amazon.com/artifact/) · 📖 [PCI DSS on AWS Guide](https://docs.aws.amazon.com/whitepapers/latest/pci-dss-scoping-on-aws/pci-dss-scoping-on-aws.html)

### Assessment Report Writing

Structure: Executive Summary → Methodology → Findings (severity-rated) → Remediation. Each finding needs: description, evidence (screenshots/CLI output), risk rating (CVSS or custom), business impact, remediation steps with AWS-specific commands.

📖 [OWASP Testing Guide — Reporting](https://owasp.org/www-project-web-security-testing-guide/) · ⚙ [CVSS Calculator](https://www.first.org/cvss/calculator/3.1) · ⚙ [PlexTrac (Report Platform)](https://plextrac.com/)

### Risk Rating & Prioritization

Contextualize severity: an admin IAM key exposed to the internet ≠ a read-only role in a dev sandbox. Factor in blast radius, data sensitivity, compensating controls, and exploitability.

📖 [NIST Risk Management Framework](https://csrc.nist.gov/projects/risk-management) · 📖 [OWASP Risk Rating Methodology](https://owasp.org/www-community/OWASP_Risk_Rating_Methodology)

**Key Resources:** [CIS Amazon Web Services Foundations Benchmark](https://www.cisecurity.org/benchmark/amazon_web_services) · [AWS Audit Manager](https://aws.amazon.com/audit-manager/) · [NIST 800-53 mapped to AWS services](https://docs.aws.amazon.com/audit-manager/latest/userguide/NIST800-53r5.html)

---

## Phase 6: Advanced & Specialization (Weeks 24–30+)

> Specialize in high-value assessment areas and build your professional edge.

### Container & Serverless Security Assessment

ECS/EKS security review: pod security policies, IRSA, network policies, image scanning (ECR). Lambda: function policies, environment variable secrets, layer supply chain, cold start timing attacks.

📖 [EKS Security Best Practices](https://aws.github.io/aws-eks-best-practices/security/docs/) · 📖 [Lambda Security Overview](https://docs.aws.amazon.com/lambda/latest/dg/lambda-security.html) · ⚙ [Trivy (Container Scanner)](https://github.com/aquasecurity/trivy) · ⚙ [kube-bench](https://github.com/aquasecurity/kube-bench)

### Infrastructure-as-Code Review

Assess CloudFormation, Terraform, CDK templates for security issues before deployment. Tools: Checkov, tfsec, cfn-nag, Semgrep for IaC. This is shift-left assessment work.

⚙ [Checkov](https://github.com/bridgecrewio/checkov) · ⚙ [tfsec](https://github.com/aquasecurity/tfsec) · ⚙ [cfn-nag](https://github.com/stelligent/cfn_nag) · ⚙ [Semgrep IaC Rules](https://semgrep.dev/)

### AI-Driven AppSec & AWS Security Agent

AWS Security Agent (pen testing GA March 2026) performs AI-driven design review, code review, and on-demand penetration testing against pre-production targets. The assessor's job is twofold: confirm it's scoped safely — ownership-validated endpoints, scoped credentials in Secrets Manager or a vendor Lambda, ≤5 concurrent runs, no CI/CD or SIEM integration yet — and document the compliance gap. AWS explicitly states it is "not a professional penetration testing service"; its stochastic findings don't satisfy PCI-DSS or SOC 2 manual pen test requirements. Practice the coverage assessment: run the agent against a vulnerable app (e.g. Juice Shop), diff its findings against a manual pen test, and articulate the residual gap — business logic flaws, complex authorization bypasses, and chained exploits that still require human testers.

📖 [AWS Security Agent User Guide](https://docs.aws.amazon.com/securityagent/latest/userguide/what-is.html) · 📖 [Security Considerations & Limitations](https://docs.aws.amazon.com/securityagent/latest/userguide/security-guidance.html) · 📖 [GA Announcement (March 2026)](https://aws.amazon.com/about-aws/whats-new/2026/03/aws-security-agent-ondemand-penetration/) · 📖 [Multi-Agent Architecture Deep Dive](https://aws.amazon.com/blogs/security/inside-aws-security-agent-a-multi-agent-architecture-for-automated-penetration-testing/)

### Incident Response & Detection Engineering

Assess detection coverage: are GuardDuty findings being actioned? Are CloudTrail logs centralized and tamper-proof? Is there alerting on root login, access key usage, or privilege escalation? Map findings to AWS TTC techniques. Review IR runbooks.

📖 [AWS Threat Technique Catalog](https://aws-samples.github.io/threat-technique-catalog-for-aws/) · 📖 [AWS GuardDuty](https://docs.aws.amazon.com/guardduty/latest/ug/what-is-guardduty.html) · ⚙ [AWS IR Playbook Samples](https://github.com/aws-samples/aws-incident-response-playbooks) · 📖 [CloudTrail Best Practices](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/best-practices-security.html) · ⚙ [Stratus Red Team](https://github.com/DataDog/stratus-red-team)

### Multi-Account & Organization Assessment

Assess AWS Organizations: SCP effectiveness, account segregation strategy, centralized logging (CloudTrail org trail), delegated admin patterns, Control Tower guardrails.

📖 [AWS Organizations Best Practices](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_best-practices.html) · 📖 [AWS Control Tower](https://docs.aws.amazon.com/controltower/latest/userguide/what-is-control-tower.html) · ⚙ [org-formation](https://github.com/org-formation/org-formation-cli)

**Key Resources:** [AWS Certified Security — Specialty](https://aws.amazon.com/certification/certified-security-specialty/) · [SANS SEC510: Cloud Security Controls](https://www.sans.org/cyber-security-courses/cloud-security-controls-mitigations/) · [fwd:cloudsec conference talks (YouTube)](https://www.youtube.com/@faborysec) · [tl;dr sec newsletter by Clint Gibler](https://tldrsec.com/)

---

## 🗓 Suggested Weekly Habit

Repeat this cycle every week while working through the phases above.

| Day | Focus | What to Do |
|-----|-------|------------|
| **Monday** | Read | Read an AWS security blog post or advisory |
| **Tuesday** | Lab | Hands-on lab (CloudGoat, Flaws.cloud, etc.) |
| **Wednesday** | Tools | Tool practice — run Prowler/Pacu/ScoutSuite against a test env |
| **Thursday** | Study | Study AWS Threat Technique Catalog + MITRE ATT&CK Cloud + a real breach case study |
| **Friday** | Write | Write mock findings / practice assessment reporting |
| **Weekend** | Explore | CTFs or deeper dive into a specific service |

**Key Principle:** The best cloud security assessors understand both the *builder's perspective* (how things are architected) and the *breaker's perspective* (how things get exploited). This weekly loop keeps you sharpening both sides.

---

## ⚡ Hands-On Labs

| Platform | Cost | Focus |
|----------|------|-------|
| [CloudGoat](https://github.com/RhinoSecurityLabs/cloudgoat) | Free | Offensive scenarios |
| [Flaws.cloud](http://flaws.cloud/) | Free | S3, EC2, IAM basics |
| [Flaws2.cloud](http://flaws2.cloud/) | Free | Attacker & defender path |
| [PentesterLab](https://pentesterlab.com/) | Paid | Cloud exploitation |
| [HackTricks Cloud](https://cloud.hacktricks.wiki/) | Free | Cheatsheets & techniques |
| [AWS Well-Architected Labs](https://www.wellarchitectedlabs.com/security/) | Free | Security pillar labs |
| [TryHackMe AWS Rooms](https://tryhackme.com/) | Freemium | Guided AWS hacking |
| [DVCA (Damn Vuln Cloud App)](https://github.com/m6a-UdS/dvca) | Free | Vulnerable-by-design |

---

## ◆ Certification Path

Prioritize in this order. Certifications validate knowledge but don't replace hands-on assessment experience.

| # | Certification | Stage | Difficulty |
|---|--------------|-------|------------|
| 1 | [AWS Cloud Practitioner](https://aws.amazon.com/certification/certified-cloud-practitioner/) | Foundation | ⬛ |
| 2 | [AWS Solutions Architect Associate](https://aws.amazon.com/certification/certified-solutions-architect-associate/) | Core | ⬛⬛ |
| 3 | [AWS Security Specialty](https://aws.amazon.com/certification/certified-security-specialty/) | Specialization | ⬛⬛⬛ |
| 4 | [CCSK (Cloud Security Alliance)](https://cloudsecurityalliance.org/education/ccsk) | Vendor-neutral | ⬛⬛ |
| 5 | [Offensive Security OSCP/OSWE](https://www.offsec.com/courses-and-certifications/) | Offensive Edge | ⬛⬛⬛⬛ |

---

## Contributing

Found a broken link, want to add a resource, or have a better lab recommendation? PRs welcome.

## License

MIT — use, share, and modify freely.
