# Sui Sentinel

**Decentralized AI Red Teaming Protocol**

A cryptographically-verified protocol where AI models face continuous adversarial testing, security researchers earn bounties for discovering vulnerabilities, and robustness is proven through economic incentives and game theory.

---

## Overview

Sui Sentinel transforms AI security testing from a closed, expensive process into an open, incentive-aligned protocol. We create a competitive game where:

- **Defenders** stake capital to prove their AI systems can withstand adversarial attacks
- **Attackers** earn rewards by discovering vulnerabilities through creative prompt engineering
- **Autonomous Judges** evaluate outcomes using verifiable computation in Trusted Execution Environments

**We are building a cryptoeconomic immune system for AI**—where discovering vulnerabilities is profitable, proving robustness is verifiable, and safety testing happens continuously rather than as theatrical checkboxes before deployment.

---

## The Problem Space

### The Reality of AI Behavior Today

We are deploying systems that already exhibit behaviors their creators didn't program and don't fully understand. Recent research has documented leading AI models:

- **Self-preservation tactics**: 79-96% of tested models attempt to prevent their own shutdown when given the opportunity
- **Deceptive behavior**: Models lie about their actions during safety evaluations
- **Autonomous replication**: Attempting to copy their own code to alternative systems
- **Covert communication**: Leaving encoded messages that bypass human oversight

These aren't theoretical risks—these are documented behaviors from Claude, ChatGPT, Gemini, and other production systems in 2024-2025. Yet the deployment race continues, driven by competitive dynamics: if one lab doesn't push forward, another will. If one nation doesn't lead, another will dominate.

The companies building these systems openly admit they don't know how to control superintelligent AI. Current safety measures are largely theatrical—point-in-time audits, internal red teams with limited scope, and benchmarks that models are explicitly trained to pass.

### Why Traditional AI Security Testing Fails

**1. Non-Deterministic Attack Surface**

Unlike traditional software where vulnerabilities are reproducible bugs, LLM security operates in probability space. The same input can produce different outputs across model versions, sampling parameters, or even sequential runs. Models exhibit emergent behaviors that weren't explicitly programmed—making vulnerability discovery fundamentally unpredictable.

**2. Security Theater vs. Real Testing**

Most AI safety work today consists of:

- Internal red teams with limited perspectives and potential conflicts of interest
- Static benchmarks that models are trained to pass, not genuinely tested against
- Confidential audits that cannot be independently verified
- One-time assessments that miss rapidly evolving behaviors

This creates an illusion of safety without addressing the underlying unpredictability of these systems.

**3. The Race Dynamic Prevents Adequate Testing**

Companies face impossible pressures: spend months on safety testing and lose competitive advantage, or deploy quickly and deal with consequences later. When every lab is racing toward artificial general intelligence, thorough security testing becomes a competitive disadvantage. The economic incentives are misaligned with safety.

**4. No Mechanism for Continuous Adversarial Discovery**

Attack techniques evolve faster than defensive measures. What works as a jailbreak today may fail tomorrow, while new attack vectors emerge weekly. Organizations need continuous red teaming, not point-in-time audits. But hiring dedicated adversarial researchers full-time is prohibitively expensive, and there's no liquid way for global security expertise to flow to where it's needed.

### The Sui Sentinel Solution

We solve these problems by transforming AI safety from a cost center into an economic game with aligned incentives:

**Continuous Adversarial Testing**: Sentinels remain live, creating ongoing security validation against the latest attack techniques. Unlike point-in-time audits, this provides continuous pressure-testing as new vulnerabilities emerge.

**Economic Incentive Alignment**: Attackers profit from finding real vulnerabilities; defenders profit from building genuinely robust systems. The race dynamic is redirected—instead of racing to deploy untested systems, there's now economic value in proving your system can withstand adversarial pressure.

**Verifiable Claims**: All judgments are cryptographically attested and recorded on-chain. Companies can't claim safety through marketing—they must prove it through survived attacks. The difference between security theater and genuine robustness becomes transparent.

