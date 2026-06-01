# bob-obsidian-redirect

Tiny static page that bridges `https://` to `obsidian://` so Obsidian deep
links become clickable in messengers that only auto-link http(s)://.

Used by **Bob** (Brinkor's internal agent) to post note links into
Nextcloud Talk. Bob himself lives in a private repo and is not exposed
to the public net — this redirect is the one piece that has to be
publicly reachable, so it lives here on GitHub Pages.

## How it works

A link like

```
https://peterfrombitworkers.github.io/bob-obsidian-redirect/?vault=Avisum&file=Operation/Bob/Runbook.md
```

opens [`index.html`](./index.html), which reads `vault` and `file` from
the query string and does

```js
window.location.href = "obsidian://open?vault=" + ... + "&file=" + ...
```

The browser hands the custom-scheme URL to the OS, which opens Obsidian
on the requested note. Fallback button is shown if the auto-redirect
doesn't fire (mobile in-app browsers).

## Updating

The canonical source of `index.html` lives in the private Bob repo under
`deploy/obsidian-redirect/index.html`. Changes are committed there first
and then mirrored here.
