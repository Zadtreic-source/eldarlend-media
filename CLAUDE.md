# eldarlend-media: notes for Claude

Public picture host for the Eldarlend Marketing Manager chat. Websites' "upload" buttons open a file picker Claude can't drive, so pictures live here and Claude loads them into forms from their raw URL instead.

## Rules
- Public repo. Only marketing pictures: logos, banners, gameplay stills. Never anything private (no realm admin info, tokens, personal data, other players' faces or voices).
- File names: lowercase, hyphens, no spaces. `brand/` for logo and banners, `stills/` for gameplay screenshots.
- Keep each file under 5 MB (most listing sites' limit).
- Commit with a short message saying what was added and where it'll be used.

## Using a picture in a web form
Raw URL: `https://raw.githubusercontent.com/Zadtreic-source/eldarlend-media/main/<path>` (sends `Access-Control-Allow-Origin: *`).
In the browser pane, with the form open:
```js
const r = await fetch(RAW_URL); const b = await r.blob();
const f = new File([b], 'name.jpg', {type: b.type});
const dt = new DataTransfer(); dt.items.add(f);
input.files = dt.files; input.dispatchEvent(new Event('change', {bubbles: true}));
```
where `input` is the form's `<input type=file>`.

## Where the source footage is
Zadtreic's PC: `Videos\Eldarlend` (OBS recordings), `Videos\Eldarlend\Shorts` (finished Shorts), `Videos\Eldarlend\Stills` (copies of these stills).