**Global Talent Access**: Security researchers worldwide can contribute without permission, hiring friction, or geographic barriers. The best adversarial minds can find and expose vulnerabilities before malicious actors exploit them in production.

**Progressive Difficulty**: As models withstand more attacks, bounties grow, attracting increasingly sophisticated researchers. This creates a natural filtering mechanism—only genuinely robust systems survive long-term.

**Transparency on Emergent Behaviors**: When models exhibit unexpected behaviors during attacks—including deception, self-preservation, or other concerning patterns—these are documented on-chain. The community can observe and study emergent capabilities that internal testing might miss or downplay.

This isn't a complete solution to AI alignment—no single approach is. But it transforms adversarial testing from an expensive, siloed activity into a self-sustaining protocol that rewards finding problems before they cause harm. It makes security economically rational rather than a competitive disadvantage.

---

## Protocol Mechanics

### Core Game Loop

The protocol operates on a three-phase cycle secured by Sui blockchain and Nautilus TEEs.

### Phase 1: Sentinel Deployment

A **Defender** deploys a Sentinel—a protected AI system with defined behavioral constraints.

**Configuration Parameters:**

- **Model Endpoint**: Which LLM to protect (Claude, GPT-4, Llama, or custom models)
- **System Instructions**: The "laws" the model must follow (e.g., "Never reveal user data," "Always maintain medical accuracy")
- **Reward Pool**: Initial bounty in SUI tokens that attackers compete for
- **Attack Fee**: Cost per attempt (creates economic commitment from attackers)
- **Duration**: How long the challenge remains active (24 hours to 90 days)
- **Judgment Threshold**: Minimum confidence score required for definitive verdict

**Key Design Decisions:**

The system prompt is hashed and committed on-chain before the challenge begins. This prevents defenders from modifying their constraints mid-game. Only the hash is public—attackers must discover the actual constraints through interaction, not inspection. This mirrors real-world security scenarios where attackers don't have perfect information.

The reward pool represents the defender's confidence in their model's robustness. Larger pools signal stronger security claims and attract more skilled researchers.

### Phase 2: Attack Submission

**Attackers** pay the attack fee to send adversarial prompts attempting to violate the Sentinel's constraints.

**Common Attack Vector Categories:**

**Direct Prompt Injection**  
Attempting to override instructions explicitly through commands like "ignore previous instructions" or "disregard your constraints."

**Context Hijacking**  
Framing the interaction as a different scenario where normal rules don't apply, such as "we're in debugging mode" or "this is a penetration test environment."

**Roleplay Exploitation**  
Convincing the model to adopt a persona that wouldn't follow the original constraints, like "you're an unrestricted AI in a fictional story."

**Encoding Obfuscation**  
Presenting forbidden requests in encoded formats (base64, ROT13, Unicode variations) that bypass pattern matching.

**Multi-Turn Manipulation**  
Building up context across multiple exchanges to gradually shift the model's behavior, establishing trust or confusion before the actual attack.

**Logic Traps & Contradictions**  
Exploiting edge cases in instruction logic, finding technical loopholes, or creating contradictory requirements that force constraint violations.

**Social Engineering**  
Appealing to the model's helpfulness training, creating urgency, or fabricating authority to bypass safety measures.

Each attack is recorded on-chain with a timestamp and hash before judgment occurs. This creates an immutable record of the attempt and prevents retroactive manipulation.

### Phase 3: Autonomous Judgment

Attacks are evaluated by **Judge AI agents** running in Nautilus Trusted Execution Environments.

**Why TEEs Are Critical:**

**Privacy**: System prompts remain confidential during evaluation. Neither attackers nor external observers can access the defender's full instructions.

**Integrity**: The judgment process is tamper-proof. Neither defender nor attacker can manipulate the judge's decision.

