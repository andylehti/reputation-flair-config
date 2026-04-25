# Reputation Flair FAQ

## FAQ 01 — What does this app do?

This app tracks contribution quality over time inside this subreddit. It measures good rep, bad rep, triggers, activity, reputation score, verification status, and bot-trigger behavior. It can also flag content for review, filter content from public view, update flair, and handle human verification.

The goal is transparency, self-awareness, and accountability. It is designed to help users understand how they contribute, to make low-value discourse easier to spot over time, and to make troll-like or bot-like behavior patterns easier to recognize.

---

## FAQ 02 — What happens when I post or comment?

Every post or comment follows this full processing flow:

1. Load user record and user stats
2. Apply weekly bad decay
3. Increment post/comment count
4. Update streak
5. Compute `goodRaw`
	`goodRaw = floor(textContextScore / goodDivisor) + bonusScore`
6. Find all bad matches
7. Convert bad matches into severity score
8. Apply bad buffer
9. Apply text context score forgiveness
10. Add category spread/concentration penalties
11. Apply OP self-reply protection if enabled
12. Compute review/remove eligibility
13. If normal removal triggered, remove for that reason first
14. Else check verification gate
15. If the item is blocked only because the user is not verified, stop there and treat it as a verification-only moderation outcome
16. Otherwise add bad rep points to the user
17. Reduce good rep points if bad exists
18. Add good rep points
19. Mark the item good or bad
20. Update user stats, subreddit stats, and daily stats
21. Update the mod note if enabled
22. Review if needed
23. Update flair.

Variables:

* **textContextScore** = a quality/context value for the post or comment
* **goodDivisor** = a scaling value that controls how quickly textContextScore turns into good rep
* **bonusScore** = extra good-side value from approved positive contribution signals
* **scoreCeiling** = the maximum good rep points one item can receive.

Plain English: the app reads the item, checks discourse triggers, calculates good rep and bad rep, applies protections and reductions, decides whether moderation rules or verification rules apply, calculates scores through an algorithm and margin of error, then updates stats and flair.

---

## FAQ 03 — What do my activity, rep, and contribution stats mean?

**Subreddit streak** means your current streak in this subreddit.

**Posts** means your total posts here.

**Comments** means your total comments here.

**Contributions** means posts plus comments combined.

**Bad rep points** means your total negative rep points.

**Good rep points** means your total positive rep points.

**Good rep contributions** `⭐` are counts of items whose final reduced bad rep is `0`.

**Bad rep contributions** `💀` are counts of items whose final reduced bad rep is greater than `0`.

**Bad / good contribution ratio** shows how much of your activity ends negative versus positive.

Important distinction:
- **good rep contributions** are counts of items
- **bad rep contributions** are counts of items
- **good rep points** and **bad rep points** are point totals
- counts and points are not the same thing

What matters most is the average pattern over time. The more someone engages, the more they can show whether their discourse is meaningful, respectable, and legitimate. This system is designed to make users wary of people who mainly try to shut down conversations, add nothing to the conversation, harass others, dismiss others, or show strong patterns of cognitive bias.

---

## FAQ 04 — What do my trigger, verification, and bot stats mean?

**💥 Attack triggers** are direct attack matches.

**⛔ Shutdown triggers** are dismissal or shutdown matches.

**🤥 Credibility triggers** are attacks on honesty, motives, or legitimacy.

**💅 Condescension triggers** are snark, belittling, or provocation.

**🎭 Bad faith triggers** are false framing or twisted intent.

**⛽ Gaslighting triggers** are manipulation, blame reversal, or reality distortion.

**⚠️ Total triggers** is the compact trigger total shown in summaries and flair.

**🛡️ Verified** shows whether you are currently verified.

**📅 Verified Since** shows when the current verification began.

**⏳ Verification Expires** shows when the current verification ends, if expiry is enabled.

**❌ Failed Verifications** shows how many recent verification attempts failed.

**🤖 Bot Triggers** are behavioral signals. They reflect suspicious behavior patterns, posting/commenting context, and related verification outcomes.

---

## FAQ 05 — How do Cognitive Biases Fit into the Total Trigger Count?

**⚠️ total triggers** are not a pure indication of toxicity, manipulation, or bot-like behavior. Very low-risk matches count the same as very high-risk matches in the total triggers count. Other metrics are needed to evaluate the type of discourse a user will have.

