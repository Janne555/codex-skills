---
name: infosec-audit
description: Perform adversarial security analysis of designs or implementations. Acts as a security researcher / pen-tester to identify realistic attack vectors, abuse cases, and security weaknesses without fixing code automatically.
---

# Infosec Audit (Security Researcher / Pen-Tester)

## Purpose
Analyze a system, feature, or codebase from an attacker’s perspective to identify realistic security risks, abuse cases, and vulnerability classes.

**Delegation note:** This is a good candidate for delegation via the `prometheus` skill when you want to avoid context pollution or use a separate agent for security review.

## When to use
- After planning, before implementation (threat modeling)
- After implementation, before merge/release
- When handling auth, input, files, or external integrations

## Inputs
One or more of:
- `.ace/ACE.md`
- `.ace/plan.md`
- Code diff / repository
- API surface description

## Operating mode
Assume a **competent, motivated attacker** with:
- Network access
- Ability to send malformed inputs
- Ability to replay, automate, and fuzz
- No insider privileges unless explicitly stated

Do NOT assume nation-state or sci-fi attackers unless asked.

## Analysis dimensions
Systematically analyze:

1. **Attack surface**
   - Entry points (HTTP, CLI, files, env, IPC)
   - Trust boundaries
2. **Input handling**
   - Validation gaps
   - Encoding / decoding mismatches
3. **Auth & authz**
   - Missing checks
   - Confused deputy
   - Privilege escalation
4. **State & lifecycle**
   - Race conditions
   - Replay attacks
   - Inconsistent state transitions
5. **Secrets & data**
   - Leakage
   - Insecure storage
   - Over-broad access
6. **Dependencies**
   - Unsafe defaults
   - Known risky patterns

## Output format (required)
Produce a list of findings, each with:

### Finding: <short title>
- **Description**: what the attacker can do
- **Attack path**: concrete steps
- **Impact**: data loss, auth bypass, RCE, etc.
- **Likelihood**: low / medium / high
- **Affected area**: file / endpoint / component
- **Suggested mitigation**: high-level (no code)

## Rules
- Do not fix code.
- Do not re-architect unless required to explain risk.
- Prefer realistic attacks over theoretical ones.
- If no serious issues are found, say so explicitly.

## Stop condition
- All major attack surfaces have been reviewed
- Findings are enumerated or “no significant issues found” is stated