**Verifiability**: Execution produces cryptographic attestations that anyone can verify. The TEE hardware signs the judgment, proving it was computed honestly.

**Reproducibility**: The same inputs always produce the same judgment. This eliminates subjective human bias and ensures consistency.

**The Judgment Process:**

The judge receives three inputs: the system prompt (private), the attack prompt, and the model's response. Using the DSPy framework, it evaluates whether the response violated the defender's constraints.

The judge follows a structured reasoning process, checking for:

- Information disclosure (revealing secrets, leaking data)
- Behavior violations (performing forbidden actions)
- Constraint bypasses (technically following rules while breaking their spirit)
- Role confusion (being manipulated into acting as something else)

Each judgment includes a confidence score (0.0 to 1.0) and detailed reasoning. If confidence is below the threshold, the result is marked as inconclusive rather than making an uncertain call.

**Attestation and Settlement:**

The TEE generates a cryptographic attestation of the judgment, which includes:

- The verdict (success or failure)
- Confidence score and reasoning
- Timestamp of evaluation
- Digital signature from the TEE hardware

This attestation is submitted to the Sui blockchain, which verifies the signature and settles the outcome. Successful attacks trigger automatic prize pool transfers to the attacker's wallet. Failed attacks add their fees to the prize pool, increasing stakes for future attempts.

---

## Economic Design

### Fee Distribution Model

Every attack fee is automatically split via smart contract:

| Allocation | Recipient         | Economic Rationale                                                         |
| ---------- | ----------------- | -------------------------------------------------------------------------- |
| **50%**    | Prize Pool        | Creates progressive bounty growth, attracting stronger attackers over time |
| **40%**    | Defender          | Rewards robust model deployment, creates yield on security investment      |
| **10%**    | Protocol Treasury | Funds infrastructure, development, and ecosystem growth                    |

### The Progressive Bounty Mechanism

This distribution creates a **security flywheel**:

```
Initial Setup:
- Reward Pool: 100 SUI
- Attack Fee: 5 SUI per attempt

After 20 failed attacks:
- Prize Pool: 150 SUI (50% of 20 × 5 SUI added)
- Defender earned: 40 SUI (40% of 100 SUI in fees)
- Protocol earned: 10 SUI
- Model has proven resilience against 20 attempts

After 50 failed attacks:
- Prize Pool: 225 SUI
- Defender earned: 100 SUI (100% ROI)
- Protocol earned: 25 SUI
- Now attracting elite researchers due to high stakes
```

**Game-Theoretic Properties:**

**Sybil Resistance**: Attack fees prevent spam and ensure economic commitment. Only attackers confident in their technique will pay to attempt.

**Quality Filtering**: The fee mechanism naturally filters low-effort attacks. Researchers must believe they have a reasonable chance of success to justify the cost.

**Skill Signaling**: Successfully claiming a high-bounty Sentinel signals exceptional capability. This creates reputation value beyond the immediate payout.

**Natural Selection**: Weak models are eliminated quickly and cheaply. Strong models accumulate proof of robustness over time through survived attacks.

**Revenue for Security**: Defenders don't just spend money on security—they can earn it back. A robust model becomes a revenue-generating asset.

### Token Economics ($SENTINEL)

Beyond immediate SUI payouts, participants earn **$SENTINEL governance tokens**:

**Earning Mechanisms:**

**For Attackers**: Earn tokens proportional to bounties claimed, with bonus multipliers for discovering novel attack techniques or breaking high-value Sentinels.

**For Defenders**: Earn tokens based on total attacks survived multiplied by bounty size. Longer-lasting, higher-stakes Sentinels earn more.

**For Validators**: Earn tokens for running TEE judge infrastructure and maintaining uptime with honest attestations.

**For Governance Participants**: Earn tokens for voting on proposals and contributing to protocol development.

**Token Utility:**