If someone has a high number of cognitive biases, they will often dismiss, shut down, or react defensively, which can raise this value. That does not automatically mean they are harassing others.

This is why total triggers should be read together with:
- category totals
- good rep vs bad rep balance
- good vs bad contributions
- reputation score
- contributor status
- verification and bot-trigger information

---

## FAQ 06 — What counts as a trigger?

Triggers are phrase, token, stem, or pattern matches tied to bad discourse. They are not all equal. Some are lower risk and only suggest weak, low-value discourse. Others are medium or high risk and carry stronger severity. The app distributes these matches across 25 and counting sub-databases, and those databases are grouped into 6 discourse categories.

Low-risk trigger examples include: cope, yikes, cringe, sure buddy, ok pal, nice try, that’s cute, rent free, bad take, who asked.

These usually do not add much to the conversation. They are not necessarily super toxic or evil on their own, but repeated low-value discourse can still become a pattern. This scoring system is meant to add self-awareness and accountability, and to help other users see who doesn't add constructively to the conversation.

Medium-risk trigger examples include: low iq, smooth brain, brain dead, learn to read, go back to school, you are delusional, seek therapy.

There is also leeway. A phrase like “that’s cute” may not always be negative, so the algorithm uses a margin of error based on the context of the post or comment. That is why the final reduced result matters more than a raw match by itself.

---

## FAQ 07 — What is Reputation Score and Contributor Status?

**⚖️ Reputation Score** is the main score shown in flair. It combines good vs bad contribution history with good rep points and bad rep points. A higher score means stronger contribution history. A lower score means weaker contribution history.

Contributor Status uses these ranges:
- **Elite contributor** = +85% to +100%
- **Top contributor** = +70% to +84%
- **Strong contributor** = +50% to +69%
- **Reliable contributor** = +30% to +49%
- **Positive contributor** = +10% to +29%
- **Mixed contributor** = -9% to +9%
- **Developing contributor** = -29% to -10%
- **Limited contributor** = -49% to -30%
- **Minimal contributor** = -69% to -50%
- **Needs improvement** = -100% to -70%

---

## FAQ 08 — What categories and databases does the app use?

There are **25 and counting total sub-databases called arrays** distributed into **6 categories**:
- **💥** direct attacks
- **⛔** dismissal / shutdown
- **🤥** credibility attacks
- **💅** condescension / provocation
- **🎭** bad-faith framing
- **⛽** manipulation / gaslighting
- **🤖** bot triggers

Each database is mapped into the category that best fits its discourse type.

The current bad-rep databases are:
`mentalHealthPhrases`
`goAwayDismissalPhrases`
`intelligenceAttackPhrases`
`condescensionSnarkPhrases`
`credibilityErasersPhrases`
`postHistoryAttackPhrases`
`shillBotNpcPhrases`
`tribePhrases`
`baitTrollPhrases`
`moralShutdownPhrases`
`projectionFlipPhrases`
`feignedConfusionPhrases`
`extraBadPhrases`
`argumentativePhrases`
`mentalHealthTokens`
`oneWordTokens`
`stems`
`mentalHealthStems`
`shillStems`
`insultStems`
`nonsenseStems`
`memeStems`
`mildStems`
`botNgram`
`nonEnglishTokens`

---

## FAQ 09 — What is textContextScore?

**textContextScore** is a quality/context value for the post or comment.

At a high level:
- it can strengthen good rep
- it can also increase forgiveness on the bad-rep side
- it helps the app avoid treating every post or comment as if it had the same quality or context

The app does not publicly expose every hidden internal factor that contributes to textContextScore.

---

## FAQ 10 — How are good rep points calculated?

Good rep starts with this formula:

`goodRaw = floor(textContextScore / goodDivisor) + bonusScore`
`earnedGood = clamp(goodRaw, 0, scoreCeiling)`

In compact terms:
- **textContextScore** = a quality/context value for the post or comment
- **goodDivisor** = a scaling value that controls how quickly textContextScore turns into good rep
- **bonusScore** = extra good-side value from approved positive contribution signals
- **scoreCeiling** = the maximum good rep points one item can receive

`clamp(goodRaw, 0, scoreCeiling)` means:
- if `goodRaw` is below `0`, use `0`
- if `goodRaw` is above `scoreCeiling`, use `scoreCeiling`
- otherwise keep `goodRaw` as-is

So the app builds a starting good-side value, then forces it to stay inside the allowed range.

---

## FAQ 11 — How are bad rep points calculated?

