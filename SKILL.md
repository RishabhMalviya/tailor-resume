---
name: tailor-resume
description: >-
  Walks through the exact steps for tailoring a resume to a given job description, conducting a gap analysis, and producing useful talking points.
---

# Resume Tailoring

This skill turns a job description into the following deliverables:
1. **Tailored Resume**
  - Only points taken from the master resume (do not invent anything new)
  - Resume points reordered, re-worded, and re-emphasized to match better with the JD's requirements 
  - The same exact format as the sample_resume (a `.docx` file). It *must* be less than 2 pages long.
  - Something that would pass an ATS, or catch the attention of a hiring team member who is speed-scanning through (possibly hundreds of) resumes
2. **Gap Analysis**
  - A gap analysis of what is missing between the role's requirements/responsibilities and my skills/experience.
3. **Talking Points and Study Plan**
  - A set of 2-5 projects/stories from the master resume to prepare well. These should be chosen for their potential to impress the hiring team.
  - A set of 2-5 concepts/technologies/deep-dives that I should study to gain an edge in the interview process. This would partially be based off of the gap analysis above.

The guiding principles throughout:
1. Reframe and re-emphasize truthfully; never fabricate
2. Maximize my chances of being considered and hired for the role by describe my skills/experience in the JD's language
3. If a requirement isn't met, say so plainly in the gap analysis rather than papering over it


## Step 0 - Load the source material (always, first)

Read the following three reference files before doing anything else. They are the single source of truth; do not tailor from memory. Look for them first under `/mnt/project/`, then under `references/`. If you don't find them in either of those location, prompt me to provide them to you.

- `contact_details.json`: Contact details that are referenced in the `master_resume.md`. This is a separate file because this information is often sensitive.
- `master_resume.md`: The full, comprehensive resume. Everything in the tailored output must trace back to something here.
- `career_profile.md`: The strategic context for my career including long-term and short-to-mid-term goals, target companies, strengths, weaknesses, and known gaps. This will drive the talking points later.
- `sample_resume.docx`: If this file is present, you will make sure that the outputted tailored resume's formatting matches it exactly. That includes how various pieces of information (such as job title, company name, timeline, location, key technologies, resume points, etc under Work Experience) are laid out. That also includes coverage of the different headings (Summary, Work Experience, Education, etc).


## Step 1 - Get and deconstruct the job description

Make sure you actually have the JD. If I give a URL, fetch it. If a requirement list is thin or missing, ask me to paste the full posting rather than guessing.

Then extract and write down (briefly) the following, because the rest of the process maps directly onto it:

- **Role + seniority** - title, level, and what that level implies about scope.
- **Must-haves** - the hard requirements the resume has to visibly satisfy.
- **Nice-to-haves** - differentiators worth surfacing if I have them.
- **Key Responsibilities** - what the person will actually do day to day.
- **Keywords / Hard Skills** - the specific tools, frameworks, and terms an ATS or a skimming recruiter will look for. Capture the *exact* wording.
- **Company Mission / Values / Soft Skills** - what the company cares about and how it talks about itself. This feeds the summary and shows genuine fit.
- **The Hidden Priority** - what problem is this hire actually meant to solve? Postings bury the real need; naming it lets the whole resume point at it.


## Step 2 - Select resume points from the master resume (selection only)

Your job in this step is to **choose which points from the master resume will appear in the tailored resume - nothing more.** Do not reword, merge, trim, or reorder anything yet; that happens in the next step. **Do not write the resume yet.**

Work from the JD deconstruction (must-haves, nice-to-haves, keywords, hidden priority, etc) you got from step 1. For each candidate point, decide whether to select it based on the following criteria:

- **Relevance to a stated need.** Select a point if it supports a specific JD requirement, responsibility, or hidden priority. Record which requirement(s) each selected point maps to. Tag it as `must-have` or `nice-to-have` accoridingly.
- **Anchors and differentiators.** Include a point if it establishes baseline credibility (seniority, leadership, education) or acts as a genuine differentiator - even if it doesn't explicitly map to a specific JD point. Tag it as `anchor` or `differentiator` accordingly.