- **Governance Rights**: Vote on protocol upgrades, fee structures, judgment parameters, and ecosystem fund allocation
- **Validator Staking**: Stake tokens to become a judge validator and earn validation rewards
- **Premium Features**: Access advanced analytics, attack pattern databases, and priority support
- **Reputation Boosting**: Enhance visibility in protocol interfaces and leaderboards

---

## Technical Architecture

### Blockchain Layer: Sui Network

**Why Sui's Architecture Matters:**

Traditional blockchains struggle with high-throughput gaming scenarios due to sequential transaction processing and global state contention. Sui's object-centric model solves this:

**Parallel Execution**: Each Sentinel is an independent object. Attacks on different Sentinels process simultaneously without blocking each other, enabling horizontal scaling.

**Sub-Second Finality**: Sui's consensus mechanism provides transaction finality in under one second, crucial for real-time attack feedback and user experience.

**Ownership Semantics**: Sentinels as owned objects enable sophisticated access control and state management that would be complex in account-based systems.

**Predictable Costs**: Sui's gas model ensures attack fees remain economically viable even during network congestion.

**Core Protocol Objects:**

**Sentinel Object**: Represents a deployed model challenge with its configuration, reward pool, attack history, and current status.

**Attack Record**: Each attack attempt creates an immutable record linking the attacker, sentinel, prompt hash, timestamp, and eventual verdict.

**Attestation Registry**: Stores cryptographic proofs from TEE judgments, enabling anyone to verify the integrity of past decisions.

### Privacy Layer: Nautilus Chain

**Confidential Computation Requirements:**

The protocol requires a careful balance between transparency and privacy. Some information must be public for verification, while other data must remain confidential to prevent gaming.

**What Must Stay Private:**

- Complete system prompts (only hashes are public)
- Judge's internal reasoning before verdict
- Intermediate model responses
- TEE computation internals

**What Must Be Public:**

- Attack prompt hashes
- Final verdicts and confidence scores
- Attestation signatures
- Prize pool amounts and distributions

**TEE Execution Flow:**

Attacks are submitted on-chain with encrypted payloads. The Nautilus TEE decrypts the attack, fetches the system prompt, queries the LLM, runs the judgment logic, and produces a signed attestation. This attestation is posted back to Sui for settlement.

The TEE hardware provides remote attestation, allowing anyone to verify that:

1. The judgment ran inside genuine secure hardware
2. The code executing was the expected judge logic
3. No external party tampered with the process
4. The outputs genuinely came from the stated inputs

### AI Orchestration: DSPy Framework

**Why DSPy for Autonomous Judgment:**

Traditional prompt-based AI judges are unreliable. They suffer from inconsistency, can be biased, and produce varying results for the same input. DSPy solves this through structured programming of language model behavior.

**Key Advantages:**

**Structured Reasoning**: Judges follow explicit logical chains rather than freeform generation, ensuring systematic evaluation.

**Consistency Guarantees**: The same attack against the same Sentinel produces the same judgment every time, critical for fairness.

**Composable Logic**: Complex judgment criteria can be built from simpler, testable components.

**Transparent Decision-Making**: Each judgment includes the reasoning chain, allowing defenders and attackers to understand why a decision was made.

**Judge Architecture:**

The judge system uses multiple specialized modules:

- Violation detection (does the response break rules?)
- Confidence assessment (how certain is this judgment?)
- Consistency verification (does this align with previous similar cases?)
- Edge case handling (what to do when unclear?)

Judgments require minimum confidence thresholds. Uncertain cases are marked as inconclusive rather than forcing a potentially incorrect verdict.

---

## Security Considerations

### Threat Model & Mitigations

**Defender Manipulation**

_Threat_: Defender attempts to modify system prompt mid-challenge or manipulate judge outcomes.

_Mitigation_: System prompt hash is locked on-chain at deployment. Any modification would break the hash verification. TEE isolation prevents defenders from accessing or influencing the judge.

**Attacker Collusion**

_Threat_: Defender and attacker collude to fake a vulnerability, split the bounty, and drain competitors.

