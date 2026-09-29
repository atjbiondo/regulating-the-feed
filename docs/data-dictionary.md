# Data Dictionary

This document defines the variables used in the *Regulating the Feed* dataset.

The dataset contains 34 regulatory actions and 44 fields. One row represents one qualifying regulatory action. Fields include descriptive information, legal-status variables, specific requirement coding, derived regulatory-area indicators, regulatory-approach indicators, source information, and research notes.

## Coding Conventions

Binary variables use:

- `1` = the regulatory action contains a qualifying requirement under the project’s coding rules
- `0` = the regulatory action does not contain a qualifying requirement under that variable

Substantive coding reflects the enacted regulatory architecture. Whether a provision was in force, partially operative, not yet effective, blocked, or otherwise affected by litigation at the study cutoff is recorded separately through the legal-status fields.

A blank text or source field does not mean the same thing as a binary `0`. A blank generally indicates that the field was not applicable or that no separate value or source was required.

The three `regulates_*` fields are derived separately from the specific requirements coded within each regulatory area. They are independent and nonexclusive: a regulatory action may address one, two, or all three areas.

The `strategy_*` fields are also nonexclusive. A single regulatory action may use more than one regulatory approach.

## Identification and Jurisdiction

| Variable | Type | Definition |
| --- | --- | --- |
| `intervention_id` | Text | Unique project identifier assigned to each regulatory action. |
| `jurisdiction` | Text | Primary regulatory system or country associated with the action. |
| `subjurisdiction` | Text | State or other subnational jurisdiction where applicable. Blank for supranational or national actions without a subjurisdiction. |
| `government_level` | Categorical | Level at which the action was enacted: `Supranational`, `National`, or `State`. |
| `intervention_name` | Text | Concise project-facing name for the regulatory action. |
| `official_name` | Text | Formal statutory, regulatory, legislative, or official citation or name associated with the action. |

## Dates and Legal Status

| Variable | Type | Definition |
| --- | --- | --- |
| `year_enacted` | Integer | Calendar year in which the action was enacted or formally adopted. |
| `enactment_date` | Date | Date on which the action was enacted, signed, adopted, or otherwise formally completed. |
| `effective_date` | Date | Principal effective or operative date used for the comparative dataset. Phased or partial implementation is explained in `status_note` where relevant. |
| `operative_status` | Categorical | Legal status of the action at the study cutoff. Categories are `In Force`, `Partially Operative`, `Not Yet Effective`, `Blocked`, and, where applicable, `Invalidated/Repealed`. |
| `status_as_of` | Date | Common cutoff date used to assess operative status. |
| `last_verified` | Date | Date on which the row was most recently checked against its supporting legal sources. This may be later than `status_as_of` because verification can occur after the historical cutoff. |

## Population and Scope

| Variable | Type | Definition |
| --- | --- | --- |
| `target_population` | Categorical | Population primarily governed by the tracked provisions: `Minors`, `Mixed`, or `All Users`. |
| `age_threshold` | Text | Relevant age threshold or age-based coverage rule stated in the action. |
| `scope_type` | Categorical | Whether the tracked action is `Social-Media Specific` or applies to `Broader Online Services`. |

## Specific Requirements

The following variables record specific legal requirements within the three regulatory areas tracked in the study.

### Account and Service Access

| Variable | Type | Coding Rule |
| --- | --- | --- |
| `account_age_restriction` | Binary | `1` where the action directly restricts or conditions account creation, maintenance, or access based on age. |
| `age_assurance` | Binary | `1` where the action imposes a qualifying age-verification or age-assurance requirement within the tracked access framework. Age determination used only to identify users subject to downstream protections is not automatically coded as Access. |
| `parental_consent` | Binary | `1` where parental or legal-representative consent is required for a minor to create, maintain, or access a covered account or service. Parental settings or supervisory tools alone do not satisfy this variable. |

### Feeds and Recommendation Systems

| Variable | Type | Coding Rule |
| --- | --- | --- |
| `personalized_feed_restriction` | Binary | `1` where the action directly restricts, conditions, or limits personalized, profile-based, or covered addictive recommendation feeds. |
| `nonprofiled_feed_choice` | Binary | `1` where the action requires or protects access to a nonprofiled, chronological, user-selected, or comparable alternative to a personalized recommendation feed. |
| `recommender_safety_duty` | Binary | `1` where the action imposes a qualifying risk, safety, assessment, or mitigation duty specifically connected to recommender systems or algorithmic recommendations. |

### Engagement Design

