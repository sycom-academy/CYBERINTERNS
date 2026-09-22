# Inject 05 — Supplier breach notification

**Release:** Week 2, Day 3, 14:00 · **Team:** GRC · **Deliverable due:** W2 D5

---

## Artefact 1 — the notification

> **From:** compliance@textway.example
> **To:** p.raman@finserve.co.uk; procurement@finserve.co.uk
> **Date:** W2 D3, 13:47
> **Subject:** Security incident notification — Textway Communications Ltd
>
> Dear Customer,
>
> We are writing to inform you of a security incident affecting Textway
> Communications Ltd.
>
> On W1 D4 we became aware of unauthorised access to a message routing
> database operated by one of our downstream delivery partners in Singapore.
> Our investigation, supported by an external forensics firm, has concluded
> that an unauthorised party had access to this system between approximately
> W-6 D3 and W1 D4.
>
> The affected database holds message delivery records. For each message this
> comprises: destination mobile number, message body, sending customer
> account, timestamp, and delivery status. Records are retained in this system
> for 90 days.
>
> We have identified that records relating to your account were present in the
> affected system. We estimate approximately 214,000 message records relating
> to FinServe Digital Bank Ltd during the affected period.
>
> We have contained the incident, rotated all credentials, and engaged our
> partner on remediation. We do not at this time have evidence of onward
> misuse of the data.
>
> We consider that Textway acts as a data controller in respect of message
> routing metadata and we have notified the relevant authority in our own
> jurisdiction. As our relationship with you is governed by our standard
> reseller terms, we would draw your attention to clause 11.3 (limitation of
> liability).
>
> Please direct any questions to this address.
>
> Textway Communications Ltd — Compliance

---

## Artefact 2 — internal, 20 minutes later

> **From:** Priya Raman, CISO
> **To:** Project Sentinel — GRC workstream
> **Cc:** Chinelo Nwosu, Data Protection Officer
> **Subject:** FW: Security incident notification — need a view by Friday
>
> This landed twenty minutes ago. I need your assessment by Friday because I
> have to tell the executive committee on Monday and I would rather tell them
> something considered than something fast.
>
> Three things I do not know the answer to and you should:
>
> 1. Is this our breach or their breach? They say they are a controller. I am
>    not sure that is right and I am not sure it matters for what we have to do.
> 2. Do we have to tell the ICO, and by when. If the answer is "the clock
>    started when they told us", say so plainly.
> 3. Do we have to tell 180,000 customers. I would like the answer to be no.
>    I need the answer to be correct.
>
> Chinelo is our DPO and will sign whatever we submit, but she is on leave
> until Monday, so you are doing the analysis.
>
> One more thing. Whoever put Textway in as a "low" criticality supplier did
> so when we used them for marketing texts. We now send one-time passcodes
> through them. I want to understand how that changed without anyone noticing.
>
> Priya

---

## What you have

- The supplier register position on Textway, from Inject 02
- [`02-ARCHITECTURE/04-Data-Flow.md`](../02-ARCHITECTURE/04-Data-Flow.md) — flow
  F6, the third-party table, and §5 on transfers
- [`02-ARCHITECTURE/03-M365-Architecture.md`](../02-ARCHITECTURE/03-M365-Architecture.md)
  for what is and is not in a FinServe OTP message

---

## What you are asked to produce

**GRC team.**

**1. Breach assessment** → `06-DELIVERABLES/GRC/Textway-Breach-Assessment.md`

- **Roles.** Controller or processor, for Textway and for FinServe, with your
  reasoning. Address their claim directly rather than around it.
- **Is it a personal data breach**, and whose. Identify the data subjects and
  the categories involved. Be specific about what is actually in the message
  body of a FinServe OTP or transaction alert.
- **Risk to data subjects.** Likelihood and severity, reasoned. This is the
  test that decides questions 2 and 3, so do it properly rather than asserting
  a conclusion.
- **Notification to the ICO.** Required or not, on what basis, and if so by
  when — state the exact moment you say the clock started and why.
- **Notification to data subjects.** Required or not, and on what basis.
- **What you would tell the executive committee**, in five sentences.

**2. Supplier register correction** → update `06-DELIVERABLES/GRC/Supplier-Register.md`

Re-assess Textway and say what changed. Then answer the CISO's last question:
what process failed such that a supplier's criticality did not move when the
data it processed changed? That is a control gap, not an administrative slip —
write it as a risk and put it in the risk register.

**3. Contractual position** → section within the assessment

You have no DPA and standard reseller terms. Say what that means for FinServe's
obligations, and what you would require before this supplier processes another
OTP. Note that they have pointed you at a liability clause in their first
communication.

## Where it goes

`06-DELIVERABLES/GRC/`, PR from `grc/<initials>/textway-breach`.

## Time budget

Two days. The Friday deadline is real — the executive committee meets Monday.

## Note

Textway's notification is written to be reassuring and to limit their exposure.
Read what it does not say as carefully as what it does. Note the retention
period they quote, the length of the access window, and the phrase "at this
time".

You may find you cannot answer one of the CISO's questions without information
you do not have. Saying so, and saying precisely what you would need, is a
legitimate answer. Inventing the information is not.
