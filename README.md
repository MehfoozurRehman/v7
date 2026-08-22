# Developer Portfolio v7

The personal developer portfolio, live GitHub contribution heatmaps, automated CV generator, and project showcase for Mehfooz-ur-Rehman built with Next.js 16 App Router, React 19, Tailwind CSS v4, and PDFKit.

## Overview

`v7` represents the latest portfolio release showcasing full-stack engineering work, live interactive GitHub calendar contributions (`react-github-calendar`), automated programmatic PDF curriculum vitae generation (`pdfkit`), EmailJS contact forms, and automated Firebase Hosting deployment.

## Tech Stack

- **Framework**: [Next.js](https://nextjs.org/) (v16 App Router)
- **Frontend Core**: React 19, TypeScript
- **Styling**: Tailwind CSS v4 (`@tailwindcss/postcss`)
- **PDF Generation**: PDFKit (`pdfkit`, `scripts/generate-cv-pdf.mjs`)
- **Visuals & Heatmaps**: `react-github-calendar`, Lucide Icons
- **Email Service**: `@emailjs/browser`
- **Hosting**: Firebase Hosting (`firebase.json`)

## Prerequisites

- Node.js (v20 or higher recommended)
- Package manager (`pnpm` v11+ recommended)

## Getting Started

1. **Install dependencies**:
   ```bash
   pnpm install
   ```

2. **Generate CV PDF**:
   ```bash
   pnpm generate:cv
   ```

3. **Run the Development Server**:
   ```bash
   pnpm dev
   ```

4. **Access the Portfolio**:
   Open `http://localhost:3000` in your web browser.

## Available Scripts

- `pnpm dev` - Starts the Next.js development server.
- `pnpm generate:cv` - Builds the PDF resume via PDFKit script.
- `pnpm build` - Generates PDF resume and compiles Next.js production build.
- `pnpm start` - Starts the production server.
- `pnpm deploy` - Compiles and deploys directly to Firebase Hosting.

## Author

Created by [Mehfooz-ur-Rehman](https://github.com/MehfoozurRehman).
