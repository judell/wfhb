# WFHB Event Moderator

A tool for curating which Bloomington community calendar events appear on the WFHB website.

## How it works

The [Bloomington community calendar](https://judell.github.io/community-calendar/xmlui/index.html?city=bloomington) aggregates events from ~75 local sources. This moderator app lets you choose which of those sources and events to show on your site.

**Your embedded viewer URL:**

```
https://judell.github.io/community-calendar/xmlui/index.html?city=bloomington&embed=true&exclude=https://raw.githubusercontent.com/judell/wfhb/main/excluded.json
```

That URL displays the community calendar filtered by your choices. Embed it on your site with an iframe.

## Setup (one time)

1. Go to https://judell.github.io/wfhb/
2. Click **Settings**
3. Paste a GitHub personal access token with `repo` scope ([create one here](https://github.com/settings/tokens/new?scopes=repo&description=WFHB%20moderator))
4. Click **Save**

The token is stored in your browser's localStorage. You only need to do this once per browser.

## Daily workflow

1. Open https://judell.github.io/wfhb/
2. The app loads all current Bloomington events from the database. New events from the nightly build appear automatically.
3. Review the three tabs:

   - **Sources** — All sources are included by default. Uncheck any source to exclude all its events from your viewer. Excluded sources appear dimmed at the bottom of the list.

   - **Visible** — Events that will appear on your site. Scroll through and click **Reject** on any individual event you don't want to show.

   - **Rejected** — Events you've rejected. Click **Restore** to bring one back.

4. Click **Publish** to push your choices to GitHub. Changes go live in about a minute.

## Tips

- **You don't need to review every event.** Everything from included sources shows up by default. Only reject the ones you don't want.
- **Source exclusions are the big lever.** If an entire source isn't relevant to WFHB, just uncheck it. You'll never see its events in the queue.
- **Your choices persist in the browser.** If you close the tab and come back, your selections are still there. But they only become public when you click Publish.
- **Multiple people can moderate.** Each person's browser has its own localStorage, but only the last Publish wins. Coordinate if you have multiple moderators.
- **Click the info icon** (circled i) on any event to see its full description before deciding.
