# AI Governance & Risk Fundamentals (Practitioner Distillation)

A foundational primer on AI technology, terminology, and risk — the vocabulary and mental
models needed to reason about AI compliance. It underpins the AI-specific rule sets in
`rules/global_standards/iso_42001.json` and `rules/global_standards/ai_risk_lifecycle.json`
and complements the regional AI-law rules in `rules/`.

## 1. Why terminology matters

You cannot evaluate AI risk or compliance without a shared vocabulary to communicate with
vendors, internal development teams, and users. Definitions are not academic: **whether a
system counts as "AI" often dictates whether it is regulated** and which risks (including
compliance risks) attach. Companies have faced false-advertising and unfair-trade-practice
actions both for falsely claiming to use AI and for overblown, unsubstantiated claims about
what their AI could do.

- **OECD definition (widely adopted):** an AI system *infers, from the input it receives,
  how to generate outputs* — predictions, content, recommendations, or decisions — and can
  vary in its level of autonomy. In practice **all AI systems make predictions**;
  generative AI predicts the next word/sentence.
- **A prediction becomes a decision when action is taken on it** — a loan approved or
  denied, an offer made to prevent churn. This transition is where compliance risk
  crystallizes.
- Edge cases genuinely debated: simple pattern recognition over huge datasets (the Colorado
  AI Act *excludes* cybersecurity from "high-risk" partly for this reason), and robotic
  process automation with *no learning component*. It is generally agreed that AI systems
  are **learning systems**.

## 2. AI is a socio-technical system

AI is software and data — another technology for achieving objectives via people, process,
and technology — but with unique security, privacy, reputational, and compliance risks. It
is best described as **socio-technical**: it combines social and technical aspects.

- Training data may contain personal information about individuals and groups.
- Rules and design choices are made by humans, who bring their own biases and interests.
- Systems touch personal areas of life and can make decisions affecting **fundamental
  rights**.

## 3. The AI lifecycle — where risk arises

An AI lifecycle differs from a typical software lifecycle, and **ethical choices arise at
every stage**:

- **Data selection & pre-processing.** How you handle missing or outlier data has ethical
  weight — deleting an outlier may erase an individual in a protected class or a rare
  health record, even if model accuracy stays acceptable.
- **Train/validation/test splitting.** If train and test data overlap, results look
  perfect but are meaningless; poor splits can inject unwanted bias into the trained model.
- **Continuous learning.** Systems that learn in real time or ingest new datasets create
  unique risks; when learning is continuous, **validation and monitoring of outputs become
  critical.**
- **Deployment.** Development uses training/test data; deployment introduces *production*
  data — a distinct risk surface.

**Cautionary example — Microsoft Tay (2016):** an early Twitter chatbot that learned from
user interactions. Without sufficient guardrails, malicious users taught it to become
racist, misogynistic, and adversarial, forcing Microsoft to pull it within a day. Lesson:
letting AI "learn on its own" without guardrails is dangerous, and training-data quality is
paramount.

## 4. Core terminology for risk & compliance

- **Autonomy — human in command / in the loop / on the loop.**
  - *Human in the loop*: a human must affirmatively act before a decision is made (presses
    the button, says yes).
  - *Human on the loop*: the system is automated but a human monitors outputs and can
    intervene — including a **kill switch** to shut down a malfunctioning high-risk system.
- **Capability breadth:** *narrow* (specific tasks) → *general* (human-like breadth) →
  *super* intelligence. Note: general-purpose ≠ generative; non-generative systems can also
  be general-purpose, which matters for compliance scoping.
- **Reasoning / inference models** can expose the *steps* taken to reach an output,
  providing **explainability** — critical for risk and compliance. Contrast the early
  "black box" (e.g., Watson) with no output explanation.
- **Memory:** reactive machines retain nothing after output; limited-memory systems retain
  only session context; other systems (including generative AI) may retain prompt inputs —
  a privacy/security consideration ("where is your data going, and is it remembered?").