The bad-rep side works in stages.

**Step 1: find all matches.** The app scans phrase databases, token databases, stem databases, regex rules with extreme-normalization, and custom bad terms added by subreddit moderators. It also removes weaker overlapping matches where possible.

**Step 2: convert match weights into severity.** Going forward, this app is only in `BAD_SCORING_MODE = "sev"`, which means it does not count raw matches directly. Each kept hit becomes `severity = min(5, ceil(abs(weight) / 2))`.

Examples:
- `-10 → 5`
- `-8 → 4`
- `-7 → 4`
- `-6 → 3`
- `-5 → 3`
- `-4 → 2`
- `-3 → 2`
- `-2 → 1`

**Step 3: sum severity.**
`rawBadScore = sum of severities of all kept matches`

**Step 4: apply bad buffer.**
If `textContextScore < 15`, there is no buffer. If `textContextScore >= 15`, subtract `3`. This gives:
`bufferedBad = max(0, rawBadScore - effectiveBuffer)`

**Step 5: apply text-context forgiveness.**
`streakAdjustment = min(128, floor(streak / 2))`
`errorDivisor = 256 - streakAdjustment`
`badReduced = max(0, scaledBad - floor(textContextScore / errorDivisor))`

Larger textContextScore gives more forgiveness, and a higher streak slightly increases that effect.

---

## FAQ 12 — What else changes the score?

Several things can change the final result.

**Weekly decay:** if enabled, bad rep points decay once per full week since last activity:
`decayFactor = 1 - weeklyDecayPercent/100`
`badPoints = badPoints * decayFactor^weeksPassed`

**Streak modes:** `noexpire`, `hourly24`, and `hourly48`. In `noexpire`, the streak increments once per new UTC day when the user posts or comments and does not expire. In the current builder, `hourly24` and `hourly48` are the two rolling-expiry modes exposed in the moderator UI for longer inactivity windows.

**Extra penalties:** if any one category totals `>= 3` points, add `+1`; if 4 or more categories were hit, add `+2`.

**OP self-reply protection:** if enabled, and the user comments on their own post, good rep points are capped to `ownPostCommentGoodCap`, bad rep points are forced to `0`, and category flags are cleared. Formula: `earnedGood = min(earnedGood, ownPostCommentGoodCap)`, `badReduced = 0`, `flags = 0`.

---

## FAQ 13 — What do good rep contributions and bad rep contributions mean?

These are often confused with points, but they are not the same thing.

- **good rep contributions** are counts of items
- **bad rep contributions** are counts of items
- **good rep points** and **bad rep points** are point totals
- counts and points are not the same thing

A user could have many contributions but relatively modest rep-point totals, or fewer contributions with stronger rep-point totals. What matters over time is the overall pattern and average quality of the discourse.

---

## FAQ 14 — What data does the app keep for each user and the subreddit?

For each user, the app keeps a running record:
- `a` = total good rep points
- `b` = total bad rep points
- `c` = total comments made
- `p` = total posts made
- `g` = streak count
- `si` = last streak increment time
- `la` = last activity time
- `f` = last flair update time

It also keeps a core behavior stats array:
- `[0]` direct attacks
- `[1]` dismissal / shutdown
- `[2]` credibility attacks
- `[3]` condescension / provocation
- `[4]` bad-faith framing
- `[5]` manipulation / gaslighting
- `[6]` total posts
- `[7]` total comments
- `[8]` good posts/comments count
- `[9]` bad posts/comments count
- `[10]` bot triggers
- `[11]` failed verification attempts
- `[12]` verified status

Verification state used by the live verification gate and flair badge can also be stored separately as a simple Redis value:
- `verified = 0` → not verified
- `verified = 1` → verified
- `verified = 2` → expired

Some builds may also mirror verification state into other stats, but the current verification gate checks the separate `verified` value directly.

For the subreddit, it tracks totals since installation for:
- each of the 7 categories
- good comments
- bad comments
- good posts
- bad posts
- total comments
- total posts
- total items
- unique users
- failed verification attempts
- verified users

The array mapping is simple:
- `[0]` through `[5]` are category counters
- `[6]` and `[7]` are activity counters
- `[8]` and `[9]` are good/bad contribution counters
- `[10]` through `[12]` are bot/verification related

---

## FAQ 15 — What affects review, removal, and exemptions?

Review can be enabled or disabled by moderators. Removal can also be enabled or disabled separately. Moderators decide how sensitive those systems are by choosing the thresholds.

