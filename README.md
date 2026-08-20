# iModel History Browser

**Live app:** https://umarinam.github.io/iModelHistoryBrowser/

A single self-contained `index.html` file — no build step, no server, no dependencies — for browsing the history of a Bentley iTwin/iModel directly from the browser using your own access token.

Paste a bearer token and an iTwin (Project) ID, pick an iModel, and browse its changesets, changeset groups, and briefcases in independent, sortable/filterable tables. Selecting a changeset lets you compare it against another to see exactly which elements changed, down to insert/update/delete and which properties changed.

## Features

- **iModels**: list every iModel in an iTwin.
- **Changesets**: index, state, decoded change-type bitmask, creator (resolved from user id to name/email), push date. Live total count via a single cheap request, plus a full sortable/filterable table.
- **Changeset Groups**: state, description, creator, created date, with a "Count all" action for an exact total.
- **Briefcases**: owner (resolved to name/email), device, acquisition date.
- **Compare Changesets**: pick a start/end changeset and run an element-level diff via the Changed Elements API — element ids, opcode (inserted/modified/deleted), decoded type-of-change bitmask, and which properties changed.
- Collapsible sections, per-section search/sort, and an optional (clearly-labeled-as-risky) local-storage "remember me" for your token and iTwin ID, plus an iTwin ID autocomplete history.

Nothing is sent anywhere except directly from your browser to `api.bentley.com` — there's no backend.

## APIs used

- [iTwin Platform iModels API v2](https://developer.bentley.com/apis/imodels-v2/overview/) — iModels, changesets, changeset groups, briefcases, and iModel users.
- [iTwin Platform Changed Elements API v2](https://developer.bentley.com/apis/changed-elements-v2/overview/) — job-based element-level comparison between two changesets.

You'll need a bearer access token with the `itwin-platform` OAuth scope. The [Changed Elements "Create Comparison Job" operation page](https://developer.bentley.com/apis/changed-elements-v2/operations/create-comparison-job/) has a "Try it" panel that can generate one for testing.

## Running locally

Just open `index.html` in a browser — it's fully static.

## Publishing

This repo is published via GitHub Pages, serving `index.html` straight from the root of the `main` branch. Any push to `main` is picked up and republished automatically by GitHub Pages — no separate build/deploy step required.
