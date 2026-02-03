---
name: website-copywriter
description: Generate SEO-optimized, bilingual (English & Chinese) website copy for hero sections and branding descriptions. This skill should be used when users need to create compelling marketing content for new websites, especially tool-focused platforms, by providing just a theme or topic name.
license: MIT
---

# Website Copywriter

This skill generates SEO-optimized website copy in both English and Chinese for hero sections and branding descriptions based on a given theme or topic.

## Purpose

When creating new websites, generating compelling, SEO-friendly copy can be time-consuming and challenging. This skill automates the creation of:

- **Branding description** - A concise tagline describing the website's purpose
- **Hero badge** - An attention-grabbing announcement or call-to-action
- **Hero title** - A powerful, memorable headline
- **Hero description** - A detailed value proposition that converts visitors

All content is optimized for:
1. **Appeal** - Engaging and conversion-focused language (primary priority)
2. **SEO** - Strategic keyword placement and density (secondary priority)
3. **Length** - Concise yet informative (150-160 characters for descriptions)

## When to Use

Use this skill when:
- Creating a new website configuration
- Need bilingual (English & Chinese) marketing copy
- Starting with just a theme/topic and need professional copy
- Building tool-focused platforms or marketplaces
- Want SEO-optimized content without manual copywriting

## How to Use

### Input Required

Ask the user for the **theme or topic name** of the website. Examples:
- "AI 图片编辑器" (AI Image Editor)
- "开源项目市场" (Open Source Marketplace)  
- "在线协作白板" (Online Collaborative Whiteboard)
- "代码片段分享平台" (Code Snippet Sharing Platform)

### Generation Process

1. **Understand the theme** - Analyze the topic to identify:
   - Core functionality and value proposition
   - Target audience
   - Key differentiators
   - Relevant SEO keywords

2. **Generate branding description** - Create a concise one-liner (5-10 words) that captures the essence

3. **Generate hero badge** - Create an attention-grabbing badge with emoji (8-15 words)
   - Use action-oriented language
   - Include emoji that matches the theme
   - Create urgency or excitement

4. **Generate hero title** - Create a powerful headline (3-6 words)
   - Use strong action verbs
   - Make it memorable and unique
   - Avoid generic phrases

5. **Generate hero description** - Create a compelling paragraph (20-30 words)
   - Lead with benefits, not features
   - Include 2-3 strategic keywords naturally
   - End with a call-to-action sentiment
   - Keep under 160 characters for meta description compatibility

### Output Format

Present the generated copy in a structured format matching the `site-config.ts` structure:

```typescript
branding: {
  name: '[Topic Name]',
  logo: '[Relevant Emoji]',
  description: '[Concise description]',
},
hero: {
  badge: {
    en: '🚀 [English Badge]',
    cn: '🚀 [Chinese Badge]',
  },
  title: {
    en: '[English Title]',
    cn: '[Chinese Title]',
  },
  description: {
    en: '[English Description]',
    cn: '[Chinese Description]',
  },
},
```

### Quality Guidelines

**English Copy:**
- Use active voice and strong verbs
- Avoid jargon unless industry-standard
- Make it conversational yet professional
- Test for natural keyword integration

**Chinese Copy:**
- Use modern, internet-friendly language (互联网化表达)
- Avoid overly formal or translated-feeling text
- Ensure cultural relevance
- Match the tone and energy of English version

**SEO Keywords:**
- Integrate 2-3 primary keywords naturally
- Use semantic variations
- Place important keywords early in descriptions
- Avoid keyword stuffing

**Emotional Appeal:**
- Lead with transformation/benefits
- Create curiosity or urgency
- Use power words (discover, unlock, transform, accelerate)
- Appeal to user aspirations

## Examples

### Example 1: AI Code Assistant

**Input:** "AI 代码助手" (AI Code Assistant)

**Output:**
```typescript
branding: {
  name: 'CodeAI',
  logo: '🤖',
  description: 'Intelligent code assistant powered by AI',
},
hero: {
  badge: {
    en: '⚡ AI-Powered Development Made Easy',
    cn: '⚡ AI 驱动，让开发更简单',
  },
  title: {
    en: 'Code Smarter, Ship Faster',
    cn: '智能编码，极速交付',
  },
  description: {
    en: 'Transform your development workflow with AI-powered code completion, debugging, and refactoring. Write better code in half the time.',
    cn: '借助 AI 驱动的代码补全、调试和重构，革新你的开发流程。用一半时间写出更好的代码。',
  },
},
```

### Example 2: Design Resource Platform

**Input:** "设计资源平台" (Design Resource Platform)

**Output:**
```typescript
branding: {
  name: 'DesignHub',
  logo: '🎨',
  description: 'Premium design resources for creative professionals',
},
hero: {
  badge: {
    en: '✨ 10,000+ Premium Design Assets',
    cn: '✨ 10,000+ 优质设计资源',
  },
  title: {
    en: 'Elevate Your Creative Projects',
    cn: '提升你的创意项目',
  },
  description: {
    en: 'Access curated design resources, templates, and tools trusted by 50k+ designers. Create stunning work with premium assets.',
    cn: '访问 50,000+ 设计师信赖的精选设计资源、模板和工具。用优质素材创造惊艳作品。',
  },
},
```

### Example 3: Online Collaboration Tool

**Input:** "在线协作工具" (Online Collaboration Tool)

**Output:**
```typescript
branding: {
  name: 'TeamSync',
  logo: '🤝',
  description: 'Real-time collaboration for distributed teams',
},
hero: {
  badge: {
    en: '🌐 Join 100k+ Teams Collaborating Worldwide',
    cn: '🌐 加入全球 100k+ 团队的协作网络',
  },
  title: {
    en: 'Work Together, Anywhere',
    cn: '随时随地，协同工作',
  },
  description: {
    en: 'Seamlessly collaborate with your team in real-time. Share ideas, track progress, and achieve goals faster with intuitive tools.',
    cn: '与团队实时无缝协作。分享想法、跟踪进度，用直观的工具更快实现目标。',
  },
},
```

## Tips for Best Results

1. **Ask clarifying questions** if the theme is too broad or ambiguous
2. **Consider the target audience** - B2B vs B2C affects tone
3. **Research competitors** if needed to ensure differentiation
4. **Iterate based on feedback** - offer 2-3 variations if requested
5. **Validate length** - ensure descriptions are under 160 characters for SEO
6. **Check natural flow** - read aloud to ensure copy doesn't feel forced

## Common Pitfalls to Avoid

- ❌ Generic titles like "The Best Platform" or "Ultimate Solution"
- ❌ Feature-first descriptions instead of benefit-first
- ❌ Keyword stuffing that makes text awkward
- ❌ Overly long descriptions that lose impact
- ❌ Mismatched tone between English and Chinese versions
- ❌ Using clichés without adding unique value
