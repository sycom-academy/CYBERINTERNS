# Textway Breach Assessment - Project Sentinel

FinServe Digital Bank Ltd

This assessment responds to the security incident notification received from Textway Communications Ltd on Wednesday 14 October at 13:47. It addresses the three questions the CISO asked and the contractual position.

## 1. Controller or processor

Textway claims to be a data controller. That claim does not survive analysis.

The test under UK GDPR Article 4(7) is who determines the purposes and means of processing. For FinServe's transactional SMS (OTP codes and transaction alerts), FinServe determines:

- The purpose: Strong Customer Authentication under the Payment Services Regulations, and customer notification of transactions
- The means: SMS to a specific phone number, with specific message content, triggered by a specific customer action
- The content: FinServe composes the message body; Textway delivers it

Textway does not decide who receives a message, what it says, or why it is sent. It provides a delivery channel. That is processing on behalf of a controller, not independent controllership.

Textway may have a separate, legitimate argument that it acts as a controller for its own message routing metadata (delivery logs, routing records, network data). That argument does not extend to the message content or the relationship between the phone number and the sending customer.

**Position:** FinServe is the controller. Textway is a processor. The downstream delivery partner in Singapore is a sub-processor. The absence of a DPA does not change the factual relationship; it means FinServe has been using a processor without the contractual safeguards required by UK GDPR Article 28.

**Why Textway's claim matters:** if FinServe accepts it, FinServe is accepting that it has no notification obligation, no obligation to assess risk to its own customers, and no standing to require information from Textway about the breach. That is precisely what the claim is designed to achieve. FinServe should not accept it.

## 2. Is this a personal data breach, and whose

Yes. This is a breach of confidentiality under UK GDPR Article 4(12): an unauthorised party had access to personal data for 43 days.

**Data subjects:** FinServe retail customers whose phone numbers were used for OTP or transaction alert delivery between approximately 26 August and 8 October 2026. Textway estimates 214,000 message records. FinServe sends approximately 62,000 SMS per day (04-Data-Flow.md, flow F6), so 214,000 records represents roughly 3 to 4 days of messages; the lower figure against a 43-day window suggests either sampling, de-duplication, or that Textway's estimate understates the exposure. This should be clarified with Textway.

**Data categories exposed, per message record:**

| Field | Category | Source |
| --- | --- | --- |
| Destination mobile number | D1 (identity: phone number) | 04-Data-Flow.md, flow F6 |
| Message body (OTP) | Contains a one-time passcode and identifies the recipient as a FinServe customer | 03-Business-Processes.md, P2 |
| Message body (transaction alert) | D3 (financial: transaction amount) | 04-Data-Flow.md, flow F6 ("amount in message body") |
| Sending customer account | Identifies FinServe as the sender | Textway notification |
| Timestamp | When the transaction or authentication occurred | Textway notification |
| Delivery status | Whether the message was delivered | Textway notification |

**What is NOT exposed:** account numbers, sort codes, balances, passwords, NI numbers, identity documents. The OTP codes themselves would have expired (typically within minutes), so they are not directly reusable for authentication.

**What IS exposed that matters:** the combination of phone number, FinServe customer status, transaction amounts and timing. This is a social engineering toolkit. An attacker can now call or text 214,000 confirmed FinServe customers, reference their recent transactions by amount and date, and impersonate the bank convincingly.

## 3. Risk to data subjects

This is the test that determines both notification obligations. UK GDPR Article 33 requires ICO notification where the breach is "likely to result in a risk to the rights and freedoms of natural persons." Article 34 requires notification to data subjects where the risk is "high."

**Likelihood of harm: moderate to high.**

- The exposed data (phone number + customer status + transaction amounts + timing) is directly usable for targeted phishing, smishing and vishing. An attacker does not need to guess who banks with FinServe or fabricate a transaction reference; the data provides both.
- The access window was 43 days (26 August to 8 October). The attacker had sustained access, not a single exfiltration event.
- Textway states they have no evidence of "onward misuse" but qualifies this with "at this time." The absence of evidence of misuse is not evidence of absence. FinServe cannot determine from Textway's notification whether data was exfiltrated, copied or accessed in bulk.
- The downstream partner is in Singapore. FinServe has no visibility into the partner's environment, no contractual relationship with them, and no ability to verify the forensic investigation independently.

**Severity of harm: moderate.**

- Financial harm: the data enables convincing social engineering that could lead to customers disclosing further credentials or authorising fraudulent transactions. FinServe's own OTP mechanism could be exploited if an attacker calls a customer, claims to be the bank, and asks them to read back an OTP "for verification."
- Reputational harm to the individual: limited. The data confirms someone is a FinServe customer and reveals transaction amounts, but not the nature of the transactions.
- The volume (214,000 records, potentially affecting a significant proportion of 180,000 customers) makes the aggregate risk material even if the per-individual risk is moderate.

