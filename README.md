# social-stack

The plugin bundle behind [protoAgent](https://github.com/protoLabsAI/protoAgent)'s
**Social Marketing archetype** — pick "Social Marketing" in the setup wizard or the
new-agent picker and this is what gets installed.

An agent that owns organic social: it holds the brand's voice, plans a balanced
calendar, drafts native to each platform, catches its own mistakes, and hands you a
pack you publish in ten minutes.

## Composition

| Member | Ships | Why it's here |
|---|---|---|
| `social` | [social-plugin](https://github.com/protoLabsAI/social-plugin) | The brand kit, the platform specs, the content queue, the linter, the export pack, a writer + editor + researcher crew, and five skills |
| `artifact` | builtin | Quote cards, previews, and the visual assets a post needs |
| `notes` | builtin | Idea capture between planning sessions |

## It does not post

No platform credentials, no API keys, no outbound calls. The agent produces the
content; a person publishes it.

That's a decision, not an omission. Platform APIs are the expensive, brittle half —
each its own OAuth app, review process, and monthly bill — and the failure mode of an
autonomous poster isn't a typo, it's a confident wrong post that's permanent and
screenshot-able. Everything the stack builds (brand kit, linter, queue, export) is
identical whether a person or an API sends the post, so nothing is wasted if that
changes. Until then: export CSV into whatever scheduler you already pay for.

## Install

Pick **Social Marketing** in the protoAgent setup wizard / new-agent picker, or:

```
python -m server plugin install https://github.com/protoLabsAI/social-stack
```

After install, enable the suggested list and say **"set up our brand kit"** — the
`brand-kit-setup` interview is what everything else is downstream of. Then
"plan two weeks of content".

## Pairs well with

- **[cowork-stack](https://github.com/protoLabsAI/cowork-stack)** — add it if you want
  LinkedIn PDF carousels, decks, and spreadsheet exports. It's kept out of this bundle
  because it pulls in a Python runtime an organic-social agent shouldn't need by default.
- **A Google connector** for reading the source material you repurpose from.

## Pin lifecycle (ADR 0049)

Member refs are release tags; `plugins.lock` records resolved SHAs;
`verified_against` is the core version this pin set was last verified on.
`scripts/check_bundle_updates.py` + the verify workflow keep pins moving only through
passing verification.