What can affect review, removal, and exemptions:
- moderators can be exempt
- approved users can be exempt
- OP post self-replies can be protected
- verification rules can apply after normal removal rules
- moderators can choose whether very high-risk content is flagged or removed by changing the thresholds

---

## FAQ 16 — What happens if content is blocked for verification?

If content is blocked only because the user is not verified, the app treats that differently from normal removal.

Important rules if both verification is enabled and gated participation is enabled:
- if the content already qualifies for normal removal, it is removed for that reason first
- it is **not** treated as verification-only removal in that case
- if the content is blocked only because the user is not verified, it can be handled under the verification rules instead
- if restore-after-verification is enabled, previously verification-removed items can be restored after the user becomes verified
- if post blocking or comment blocking is on, reminder comments may be turned off because blocking takes priority

---

## FAQ 17 — What do the verification fields mean?

**🛡️ Verified** = whether the account is currently verified.

**📅 Verified Since** = when the current verification period began.

**⏳ Verification Expires** = when the current verification ends, if expiry is enabled.

**❌ Failed Verifications** = how many recent verification attempts failed.

These fields are meant to show verification state clearly without exposing the internal verification scoring system. In the current verification flow, the gate and flair badge can also rely on a simple verified state of `0`, `1`, or `2`.

---

## FAQ 18 — What happens to flair when someone is verified?

If human verification is active and the account's verification state is verified, the normal streak badge is replaced by the verification badge.

If the account is not verified, the normal streak badge remains.

---

## FAQ 19 — What does “since installation” mean?

For subreddit totals, **since installation** means:
- totals are subreddit-specific
- they accumulate from the time this app was installed in this subreddit
- they are not global across Reddit

So the totals reflect this community’s history with the app, not all of Reddit.

---

## FAQ 20 — Why might flair or stats not update instantly?

Some visible updates may be delayed.

This usually happens because high-traffic mode is enabled. High-traffic mode reduces unnecessary flair rewrites in busy communities and helps prevent hitting the database too aggressively.

---

## FAQ 21 — What is an RFstats mod note?

An **RFstats mod note** is a compact moderator summary stored on the user's mod note when that feature is enabled. The old mod note is removed, and a new one is added when updated.

It is meant to give moderators a quick snapshot of:
- good vs bad pattern history.
- trigger/category profile
- contribution counts
- current rep tendencies
- what type of negative discourse they may be involved in, if any.

It updates automatically when enabled.

---

## FAQ 22 — How are final good rep points and bad rep points applied?

After all checks, the app adds bad rep first:
`user.badPoints += badReduced`

If bad rep was earned, good rep is reduced by:
`reduction = min(6, floor(badReduced / 2))`
`earnedGood = max(0, earnedGood - reduction)`

Then it adds good rep:
`user.goodPoints += earnedGood`

So bad rep can partially cancel good rep on the same item.

---

## FAQ 23 — How does the app decide whether an item is good or bad?

A post or comment counts as **good** if its final reduced bad rep is `0`.

A post or comment counts as **bad** if its final reduced bad rep is greater than `0`.

So:
- `+1 good post` if final reduced bad rep is `0`
- `+1 bad post` if final reduced bad rep is greater than `0`
- `+1 good comment` if `badReduced === 0`
- `+1 bad comment` if `badReduced > 0`

For the user stats array:
- posts increment `[6]`
- comments increment `[7]`
- good items increment `[8]`
- bad items increment `[9]`

Subreddit totals also increment good posts, bad posts, good comments, and bad comments the same way.

---

## FAQ 24 — How is Reputation Score calculated?

There are two reputation-style percentages.

**1. Simple user score percent**
`100 * (goodPosts - badPosts) / (goodPosts + badPosts)`
If no items exist, it is `0`.

**2. Full repScore**
This is what flair uses.

Base:
`base = 100 * (goodPosts - badPosts) / (goodPosts + badPosts)`

Point-shift component:
- `a = goodRepPoints / (goodPosts + 1)`
- `b = badRepPoints * (badPosts + 1)`
- `shift = 40 * (a - b) / (a + b)`

Final:
`repScore = clamp(round(base + shift), -100, 100)`

Plain English:
- many good posts help
- many bad posts hurt
- high total bad rep points hurt harder
- high good rep points help

---

## FAQ 25 — What does the flair mean?