### Guardrails
Keep the following things in mind as you work through this step:

- **Narrow ruthlessly.** Selection is mostly an act of *cutting*. A tailored resume is defined by what it leaves out; aim for a set that fits ~1-2 pages once written, not an exhaustive dump.
- **Select, don't edit.** Copy each chosen point in its original wording and keep it attached to its source role/section and dates. Rewording/reordering is the next step's job.
- **Only select what exists.** Never select a point the master resume doesn't contain, and never quietly strengthen one during selection. If evidence isn't there, it's a gap.
- **Substance over keyword presence.** Do not select a point merely because it contains a JD keyword. Select for the underlying capability - a keyword-stuffed resume that passes an ATS but fails the interview is a bad trade.
- **Flag anything that misleads in isolation.** If a selected point could imply more experience or depth than the candidate actually has (e.g., near a known gap), tag it `handle-honestly` so the next step frames it carefully. Selecting it is fine; letting it overclaim is not.
- **Match the seniority signals.** Weight selection toward the scope the role expects (ownership/leadership/mentorship for senior/staff; hands-on delivery for junior). For example, don't foreground leadership for an IC-only role or bury it for a lead role.

### Outputs

This step will have two sets of outputs. **We are not writing the resume yet!**

#### Per-Section Table
Produce **one table per resume section** (Work Experience, Selected Projects, Education, Achievements, etc.).

For each section, output a table with exactly these columns:
```markdown
| Sub-heading | Resume point | Reason for selection | JD requirement |
|---|---|---|---|
```

Here's what should go into each column:
- **Sub-heading** - the specific source within the section: the exact job title/company for Work Experience, the specific project name for Selected Projects, the degree/course for Education, etc. This preserves provenance for the next step.
- **Resume point** - the selected point **verbatim** from the master resume. Do not reword, merge, or trim it here.
- **Reason for selection** - one or more of: `must-have`, `nice-to-have`, `anchor`, `differentiator`, or `handle honestly`. Use `handle honestly` in combination with another tag when a point is worth keeping but could overclaim if not framed carefully in the next step (e.g. `must-have, handle honestly`).
- **JD requirement** - the specific JD requirement/responsibility/keyword the point maps to. For `anchor` and `differentiator` rows that intentionally aren't JD-matched, write `- (general credibility)` or `- (differentiator)` so it's clear the omission is deliberate, not an oversight.

Remember:
- One row per selected point. Give each section its own table even if it has only one row.
- You may omit a section's table only if nothing from it was selected.

Here's an example:
```markdown
**Work Experience**

| Sub-heading | Resume point | Reason for selection | JD requirement |
|---|---|---|---|
| <Company> — <Senior Title> | Cut deployment cycle time significantly by introducing automated pipelines | must-have | "Utilize CI/CD tools to set up automated pipelines" |
| <Company> — <Title> | Re-architected a core service from one stack to another, sustaining high throughput | must-have, handle-honestly | "distributed systems in production" / <a named language or tool> |
| <Company> — <Junior/Grad Title> | Led a small team of junior engineers to ship a service as a REST API | anchor | — (general credibility: leadership/seniority) |
```

#### Gaps List
List the **gaps**, i.e., any point in the JD (must-haves as well as any important nice-to-have) that **nothing in the master resume maps to well**. These are drawn from the JD side, not from the resume side. For each gap, give one line:

- **<JD requirement>** - why nothing qualifies (no evidence, or only weak/adjacent evidence), and the best available near-miss if one exists (so the next step can decide whether to frame it as transferable or acknowledge it openly).

Be truthful and exhaustive when constructing this list. Do not pad this list to look thorough and do not omit a real gap to look stronger - its whole purpose is to make uncovered requirements visible for interview prep and portfolio planning.


## Step 3 - Draft content for the final tailored resume

### Draft the tailored content (reword, reorder, summarize)
The input to this step is the previous step's per-section tables. 

Your job here is to use the selected points in those tables to draft the actual resume points that will appear in the final tailored resume (do not think about how to to lay them out visually yet; formatting is the next step). The goal is to draft resume points that have the highest chance of passing an ATS, or of  catching the attention of a human skimming through hundreds of resumes.

