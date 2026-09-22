# Agent Skill: `tailor-resume`

An agent skill built for low-volume job apping. It takes in a job description, and produces:

1. **A tailored resume.** Points are picked from your master resume, then reordered and reworded to match the posting. Nothing is made up. The output matches your sample resume's formatting and stays under 2 pages.
2. **A gap analysis.** A plain list of what the role asks for that your experience doesn't cover.
3. **Talking points and a study plan.** The projects and stories worth preparing for interviews, and the topics worth studying before them.

## Repository Layout

```
tailor-resume/
├── SKILL.md                    # The skill's instructions
└── references/
    ├── master_resume.md        # Template: your full, comprehensive resume
    ├── career_profile.md       # Template: your goals, target companies, strengths, gaps
    ├── contact_details.json    # Your contact info (git-ignored, create your own)
    └── sample_resume.docx      # Optional: a resume whose formatting the output should copy (git-ignored)
```

## Setup

Since this skill is meant for low-volume applications, it requires you to do a bit of homework. Before using it, prepare these files:

| File | Required | What goes in it |
|---|---|---|
| `master_resume.md` | Yes | Every role, project, bullet point, skill, and achievement you might ever want to show. Put in more than you need; the skill picks the right subset for each job. |
| `career_profile.md` | Yes | Your long-term and near-term goals, ideal next role, target companies, strengths, and known gaps. This shapes the summary and talking points. |
| `contact_details.json` | Yes | Location, phone, email, and links. It's kept separate from the resume because it's sensitive. |
| `sample_resume.docx` | No | An existing resume whose layout, fonts, and heading order the output should match exactly. Without it, the skill outputs markdown and offers to convert it to a `.pdf` or `.docx` file. |

Templates are provided for each of the required file under the [`references`](references) folder. Once you've filled in the files with your information, run the following command from the root of the repo and you should be good to go:
```bash
for f in references/*.template; do mv -- "$f" "${f%.template}"; done
```

## Usage

Agent skills are an open format: a folder with a `SKILL.md` file (YAML frontmatter plus markdown instructions) and optional supporting files. Many agent harnesses can discover and load skills in this format. The exact steps depend on your tool, but the general process is the same.

### 1. Check what your agent needs

For the skill to run end to end, the agent needs to be able to:

- **Read files** from the skill folder, or from wherever you put your reference files.
- **Fetch web pages**, if you give it job posting URLs. If it can't, paste the job description text instead.
- **Run code or create files**, to read `sample_resume.docx` and write the tailored resume as a `.docx`, for example with a docx-handling skill or a library like `python-docx`. Without this, you still get the resume content as markdown, plus the gap analysis and talking points.

### 2. Install the skill

- **If your agent supports skills:** copy or clone this folder into the directory your agent scans for skills, keeping `SKILL.md` at the top level of the `tailor-resume/` folder. Some tools instead expect you to upload the folder as a ZIP. Check your tool's docs for the skills location or upload flow.
- **If your agent doesn't support skills:** you can still use the instructions directly. Paste the contents of `SKILL.md` (everything below the frontmatter) into the system prompt, custom instructions, or the first message of a conversation, and attach your reference files alongside it.

### 3. Provide your reference files

Fill in the files described in [Setup](#setup) and make them available to the agent in one of these ways:

- Put them in the skill's `references/` folder (the simplest option for local agents).
- Upload or attach them to the conversation or workspace. In [Claude Projects](https://support.claude.com/en/articles/9517075-what-are-projects), you can add them to the project's context. 
- If they are somewhere other than `/mnt/project/` or `references/`, the agent will ask you where the files are each time. You can change this behavior by editing [this section](SKILL.md#step-0---load-the-source-material-always-first) of the [SKILL.md](SKILL.md)

### 4. Trigger it

Agents with skill support decide when to load a skill by matching your request against the `description` in the frontmatter, so describe what you want in plain language and include the job posting:

> Here's a role I want to apply for: <link or pasted JD>. Tailor my resume for it.

Other phrasings that should trigger it:

- "Am I a fit for this?" + the job description
- "Do a keyword/ATS gap check against this posting"
- "Which of my projects should I feature for this role?"

If the skill doesn't trigger, name it explicitly (e.g. "Use the tailor-resume skill on this posting"). Many tools also let you invoke a skill by name, often as `/tailor-resume`.

### 5. Review the output at each stage

The skill works in stages: it breaks down the job description, selects points from your master resume (with the reason for each), rewrites them, and then produces the final resume, gap analysis, and talking points. Check each stage before moving on. Correct anything that overstates your experience or doesn't sound like you, since you'll be the one defending it in an interview.

# Customizing

`SKILL.md` is plain markdown, so you can edit it to fit your preferences, such as page limit, summary length, or how many talking points you want. If you change what the skill should respond to, update the `description` in the frontmatter too, since that's what Claude uses to decide when to trigger it.

# Privacy note

Your resume, career profile, and contact details are personal. Keep `contact_details.json` and `sample_resume.docx` out of version control (they're already in `.gitignore`). If you fork this repo, don't commit your filled-in `master_resume.md` or `career_profile.md` to a public repository.
