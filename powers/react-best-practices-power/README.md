# React Best Practices Power

A Kiro Power for React and Next.js performance optimization best practices from Vercel Engineering.

## Overview

This is a **Knowledge Base Power** (no MCP server) that provides comprehensive performance optimization guidance for React and Next.js applications. It contains 47 rules across 8 categories, prioritized by impact.

## Structure

```
react-best-practices-power/
├── POWER.md              # Main power documentation with quick reference
├── steering/             # Individual rule files (47 files)
│   ├── async-*.md        # Eliminating Waterfalls rules (5 files)
│   ├── bundle-*.md       # Bundle Size Optimization rules (5 files)
│   ├── server-*.md       # Server-Side Performance rules (5 files)
│   ├── client-*.md       # Client-Side Data Fetching rules (4 files)
│   ├── rerender-*.md     # Re-render Optimization rules (7 files)
│   ├── rendering-*.md    # Rendering Performance rules (7 files)
│   ├── js-*.md           # JavaScript Performance rules (12 files)
│   └── advanced-*.md     # Advanced Patterns rules (2 files)
└── README.md             # This file
```

## Power Type

**Knowledge Base Power** - Pure documentation without MCP server integration.

## Installation

### Via Kiro Powers UI

1. Open Kiro Powers panel
2. Click "Add Custom Power"
3. Select "Local Directory"
4. Provide path: `./agent-skills/powers/react-best-practices-power`
5. Click "Add"

### Via File Copy

```bash
cp -r powers/react-best-practices-power ~/.kiro/powers/
```

## Usage

Once installed, the power will be activated when working with React/Next.js code. Keywords that trigger this power:

- react
- nextjs
- performance
- optimization
- vercel
- bundle
- rendering
- server-components

### Quick Reference

The POWER.md file provides:
- Overview of all 8 rule categories
- Quick reference for all 47 rules
- Common patterns and troubleshooting
- Best practices for applying rules

### Detailed Rules

For complete details on any specific rule, agents can access individual steering files:

```
# Example: Load barrel imports rule
Call action "readSteering" with powerName="react-best-practices", steeringFile="bundle-barrel-imports.md"

# Example: Load parallel fetching rule
Call action "readSteering" with powerName="react-best-practices", steeringFile="async-parallel.md"
```

This enables efficient dynamic loading - agents only load the specific rules they need for the current context.

## Rule Categories

1. **Eliminating Waterfalls** (CRITICAL) - 5 rules
2. **Bundle Size Optimization** (CRITICAL) - 5 rules
3. **Server-Side Performance** (HIGH) - 5 rules
4. **Client-Side Data Fetching** (MEDIUM-HIGH) - 4 rules
5. **Re-render Optimization** (MEDIUM) - 7 rules
6. **Rendering Performance** (MEDIUM) - 7 rules
7. **JavaScript Performance** (LOW-MEDIUM) - 12 rules
8. **Advanced Patterns** (LOW) - 2 rules

## Source

Converted from the react-best-practices skill located at:
`skills/react-best-practices/`

Original content maintained by Vercel Engineering.

## License

MIT

## Version

1.0.0 (January 2026)