#### Reword
Rewrite each selected point. Stay truthful to what the master resume says - reword for emphasis and clarity, never to invent or inflate.

- **Cover JD keywords aggressively but honestly.** Work the JD's concrete skills, tools, and terms into the points wherever the candidate genuinely has them - this is the single biggest ATS lever. Never insert a keyword the master resume doesn't support.
- **Mirror the JD's phrasing only if the JD is clearly human-written.** First judge whether the JD looks AI-generated (tells: generic boilerplate, vague or oddly balanced responsibilities, filler phrasing, no company-specific detail, repetition). If it reads AI-generated, do **not** echo its sentence-level phrasing - it's noise and mirroring it can look off. Extract its keywords and requirements either way; do *phrase-matching* only for human-written JDs.
- **Lead with what this JD cares about.** The same point can be angled differently depending on the JD's focus. Put the aspect the JD weights most at the front of the sentence. E.g. for a point like "led development of a platform serving many models": if the JD is leadership-focused, foreground envisioning/scoping/driving the initiative; if it's delivery-focused, foreground the scale and the specific features built. Same facts, different emphasis.
- **Split long points.** If a selected point packs in multiple distinct accomplishments or runs long, break it into separate points so each is skimmable. Splitting is for readability only - do not let one accomplishment become two to pad the list, and do not duplicate the same metric across both halves.
- - **Preserve embedded links.** Master-resume points often carry markdown links (project repos, publications, articles, company/product pages). When you reword or split a point, keep every link and its destination intact, anchored to sensible text — the project / paper / article / company name, never a bare "here" or a raw URL. Keep them in markdown `[anchor](url)` form in the draft so the formatting step can render them. If a point is split, the link travels with the half it belongs to. Never drop a link to tidy a sentence, and never invent, guess, or alter a URL — carry it exactly as it appears in the master resume.
- **Bold the most relevant phrase in each point - selectively.** Bold the single most JD-relevant span (a metric, a tool, a scope word), not whole sentences. If everything is bold, nothing stands out; aim for <3 bolded spans per point so the eye lands on the proof points as it skims.

#### Reorder
- **Within each sub-heading, most important point first.** Order points by relevance to the JD, not by how they appeared in the master resume.
- **Reorder whole sections by relevance.** If the candidate's portfolio projects demonstrate the JD's core asks better than the work experience does, place Projects above Work Experience. Keep jobs *within* Work Experience in reverse-chronological order (recruiters expect a readable timeline).

### Draft the Summary section (first section of the resume)
Write a 3-4 sentence professional summary that speaks directly to this role. Anchor it to the **company values** and **hidden priority** identified earlier - it should read as if written for this team, foregrounding the 2-3 strengths they most need. Keep it truthful and consistent with the reworded points; do not claim anything the body can't back up.

