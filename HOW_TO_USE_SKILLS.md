Agent skills are just a folder with a `SKILL.md` file and optional supporting files.

At it's core, a `SKILL.md` just contains markdown text which gets added to your prompt whenever the skill is invoked. How the skill is invoked depends on two additional pieces of information defined at the beginning of the `SKILL.md` file - the `name` and `description`.

While the exact steps for making this skill available to your agent harness would depend on the tool, the general process is the same.

### 1. Check what your agent needs

For the skill to run end to end, the agent needs to be able to:

- **Read files** from the skill folder, or from wherever you put your reference files.
- **Fetch web pages**, if you give it job posting URLs. If it can't, paste the job description text instead.
- **Run code or create files**, to read `sample_resume.docx` and write the tailored resume as a `.docx`, for example with a docx-handling skill or a library like `python-docx`. Without this, you still get the resume content as markdown, plus the gap analysis and talking points.

These are pretty stnadard in modern agent harnesses; in Claude, for example, you just have to toggle certain flags in your settings to enable all of these capabilities.

### 2. Install the skill

- **If your agent supports skills:** copy or clone this folder into the directory your agent scans for skills, keeping `SKILL.md` at the top level of the `tailor-resume/` folder. Some tools instead expect you to upload the folder as a ZIP. Check your tool's docs for the skills location or upload flow.
- **If your agent doesn't support skills:** you can still use the instructions directly. Paste the contents of `SKILL.md` (everything below the frontmatter) into the system prompt, custom instructions, or the first message of a conversation, and attach your reference files alongside it.

### 3. Provide your reference files

Fill in the files described in [Setup](README.md#setup) and make them available to the agent in one of these ways:

- Put them in the skill's `references/` folder (the simplest option for local agents).
- Upload or attach them to the conversation or workspace. In [Claude Projects](https://support.claude.com/en/articles/9517075-what-are-projects), you can add them to the project's context. 
- If they are somewhere other than `/mnt/project/` or `references/`, the agent will ask you where the files are each time. You can change this behavior by editing [this section](SKILL.md#step-0---load-the-source-material-always-first) of the [SKILL.md](SKILL.md)

### 4. Trigger it

Agents with skill support decide when to load a skill by matching your request against the `description` in the frontmatter, so describe what you want in plain language and include the job posting:

> Here's a role I want to apply for: {link or pasted JD}. Tailor my resume for it.

Other phrasings that should trigger it:

- "Am I a fit for this?" + the job description
- "Do a keyword/ATS gap check against this posting"
- "Which of my projects should I feature for this role?"

If the skill doesn't trigger, name it explicitly (e.g. "Use the tailor-resume skill on this posting"). Many tools also let you invoke a skill by `name` (as defined at the top of the [`SKILL.md`](SKILL.md)). For this skill, this would be done by typing `/tailor-resume` at the beginning of your prompt, like this:

> /tailor-resume {link-to-JD}

### 5. Review the output at each stage

The skill works in stages: it breaks down the job description, selects points from your master resume (with the reason for each), rewrites them, and then produces the final resume, gap analysis, and talking points. Check each stage before moving on. Correct anything that overstates your experience or doesn't sound like you, since you'll be the one defending it in an interview.
