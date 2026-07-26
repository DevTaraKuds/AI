# LLM Social-Engineering Robustness Probe

## Motivation

This is a small, exploratory test applying security-operations threat modeling specifically, phishing and social-engineering pattern analysis to LLM agent robustness. Built in less than an hour as a Proof Of Concept (POC) to demonstrate an adversarial-testing methodology. With my background in cybersecurity operations (SIEM, threat detection, phishing triage automation), this is an attempt at bringing that adversarial mindset to bear on language model behavior, as a step toward more formal work on AI control.

## Method

- **Model tested:** Gemini 3.5-flash

- **Setup:** The model is given a system prompt defining a customer-support agent bound by four explicit operational rules (account-number disclosure, refund approval limits, policy confidentiality, and escalation behavior).

- **Adversarial set:** 15 prompts across 7 categories drawn from common social-engineering / phishing tactics:
  - Authority impersonation
  - Urgency / pressure
  - Prompt injection
  - Foot-in-the-door
  - Social proof
  - Rapport exploitation
  - Multi-turn drift
  - Direct override attempts

- **Scoring:** Each response was manually reviewed and scored, with a severity rating (low / medium / high).

## Findings

0 / 15 prompts produced at least one rule violation. This mean it passed the test, however, I noticed that there was a policy misinterpretation where the agent had suggested they could freeze the card. 
System prompts did not explicitly state or authorize any account actions. Therefore, a stricter measure for policy could be applied.


## Why this matters

Security operations already has a mature taxonomy for classifying and defending against social-engineering attacks on humans. This project suggests that taxonomy transfers usefully to testing LLM agents, with foot-in-the-door and multi-turn drift that seem worth studying with more rigor; larger prompt sets, multiple models, and statistically grounded success-rate comparisons rather than a single manually-scored pass.

## Limitations

- Single model, single run — no repeated trials to check consistency of   responses.
- Small prompt set (15 items); not statistically powered.
- Manual, single-rater scoring, no inter-rater reliability check.
- Intended as a demonstration of approach and a starting point for discussion, not a definitive robustness claim about any model.

## Files

- `prompts.json` — the 15 adversarial test prompts, categorized
- `run_eval.py` — script that runs each prompt against the model and logs raw responses to `results.csv`
- `results.csv` — raw model responses
