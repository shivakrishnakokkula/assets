# assets

Images for listings and READMEs that live in private repositories.

The extensions published under this account are developed in private repos.
That is a deliberate choice and not one this repository is trying to work
around — it exists because of a narrower problem it creates.

A marketplace listing is rendered from a README, and an image in that README
has to be fetched by whoever is reading the listing. `vsce` rewrites a
relative image path to `raw.githubusercontent.com` against the extension's own
`repository` field at package time, so a private repository publishes a
listing whose every screenshot is a 404 for every reader. A published listing
cannot be edited after the fact; the only repair is republishing.

So the images live here, in the open, and nothing else does. Each listing
references them by absolute HTTPS URL.

## The rules, and why each one is a rule

**Images only.** No source, no configuration, no notes. This repository is
public and the entire reason it exists is so that nothing else has to be. A
file that is not an image does not belong here even once.

**Absolute HTTPS URLs, pinned to a commit.** Reference a file by the full
40-character SHA of the commit that added it, never by `main`:

    https://raw.githubusercontent.com/shivakrishnakokkula/assets/<sha>/claude-action-timeline/<file>.png

A published listing is immutable but the branch behind it is not. Pointing at
`main` means replacing a screenshot silently rewrites every listing already
published, including versions whose users are looking at software that no
longer matches the picture. Pinning to a SHA means each release keeps the
image that shipped with it, and a new screenshot is a new URL in a new
release — which is the honest shape, because that is exactly what happened.

**PNG, not SVG.** `vsce` rejects SVG images in a README unless they come from
a host on its trust list, rejects SVG data URLs outright, and rejects inline
`<svg>`. Non-SVG images have no host restriction, which is what makes this
repository workable at all.

**Nothing is deleted, only added.** A file removed here breaks every already-
published listing that pinned it, and those cannot be edited. Superseding a
screenshot means adding the new one alongside.

## Layout

One directory per application, named exactly as its extension is:

    claude-action-timeline/
    claude-usage-meter/

## Rights

These are screenshots and artwork of the author's own applications, published
here so that their listings can render. No licence is granted for reuse; all
rights reserved.
