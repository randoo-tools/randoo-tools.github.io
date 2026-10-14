# randoo-privacy

Public legal pages for the [randoo](../randoo-tools) family of Android apps.
Nothing here is code.

| File | Why it exists |
| --- | --- |
| `index.html` | The privacy policy. Google Play and AdMob both need a publicly reachable URL for it. |
| `ads.txt` | AdMob's Authorised Digital Sellers declaration. Required for ads to fill at all. |

## Publishing

GitHub Pages, from this repository's **Settings → Pages**, source **Deploy from a
branch**, `/ (root)`, branch `main`. Once live:

- policy: `https://randoo-tools.github.io/randoo-privacy/`
- ads.txt: `https://randoo-tools.github.io/ads.txt`

Note the second one. `ads.txt` has to be at the **root** of the domain, not in
this repository's subpath. A GitHub Pages *user* site is published from a
`github.io` repository named after the account, and a *project* site lives under
`/<repo>/`. Only the root path counts, so if the project URL is the one that works
for you, this needs to move to a user site or a custom domain instead. Check
where it actually resolves before shipping.

## Before publishing

1. Replace `pub-0000000000000000` in `ads.txt` with the real seller id from the
   AdMob console (Settings → Account information → Seller ID).
2. Replace `privacy@randoo.app` in `index.html` with an address you read.
3. Re-read the policy against the current app. It describes what the code
   actually does; if the dependencies change, the policy has to change with them.
4. Keep the Play Console data safety form consistent with it. A policy and a
   data safety declaration that disagree are the kind of thing that gets an
   app reviewed.