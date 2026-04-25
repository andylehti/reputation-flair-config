# Terms and Conditions for Reputation Flair

***Last updated:** April 25, 2026*

Please read these Terms and Conditions carefully before using the Reputation Flair Devvit application (the “App” or “Service”).

This application may be referred to interchangeably as “Reputation Flair” (“RF”), “Reputation Flair System” (“RFS”), “reputation-flair,” “reputation_flair,” “Bot Shield,” “Human Verification Module,” “Subreddit Stats by Reputation Flair,” or the “Reputation Portal,” including any capitalization or formatting variations thereof, all of which refer to the same underlying system and service (collectively, “Reputation Flair,” the “App,” the “Service,” “we,” “us,” or “our”).

By accessing or using the App, you agree to these Terms. If you do not agree, do not use the App.

## 1. Definitions

**Application** means the Devvit application identified as Reputation Flair.

**Service** means the Reputation Flair application and related features made available through Reddit and Devvit.

**Operator** means the person or entity responsible for publishing and maintaining the App.

**Reddit Platform** means Reddit, Devvit, Reddit APIs, Reddit services, Reddit content, and related Reddit policies, permissions, infrastructure, and developer services.

**You** means the person or entity using, accessing, configuring, moderating through, or interacting with the App.

**Subreddit** means a Reddit community where the App is installed or used.

## 2. Operator Information

Reputation Flair is operated by Andrew Lehti and/or Metopedia, as applicable to the published App listing.

For legal, support, or policy questions, replace this line with the correct live contact email before publishing.

## 3. Reddit Platform and Third-Party Terms

Reputation Flair operates on Reddit’s Devvit platform and depends on Reddit infrastructure, permissions, APIs, content, and policies.

Your use of the App is also subject to Reddit’s applicable terms, rules, policies, developer terms, data protection terms, and platform requirements, including Reddit’s User Agreement, Privacy Policy, Reddit Rules, Developer Terms, Devvit Rules, Data API Terms where applicable, and related Reddit policies.

The App does not require your Reddit password and does not ask you to provide login credentials.

## 4. Eligibility

You must be at least 13 years old to use the App. If you are under the age of majority in your jurisdiction, you may use the App only with the involvement and permission of a parent or legal guardian.

You must also be eligible to use Reddit and the subreddit where the App is installed.

## 5. Description of the Service

Reputation Flair is a subreddit-focused reputation, moderation-assistance, flair, dashboard, transparency, and optional human-verification tool.

Depending on moderator configuration, the App may include features such as:

- subreddit-specific reputation scoring
- good and bad reputation counters
- broad discourse trigger categories
- user flair updates
- reputation-based flair color
- preserved user flair-head text
- subreddit leaderboards
- subreddit transparency dashboards
- daily and all-time subreddit statistics
- RFstats moderator notes
- moderator review routing
- public-view removal routing
- verification-only participation gates
- human-verification challenges
- verification badges
- verification-only removal restoration
- portal custom posts
- exact comment commands such as `!rfcheck me`, `!rfcheck op`, and `!rfcheck u/username`
- rate limits and abuse-prevention controls

The Service may change over time. We may add, modify, suspend, or remove features at any time.

## 6. Moderator Configuration

Subreddit moderators may configure the App through Reddit/Devvit settings or an external configuration generator. Moderators are responsible for choosing settings appropriate for their subreddit, including settings for flair, review, removal, verification, restoration limits, and display behavior.

The App may behave differently across subreddits depending on moderator settings.

We may change available configuration options, defaults, supported fields, UI labels, and internal behavior over time.

## 7. User Conduct

You agree not to:

- use the App for unlawful activity
- harass, threaten, abuse, or target others
- attempt to exploit, reverse engineer, disrupt, or interfere with the App or Reddit systems
- automate abuse, spam, vote manipulation, or other prohibited platform activity
- scrape, harvest, or exfiltrate Reddit data through the App
- use the App in violation of Reddit’s rules, Devvit rules, subreddit rules, or applicable law
- attempt to bypass reputation, scoring, verification, moderation, rate-limit, or anti-abuse safeguards
- submit commands, comments, posts, or interactions designed to overload the App or evade restrictions

We may limit, restrict, suspend, or terminate access if your use creates legal, security, abuse, moderation, technical, or platform-risk concerns.

## 8. Reputation Scores, Flair, and Statistics

The App may calculate and display reputation scores, good/bad contribution counts, reputation points, category counters, bot-trigger rates, streaks, verification state, and leaderboard positions.

These values are App-generated, subreddit-specific, approximate operational signals. They are not official Reddit account status, legal findings, employment-screening data, background-check data, or proof of a user’s character, identity, or intent.

The App may update or recalculate values after new activity, configuration changes, verification changes, app updates, bug fixes, moderation actions, or data cleanup.

We do not guarantee that any score, flair, leaderboard position, statistic, command reply, dashboard value, mod note, or transparency value will be accurate, uninterrupted, complete, permanent, or available indefinitely.

## 9. Moderation Assistance and Removal Behavior

If enabled by moderators, the App may route content for review, apply public-view removals, add or update moderator notes, or mark moderation state. The App is a moderation-assistance tool and does not replace moderator judgment.

Moderators remain responsible for enforcing subreddit rules and Reddit rules. Users remain responsible for the content they post or comment.

The App may remove or flag content when configured thresholds are met. It may also decline to restore content when content was removed for reasons other than verification-only gating.

## 10. Human Verification

If enabled, the App may provide a human-verification challenge. Verification features may affect flair, verification badges, participation gates, restoration of verification-only removals, and dashboard fields.