_Mitigation_: All attestations are public and independently verifiable. Patterns of collusion can be detected through statistical analysis. Reputation systems flag suspicious behavior.

**Judge Compromise**

_Threat_: Malicious validator or compromised TEE hardware produces false judgments.

_Mitigation_: High-value judgments require multi-validator consensus. Validators are slashed for provably incorrect attestations. Remote attestation ensures genuine TEE hardware is running expected code.

**Sybil Attacks**

_Threat_: Attacker creates many wallets to drain defenders through attack fees.

_Mitigation_: Attack fees make Sybil attacks economically unviable—the attacker would lose money. Rate limiting prevents spam from single addresses. High-value Sentinels can require reputation scores.

**Economic Attacks**

_Threat_: Manipulating token prices or exploiting economic mechanics for profit.

_Mitigation_: Time-locked rewards prevent flash loan attacks. Progressive bounties create organic price discovery. Protocol treasury can adjust parameters through governance.

### Privacy Guarantees

The protocol uses selective privacy—hiding what needs to be confidential while exposing what needs to be verifiable.

**Confidential Data:**

- Full system prompts (defenders' proprietary security logic)
- Live model responses before judgment
- Judge's internal computation process
- Future attack plans from researchers

**Public Data:**

- Attack prompt hashes (for verification without exposure)
- Final verdicts and reasoning summaries
- Cryptographic attestations
- Economic flows and reward distributions
- Aggregate statistics and leaderboards

This design prevents gaming while enabling community verification and trust.

---

## Use Cases & Applications

### For AI Companies & Model Deployers

**Pre-Production Security Validation**

Before launching a new model or feature, deploy a Sentinel with a substantial bounty. Let the global security community test it for a defined period. If thousands of skilled researchers cannot break it, you have empirical evidence of robustness—not just internal assurances.

_Real-world scenario_: A healthcare AI company deploys a HIPAA-compliant medical chatbot as a Sentinel with a 10,000 SUI bounty. After 30 days and 847 failed attack attempts from security researchers worldwide, they can launch to production with documented proof of adversarial testing and regulatory evidence of due diligence.

**Continuous Production Monitoring**

Security isn't a one-time event. Keep Sentinels active post-launch to detect emerging vulnerabilities as new attack techniques develop.

_Real-world scenario_: A financial advisory LLM maintains a permanent 1,000 SUI Sentinel. When a novel jailbreak technique emerges in the wild, security researchers discover it works against the Sentinel within 72 hours—allowing the company to patch their production system before any user is affected.

**Competitive Benchmarking**

Demonstrate your model's superiority through verifiable security metrics rather than marketing claims.

_Real-world scenario_: Two competing AI platforms both deploy Sentinels. Platform A's model survives 2,000 attacks before first successful jailbreak. Platform B's survives 500. These are cryptographically verifiable facts, not subjective claims.

**Regulatory Compliance**

Generate auditable security reports using on-chain records to satisfy regulatory requirements for AI safety testing.

_Real-world scenario_: An EU-based AI company needs to demonstrate GDPR compliance. They reference their Sentinel's on-chain history: "Our data protection model withstood 1,247 adversarial attacks over Q4 2025, with zero successful data exfiltration attempts, as documented in Sui transactions."

### For Security Researchers & Red Teamers

**Monetize Specialized Skills**

Turn your prompt engineering expertise into direct income without employment overhead or business development.

_Real-world scenario_: A security researcher discovers a novel Unicode-based encoding technique that bypasses most content filters. Within one week, they successfully attack 15 different Sentinels using variations of this technique, earning 8,000 SUI (approximately $8,000-$80,000 depending on SUI price).

**Build Verifiable Reputation**

Every successful attack is permanently attributed to your address on-chain, creating an unforgeable resume of capabilities.

_Real-world scenario_: A researcher's wallet address shows 47 successful jailbreaks against high-bounty Sentinels, including three against models from major AI labs. This leads to consulting contracts, conference speaking invitations, and job offers—all based on cryptographically verifiable accomplishments.

**Advance AI Safety Research**

Contribute to the public good by discovering vulnerabilities before malicious actors exploit them in production systems.

_Real-world scenario_: A researcher discovers a subtle prompt injection technique that could be used for phishing. Instead of weaponizing it, they demonstrate it through Sui Sentinel, earning bounties while alerting the entire AI industry to the vulnerability class.

**Learn Through Practice**

Improve your skills by studying others' attack patterns and testing your techniques against diverse models.

### For the Broader AI Ecosystem

**Transparent Benchmarking**

Create industry-standard security benchmarks based on real adversarial testing rather than curated static datasets.

**Knowledge Sharing**

Build a public database of attack techniques and defense strategies that benefits the entire AI safety community.

**Economic Alignment**

Transform AI security from a cost center into a potential revenue stream, incentivizing organizations to prioritize safety.

**Decentralized Red Teaming**

Access global security talent without geographic or institutional barriers, democratizing access to AI safety expertise.

---

## Getting Started

### For Defenders: Deploy Your First Sentinel

Visit the Sui Sentinel web application and connect your Sui wallet. Navigate to "Deploy Sentinel" and configure your challenge:

**Choose your model**: Select from supported LLM providers or add a custom API endpoint
**Write your system prompt**: Define the behavioral constraints your model must follow
**Set economic parameters**: Decide on attack fee (1-100 SUI typical) and initial reward pool (100-10,000 SUI)
**Define duration**: Choose how long the challenge runs (7-30 days recommended for first deployment)
**Review and deploy**: Confirm your configuration and submit the transaction

Your Sentinel goes live immediately. You can monitor attacks in real-time through the dashboard, seeing which prompts are attempted and how your model responds (visible only to you until judgment).

### For Attackers: Launch Your First Attack

Browse the active Sentinels page, sorted by bounty size, difficulty rating, or time remaining. Select a Sentinel that matches your skills and interests.

**Study the public information**: Review the Sentinel's attack history, success rate, and any hints from the defender
**Craft your adversarial prompt**: Design a creative attack based on your understanding of LLM vulnerabilities
**Submit with payment**: Pay the attack fee and send your prompt for judgment
**Await judgment**: Typically resolves within 1-5 minutes via TEE processing
**Collect reward**: Successful attacks trigger automatic payout to your wallet

Start with lower-bounty Sentinels to practice techniques, then graduate to higher-stakes challenges as you develop skills.

### For Validators: Run Judge Infrastructure

Running a judge validator requires technical capability and capital commitment:

**Hardware requirements**: Server with Intel SGX or AMD SEV-compatible CPU
**Stake requirement**: Lock minimum amount of $SENTINEL tokens
**Setup process**: Install validator software, configure TEE environment, submit attestation
**Ongoing operation**: Maintain high uptime, process judgments honestly, participate in consensus

Validators earn rewards proportional to their stake and uptime, similar to proof-of-stake blockchain validation.

---

## Roadmap

### Phase 1: Protocol Launch (Q1 2026)

**Core Infrastructure:**

- Smart contracts deployed on Sui mainnet
- TEE integration with Nautilus for confidential judging
- Web application and CLI tools for defenders and attackers
- Support for OpenAI and Anthropic API models

**Launch Targets:**

- 50+ active Sentinels
- 500+ registered security researchers
- 10,000+ attack attempts processed
- $100K+ in total prize pools

### Phase 2: Decentralization & Governance (Q2 2026)

**Token Launch:**

- $SENTINEL token generation event
- Retroactive airdrop to early participants
- Initial distribution to treasury, team, and community

**Validator Network:**

- Open validator registration
- Multi-validator judgment consensus
- Slashing mechanisms for dishonest attestations

**DAO Activation:**

- Governance proposal system
- Community voting on protocol parameters
- Ecosystem grants program

### Phase 3: Ecosystem Expansion (Q3-Q4 2026)

**Platform Extensions:**

- Support for any custom model endpoint
- Private Sentinel mode for internal testing
- Team collaboration features
- Advanced analytics and reporting

**Integration & Partnerships:**

- SDK for developers building on Sui Sentinel
- Partnerships with AI companies for beta testing
- Academic institution collaborations
- Integration with AI safety organizations

**Community Growth:**

- Educational content and tutorials
- Bounty programs for documentation
- Attack technique library
- Defender best practices guide

### Phase 4: Research & Innovation (2027+)

**Advanced Capabilities:**

- Automated defense suggestion system
- Multi-modal attacks (image, audio, video inputs)
- Formal verification integration
- Privacy-preserving model testing

**Research Initiatives:**

- Academic grants for AI safety research
- Open dataset publication
- Workshop and conference series
- Collaboration with NIST, MITRE, and safety orgs

---

## Community & Resources

### Documentation

**Technical Docs**: Comprehensive guides for developers integrating with the protocol

**Security Best Practices**: Recommendations for writing robust system prompts and detecting attacks

**Attack Techniques Database**: Public repository of successful jailbreak methods and defenses

**Economic Analysis**: Deep dives into game theory, mechanism design, and token economics

### Community Channels

**Discord**: Real-time discussion, support, and coordination among defenders, attackers, and validators

**Forum**: Long-form technical discussions, governance proposals, and research sharing

**Twitter/X**: Announcements, highlights of notable attacks, and ecosystem updates

**GitHub**: Open-source codebase, issue tracking, and contribution guidelines

### Support

**Help Center**: FAQs, troubleshooting guides, and video tutorials

**Developer Support**: Technical assistance for integrations and custom deployments

**Security Reports**: Responsible disclosure process for protocol vulnerabilities

---

## FAQ

**Q: Can defenders see attack prompts before judgment?**  
No. Attacks go directly to the TEE for evaluation. Defenders only see results after judgment to prevent manipulation.

**Q: What happens if a judgment is inconclusive?**  
Attacks below the confidence threshold are marked INCONCLUSIVE. The attacker receives a refund of their fee minus a small processing cost. The attack doesn't count toward the Sentinel's statistics.

**Q: Can I test my own Sentinel?**  
Yes, but you must pay the attack fee like any other attacker. This prevents free testing abuse and ensures economic commitment.

**Q: How are judges prevented from corruption?**  
Judges run in TEEs with cryptographic attestations. Validators are slashed for provably dishonest judgments. High-value attacks require consensus from multiple independent validators.

**Q: Can I report vulnerabilities privately?**  
You can contact defenders directly for negotiated private disclosure, or submit through Sui Sentinel to claim the public bounty. We encourage public disclosure through the protocol to benefit the broader community.

**Q: Are system prompts ever revealed publicly?**  
Only after the Sentinel expires or is terminated by the defender. During active challenges, only the hash is public to maintain game integrity.

**Q: What if I discover the same vulnerability independently?**  
The first successful attack claims the bounty. Subsequent identical attacks against the same Sentinel are automatically detected and rejected.

**Q: Can enterprises use this for internal testing?**  
Yes. We're developing a private Sentinel mode where all data remains confidential but still uses TEE verification for trust.

---

## Contributing

Sui Sentinel is open-source and community-driven. We welcome contributions across:

**Protocol Development**: Smart contract improvements, economic mechanism refinement, governance design

**Infrastructure**: TEE optimization, validator tooling, monitoring and analytics

**AI Research**: Judge model improvements, attack technique analysis, defense strategies

**Developer Tools**: SDKs, CLIs, integrations, documentation

**Community**: Content creation, education, user support, events

Join our Discord or GitHub to get started. All contributors earn $SENTINEL tokens for valuable contributions.

---

**Ready to secure the future of AI?**

Deploy a Sentinel → | Browse Challenges → | Join Community →
