# Themis Kavour — Portfolio

Source for [kavourei.github.io](https://kavourei.github.io), a personal CV/portfolio site.

## Structure

- `index.html` — CV / landing page
- `projects.html` — projects showcase
- `support.js` — runtime that renders the `<x-dc>` page templates (loads React, ReactDOM, and Babel Standalone from unpkg at page load)
- `image-slot.js` — drag-and-drop `<image-slot>` custom element used for the profile photo
- `.nojekyll` — tells GitHub Pages to serve the files as-is, with no Jekyll build step

## Development

These are static files with no build step. Open `index.html` directly in a browser, or serve the directory locally:

```
python3 -m http.server
```

## License

See [LICENSE](LICENSE).

## Contact

[themis.kavour@icloud.com](mailto:themis.kavour@icloud.com)
