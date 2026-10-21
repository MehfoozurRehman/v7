# v7

A personal developer portfolio built with Next.js: project case studies, a GitHub contribution calendar, a contact form, and a generated PDF CV.

**Status:** Shipped. The site is complete across its pages and deploys to Firebase Hosting from GitHub Actions on merges. I did not check the live site.

## The problem

A developer needs one public page that presents their services, projects, experience and contact details, and that a visitor can read on any device. The CV also needs to be available as a PDF, without being edited by hand each time. This project does both from one content file.

## What it does

- **Portfolio home page:** profile, services, selected projects, experience, education, tech stack and testimonials, all read from `data.ts`.
- **Case study pages:** one page per project at `/case-studies/[slug]`, pre-rendered at build time with `generateStaticParams`.
- **GitHub activity:** a contribution calendar loaded with `react-github-calendar`.
- **Contact form:** sends messages through EmailJS, with the service, template and public key read from environment variables.
- **Generated CV:** `scripts/generate-cv-pdf.mjs` builds a PDF from `scripts/cv-content.mjs` before every build.
- **Light and dark themes:** a theme toggle, with a script that sets the theme before the page paints.

## How it's built

- Next.js 16 App Router with `output: 'export'`, so the build produces a static site in `out/`.
- React 19, TypeScript and Tailwind CSS v4. Icons from Lucide.
- PDFKit writes the CV as a PDF, and `sharp` is a dev dependency for image work.
- Content lives in typed exports in `data.ts` (`profile`, `projects`, `services`, `experience` and others), so the pages and the CV can share one source.
- `firebase.json` serves the `out/` folder, and the workflows in `.github/workflows` deploy it. The merge workflow runs on pushes to `main`.

## Running it locally

Requires Node.js 20+ and pnpm 11. For the contact form, set `NEXT_PUBLIC_EMAILJS_PUBLIC_KEY`, `NEXT_PUBLIC_EMAILJS_SERVICE_ID` and `NEXT_PUBLIC_EMAILJS_TEMPLATE_ID` in `.env.local`.

```bash
pnpm install
pnpm generate:cv   # writes the CV PDF
pnpm dev           # http://localhost:3000
```

Other scripts: `pnpm build` (generates the CV, then builds the static site), `pnpm start`, and `pnpm deploy` (builds, then runs `firebase deploy --only hosting`, which needs a Firebase login).

## What's left

- **Contact form needs keys:** without the three EmailJS variables the form cannot send anything. The keys are read from the build environment, so they are visible in the published bundle, which is normal for EmailJS public keys.
- **No tests** are present.
- **Content is in code:** adding a project or job means editing `data.ts` and redeploying.
- **Dependabot is configured,** but no automated test runs before deploy beyond the build.
