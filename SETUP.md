# Getting This Onto GitHub

## 1. Create the repository

1. Go to github.com and click **New repository**
2. Name it something clear and searchable, e.g. `technical-writing-portfolio`
3. Set it to **Public** (so recruiters/hiring managers can view it without a login)
4. Don't initialize with a README (you already have one) — leave it empty

## 2. Push these files

From the folder containing this portfolio, run:

```bash
cd portfolio
git init
git add .
git commit -m "Initial portfolio: 5 writing samples"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/technical-writing-portfolio.git
git push -u origin main
```

## 3. Polish the GitHub presentation

- Add a short repo **description** on GitHub: "Technical writing portfolio — networking, aerospace, and API documentation samples"
- Add **topics/tags**: `technical-writing`, `documentation`, `portfolio`, `api-docs`
- Pin this repo on your GitHub profile (Profile → Customize your pins)
- Link it from your resume and LinkedIn as "Portfolio: github.com/YOUR-USERNAME/technical-writing-portfolio"

## 4. Next steps to strengthen it further

- **Replace with real (redacted) work where possible.** These samples are built from scratch to match your experience. If you can adapt genuinely written material — with anything proprietary/confidential removed or fictionalized — real samples carry more weight than newly constructed ones. Check your employment agreements before publishing anything derived from actual employer content.
- **Add a 6th sample: a short DITA topic.** You list DITA on your resume but none of the current samples use it directly. A single well-formed DITA topic (task, concept, or reference type) with its XML source visible would directly back up that skill.
- **Add screenshots.** If you can create clean, non-confidential mockups in MadCap Flare or RoboHelp output, a couple of screenshots showing your work in the actual tool add credibility.
- **Consider a short "How I use AI in documentation workflows" write-up.** Your resume specifically flags this — it's a strong current differentiator and a portfolio piece can go deeper than a bullet point can.