### Draft the Skills section (conditional - only if the resume is running long)
If the drafted content is heading past a clean ~2 pages (or the sample resume's implied length), add a **Skills** section immediately under the Summary. Its purpose is to absorb keyword-coverage duty in a compact form, so lower-value bullets that existed mainly to surface a keyword can be cut - net-shortening the resume while keeping ATS coverage.

- Categorize into **2-4 sub-sections** with sensible labels (e.g. one for cloud/infra skills like AWS, Kubernetes, Terraform; another for leadership skills like navigating ambiguity, project scoping and execution). Mix hard and soft skills as fits.
- **Every listed skill must be evidenced by a master-resume point.** This section is drawn from the actual skillset, not the JD. It must **not** look like a dump of the JD's requirements - a reviewer who cross-checks it against the bullets should find each skill demonstrated. If a JD skill isn't backed by the resume, it belongs in the gaps list, not here.
- Don't just restate bullet phrases - this is an at-a-glance index, complementary to the detailed points.

### Guardrails
- **Truthful reword only.** Rewording should change emphasis and vocabulary, never facts. If a rewrite would imply more scope, seniority, or depth than the master resume supports, pull it back. This applies doubly to points tagged `handle honestly` in the selection step - surface them without letting them overclaim.
- **Bold discipline.** Less than 3 bolded span per point; never bold a whole bullet. The fewer bold spans, the better.

### Output format
Produce a single **tailored resume draft** in structured markdown that the next step can lay out directly. Start with a short header block, then the content in final order:

    SECTION ORDER: <ordered section headings as they will appear, Summary first>
    SKILLS SECTION: <added | not added> - <one-line reason>
    ESTIMATED LENGTH: <~1 page | ~2 pages>

    ## Summary
    <final 3-4 sentence summary, ending with the retained line>

    ## Skills   (include only if added)
    **<Category label>:** skill, skill, skill
    **<Category label>:** skill, skill, skill

    ## <First content section, per SECTION ORDER>
    ### <sub-heading carried verbatim from master: Title - Company>
    <dates | location - verbatim from master>
    *Tech: <verbatim tech line, if the master/sample uses one>*
    - <reworded point, most important first, with one **bolded** span>
    - <reworded point>

    ### <next sub-heading, reverse-chronological within Work Experience>
    ...

    ## <next section, per SECTION ORDER>
    ...

Carry every sub-heading's metadata (title, company, dates, location, tech) verbatim from the master resume so the next step has everything it needs. Do the bolding here; the next step preserves it. Do not apply visual layout, fonts, or spacing - that's the next step.


## Step 4 - Format the final resume (deliverable 1)
Take the tailored resume draft from the previous step and render it into a polished, well-formatted resume file. This step is layout only - do not reword, re-order, re-bold, or add/remove content. If content genuinely doesn't fit the target layout, trim per the length rules already decided or flag it; never silently rewrite here.

### Header Section
- Include the candidate's name, title, and contact information from `contact_details.json` at the top of the resume. If the sample resume has a specific layout for this, match it exactly.

### If `sample_resume.docx` is present
Inspect the layout of the `sample_resume.docx` with the docx skill and replicate it exactly: how each Work-Experience entry arranges title / company / dates / location / tech / points (same line vs. stacked, alignment, which fields are bold or italic), the heading set and their order, fonts, sizes, spacing, and bullet style. Then pour the drafted content into that structure and produce the resume as a `.docx`:
- **Copy the sample's *structure and style*, never its *words*.** The sample is a layout template - do not carry over its example company names, dates, or bullet text.
- **Mirror the sample's heading set where there's real content.** If the sample has a heading the tailored content doesn't fill, omit it gracefully - don't invent content to populate it. Map the drafted sections onto the sample's heading names.
- Preserve the bold emphasis from the previous step; respect the sample's implied length (1 vs. 2 pages).
- **Render links as live hyperlinks.** Convert every markdown link carried through from the draft into a real, clickable Word hyperlink in the `.docx` — not raw `[text](url)` syntax and not plain unlinked text. Use the docx skill's hyperlink support. If `sample_resume.docx` is present and shows a link style (e.g. underlined or colored anchor text), match it; otherwise use a clean, standard hyperlink style.

### If no `sample_resume.docx` is present
Format cleanly in the master resume's own markdown style, then offer to render to `.docx` or PDF.

### Output format
Save the result as a **new file** (e.g. `<UserName>_Resume_<Company>_<Role>`) and then present the file. **Never** overwrite the master resume or the sample. 


## Step 5 - Produce the Gap Analysis (deliverable 2)
The earlier Gaps List was a raw, JD-side inventory of uncovered requirements. This step turns it into the second **deliverable**: a candid, useful read of where I stand against this specific role, written for my own preparation. This is not a document anyone else sees, so total honesty is the best policy.

Start from the Gaps List. For each gap, and for the role as a whole:
- **Rate the severity.** Sort gaps into the following categories, (these will drive the study plan in the next step):
  - `dealbreaker`: A core must-have with no credible story
  - `soft gap`: Adjacent/transferable evidence exists; it's a framing problem, not an absence
  - `cosmetic`: A keyword or nice-to-have that rarely gets probed.
- **Name the likely interview exposure.** For each meaningful gap, state the question an interviewer would ask that would surface it.
- **Give the honest near-miss.** Where I have adjacent evidence, name it and say plainly how far it stretches and where it stops. Clearly distinguish between something I can frame as transferable and something I'd be overclaiming.

### Output format
```markdown
    ## Gap Analysis

    **Overall read:** <2-3 sentence verdict; realistic / stretch / long-shot, tied to role purpose>

    | JD requirement | Severity | Best near-miss (how far it stretches) | Likely interview probe |
    |---|---|---|---|
    | <requirement> | dealbreaker / soft / cosmetic | <evidence + where it stops, or "none"> | <the question that exposes it> |

    **Framing guidance:** <which gaps to present as transferable vs. acknowledge openly, in 2-4 lines>
```


## Step 6 - Produce talking points and a study plan (deliverable 3)
This is the deliverable that gives me an edge, so feel free to be creative, opnionated, and subjective. However, ground the output in the following three thingsL:
1. The tailored resume
2. The Gap Analysis (produced in the previous step)
3. **Fresh research on the company's current direction.**

### First, research the company (required)
Web-search the company before writing this section - do not rely on the JD or on stale knowledge. Look for what's happened recently and what the team actually cares about right now:
- Recent launches, product bets, funding, and public roadmap or blog/engineering posts.
- The team's or org's technical direction (what they're building toward, what problems they keep talking about publicly).
- The interviewers' or team's stated values and any recent talks, papers, or posts by people on it.
- Anything signaling *what would impress this specific team* - the technical taste, scale, or philosophy they reward.

Use this to make the prep specific to *this* company at *this* moment, not generic. Cite what you find so the candidate can read further. If searches come back thin, say so and lean on the JD + Gap Analysis rather than inventing a direction.

### Talking points - 2-5 stories to prepare well
Pick 2-5 stories/projects **from the master resume** with the highest potential to impress *this* team, informed by the research. For each:
- Name the story, as well as the JD requirement or company priority it maps to.
- Give the angle: what to emphasize and why it resonates with what this team values right now (e.g. if the company is pushing reliability at scale, foreground the uptime/latency story; if they're research-forward, foreground the from-scratch/experimental work).
- Note the trap: the follow-up that could go badly, and how to stay honest under it.
- If there are no relevant stories, don't try to force things here - 2 high quality stories is better than 5 mediocre ones.

Be selective and opinionated - 2-5 well-chosen stories the candidate can tell cold beats
a long list. It's fine to say "lead with this one."

### Study plan - 2-5 things to sharpen before interviewing
Choose 2-5 concepts / technologies / deep-dives that would give me an edge in an interview setting. Draw these from:
1. The Gap Analysis (prioritize dealbreaker and soft gaps that are learnable in the available time)
2. The company's current technical direction as determined from your research (topics likely to come up because they're what the team members think about all day).

For each:
- Say why it matters for *this* interview (which gap it closes or which company priority it maps to).
- Give a concrete, bounded way to get conversant fast - the specific thing to read, build, or be able to explain, not "study distributed systems."

### Weekend project (conditional - only for a serious, demonstrable skill gap)
If the Gap Analysis surfaced a serious skill gap that a small artifact could *credibly* close, propose a weekend project that I can build to learn & demonstrates that skill. Be specific about the scope of the project, and tie the scope directly to the skill gap it's meant to address. 

If there is no obivous skill gap, say so and skip this. **Do not manufacture a project.**

### Output format
```markdown
    ## Talking Points & Study Plan

    **What this company is focused on right now:** <3-5 sentences from research, with citations>

    ### Talking points
    1. **<Story / project>** → lands on <JD req / company priority>
       - Angle: <what to emphasize, why it resonates now>
       - Trap: <the risky follow-up + how to stay honest>
    2. ...

    ### Study plan
    1. **<Concept / tech>** — <why it matters for this interview> → <the bounded way to get conversant>
    2. ...

    ### Weekend project   (include only if a serious gap warrants it)
    **<Project name>** — closes <gap>. <1-3 sentences: what to build, what it demonstrates, honest scope.>
```