**Assessment: the breach is likely to result in a risk (Article 33 threshold met) and, given the combination of data, the volume of affected individuals and the social engineering potential, is likely to result in a high risk (Article 34 threshold met).**

This is a judgement call. The DPO should confirm on her return. The factors that could change this assessment downward: evidence that the data was not exfiltrated (Textway has not provided this), or evidence that the downstream partner's system was accessed but not read in bulk.

## 4. Notification to the ICO

**Required.** The risk assessment in section 3 concludes that the breach is likely to result in a risk to data subjects. UK GDPR Article 33(1) requires the controller to notify the ICO without undue delay and, where feasible, within 72 hours of becoming aware.

**When the clock started.** FinServe became aware of the breach when Textway's notification email was received on Wednesday 14 October at 13:47. This is the moment of awareness under Article 33. It does not matter that Textway became aware earlier (8 October) or that Textway has made its own notification; FinServe's obligation as controller runs independently.

**The 72-hour deadline was Saturday 17 October at 13:47.**

If this assessment is being read on or after Saturday 17 October, FinServe has missed the 72-hour window. Article 33(1) permits late notification if accompanied by reasons for the delay. The reasons here are: the CISO received the notification on Wednesday afternoon, the DPO is on leave until Monday, and an external assurance team was asked to provide the analysis.

Those reasons are explainable but not strong. The ICO's guidance makes clear that the 72-hour period is not suspended by the absence of the DPO. FinServe should notify the ICO on the first available working day (Monday 19 October) and state the reasons for the delay.

**What the notification should contain** (per Article 33(3)):

- The nature of the breach: unauthorised access to message delivery records held by a sub-processor in Singapore
- The categories and approximate number of data subjects: retail banking customers, approximately 214,000 message records (the number of distinct individuals may be lower; FinServe should estimate this from its own records)
- The name and contact details of the DPO
- The likely consequences: targeted phishing and social engineering using confirmed customer status and transaction data
- The measures taken or proposed: this assessment, the measures in section 7 below, and any customer notification

FinServe may submit an initial notification and supplement it as further information becomes available. The ICO prefers a timely incomplete notification to a late complete one.

## 5. Notification to data subjects

**Required, subject to DPO confirmation.** The risk assessment in section 3 concludes that the breach is likely to result in a high risk to data subjects. UK GDPR Article 34(1) requires the controller to communicate the breach to the data subject without undue delay.

**The CISO asked whether 180,000 customers must be notified.** The honest answer is: probably, but not necessarily all of them.

FinServe can identify from its own records which customers received an OTP or transaction alert SMS during the 43-day access window. The notification obligation attaches to those customers, not to the entire customer base. The number may be lower than 180,000 if some customers did not transact or authenticate during that period, or higher if some received multiple messages. FinServe should run this query before deciding the scope of notification.

**What the notification should contain** (per Article 34(2)):

- A description in clear and plain language of the nature of the breach
- The name and contact details of the DPO
- The likely consequences: their phone number, the fact that they are a FinServe customer, and details of their recent transactions may have been accessed by an unauthorised party
- Practical advice: be alert to unsolicited calls, texts or emails claiming to be from FinServe; FinServe will never ask for a passcode or password by phone; report suspicious contact to the bank

**What the notification should NOT contain:** the name "Textway" (customers do not know who delivers their SMS and naming the supplier creates confusion), or technical details of the sub-processor compromise.

**Article 34(3) exemptions.** The three exemptions are: (a) appropriate technical and organisational measures rendered the data unintelligible (not met: messages were in clear text); (b) subsequent measures ensure the high risk is no longer likely to materialise (not met: FinServe cannot recall the data or undo its exposure); (c) it would involve disproportionate effort, in which case a public communication would suffice. Exemption (c) might apply if the affected population is very large, but the ICO's guidance favours direct communication where the controller holds contact details, and FinServe holds every affected customer's phone number and email address.

**Recommendation:** notify affected customers directly, by in-app message and email, within the next seven days. The CISO wanted the answer to be no. The answer is yes, and the reason is that customers are better protected if they know to expect targeted phishing than if they do not.

## 6. What to tell the executive committee

Five sentences:

1. An unauthorised party had access to our SMS delivery records for 43 days through a Textway sub-processor in Singapore, exposing approximately 214,000 message records containing customer phone numbers, the fact that they bank with us, and their transaction amounts.
2. We are the data controller for this data regardless of what Textway claims, and the notification obligations are ours.
3. We must notify the ICO, and the 72-hour deadline has likely passed; we should file on Monday with reasons for the delay.
4. We must notify affected customers because the exposed data enables convincing targeted phishing, and they are better protected knowing about it.
5. Textway has no DPA with us, processes our SCA passcodes as our sole SMS provider with no fallback, and was rated "low" criticality because nobody reassessed it when we moved from marketing texts to one-time passcodes; that is a control failure we need to fix immediately.

