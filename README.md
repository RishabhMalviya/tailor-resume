# Agent Skill: `tailor-resume`

An agent skill built for low-volume job apping. It takes in a job description, and produces:

1. **A tailored resume.** Points are picked from your master resume, then reordered and reworded to match the posting. Nothing is made up. The output matches your sample resume's formatting and stays under 2 pages.
2. **A gap analysis.** A plain list of what the role asks for that your experience doesn't cover.
3. **Talking points and a study plan.** The projects and stories worth preparing for interviews, and the topics worth studying before them.

If you've never used an Agent Skill before, refer to [HOW_TO_USE_SKILLS.md](HOW_TO_USE_SKILLS.md).

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

## Privacy note

Your resume, career profile, and contact details are personal. Keep `contact_details.json` and `sample_resume.docx` out of version control (they're already in `.gitignore`). If you fork this repo, don't commit your filled-in `master_resume.md` or `career_profile.md` to a public repository.
