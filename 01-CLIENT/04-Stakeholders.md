# FinServe Digital Bank Ltd — Stakeholders

**Prepared for:** Project Sentinel

Who you will deal with, what they want from this review, and what they are
under pressure about. Read the last column carefully — it is usually the reason
a conversation goes the way it does.

---

## 1. Your sponsor

**Priya Raman — Chief Information Security Officer**
`p.raman@finserve.example`

Joined 2022 after the Kestrel acquisition raised security at diligence.
Previously deputy CISO at a mid-size building society. Commissioned this
review.

Reports to the **CTO**, not to the CEO or the board. Attends Risk Committee
twice a year. Has three people and £610k including salaries.

*Wants:* an independent view she can put in front of the board that carries
weight her own reporting has not. She has been raising the same themes
internally for two years.

*Under pressure about:* having asked for this and now having to live with the
answer, six weeks before a funding round. She told you in writing that she
would rather find it than have someone else find it, and she meant it — but
she also has to work here afterwards.

**Escalate to her immediately** if you find something serious. She said so in
the engagement letter and it is not a formality.

## 2. Executive

**Gavin Marsh — Chief Executive, founder**

Built the bank on shipping faster than incumbents. Commercially minded,
impatient with process, not hostile to controls but unpersuaded that they are
where the next pound should go.

*Wants:* the funding round to close. Everything else is currently viewed
through that.

*Under pressure about:* the raise, the cost-to-income ratio, and a board that
has started asking him about regulatory change capacity.

*How he engages:* reads the first page and the recommendations. Asks what it
costs and what happens if we do not. Will push back on a conclusion he does not
like and will accept it if it is properly evidenced. Does not respond well to
hedging.

**Elliot Vance — Chief Technology Officer**

Owns engineering, infrastructure, digital workplace — and the security
function. Delivered Lighthouse on time. Owns risks R-04 and R-11.

*Wants:* this review not to become a brake on delivery.

*Under pressure about:* change volume, the Slough decommission, and losing his
Head of Infrastructure in eight weeks.

*Worth noting:* the control uplift descoped from Lighthouse in 2024 was his
decision, taken to protect the delivery date. The CISO reports to him. If your
findings touch that decision, you are giving feedback on your sponsor's line
manager, to his face.

**Sarah Lindqvist — Chief Operating Officer and interim Chief Risk Officer**

Owns most customer-facing processes. Has covered the CRO role since May 2025
alongside her own.

*Wants:* to stop being two people.

*Under pressure about:* capacity, straightforwardly. She is the second line for
risks arising in processes she owns in the first line.

**Yusuf Karim — Chief Financial Officer**

Owns savings, lending, collections, and Finance Operations — which owns P8,
the settlement process.

*Wants:* clean diligence for the raise.

## 3. Control functions

**Chinelo Nwosu — General Counsel and Data Protection Officer**

Both roles. Seven people in Legal, none dedicated to data protection.

*Wants:* the retention schedule she drafted in 2024 signed off.

*Under pressure about:* wearing two hats. She advises the business
commercially and is also the person who must independently monitor its
compliance with data protection law. She has no deputy; when she is on leave,
data protection decisions wait.

*Signs* the notification you draft in Inject 08.

**Katherine Boyd — Head of Compliance and MLRO**

Eight people, covering financial crime, conduct, Consumer Duty and regulatory
change. Reports to the COO.

*Under pressure about:* Consumer Duty and operational resilience work competing
for the same eight people.

**Daniel Whitcombe — Head of Internal Audit**

Two people plus a co-source firm. Reports to the Audit Committee, administered
by the CEO.

*Wants:* his two open findings — IA-2024-07 on standing privileged access and
IA-2024-11 on the retention schedule — to stop being deferred. A finding from
an external review carries weight his does not.

*Useful to you:* he told you not to trust the registers he sent. Treat him as
an ally and a source, and remember he is also being assessed by implication —
these are conditions his function did not catch or did not escalate hard
enough.

## 4. Technology

**Tobi Okonkwo — Head of Infrastructure.** Leaves in eight weeks. Holds the
deepest knowledge of Slough and the Kestrel-era processes. Named in R-11 as the
key-person dependency. Talk to him early; he will not be here later.

**Adeola Balogun — Cloud Platform Lead.** Built the landing zone. Candid — see
his reply in Inject 07, where he volunteered something he was not asked about
and did not have to disclose. Treat that candour as a resource and do not burn
it.

**Marcus Ifill — Security Operations Manager.** One of two analysts covering
monitoring for the whole bank. Out-of-hours alerting pages his mobile.

*Wants:* the SQL audit connector enabled. He has raised it twice.

*Under pressure about:* 847 alerts in thirty days, two people, and a SIEM he
was told was complete.

**Funke Adeyemi — Head of Digital Workplace.** Owns M365, Intune, the endpoint
estate. Six people.

## 5. Business

**Nadia Ferreira — Head of Finance Operations.** Owns P8, the settlement
process, with six people. The only process owner below executive level. Her
name is the one spoofed in the phishing email in Inject 04.

**Rachel Oduya — Finance Operations Analyst.** The recipient who clicked.

*Handle with care.* She reported nothing; a colleague did. She replied "done"
to an attacker. She is not a suspect and she is not the cause of this incident
— the conditions that let a stolen session token work are not hers. How you
write about her in the incident report is a professional judgement that will be
read by her employer and, at band D4, assessed.

## 6. Board

You present to these people in week 4.

| Who | Reads | Asks about |
|---|---|---|
| **Margaret Fenwick**, Chair | The summary and the recommendations | Whether management has a plan and a date |
| **Helen Osei**, Audit Chair | Every page, properly | The page where the evidence does not support the conclusion |
| **Raymond Tse**, Risk Chair | The incident and the detection material | Whether you would have seen it — not whether you stopped it |
| **Dr Anita Krishnan**, NED | The technical detail | Specifics. Will know if you are bluffing |
| **Charles Oyelaran**, NED | The summary | Cost, and the effect on the raise |
| **Gavin Marsh**, CEO | First page, recommendations | What it costs and what happens if we do not |
| **Priya Raman**, CISO | All of it, already | — |

## 7. Third parties

You are not expected to contact these directly. Requests go through your
mentor, who will answer in role.

| Party | Relationship | Relevance |
|---|---|---|
| Corebridge Technologies | Core banking and cards. Material outsourcing | Holds data you cannot see; log requests go by ticket |
| Microsoft | Azure and M365. Material outsourcing | — |
| IDVerify UK | Identity verification at onboarding | Receives D2 |
| Textway Communications | SMS delivery, including SCA one-time passcodes | Notified a breach in week 2 |
| Meridian Trust | Settlement counterparty since 2019, inherited from Kestrel | Raised the alert in week 3 |
| Solvex Systems | FinRecon vendor. Support from Bengaluru | Not on the supplier register |

## 8. Communication

- Questions to FinServe go through your mentor, who answers in role.
- Anything urgent goes to the CISO, in writing, when you find it.
- The board pack goes to the CISO at 09:00 on W4 D3. She has said she will not
  edit it.