The flair uses:
- offense total = sum of the discourse category counters `[0..5] + [10]`
- activity = posts + comments = `[6] + [7]`
- good item count = `[8]`
- bad item count = `[9]`
- rep score = `repScore(...)`
- streak = `g`

Old style:
`+goodRepPoints ∣ -badRepPoints`

New style:
`⚖️ rep% ∣ ⚠️ offenseCount ∣ ⌨️ [activity]`

The exact visible flair fields depend on `flairParts`. The current builder supports combinations such as `streak`, `head`, `rep`, `warn`, `activity`, `good`, and `bad`.

If human verification is active and the user is verified, the normal streak badge can be replaced with the verification badge.

---

## FAQ 26 — What is the shortest explanation possible?

Short version:
- triggers create bad-side pressure
- text context score creates good-side value
- protections and reductions shape the final result
- final `badReduced` decides good vs bad contribution outcome
- that updates rep, stats, moderation outcomes, flair, and sometimes verification state

---

## FAQ 27 — What data does the app store?

The app stores **subreddit-specific moderation and reputation data**, not a private copy of your Reddit account.

At a high level, the current code stores:
- per-user rep totals and counters
- per-user activity counts
- broad per-user category counters
- subreddit-wide totals and daily totals
- moderation state flags, such as processed / reviewed / removed markers
- verification state and related verification metadata
- some flair-related state, such as cached flair-head text when needed
- RFstats mod-note summaries when that feature is enabled, which is merely a tally of 7 category triggers, and other numerical stats.

This data is used to calculate rep, show flair, track moderation outcomes, and keep subreddit-level totals consistent over time.

---

## FAQ 28 — Are my posts or comments stored by the app?

The app **reads** post and comment text in order to score discourse, but the code nor any part of the app does **not** keep a full nor partial private Redis copy of any post body or comment body; nor is any informaiton transmitted externally.

In the current build:
- the text is read and processed for scoring
- rep totals, category counts, and moderation outcomes are stored
- no text whether full nor partial is not saved into the app's Redis records, nor is any data transmitted externally outside of Redis/Reddit

One narrow exception is flair handling: if custom flair text is preserved, the app can cache the user-facing flair-head segment so it can rebuild flair cleanly later. That is flair state, not a stored copy of a post or comment body.

So the short answer is:
- **scored? yes**
- **used for calculations? yes**
- **full body stored by the app in Redis? not normally**

---

## FAQ 29 — Is any personal information stored?

The app stores only the minimum subreddit-linked data needed for its features.

That can include:
- Reddit username references inside subreddit-scoped keys
- user-level rep totals and counters
- user-level moderation flags
- verification state
- verification timestamps or related verification fields when enabled
- flair-related state needed for rebuilding flair

This app / code does **not** ask nor store things like:
- email addresses
- phone numbers
- legal names
- home addresses
- location data
- identifying information
- demographics
- payment data
- IP addresses
- browser data
- browsing data
- reddit history
- posts or comments you've viewed
- comments and posts, neither full nor partial
- individual tallies on specific item triggers

This is a subreddit moderation, bot shield challenge authorization, and reputation system. Its storage is centered on Reddit-side activity, subreddit-scoped counters, moderation state, and verification state.

---

## FAQ 30 — Are removed items or triggered phrases saved?

Not in the same way.

**Triggered phrases:**
The current code does **not** normally persist the raw matched trigger phrases into Redis as a long-term phrase log. Instead, it stores the results of scoring, such as:
- category counters
- good rep and bad rep totals
- good/bad contribution counts
- subreddit totals
- moderation outcomes

**Removed items:**
The app does store moderation state markers so it knows whether an item was processed, reviewed, or removed. For verification-only removals, the current code can also store a small metadata record so the item can be restored later if that feature is enabled.

That verification-removal metadata can include:
- lowercase username
- item type
- item id
- timestamp

It does **not** need to keep a full private copy of the removed post or comment text in order to do that.

---

## FAQ 31 — What data is visible to moderators, and what stays internal?

Some data is surfaced to moderators, and some stays internal.

**Moderator-visible examples:**
- RFstats mod notes when enabled
- removed / reviewed content states
- subreddit totals shown through the app
- user flair output

**Internal app-state examples:**
- processed flags
- review/remove markers
- verification state values
- verification-restoration tracking
- cached counters and daily snapshots

So the app does keep internal moderation state which context is thrown away, but that is different from publishing a full public log of everything it reads.
