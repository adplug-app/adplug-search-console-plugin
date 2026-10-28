# Testing AdPlug: Google Search Console in Grok, Grok Bot and Cursor

For marketplace reviewers. The login's password is in AdPlug's submission form (or ask support@adplug.app).

These steps take about 10 minutes. The Search Console property on this login is our own, with view-only access. Please preview changes but don't apply any.

1. Install it.
   - In Grok Bot: open Connect apps in the sidebar (on the phone: tap your avatar, then Connect apps), find AdPlug: Google Search Console, click Add, then Authenticate.
   - In Cursor: run /add-plugin adplug-search-console in a chat, or install it from the Marketplace.
   - In Grok (grok.com): open Plugins in the sidebar, click New Connector, choose Custom, enter the name AdPlug Search Console and the server URL https://api.adplug.app/mcp/google-search-console , then Add Connector.
   - If it isn't listed yet: in Grok Bot, send your Bot this message: Add a custom MCP server called AdPlug Search Console at https://api.adplug.app/mcp/google-search-console , then click Authorize on the card it posts and Continue. In Cursor, add https://api.adplug.app/mcp/google-search-console as a server in Cursor's MCP settings.

2. A browser tab opens on AdPlug's sign-in page. Sign in with email and password (not "Continue with Google"):
   - Email: mcp-review-grok@adplug.app
   - Password: the one given in AdPlug's marketplace submission

3. Next is AdPlug's "Authorize access" screen. From Grok Bot and Cursor it reads "Cursor wants to access your AdPlug account". That's expected, because Grok Bot connects apps through Cursor. Click Approve.

4. Check the connection. Ask:
   - Which Search Console properties can you see, and how did each one do over the last 28 days?

5. Try a few analyses, one at a time:
   - Compare the last 28 days with the 28 before on adplug.app: which pages and queries gained or lost the most clicks, and why?
   - Find queries on adplug.app ranking between positions 5 and 20 with real impressions, and tell me which page should win each one.
   - Inspect https://adplug.app/pricing. Is it indexed? Compare what Google saw with the live page.
   - Check the sitemaps for adplug.app and audit the URLs inside.

6. Preview one change without applying it. Send:
   - Preview submitting https://adplug.app/sitemap.xml as a sitemap for adplug.app. Don't apply it.
   - You should get a preview of the exact change, and nothing changes. AdPlug only applies a Search Console change when the execute tool is called with that preview's ID, and this login's Google access is view-only, so Google would refuse it anyway.

7. Optional, removing it: in Grok Bot, open Connect apps, select it and click Disconnect. In Cursor, uninstall the plugin or remove the server.

8. Questions or problems: support@adplug.app. Daniel Popa, AdPlug's founder, will reply, usually the same business day.
