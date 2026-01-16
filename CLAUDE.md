# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Sui Sentinel is a documentation site for a decentralized AI safety and alignment platform on the Sui blockchain. The platform gamifies AI red teaming through adversarial testing, where defenders stake capital to prove their AI models can withstand attacks, and attackers earn rewards by discovering vulnerabilities.

## Tech Stack

- **Mintlify**: Documentation framework (configured via `docs.json`)
- **MDX**: Markdown + JSX format for content pages
- **Theme**: Willow theme with custom styling

## Development Commands

### Local Preview
```bash
# Install Mintlify CLI globally (if not already installed)
npm i -g mint

# Start development server at root of repo (where docs.json is located)
mint dev
```

The local preview runs at `http://localhost:3000`.

## Architecture

### docs.json Configuration

The `docs.json` file is the central configuration that controls:
- Navigation structure (groups and pages)
- Theme and styling (colors, logo, favicon)
- Navbar and footer links
- Social media integration

### Content Structure

Documentation is organized by groups in `docs.json`:

- **First steps**: Core protocol concepts (mechanics, judgment process, economic design)
- **Guides**: User guides for defenders, attackers, and scouts
- **Concepts**: AI red teaming fundamentals and attack vectors
- **Tokenomics & Incentives**: Economic model and reward structures
- **Advance Concepts**: Technical deep-dives (signature generation, prompt injection, AI safety research)
- **Reference**: Audits and contract addresses

### Content Files

- All content files use `.mdx` extension (MDX format)
- Frontmatter defines title and description
- Navigation entries in `docs.json` reference files without extension (e.g., `"first-steps/index"` maps to `first-steps/index.mdx`)

### Key Assets

- `/logo/`: Light and dark mode logos
- `/images/`: Documentation images and thumbnails

## External References

- Protocol app: https://app.suisentinel.xyz
- Contracts: https://github.com/sui-sentinel/contracts
- Community: Telegram (https://t.me/suisentinel), Discord, Twitter/X