| Variable | Type | Coding Rule |
| --- | --- | --- |
| `addictive_design_restriction` | Binary | `1` where the action directly restricts or prohibits covered addictive, compulsive, or comparable engagement-design practices. |
| `autoplay_restriction` | Binary | `1` where the action restricts autoplay or requires controls relating to automatic playback of content. |
| `infinite_scroll_restriction` | Binary | `1` where the action restricts continuous or infinite scrolling or requires controls over that feature. |
| `streak_reward_restriction` | Binary | `1` where the action restricts streaks, rewards, gamified engagement, or comparable engagement mechanisms. |
| `notification_restriction` | Binary | `1` where the action restricts push notifications or comparable engagement-prompting notifications. |
| `time_use_limit` | Binary | `1` where the action imposes, requires, or provides qualifying controls for daily use limits, scheduled access limits, mandatory breaks, or comparable time-based restrictions. |
| `warning_interruption` | Binary | `1` where the action requires a warning, pop-up, interruption, or comparable friction mechanism during access or continued use. |
| `design_harm_duty` | Binary | `1` where the action imposes a broader duty to assess, avoid, mitigate, or address harms arising from platform or product design rather than only regulating a named feature. |

## Derived Areas of Regulation

The three area indicators summarize whether each regulatory action addresses the project’s three broad areas of regulation.

The indicators are **independent and nonexclusive**. A regulatory action may address one, two, or all three areas.

| Variable | Type | Derivation |
| --- | --- | --- |
| `regulates_access` | Binary, derived | `1` if at least one of `account_age_restriction`, `age_assurance`, or `parental_consent` is coded `1`; otherwise `0`. |
| `regulates_recommendation` | Binary, derived | `1` if at least one of `personalized_feed_restriction`, `nonprofiled_feed_choice`, or `recommender_safety_duty` is coded `1`; otherwise `0`. |
| `regulates_engagement` | Binary, derived | `1` if at least one of `addictive_design_restriction`, `autoplay_restriction`, `infinite_scroll_restriction`, `streak_reward_restriction`, `notification_restriction`, `time_use_limit`, `warning_interruption`, or `design_harm_duty` is coded `1`; otherwise `0`. |

Because these areas overlap, the number of actions coded across the three fields can exceed the total number of regulatory actions in the dataset.

## Regulatory Approaches

These variables classify the broader form of legal intervention used by each regulatory action.

They are analytically distinct from the areas of regulation above:

- an **area of regulation** identifies what part of the platform or user experience is regulated;
- a **regulatory approach** identifies how the law intervenes.

The approach variables are nonexclusive. One regulatory action may use multiple approaches.

| Variable | Reader-Facing Label | Type | Definition |
| --- | --- | --- | --- |
| `strategy_restriction` | Direct Limits | Binary | Indicates that the action uses direct prohibitions, restrictions, defaults, or limits on access, features, or platform practices. |
| `strategy_user_control` | User Choice and Control | Binary | Indicates that the action gives users qualifying choices or controls over feeds, features, settings, or use. |
| `strategy_parental_control` | Parental Controls | Binary | Indicates that the action uses parental authorization, supervision, or control mechanisms. |
| `strategy_friction` | Warnings and Interruptions | Binary | Indicates that the action uses warnings, interruptions, prompts, or comparable friction mechanisms to interrupt or alter use. |
| `strategy_duty_based` | Broader Safety Duties | Binary | Indicates that the action imposes broader safety, risk-management, design, assessment, or mitigation duties on covered services rather than relying only on discrete feature rules. |

## Sources and Research Notes

| Variable | Type | Definition |
| --- | --- | --- |
| `primary_source_url` | URL | Primary legal or official source used to establish the enacted regulatory action and its substantive requirements. |
| `status_source_url` | URL | Source used to establish operative status where separate verification was required, such as litigation, an injunction, an implementation rule, or an effective-date source. |
| `supporting_source_urls` | URL / Text | Additional official or legal sources used to support coding, interpretation, amendments, implementation, or status. |
| `status_note` | Text | Concise explanation of operative status, including material litigation, injunctions, phased implementation, or other status qualifications. |
| `coding_note` | Text | Explanation of material or non-obvious coding decisions for the regulatory action. |
| `needs_review` | Categorical / QA | Internal quality-assurance flag identifying whether a row has an unresolved review issue. `No` indicates no outstanding review flag at publication. |
| `core_intervention_summary` | Text | Short plain-language summary of the principal regulatory intervention captured by the row. |

## Interpretation

Binary coding should not be interpreted as a score of regulatory strength, quality, restrictiveness, or effectiveness. A value of `1` indicates only that the action contains a qualifying legal requirement under the project’s defined coding rules.

Likewise, a value of `0` does not establish that a jurisdiction has no law or policy addressing that subject. It means that the specific regulatory action represented by that row does not contain a qualifying requirement for that variable within the scope of this project.

The dataset describes enacted legal architecture and operative status at a defined cutoff date. It does not measure implementation quality, enforcement intensity, platform compliance, behavioral effects, or policy effectiveness.

For the full sample-construction, inclusion, legal-status, sourcing, and coding methodology, see [`methodology.md`](methodology.md).