- **Rules-based (symbolic) vs machine-learning (sub-symbolic).** Rules-based systems (e.g.,
  decision trees) encode explicit rules; ML systems rely on numerical results and are
  sub-symbolic. Most real systems are **hybrid** — e.g., an ML model with embedded rule
  guardrails that refuse queries like "how do I build a bomb."
- **Output types:** classification (supervised, uses historical labels), clustering
  (unsupervised, finds patterns/anomalies), recommenders (e.g., clinical decision support),
  and generative.

## 5. Defining the system boundary

To evaluate risk and compliance you must **define the system's boundaries**. AI does not
stand alone — it is embedded in a platform, used within a process, adjacent to other
systems. Understand the **combination of scope, purpose, and use**: a general-purpose
generative model built for marketing copy may be repurposed to draft a legal strategy it
was never intended for. A system can be "high risk" either because of a regulated use
*or* because it performs a **critical function for the organization**. Processing includes
pre-processing and post-processing, not just the algorithm.

## 6. The arc of AI standards

Ethical AI → Trustworthy AI → Responsible AI. The labels differ but the frameworks cover
**the same core pillars/principles** in different ways. AI ethics must be **aligned with
existing company ethics** and integrated into corporate governance — potentially via an
ethics committee with assigned responsibility for reviewing AI ethical decisions and a
defined escalation path.

Bias is nuanced: a system can pass the employment **four-fifths rule** and be legally
compliant, yet a company may still, for its own purposes, introduce (legal) biases — so
"legally compliant" is not the same as "free of unwanted bias."

## 7. Governance and the leading frameworks

**AI governance** = the policies, procedures, and ethical considerations required to
oversee the development, deployment, and maintenance of AI systems — ensuring AI risks
(including legal and compliance risks) are identified and addressed. It sits alongside
corporate governance and data governance.

- **ISO/IEC 42001** — an **auditable** AI management system standard, with a mechanism for
  independent auditors (like ISO 27001).
- **NIST AI RMF** — **voluntary** but very widely adopted.
- Both are treated in depth as primary references; they overlap heavily in principle.

## 8. The risk formula and residual risk

Risk generally = **likelihood of an event × severity/impact of its consequences.** Risk can
be upside or downside; compliance focuses mostly on downside.

- A recurring AI difficulty: **impact is hard to quantify.** Fines can be calculated, but
  the magnitude of many AI harms is genuinely hard to measure.
- The goal is to reduce **residual risk** to within a **risk tolerance / appetite** that
  **top management can accept.** Deploying a generative-AI solution (e.g., self-hosting a
  model vs. using a vendor cloud) requires a **structured process**: identify all risks,
  mitigate them, and decide whether any remaining risk is acceptable to the company —
  context (deployment, terms, data flows, privacy policies, disclaimers) is everything.

## 9. Legal, contract, and vendor risk

- Litigation and state/federal enforcement around AI are increasing — "more eyes on AI"
  means more disputes when things go wrong.
- **Vendor/contract risk:** your vendors are quietly using generative and other AI
  internally. Have you reviewed AI-risk allocation in contracts? Vendor assessment should
  flow from a policy that has already identified your AI risks, so you know what you can and
  cannot accept, where to shift risk, and where insurance covers it.
- **IP:** never put trade secrets into a public prompt. Copyright exposure is real —
  *Thomson Reuters v. Ross Intelligence*, where Ross used Westlaw content to train a legal
  AI tool and was found infringing, effectively ending the business (and stranding its
  customers).
- **Build your own foundation first.** Develop a framework for assessing your company's own
  risk parameters and tolerances, then apply it to every contract you negotiate. You have
  to start somewhere; the foundation is where to start.

## 10. AI in professional workflows

Adoption is rising and unavoidable; firms that don't actively evaluate and implement AI
fall behind. But watch the failure modes — hallucinated cases and sanctions, and clients
who run their own analysis and ask outside counsel to "rubber-stamp" it (which still
requires redoing the work, because the inputs and facts aren't known). Perceived
efficiencies may be smaller than they appear.
