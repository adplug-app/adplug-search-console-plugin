# AdPlug: Google Search Console for Grok Bot and Cursor

AdPlug is a hosted MCP server that safely connects Google Search Console to Grok, Grok Bot and Cursor.

Your agent can check rankings and clicks, find the pages losing traffic, explain why a page isn't indexed and, on a paid plan, submit the sitemaps you approve.

The plugin adds one remote MCP server, `https://api.adplug.app/mcp/google-search-console`, and nothing else. There's no code, no script and no hook in it.

## Install in Grok Bot

1. Open **Connect apps** in the sidebar. On your phone, tap your avatar at the top left, then **Connect apps**.
2. Find **AdPlug: Google Search Console** and click **Add**.
3. Click **Authenticate** (it says **Authorize** on the phone).
4. Sign in to AdPlug, or create a free account, and click **Approve**. The approval screen says "Cursor wants to access your AdPlug account". That's expected: Grok Bot connects apps through Cursor.

You can also add it from a chat. Send your Bot this message:

> Add a custom MCP server called AdPlug Search Console at https://api.adplug.app/mcp/google-search-console

Click **Authorize** on the card it posts, then **Continue**, then sign in to AdPlug in the browser tab that opens and click **Approve**.

## Install in Cursor

Run `/add-plugin adplug-search-console` in a chat, or install it from the Cursor Marketplace.

To set it up by hand, add `https://api.adplug.app/mcp/google-search-console` as a server in Cursor's MCP settings, or put this in `.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "adplug-search-console": {
      "url": "https://api.adplug.app/mcp/google-search-console"
    }
  }
}
```

The first time you connect, a browser tab opens on AdPlug's sign-in. Sign in, or create a free account, and click **Approve**.

## What you need

- An AdPlug account. The free plan connects one platform, comes with a monthly request limit and is view only: your agent can read your Search Console data and preview changes, but not apply them. A paid plan lets the agent make changes and connect more Google accounts (3 on Pro, 5 on Max): see [adplug.app/pricing](https://adplug.app/pricing).
- Search Console connected once in AdPlug, at [adplug.app/dashboard/connections](https://adplug.app/dashboard/connections), with your Google sign-in.

There's no API key or client ID to set up. Sign-in is OAuth 2.1 with dynamic client registration and PKCE.

## What your agent can do

- **Properties:** every Domain and URL-prefix property your Google account can use, or a one-call overview of all of them with 28-day totals (handy for agencies).
- **Reports:** clicks, impressions, CTR and average position by query, page, country, device, search appearance, day, week, month or hour. Web, image, video, news, Discover and Google News, with filters, regex and period comparison.
- **Ready-made analyses, worked out on AdPlug's server so the numbers are exact:** what changed, anomalies, declining pages, striking-distance queries, CTR opportunities, cannibalisation, new and lost queries, brand versus non-brand, the CTR shift that shows AI Overviews' footprint, Core Web Vitals, and paid versus organic when Google Ads is connected to the same AdPlug account.
- **URL inspection:** up to 25 URLs at a time, Google's index status next to what the live page says now, and what changed since AdPlug last inspected it.
- **Sitemaps:** Search Console's status for each one, sitemaps listed in robots.txt, and a live audit of the URLs inside with an estimated indexed share.
- **Changes:** submit or remove a sitemap, add or remove a property.

What Google's API doesn't offer, so AdPlug can't either: **Request indexing** for normal pages, and the Page indexing, Links, Manual actions, Security issues and Crawl stats reports, removals and disavow. Your agent sends you to Search Console for those.

`adplug_get_status` tells the agent whether Search Console is connected and what your plan allows.

## Example prompts

- "Organic clicks on [site] fell this month. Compare the last 28 days with the 28 before: which pages and queries lost the most, was it rankings, CTR or demand, and did a Google update land in that window?"
- "Find queries on [site] ranking between positions 5 and 20 with real impressions. Rank them by the clicks I'd gain at position 3 and tell me which page should win each one."
- "Inspect https://[your-site].com/[page]. Is it indexed? Compare what Google saw with the live page and tell me what to fix first."
- "Summarise every property I can see: clicks and impressions for the last 28 days, the change against the 28 days before, biggest sites first."

## How changes are kept safe

- Every change starts as a preview that shows exactly what will happen. AdPlug's server only makes a change when the execute tool is called with that preview's ID.
- On the free plan, the change tools refuse to apply anything.
- On Max and Agency plans, a team owner can set a teammate to View only for Search Console. AdPlug then hides and blocks the change tools for that teammate.
- Grok Bot and Cursor can also ask you before a tool runs, depending on your settings.
- Every call is logged on the [usage page](https://adplug.app/dashboard/usage) of your AdPlug dashboard.

## Your data and where it goes

Every tool call goes to one endpoint, `https://api.adplug.app/mcp/google-search-console`. Sign-in goes through AdPlug's pages on adplug.app and its sign-in provider, Supabase (named in api.adplug.app's OAuth metadata). The plugin adds no software and runs no scripts on your computer.

Search Console data travels between Google and your agent through AdPlug's servers at api.adplug.app. Reports are fetched live and not kept. AdPlug keeps the results of URL inspections so it can tell you what changed since the last one, keeps a change preview for up to two days so it can be applied, and logs each call's tool and time for your usage page, never its arguments or results. Google sign-in tokens are stored encrypted.

This repo holds the plugin manifest (`.cursor-plugin/plugin.json`), the server address (`mcp.json`), the logo, this README, a testing guide, a changelog and the licence.

- Privacy policy: [adplug.app/privacy](https://adplug.app/privacy)
- Terms: [adplug.app/terms](https://adplug.app/terms)
- Data processing agreement: [adplug.app/dpa](https://adplug.app/dpa)

## Support and links

- Email [support@adplug.app](mailto:support@adplug.app) and Daniel Popa, AdPlug's founder, will reply, usually the same business day.
- Website: [adplug.app/integrations/google-search-console](https://adplug.app/integrations/google-search-console)
- Setup guide: [adplug.app/guides/google-search-console](https://adplug.app/guides/google-search-console)
- Plans: [adplug.app/pricing](https://adplug.app/pricing)
- AdPlug's ad platforms (Google Ads, Meta Ads, LinkedIn Ads and Microsoft Ads) have their own plugin: [adplug-app/adplug-cursor-plugin](https://github.com/adplug-app/adplug-cursor-plugin)

## Licence

MIT, see [LICENSE](LICENSE). Published by AdPlug, the trading name of MEANDATA IT SRL.
