# Keycloak Audit Skill

Enterprise-grade Keycloak integration auditing skill for modern applications.
Works with Cursor, Claude, and other AI assistants that support skill-style instructions.

## What This Skill Does

`keycloak-audit` reviews your codebase to evaluate how Keycloak is integrated and secured.
It performs a structured IAM/security audit and returns a strict JSON report.

The audit includes:

- Keycloak usage detection
- Architecture detection (SPA, backend API, monolith, microservices, BFF)
- Rule-based security review from `rules.json`
- Numerical security score from `scoring.json` (0-100)
- Actionable findings with severity and recommendations

## Who This Is For

Use this skill if you:

- Integrate Keycloak in frontend, backend, or full-stack projects
- Want a fast security review before release
- Need consistent audit output for CI, QA, or security checks

## How To Use

From your project workspace, ask your assistant to run the skill:

`Run keycloak-audit`

The skill will then:

1. Detect whether Keycloak is present
2. Identify project architecture
3. Apply security rules strictly
4. Calculate a final security score
5. Return a machine-readable JSON report

## Output Format

The result is always strict JSON, similar to:

```json
{
  "project_type": "full-stack",
  "architecture": "SPA + Backend API",
  "keycloak_detected": true,
  "score": 82,
  "issues": [
    {
      "rule_id": "KC-004",
      "severity": "high",
      "file": "src/auth/keycloak.ts",
      "description": "Access token is stored in localStorage.",
      "recommendation": "Use secure HTTP-only cookies or in-memory strategy."
    }
  ],
  "strengths": [
    "PKCE enabled for public client"
  ],
  "summary": "Keycloak is integrated correctly but token storage and logout flow need hardening."
}
```

## Notes

- If Keycloak is not detected, the skill returns a minimal JSON response and stops analysis.
- The audit is intentionally strict and designed for enterprise security expectations.

## Version

`v0.1.0`