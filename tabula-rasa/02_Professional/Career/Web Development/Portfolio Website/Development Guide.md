---
date created: Sunday, August 3rd 2025, 9:19:05 pm
date modified: Monday, August 4th 2025, 9:32:56 am
---

# Portfolio Website Development Guide

## Overview

Complete step-by-step guide for building a professional security portfolio website with React, Next.js, and Tailwind CSS.

---

## Table of Contents

- [[#Phase 1 - GitHub & Development Setup|Phase 1: GitHub & Development Setup]]
- [[#Phase 2 - Project Structure & Configuration|Phase 2: Project Structure & Configuration]]
- [[#Phase 3 - Core Development|Phase 3: Core Development]]
- [[#Phase 4 - Content Management|Phase 4: Content Management]]
- [[#Phase 5 - Deployment|Phase 5: Deployment]]
- [[#Quick Reference|Quick Reference]]

---

## Phase 1 - GitHub & Development Setup

### 📁 Create GitHub Repository

1. **Navigate to GitHub** → Click "New Repository"
2. **Configure repository settings:**
    - **Repository name:** `yourname.dev` (matches your domain) ✓
    - **Description:** "Personal portfolio showcasing security projects and technical writeups" ✓
    - **Visibility:** Public ✓
    - **Initialize with README:** ✓
    - **Add .gitignore:** Node ✓
    - **Add license:** MIT ✓

 **Clone repository locally:**
```bash
git clone https://github.com/yourusername/yourname.dev.git
cd yourname.dev
```

### 🛠️ Initialize Next.js Project

```bash
# Create Next.js app in current directory
npx create-next-app@latest . --tailwind --app --typescript

# Select these options when prompted:
# ✓ Would you like to use TypeScript? → Yes
# ✓ Would you like to use ESLint? → Yes
# ✓ Would you like to use Tailwind CSS? → Yes
# ✓ Would you like to use `src/` directory? → No
# ✓ Would you like to use App Router? → Yes
# ✓ Would you like to customize import alias? → No
```

### 💻 VS Code Setup

#### Install Essential Extensions:

1. **ES7+ React/Redux/React-Native snippets**
2. **Tailwind CSS IntelliSense**
3. **Prettier - Code formatter**
4. **ESLint**
5. **GitLens**
6. **Auto Rename Tag**
7. **Path Intellisense**

#### Create VS Code Settings:

Create `.vscode/settings.json`:

```json
{
  "editor.formatOnSave": true,
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
  },
  "tailwindCSS.includeLanguages": {
    "javascript": "javascript",
    "html": "HTML"
  },
  "files.exclude": {
    "**/.git": true,
    "**/node_modules": true,
    "**/.next": true
  }
}
```

---

## Phase 2 - Project Structure & Configuration

### 📂 Create Folder Structure

```bash
# Create all necessary directories
mkdir -p app/{projects,writeups,blog,cv,contact}
mkdir -p components/{Layout,UI,Cards}
mkdir -p lib
mkdir -p public/{images,documents}
mkdir -p content/{writeups,blog}
mkdir -p styles
```

### ⚙️ Configuration Files

#### Create `.prettierrc.json`:

```json
{
  "semi": true,
  "trailingComma": "es5",
  "singleQuote": true,
  "tabWidth": 2,
  "useTabs": false,
  "plugins": ["prettier-plugin-tailwindcss"]
}
```

#### Update `.gitignore`:

```gitignore
# Dependencies
/node_modules
/.pnp
.pnp.js

# Next.js
/.next/
/out/
/build

# Local env files
.env*.local
.env

# Vercel
.vercel

# IDE
.vscode/*
!.vscode/settings.json
.idea

# OS
.DS_Store
Thumbs.db
```

### 📦 Install Dependencies

```bash
# Core dependencies
npm install react-icons gray-matter next-mdx-remote

# Development dependencies
npm install -D prettier prettier-plugin-tailwindcss eslint-config-prettier

# Optional enhancements
npm install framer-motion react-intersection-observer
```

---

## Phase 3 - Core Development

### 🏠 Create Layout Component

**`components/Layout/Navbar.jsx`:**

```jsx
import Link from 'next/link';

export default function Navbar() {
  return (
    <nav className="fixed top-0 w-full bg-gray-900 text-white z-50">
      <div className="max-w-6xl mx-auto px-4">
        <div className="flex justify-between items-center h-16">
          <Link href="/" className="font-bold text-xl">YourName</Link>
          <div className="flex space-x-6">
            <Link href="/projects" className="hover:text-blue-400">Projects</Link>
            <Link href="/writeups" className="hover:text-blue-400">Writeups</Link>
            <Link href="/blog" className="hover:text-blue-400">Blog</Link>
            <Link href="/cv" className="hover:text-blue-400">CV</Link>
            <Link href="/contact" className="hover:text-blue-400">Contact</Link>
          </div>
        </div>
      </div>
    </nav>
  );
}
```

### 🎨 Create Home Page

**`app/page.jsx`:**

```jsx
import { FaGithub, FaLinkedin, FaTwitter } from 'react-icons/fa';

export default function Home() {
  const skills = {
    security: ["Linux Security", "Network Analysis", "OSINT", "Vulnerability Assessment"],
    programming: ["Python", "Bash Scripting", "JavaScript", "SQL"],
    tools: ["Wireshark", "Nmap", "Metasploit", "Git"]
  };

  return (
    <main className="min-h-screen">
      {/* Hero Section */}
      <section className="h-screen flex items-center justify-center bg-gradient-to-b from-gray-900 to-gray-800 text-white">
        <div className="text-center">
          <h1 className="text-5xl font-bold mb-4">Hi, I'm [Your Name]</h1>
          <p className="text-xl mb-8">Aspiring SOC Analyst | Security Enthusiast</p>
          
          {/* Social Links */}
          <div className="flex justify-center space-x-4 mb-8">
            <a href="https://github.com/yourusername" className="text-3xl hover:text-blue-400">
              <FaGithub />
            </a>
            <a href="https://linkedin.com/in/yourusername" className="text-3xl hover:text-blue-400">
              <FaLinkedin />
            </a>
          </div>
          
          <button className="bg-blue-600 px-6 py-3 rounded-lg hover:bg-blue-700">
            View My Work
          </button>
        </div>
      </section>
    </main>
  );
}
```

### 📝 Create Additional Pages

Create similar structures for:

- `app/projects/page.jsx`
- `app/writeups/page.jsx`
- `app/blog/page.jsx`
- `app/cv/page.jsx`
- `app/contact/page.jsx`

---

## Phase 4 - Content Management

### 📄 Markdown Processing

**Create `lib/mdx.js`:**

```javascript
import fs from 'fs';
import path from 'path';
import matter from 'gray-matter';

export function getContentBySlug(type, slug) {
  const contentDir = path.join(process.cwd(), 'content', type);
  const filePath = path.join(contentDir, `${slug}.md`);
  const fileContent = fs.readFileSync(filePath, 'utf-8');
  
  const { data, content } = matter(fileContent);
  
  return {
    metadata: data,
    content
  };
}

export function getAllContent(type) {
  const contentDir = path.join(process.cwd(), 'content', type);
  const files = fs.readdirSync(contentDir);
  
  return files.map(filename => {
    const slug = filename.replace('.md', '');
    const { metadata } = getContentBySlug(type, slug);
    return { slug, ...metadata };
  });
}
```

### 📑 Content Templates

**Writeup Template (`content/writeups/template.md`):**

````markdown
---
title: "OverTheWire Bandit Level X"
date: "2024-08-03"
category: "OverTheWire"
difficulty: "Easy"
tags: ["linux", "permissions", "bash"]
---

## Challenge Description
Brief description of the challenge

## Initial Analysis
My thought process and approach

## Solution
```bash
# Commands used
ssh bandit0@bandit.labs.overthewire.org -p 2220
cat readme
````

## Key Takeaways

- Important concept learned
- Technique to remember

````

---

## Phase 5 - Deployment

### 🌐 Environment Setup

**Create `.env.local`:**
```env
NEXT_PUBLIC_SITE_URL=https://yourname.dev
NEXT_PUBLIC_GITHUB_URL=https://github.com/yourusername
NEXT_PUBLIC_LINKEDIN_URL=https://linkedin.com/in/yourusername
````

### 🚀 Deploy to Vercel

1. **Install Vercel CLI:**

```bash
npm i -g vercel
```

2. **Deploy:**

```bash
vercel
# Follow prompts to connect GitHub repository
```

3. **Configure Custom Domain:**
    - Purchase domain from Cloudflare
    - In Vercel Dashboard → Settings → Domains
    - Add custom domain and follow DNS instructions

### 🔍 SEO Configuration

**Update `app/layout.jsx`:**

```jsx
export const metadata = {
  title: 'Your Name - Security Portfolio',
  description: 'Aspiring SOC Analyst showcasing security projects and writeups',
  openGraph: {
    title: 'Your Name - Security Portfolio',
    description: 'Security projects, writeups, and technical blog',
    url: 'https://yourname.dev',
    siteName: 'Your Name',
    type: 'website',
  },
};
```

---

## Quick Reference

### 💻 Development Commands

```bash
# Start development server
npm run dev

# Build for production
npm run build

# Run production build locally
npm run start

# Lint code
npm run lint

# Format code
npm run format
```

### 🔧 Git Workflow

```bash
# Check status
git status

# Stage changes
git add .

# Commit
git commit -m "feat: add projects page"

# Push to GitHub
git push origin main

# Create feature branch
git checkout -b feature/new-feature

# Merge branch
git checkout main
git merge feature/new-feature
```

### 📋 VS Code Shortcuts

|Shortcut|Action|
|---|---|
|`Cmd/Ctrl + P`|Quick file open|
|`Cmd/Ctrl + Shift + P`|Command palette|
|`Cmd/Ctrl + B`|Toggle sidebar|
|` Cmd/Ctrl + `` `|Toggle terminal|
|`Cmd/Ctrl + /`|Comment line|

---

## 📊 Progress Checklist

### Week 1

- [ ] GitHub repository created
- [ ] Development environment setup
- [ ] Basic page structure complete
- [ ] Navigation working

### Week 2

- [ ] 5+ writeups published
- [ ] 2+ projects documented
- [ ] CV page complete
- [ ] Contact form functional

### Week 3

- [ ] Custom domain configured
- [ ] SEO optimized
- [ ] Performance optimized
- [ ] Mobile responsive

### Week 4

- [ ] 15+ total content pieces
- [ ] Social media linked
- [ ] Analytics configured
- [ ] Ready for applications

---

## 📚 Additional Resources

- [Next.js Documentation](https://nextjs.org/docs)
- [Tailwind CSS Documentation](https://tailwindcss.com/docs)
- [Vercel Deployment Guide](https://vercel.com/docs)
- [MDX Documentation](https://mdxjs.com/)

---

_Last Updated: August 2024_