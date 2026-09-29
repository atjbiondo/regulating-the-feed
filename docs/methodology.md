# Methodology

## Scope

*Regulating the Feed* examines enacted legal responses to the design and operation of social media platforms between January 1, 2018 and September 11, 2026. The study focuses on three areas of regulation: account and service access, feeds and recommendation systems, and engagement design.

The central research question is:

> How are selected regulatory systems using enacted law to regulate social media access, recommendation systems, and engagement design, and how does the U.S. state-led approach compare with approaches in the other sampled systems?

## Comparative Sample

The project uses a purposive sample of eight regulatory systems: the European Union, United Kingdom, Australia, United States, Canada, Brazil, China, and Indonesia. The sample was designed to compare the developing U.S. state-level landscape with a broader set of non-U.S. regulatory approaches rather than to provide a globally representative census of social media regulation.

Within each selected system, the research process screened enacted statutes, regulations, and binding subordinate legislation for provisions that directly addressed at least one of the three regulatory areas tracked in the study. Screening was not limited to instruments formally described as “social media laws”; eligibility depended on the substance of the legal requirements.

This process produced 34 qualifying regulatory actions. Twenty-seven are U.S. state-level actions and seven are non-U.S. actions. Canada remained part of the comparative sample even though no enacted action met the project’s inclusion criteria during the study period.

## Inclusion and Exclusion

A legal instrument was included when it had been enacted or formally adopted and imposed a binding requirement addressing at least one tracked area of regulation.

The study excludes proposed legislation, nonbinding guidance, voluntary codes, policy proposals, and other materials that do not create binding legal obligations. Instruments concerning online safety, children, privacy, or digital services were not included solely because they addressed those subjects; they had to satisfy the project’s defined regulatory criteria.

## Unit of Analysis

The dataset treats one material enacted regulatory intervention as one **regulatory action**. Each qualifying action occupies one row in the dataset.

This approach allows multiple regulatory actions from the same jurisdiction to be analyzed separately when they create materially distinct legal interventions.

## Coding Framework

Each regulatory action was reviewed against a common coding framework.

The three broad **areas of regulation** are:

**Account and Service Access** — rules governing whether and under what conditions users may access or maintain accounts on covered services.

**Feeds and Recommendation Systems** — rules governing personalization, recommender systems, feed choice, or duties associated with algorithmic recommendations.

**Engagement Design** — rules governing platform features or design practices intended to shape or prolong user engagement.

Within those areas, the dataset tracks specific legal requirements using binary variables. A value of `1` indicates that the enacted legal text contains a qualifying requirement under the project’s coding rules; a value of `0` indicates that it does not.

The dataset also maps regulatory actions to broader **regulatory approaches**: Direct Limits, User Choice and Control, Parental Controls, Warnings and Interruptions, and Broader Safety Duties. These variables describe the form of intervention rather than the subject matter being regulated.

The full variable definitions and coding rules are documented separately in the data dictionary.

## Legal Status

Because enactment does not necessarily mean that a law is currently operative, legal status is treated separately from substantive coding.

Each regulatory action is classified as:

**In Force**, **Partially Operative**, **Not Yet Effective**, **Blocked**, or **Invalidated/Repealed**.

Status reflects the legal position as of **September 11, 2026**. Where litigation, injunctions, implementation dates, or other developments affected operation of a law, those developments were reviewed separately from the enacted text.

Substantive coding generally reflects the enacted regulatory architecture even when a provision is blocked or not yet operative. The `operative_status`, `status_note`, and related source fields identify those distinctions.

## Sources and Verification

Primary legal sources were used wherever available, including enacted statutory text, regulations, official legislative materials, and official legal publications. Separate status sources were used where necessary to verify litigation, injunctions, effective dates, or other developments affecting operation of a regulatory action.

The dataset records primary-source URLs, status-source URLs where applicable, supporting sources, coding notes, status notes, and the date on which each action was last verified.

## Limitations

The project is descriptive and comparative rather than inferential. The eight regulatory systems form a purposive sample and should not be interpreted as representative of all global approaches to social media regulation.

The analysis describes enacted legal requirements and their operative status at a defined cutoff date. It does not measure enforcement intensity, platform compliance, behavioral effects, policy effectiveness, or the ultimate outcome of ongoing litigation.
