# randoo-privacy

Public legal pages for the [randoo](../randoo-tools) family of Android apps.
Nothing here is code.

| File | Why it exists |
| --- | --- |
| `index.html` | The landing page, and the table of policies. Not itself a policy. |
| `<app>.html` | One privacy policy per app. Play needs a URL per listing, and each app has its own data practices. |
| `ads.txt` | AdMob's Authorised Digital Sellers declaration. Required for ads to fill at all. Account level: one seller id covers every app, so this is the one file that is *not* per app. |

## One policy per app

They look almost identical, and that is deliberate: the apps share a toolkit, so their
behaviour is the same. What differs is whether that app shows ads, and that difference has to
be exact. A page describing ad tracking for an app that shows none is a wrong policy for that
app, and it is the kind of thing a Play reviewer checks against the listing.

So the rule is: copy the text, change only the advertising section, and keep everything else
byte-identical. If they ever describe different behaviour, something has gone wrong upstream.

Keep `index.html` as an index only. When Coin Flip had a policy here, it was easy to link the
wrong URL from a listing; there is now no page that could be mistaken for an app's policy.

## Publishing

Published through GitHub Pages, from **Settings → Pages**, source **Deploy from
a branch**, `/ (root)`, branch `main`.

The repository is named `randoo-tools.github.io` on purpose. `ads.txt` has to
live at the **root** of the domain, and a GitHub Pages site only does that when
the repository is named after the account it serves. As a project site under
`/randoo-privacy/` it would have been on the wrong path, which fails silently
and means no ad fill and no revenue.

So:

- policy: <https://randoo-tools.github.io/>
- ads.txt: <https://randoo-tools.github.io/ads.txt>

## `ads.txt`

One line, no comments:

```
google.com, pub-5108703063436913, DIRECT, f08c47fec0942fa0
```

Kept to the record alone on purpose. The IAB spec permits `#` comment lines
and the parser Google uses does ignore them, but the only consumer of this file
is a machine at an ad exchange, and a naive one need not strip comments before
validating. Nothing is gained by the prose here, so it lives in this file
instead.

Four fields, all required:

| Field | Value | What it means |
| --- | --- | --- |
| Domain | `google.com` | the ad exchange's domain, not yours |
| Seller ID | `pub-5108703063436913` | your publisher ID |
| Relationship | `DIRECT` | you own the inventory and are paid by Google |
| Certification | `f08c47fec0942fa0` | Google's own id, identical for every publisher |

One line for the whole family. Each app is its own AdMob app with its own ad unit, but the
*seller* id belongs to the AdMob account, not to an app, so a single record here covers every
randoo app.

The seller ID is the same number that sits inside each app's AdMob App ID, which
is why it can be read either way:

```
ca-app-pub-5108703063436913~3733568661
    └──────┬──────┘
     publisher / seller ID
```

It is public. Google lists every AdMob seller, including confidential ones, in
its published `sellers.json`. Nothing secret is in this file, which is why it can
live in a public repository and why the file has to be publicly readable at all.

## Before publishing

1. Replace `pub-0000000000000000` in `ads.txt` with the real seller id from the
   AdMob console (Settings → Account information → Seller ID).
2. The contact address is `randoo-privacy@merandoo.com`. It is deliberately
   separate from any other app family under `merandoo.com`: ads change what a
   privacy answer looks like, and a shared inbox would answer the wrong question.
3. Re-read the policy against the current app. It describes what the code
   actually does; if the dependencies change, the policy has to change with them.
4. Keep the Play Console data safety form consistent with it. A policy and a
   data safety declaration that disagree are the kind of thing that gets an
   app reviewed.