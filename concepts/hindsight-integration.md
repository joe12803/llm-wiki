---
title: Hindsight Integration
type: concept
tags: [#tool, #lesson]
created: 2026-05-06
updated: 2026-05-06
---

# Hindsight Integration

## Summary
Attempted to integrate `vectorize-io/hindsight` as a memory system.

## Lessons Learned
- **API Sensitivity**: Hindsight's `HindsightServer` is sensitive to API providers. Passing a proxy API key to the native Gemini provider causes 400 errors.
- **Dependency Heavy**: Requires significant local resources for embedding and fact extraction.
- **Alternative**: User's own [[llm-wiki]] is preferred for its transparency and simplicity.

## Resources
- Repo: `https://github.com/vectorize-io/hindsight`
