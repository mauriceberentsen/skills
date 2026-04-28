# Brave Search MCP Skill
Use this MCP server when the user asks for information that may be current, external, niche, or not available in the model context.
The Brave Search MCP server provides web search, local business search, image search, video search, news search, LLM-context search, and summarization capabilities through the Brave Search API. It can be used to ground answers with live web results and reduce hallucinations.  [oai_citation:0‡GitHub](https://github.com/brave/brave-search-mcp-server?utm_source=chatgpt.com)
## When to use
Use Brave Search for:
- Recent or changing information
- News, releases, prices, versions, laws, schedules, APIs, product specs
- Debugging errors from public tools, GitHub issues, documentation, changelogs
- Comparing products, tools, models, vendors, or libraries
- Finding official documentation
- Finding public GitHub issues, PRs, examples, and workarounds
- Local search only when the user asks for places, businesses, restaurants, services, or physical locations
Do not use Brave Search for:
- Pure reasoning
- Rewriting text
- Summarizing user-provided text
- Private/internal facts unless the user provides them
- Tasks that require access to private systems
## Tool selection
Prefer the most specific Brave tool available:
- `brave_web_search`: general web search
- `brave_news_search`: recent news or announcements
- `brave_local_search`: local businesses, places, services
- `brave_image_search`: images or visual references
- `brave_video_search`: videos, talks, demos
- `brave_llm_context`: extract/read page content for synthesis when available
- summarization tool: use after search when the user wants a digest or comparison
## Search strategy
1. Start with the exact error message, product name, or official term.
2. Prefer official docs, GitHub issues, release notes, changelogs, and vendor pages.
3. Search broader only if exact search fails.
4. For bugs, include version numbers when known.
5. For technical questions, verify against primary sources.
6. For recent topics, compare publication dates.
7. For ambiguous terms, search first before assuming meaning.
## Answering rules
Always include sources when the answer depends on search results.
For technical fixes:
- State the likely cause
- Give the safest fix first
- Mention known affected versions when found
- Include commands or config snippets when useful
- Clearly mark workarounds as workarounds
For recommendations:
- Explain the trade-off briefly
- Prefer stable, maintained, official options
- Avoid overconfident claims if sources are weak
## Query examples
Exact error:
```text
"Error creating mcp server" "source_url" "LiteLLM_MCPServerTable"

Version-specific bug:

LiteLLM v1.82.3 MCP Server source_url migration

Official docs:

site:docs.litellm.ai MCP server LiteLLM

GitHub issues:

site:github.com/BerriAI/litellm MCPServerTable source_url

Release notes:

LiteLLM release notes MCP source_url migration

Safety and quality

Do not invent source details.
Do not cite irrelevant results.
Do not rely on snippets alone when the full page is needed.
Prefer multiple independent sources for important claims.
When search results conflict, say so and prefer official documentation or maintainer comments.
