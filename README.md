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
4. Optionally enable **Require approval for new events** if you want new events hidden from the viewer until you review them
5. Click **Save**

The token is stored in your browser's localStorage. You only need to do this once per browser.

## Daily workflow

1. Open https://judell.github.io/wfhb/
2. The app loads current state from `excluded.json` in this repo, and events from the database.
3. Review the four tabs:

   - **Sources** — All sources are included by default. Uncheck any source to exclude all its events from your viewer. Excluded sources appear dimmed at the bottom of the list.

   - **New** — Events added since your last review. If **Require approval** is on, these are hidden from the viewer until you click **Mark all reviewed**. If off, they show in the viewer immediately and this tab is just informational.

   - **Visible** — All events that will appear on your site. Scroll through and click **Reject** on any individual event you don't want to show.

   - **Rejected** — Events you've rejected. Click **Restore** to bring one back.

4. Click **Save choices** to push your choices to GitHub. Changes go live in about a minute.

## Approval modes

- **Require approval OFF** (default): New events from the nightly build appear in the viewer immediately. Use the New tab to scan for anything to reject.

- **Require approval ON**: New events are hidden from the viewer until you review them. Open the moderator, check the New tab, reject any you don't want, then click **Mark all reviewed** and **Save choices**. Events become visible in the viewer.

## Tips

- **You don't need to review every event.** Everything from included sources shows up by default. Only reject the ones you don't want.
- **Source exclusions are the big lever.** If an entire source isn't relevant to WFHB, just uncheck it.
- **Your choices are shared.** State lives in `excluded.json` in this repo, not in your browser. Any collaborator on this repo can moderate from any machine.
- **Multiple moderators**: anyone with a GitHub token that has write access to this repo can save choices. The last save wins — coordinate if multiple people moderate.
- **Click the info icon** (circled i) on any event to see its full description before deciding.
- **Rejected events age out.** Once a rejected event's date passes, it drops out of the results automatically.
