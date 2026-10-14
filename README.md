# randoo-privacy

Public legal pages for the [randoo](../randoo-tools) family of Android apps.
Nothing here is code.

| File | Why it exists |
| --- | --- |
| `index.html` | The privacy policy. Google Play and AdMob both need a publicly reachable URL for it. |
| `ads.txt` | AdMob's Authorised Digital Sellers declaration. Required for ads to fill at all. |

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

## Before publishing

1. Replace `pub-0000000000000000` in `ads.txt` with the real seller id from the
   AdMob console (Settings → Account information → Seller ID).
2. Replace `privacy@randoo.app` in `index.html` with an address you read.
3. Re-read the policy against the current app. It describes what the code
   actually does; if the dependencies change, the policy has to change with them.
4. Keep the Play Console data safety form consistent with it. A policy and a
   data safety declaration that disagree are the kind of thing that gets an
   app reviewed.