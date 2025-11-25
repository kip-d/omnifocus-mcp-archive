# OmniFocus MCP Development Archive

## What is This?

This repository contains the complete, unfiltered development history of the OmniFocus MCP server from initial prototype to production v2.0.0.

## Why Preserve This?

These documents show:
- **Failed approaches** that seemed promising but didn't work
- **Performance investigations** including the discovery that JXA's `whose()` method was the root cause of 25-second queries
- **Architectural pivots** from many specialized tools to consolidated operations
- **Debugging sessions** tracking down obscure issues like 51KB script truncation
- **Dead ends** that consumed weeks of effort

## Structure

### `/journey/performance/`
The dramatic performance improvement story:
- From 25+ second queries to <1 second
- Discovery of the `whose()` catastrophe
- Various optimization attempts and measurements

### `/journey/technical/`
Deep technical investigations:
- JXA capabilities and limitations
- Bridge context issues
- Script size problems
- Hybrid approach research

### `/journey/sessions/`
Day-by-day development logs:
- Real-time problem solving
- Decision points and rationale
- Testing protocols and results

## Key Lessons (TL;DR)

The main insights are captured in the production repo's [LESSONS_LEARNED.md](https://github.com/yourusername/omnifocus-mcp/blob/main/docs/LESSONS_LEARNED.md).

## Why Not in Main Repo?

- **Size**: 212KB of historical documents
- **Relevance**: Most developers just need the working solution
- **Clarity**: Keeps main repo focused on current architecture

## For Researchers

If you're studying:
- **LLM-assisted development**: See how Claude helped solve complex problems
- **Performance optimization**: Follow the systematic investigation process
- **API evolution**: Understand why we consolidated from 22 to 14 tools
- **Real-world debugging**: Learn from actual debugging sessions

## Navigation Guide

Start with:
1. `journey/README.md` - Overview of the entire journey
2. `journey/performance/PERFORMANCE_BREAKTHROUGH.md` - The game-changing discovery
3. `journey/technical/JXA_CAPABILITIES_AUDIT.md` - Understanding platform limits

## Contributing

This is a historical archive and won't be updated. For current development, see the [main repository](https://github.com/yourusername/omnifocus-mcp).

## License

Same as main repository (MIT). These documents are provided as-is for educational purposes.

---

*"Those who don't understand history are doomed to repeat it."*