## 7. Contractual position

**Current position:** FinServe has no DPA with Textway (Supplier Register, S-04). The relationship is governed by Textway's standard reseller terms. Textway's notification email draws attention to clause 11.3 (limitation of liability) in its first communication about a breach. There is no contractual obligation on Textway to notify FinServe of a breach, to provide forensic findings, to give access for audit, or to assist with FinServe's own ICO notification.

**What this means for FinServe:**

- FinServe cannot compel Textway to provide the information it needs to assess the breach fully (whether data was exfiltrated, the identity of the sub-processor, the forensic report)
- FinServe cannot require Textway to co-operate with any ICO investigation
- Textway's liability clause may cap or exclude liability for losses arising from the breach
- FinServe is in breach of UK GDPR Article 28 for using a processor without the required written contract setting out the subject-matter, duration, nature and purpose of processing, and the controller's obligations

**What FinServe must require before Textway processes another OTP:**

1. A DPA compliant with Article 28, including mandatory breach notification within a defined timeframe, audit rights, sub-processor approval, and data deletion obligations
2. An International Data Transfer Agreement (IDTA) or UK Addendum covering the Singapore sub-processor
3. A supplier risk assessment, including the downstream delivery partner
4. Evidence of remediation from the current incident, including the forensic report
5. A contractual SLA with availability commitments appropriate for a service that carries SCA

If Textway cannot or will not provide these within a defined period (we suggest 30 days), FinServe should begin procurement of a replacement SMS provider. The current arrangement is untenable: FinServe is processing 62,000 SCA and transaction messages per day through a supplier with no contract, no DPA, no fallback, a known breach, and a liability limitation.

**Immediate action:** do not suspend Textway now (doing so would stop all payment initiation with no fallback), but this dependency must be resolved before any regulatory examination of the incident reaches the supplier chain.

## 8. Supplier register correction and control gap

### Textway re-assessment

The supplier register entry for Textway (S-04) must be updated:

| Field | Was | Is now |
| --- | --- | --- |
| Criticality | Low | Critical |
| Risk assessment | Critical (unchanged, already rated Critical in Inject 02 based on the DPA gap; the breach confirms rather than changes the assessment) |  |
| Contract status | Reseller terms only | Reseller terms only; DPA required before continued processing |
| Incident | None | Active: breach at downstream partner, 43-day access window, 214,000 records, forensic investigation ongoing |

### The control gap: supplier criticality is static

The CISO asked how a supplier's criticality did not move when the data it processed changed. The answer is a control gap in FinServe's supplier lifecycle management.

Textway was onboarded in 2022 by the marketing team for campaign messaging, under the threshold for procurement due diligence (annual value £22,000). When the business extended Textway to transactional OTP delivery for Strong Customer Authentication, no reassessment was triggered because:

- The supplier register has no field for what data the supplier receives or what business service it supports
- There is no process to reassess supplier criticality when the scope of an existing engagement changes
- The contract owner remained Head of Marketing, even though the primary use case moved to an operationally critical function (payment initiation under SCA)
- The Outsourcing and Third Party Policy (P-06) is 12 months overdue for review and does not address scope changes to existing arrangements

This is not an administrative slip. It is the absence of a control. FinServe's supplier lifecycle has no trigger for the question "has what we send this supplier changed since we onboarded them?"

### New risk register entry: RS-19

Because FinServe has no process to reassess supplier criticality, contractual terms or data protection controls when the scope of an existing supplier engagement changes, there is a risk that suppliers originally onboarded for low-risk purposes are extended to critical functions without DPAs, without due diligence and without operational resilience mapping, resulting in uncontrolled processing of customer data and, as demonstrated by the Textway breach, exposure of that data without adequate contractual remedies.

| Field | Value |
| --- | --- |
| Assets | External: all suppliers whose scope has changed since onboarding |
| Data | Varies by supplier |
| Inherent | L5 x I4 = 20 |
| Controls evidenced | None. The supplier register has no mechanism for scope-change review. The overdue outsourcing policy does not address it. |
| Residual | L5 x I4 = 20 (Critical) |
| Owner | COO |
| FinServe score | Not on the register |
| Recommended treatment | Implement a supplier scope-change trigger in the procurement process: any change to the data categories a supplier receives, or the business service it supports, requires reassessment of criticality, DPA status and due diligence. Review all current suppliers for scope changes since onboarding. Update P-06 to include this control. |
