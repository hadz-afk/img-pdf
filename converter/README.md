# Image to PDF Converter

A browser-only image-to-PDF workspace. Images stay on the device; there is no upload endpoint, database, authentication requirement in the application, or third-party PDF service.

## Run

Serve `dist` with any static HTTP server. No build or dependencies are required. Node.js can check the application with `node --check dist/app.js`. Deploy `dist` to a static host; the Sites manifest contains the registered deployment identity.

## Features

- JPG/JPEG, PNG, WEBP, multiple-file picker and drag-and-drop.
- Drag sorting, move buttons, duplicates, deletion, and clearing.
- Non-destructive crop, rotation, flips, brightness, contrast, saturation, grayscale, and sharpening.
- Standard and custom page sizes, selectable units, automatic orientation.
- Fit, fill, stretch, original-size (96 DPI), and custom sizing/position with aspect lock.
- Independent margins, grid layouts and spacing, alignment, colored or transparent backgrounds.
- Shared page renderer for preview and PDF export, downloadable PDF 1.4 with compressed raster images and optional alpha masks.
- Responsive layout, accessible control names, status announcements, export progress, and validation.

## Limits and behavior

100 input images; each under 30 MB and 60 megapixels. Export resolutions: 96, 150, or 300 DPI, capped at 5,000 pixels per page edge. Pages are rasterized, so PDFs have no editable image objects per input or searchable text. Crops use percentages of original image dimensions; image placement offsets and margins use mm. Images clip to their grid cells. Transparent backgrounds preserve image alpha in the PDF, though viewers commonly display white. Settings and images are session-local and are cleared on refresh. Fonts are optional external resources; system fonts remain usable without them.

## Verification

`check.cjs` uses the environment's bundled Playwright with installed Edge to exercise multiple-image upload, order controls, rotation, duplication, grid export, and mobile overflow. It writes local QA screenshots and a sample PDF. These files are not deployed. Generated PDFs were also independently parsed to confirm page count, A4 dimensions, and embedded image data.