Verification does not guarantee identity, trustworthiness, safety, or rule compliance. It only reflects the App’s current verification state for the subreddit and the configured feature set.

Verification may expire. In the current design, expiry is evaluated lazily when a verified user later posts or comments after expiration, rather than through a continuous background scan.

## 11. Verification-Only Removed Content

If enabled, the App may temporarily remove posts or comments only because a user is not verified. If restore-after-verification is enabled, the App may later approve eligible verification-only removed items after the user verifies, subject to configured caps.

The App will not intentionally approve items removed for other moderation reasons, such as normal removal thresholds or moderator action unrelated to verification-only gating.

Restoration is not guaranteed. It may fail because of Reddit platform behavior, permission limits, deleted content, moderator actions, configuration changes, app errors, or other technical reasons.

## 12. Portal, Commands, and Dashboard

The App may create or repair a subreddit portal post. The portal may show dashboards, leaderboards, transparency data, and lookup features.

The App may also reply to exact commands such as `!rfcheck me`, `!rfcheck op`, or `!rfcheck u/username`. Commands are rate-limited and may be disabled, ignored, or changed at any time.

Portal, dashboard, command, and lookup data may be delayed, cached, unavailable, or incomplete.

## 13. Data Use and Privacy

The App retains only data reasonably needed to operate, secure, improve, and administer the Service. Some data may be stored temporarily in Redis or related Devvit runtime storage for scoring, caching, stats, leaderboards, moderation-safe operations, verification, rate-limiting, abuse prevention, and audit or diagnostic purposes.

Your use of the Service is also governed by the App’s Privacy Policy, which explains what data the App collects, how it is used, how long it may be retained, and how deletion-related handling works.

## 14. No Scraping, Re-Identification, or Surveillance Use

You may not use the App to scrape Reddit, harvest data outside authorized access paths, overload systems, identify users outside Reddit, de-anonymize users, re-identify users across unrelated datasets, conduct background checks, or create surveillance-style datasets.

The App is intended to operate within the subreddit context where it is installed and authorized.

## 15. Changes to Rules, Settings, and Stored Data

Reputation Flair may change its scoring rules, categories, thresholds, flair format, verification rules, portal design, dashboard behavior, command behavior, storage schema, subreddit settings, or other operational settings at any time.

When significant changes occur, the App may purge, rebuild, overwrite, or stop using stored data to preserve consistency, technical integrity, and moderation safety. This may include deletion or rebuilding of reputation data, leaderboards, daily counters, cached snapshots, portal metadata, verification state, rate-limit records, moderation markers, and user statistics.

Some temporary or separately scoped technical records may expire automatically rather than being deleted immediately.

Users should not rely on permanent storage of scores, flair states, leaderboards, dashboards, command replies, moderation markers, or verification state.

## 16. User Actions and Posted Content

If the App provides features that create or submit content on Reddit, those features are subject to Reddit and Devvit permissions, review status, and platform behavior.

You remain responsible for content you submit or authorize through Reddit or through the App. You must not use the App to create prohibited, unlawful, abusive, manipulative, spammy, infringing, or policy-violating content.

We may disable or restrict posting-related features at any time.

## 17. Intellectual Property

The App, including its software, logic, design, branding, text, non-user-generated content, and related materials, is owned by its operator or licensors and protected by applicable intellectual property law.

You may use the App only as permitted by these Terms and applicable platform rules.

Reddit, Devvit, subreddit names, Reddit usernames, posts, comments, and other Reddit platform materials remain subject to Reddit’s policies and the rights of their respective owners.

## 18. Feedback

If you provide feedback, suggestions, bug reports, feature requests, or related information, you grant us permission to use that feedback to improve, modify, operate, and maintain the App without compensation or obligation to you.

## 19. Termination and Suspension

We may suspend, restrict, or terminate access to the App at any time, with or without notice, including where required by law, Reddit platform rules, subreddit moderator configuration, security concerns, abuse prevention, technical issues, or operational necessity.

Upon termination, your right to use the App ends immediately.

## 20. Disclaimer of Warranties

The Service is provided on an “as is” and “as available” basis. To the fullest extent permitted by law, we disclaim all warranties, express or implied, including warranties of merchantability, fitness for a particular purpose, non-infringement, availability, accuracy, reliability, security, and loss-free operation.

We do not guarantee that the Service will always be available, error-free, secure, accurate, complete, or free from data loss.

## 21. Limitation of Liability

To the fullest extent permitted by law, we will not be liable for any indirect, incidental, special, consequential, exemplary, or punitive damages, or for any loss of data, scores, access, goodwill, reputation, verification status, leaderboard position, moderation outcome, or use arising from or related to the Service.

If liability cannot be excluded, our total liability arising out of or related to the Service will be limited to the lesser of:

- the amount you paid us directly for the Service in the prior 12 months, or
- USD $100.

## 22. Indemnity

To the fullest extent permitted by law, you agree to defend, indemnify, and hold harmless the App operator and related parties from claims, damages, liabilities, costs, and expenses arising from your misuse of the App, violation of these Terms, violation of Reddit or subreddit rules, or violation of applicable law.

## 23. Changes to the Service or Terms

We may update the Service or these Terms at any time. If we make material changes, we may update the date above and provide notice where appropriate. Continued use of the App after changes take effect means you accept the revised Terms.

## 24. Governing Law

These Terms are governed by the laws of the State of Minnesota, United States, except where applicable law or Reddit’s applicable platform terms require otherwise.

## 25. Contact

For legal, support, or policy questions, contact the App operator.

**Operator:** Andrew Lehti and/or Metopedia or any account operated by either party, as applicable to the published App listing.

**Email:** policy@metopedia.com
