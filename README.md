# Claude Plugin Marketplace

A curated marketplace of Claude skills for founders and startups, powered by Claude.

## Overview

This repository hosts a collection of specialized Claude skills designed to help you work more effectively. Each skill provides structured workflows and domain expertise that can be instantly added to your Claude conversations.

## Available Skills

### Market Research Analyst

**Version:** 1.0.0

A 4-stage market research pipeline for D2C founders and startups.

**What it does:**
- Runs structured competitor analysis, PMF analysis, or comprehensive market research
- Provides citation-backed insights with no fabrication
- Outputs plain language reports from product descriptions

**Research modes:** Competitor | PMF | Comprehensive

## Installation

### Via Claude.ai Marketplace (Recommended)

1. Go to [claude.ai](https://claude.ai).
2. Click **Customize**.
3. Select **Add plugin**
4. Choose **Add marketplace**
5. Select **Add from repository**
6. Paste the repository link: `https://github.com/KeyValueSoftwareSystems/keyvalue-claude-marketplace`
7. Click **Sync**

All skills in this repo will be available.

## Usage

Once installed, skills are automatically available in your Claude conversations. Each skill triggers based on specific keywords or contexts relevant to its domain.

**Example:** For market research, simply describe your product or market:
```
"I'm building a sustainable activewear brand. 
I want to understand the competitive landscape."
```

The relevant skill will activate and guide you through its workflow.

## Repository Structure

```
keyvalue-claude-marketplace/
├── .claude-plugin/
│   ├── marketplace.json       # Marketplace configuration
│   └── plugin.json             # Root plugin metadata
└── skills/
    └── [skill-name]/           # Individual skill packages
        ├── .claude-plugin/
        └── skills/
```

Each skill is self-contained with its own documentation and configuration.

## Version

Current version: `1.0.0`

## Owner

Maintained by **aghash**

## Contributing

Contributions are welcome! You can:
- Submit new skills to the marketplace
- Enhance existing skills with new features
- Report issues or suggest improvements
- Improve documentation

Please submit issues or pull requests following the repository guidelines.

## License

[Add your license information here]

## Support

For questions, issues, or feature requests, please open an issue in this repository.
