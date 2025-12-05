# Contributing to The RS Guide

Welcome! This repository contains the MDX content for The RS Guide website. This is a submodule that gets merged into the main Next.js [Fumadocs](https://fumadocs.dev/) application at build time.

## Table of Contents

- [How to Contribute](#how-to-contribute)
  - [Creating Issues](#creating-issues)
  - [Opening Pull Requests](#opening-pull-requests)
- [Understanding MDX](#understanding-mdx)
  - [What is MDX?](#what-is-mdx)
  - [MDX File Structure](#mdx-file-structure)
  - [Frontmatter](#frontmatter)
- [JSX Components in MDX](#jsx-components-in-mdx)
  - [Why JSX?](#why-jsx)
  - [Common Components](#common-components)
- [Meta.json Files](#metajson-files)
  - [What are Meta.json Files?](#what-are-metajson-files)
  - [Meta.json Structure](#metajson-structure)
  - [When to Create or Edit Meta.json Files](#when-to-create-or-edit-metajson-files)
  - [Tips for Meta.json Files](#tips-for-metajson-files)
- [File Structure](#file-structure)
- [Need Help?](#need-help)

## How to Contribute

We welcome contributions from everyone! There are two main ways to contribute:

### Creating Issues

If you've found a problem, have a suggestion, or want to request new content, please create an issue on GitHub:

1. Go to the [Issues](https://github.com/TheJoshJ/TheRSGuide/issues) page
2. Click "New Issue"
3. Choose the appropriate issue template (if available) or select "Get started" for a blank issue
4. Fill in the title and description with:
   - What you'd like to see changed or added
   - Why it would be helpful
   - Any relevant details or examples
5. Click "Submit new issue"

### Opening Pull Requests

If you'd like to make changes directly to the content, you can open a pull request (PR). Here's how:

#### Option 1: Fork the Repository (Recommended for External Contributors)

1. **Fork the repository** by clicking the "Fork" button at the top right of the GitHub page
2. **Clone your fork** to your computer:
   ```bash
   git clone https://github.com/TheJoshJ/TheRSGuide.git
   cd TheRSGuide
   ```
3. **Create a new branch** for your changes.
   ```bash
   git checkout -b your-branch-name
   ```
   > **Note:** Replace `"your-branch-name"` with a brief description of what you will be contributing (e.g., `"fix-typeo-in-guide"` or `"fix-directions-in-guide"`). Avoid using the placeholder name `"your-branch-name"`.
4. **Make your changes** to the MDX files (see sections below for guidance)
5. **Commit your changes**:
   ```bash
   git add .
   git commit -m "A short summary of your changes"
   ```
   > **Note:** Replace `"A short summary of your changes"` with a brief but specific explanation of what you changed (e.g., `"Fix typo in melee guide"` or `"Add new section on threshold abilities"`). Avoid using the placeholder message of `"add description of your changes"`.
6. **Push to your fork**:
   ```bash
   git push origin your-branch-name
   ```
   > **Note:** Replace `"your-branch-name"` with the name of the branch you chose in step 3.
7. **Open a Pull Request**:
   - Go to the repository on [GitHub](https://github.com/TheJoshJ/TheRSGuide)
   - You should see a banner suggesting to create a PR from your recent push
   - Click "Compare & pull request"
   - Fill in the PR description explaining your changes
   - Click "Create pull request"


## Understanding MDX

### What is MDX?

MDX stands for **Markdown + JSX**. It's a file format that lets you write Markdown (a simple text formatting language) while also using JSX components (React components) within your content.

Think of it like this:

- **Markdown** = Easy-to-write text formatting (like bold, headings, lists)
- **JSX** = Interactive components that can do more complex things
- **MDX** = The best of both worlds!

> **New to Markdown?** Check out the [GitHub Flavored Markdown guide](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax) for a complete reference on Markdown syntax, including headings, lists, links, images, and more.

### MDX File Structure

Every MDX file in this repository follows a standard structure:

```mdx
---
title: Page Title
description: A brief description of the page
---

# Page Title

Your content goes here in Markdown format.

## Section Heading

You can write paragraphs, lists, and use formatting.

<Cards>
  <Card
    title="Card Title"
    href="https://example.com"
  />
</Cards>
```

### Frontmatter

The section at the top between the `---` lines is called **frontmatter**. It contains metadata about the page:

- **title**: The page title that appears in the navigation and page header
- **description**: A brief description used for SEO and page previews

Both fields are required for every page.

## JSX Components in MDX

### Why JSX?

You might notice that some pages contain code that looks like HTML but uses angle brackets with component names (like `<Cards>` or `<Card>`). This is JSX (JavaScript XML), and it allows us to embed interactive React components directly in our Markdown content.

JSX components allow us to:

- Create interactive elements that wouldn't be possible with plain Markdown
- Maintain consistent styling and layout across the site
- Build reusable components that can be used throughout the guide
- Add functionality like navigation cards, code examples, and more

Don't worry if you're not familiar with JSX - you can contribute great content using just Markdown! The JSX components are provided for specific use cases, and you can always ask in an issue if you're unsure how to use them.

### Common Components

For detailed information about available components and how to use them, see our [components guide](components.md).

> **Note:** At this time, we do not accept contributions that include custom JSX components that do not already exist in our component library. Please use only the components documented in the [components guide](components.md), or use plain Markdown for your content. If you need a component that doesn't exist, please open an issue to discuss it first.

## Meta.json Files

### What are Meta.json Files?

In Fumadocs (the documentation framework used by the main site), `meta.json` files control the **order and structure** of pages in the navigation sidebar. They tell Fumadocs which pages exist and in what order they should appear.

### Meta.json Structure

A `meta.json` file is a simple JSON file that contains a `pages` array:

```json
{
  "pages": ["index", "keybinds", "combat-basics", "damage"]
}
```

**Important points:**

- Each entry in the `pages` array is a **filename without the `.mdx` extension**
- The order in the array determines the order pages appear in the navigation
- The `index` page is typically first and serves as the overview page for that content section

### When to Create or Edit Meta.json Files

#### Adding a New Page to an Existing Section

If you're adding a new page to an existing directory (like `content/getting-started/`), you need to add it to that directory's `meta.json` file:

1. Open the `meta.json` file in the directory where your new page will live
2. Add the filename (without `.mdx`) to the `pages` array in the desired position
3. Make sure the JSON is valid (commas between items, proper brackets)

**Example:** Adding a new page called `skilling-basics.mdx` to `content/getting-started/`:

**Before:**

```json
{
  "pages": ["index", "keybinds", "combat-basics"]
}
```

**After:**

```json
{
  "pages": ["index", "keybinds", "combat-basics", "skilling-basics"]
}
```

#### Creating a New Section with Multiple Pages

If you're creating a completely new section (new directory), you'll need to:

1. Create the new directory (e.g., `content/new-section/`)
2. Create your MDX files in that directory
3. Create a `meta.json` file in that directory listing all your pages
4. Add the new section to the parent directory's `meta.json` (if it's a subsection)

**Example:** Creating a new section called `Bossing`:

1. Create `content/guides/pvp/index.mdx`
2. Create `content/guides/pvp/strategy.mdx`
3. Create `content/guides/pvp/meta.json`:
   ```json
   {
     "pages": ["index", "strategy"]
   }
   ```
4. Add `"pvp"` to `content/guides/meta.json`:
   ```json
   {
     "pages": ["index", "early-game", "mid-game", "late-game", "Bossing"]
   }
   ```

### Tips for Meta.json Files

- Always include `"index"` as the first page in a section's meta.json
- Keep page names consistent (use kebab-case: `my-page-name.mdx`)
- The order matters - arrange pages in a logical reading order
- If you're unsure where a page should go, ask in an issue or PR description

## File Structure

The content is organized in the `content/` directory with the following structure:

```
content/
├── getting-started/
│   ├── meta.json
│   ├── index.mdx
│   ├── combat-basics.mdx
│   └── combat-options/
│       ├── meta.json
│       ├── index.mdx
│       └── ...
├── guides/
│   ├── meta.json
│   ├── early-game/
│   ├── mid-game/
│   └── late-game/
└── setup/
    ├── meta.json
    └── ...
```

Each directory can contain:

- MDX files (the actual content)
- A `meta.json` file (defines page order)
- Subdirectories (for organizing related content)

## Need Help?

If you have questions or need clarification:

- Open an issue on GitHub with your question
- Check existing issues and pull requests for examples
- Ask in your pull request description - we're happy to help!

Thank you for contributing to The RS Guide!