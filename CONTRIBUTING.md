# Contributing to devrelskills

Thanks for your interest in contributing. This project adapts marketing AI skills for developer audiences, so contributions should follow DevRel principles: code-first, technically accurate, no marketing fluff.

## How to contribute

### Adding a new skill

1. Create a directory under `skills/` with your skill name:

```bash
mkdir -p skills/your-skill-name
```

2. Create a `SKILL.md` file following this structure:

```markdown
---
name: your-skill-name
description: One-line description. Include trigger phrases
  that tell Claude when to activate this skill.
---

# Role Definition
Who Claude should act as for this skill.

## Context Awareness
What files to check before asking questions.

## Information Needed
What to ask the user before generating output.

## Output Structure
The template/format for the output.

## Quality Rules
What makes good output for this skill.

## Voice and Tone
How the output should sound (technical, direct, no buzzwords).

## Examples
Good vs bad output examples.
```

3. Add an example output in `examples/outputs/your-skill-name-example.md`
4. Update the README.md skills table
5. Submit a pull request

### Skill quality checklist

Before submitting, verify your skill:

- [ ] Has complete frontmatter with name, description, and trigger phrases
- [ ] Defines a clear role (technical writer, not marketer)
- [ ] Bans marketing buzzwords (revolutionary, seamless, leverage, unlock, etc.)
- [ ] Requires complete, copy-pastable code examples
- [ ] Includes good vs bad output examples
- [ ] Has been tested with at least 3 different prompts
- [ ] Produces output that a developer would actually find useful

### Adapting an existing marketing skill

If you're adapting a skill from [marketingskills](https://github.com/coreyhaines31/marketingskills):

1. Read `docs/adapting-marketing-skills.md` for the conversion process
2. Replace the role definition (technical writer, not copywriter)
3. Add banned marketing words to the voice guidelines
4. Require code examples in the output
5. Restructure output to lead with code, not benefits
6. Replace all examples with developer-appropriate ones
7. Document your adaptation in `examples/skill-audit-checklist.md`

### Improving existing skills

Found a skill producing bad output? Fix it:

1. Note the prompt you used and what went wrong
2. Identify which section of SKILL.md needs strengthening
3. Add stronger guidelines or better examples
4. Test with your original prompt to confirm the fix
5. Submit a PR with before/after examples

### Adding example outputs

Example outputs help others understand what each skill produces:

1. Run a skill with a realistic prompt
2. Save the output to `examples/outputs/skill-name-example.md`
3. Include the prompt you used at the top of the file
4. Light editing for formatting is fine; don't rewrite the output

## Guidelines

### Do

- Keep skills focused on one task
- Include realistic, tested examples
- Write for developers who know how to code
- Be specific in guidelines ("add Python example showing pagination" not "improve examples")
- Test with multiple prompts before submitting

### Don't

- Add marketing language to any skill
- Create skills that overlap significantly with existing ones
- Submit untested skills
- Use vague or generic guidelines
- Add skills that don't serve developer audiences

## Development setup

```bash
# Clone the repo
git clone https://github.com/YOUR_USERNAME/devrelskills.git
cd devrelskills

# Install skills locally for testing
cp -r skills/* ~/.claude/skills/

# Test a skill
# Open Claude Code and run: /your-skill-name
```

## Pull request process

1. Fork the repo
2. Create a branch: `git checkout -b add-skill-name`
3. Add your skill + example output
4. Update README.md if adding a new skill
5. Submit PR with:
   - What the skill does
   - Example prompt and output
   - How you tested it

## Code of conduct

Be helpful, be technical, be honest. This project exists to help DevRel teams produce better content for developers. Keep that goal in focus.
