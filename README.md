# Cake pre-order site (Munich, Pasing)

A single-page, phone-first site: product cards, a product sheet with size choice, and an order basket that sends the whole order via WhatsApp or copies it for WeChat. No build step.

Files: `index.html` (the site), `impressum.html` (Impressum + Datenschutzerklärung), `images/`, `fonts/` (self-hosted, SIL Open Font License; no Google Fonts connection). The Chinese headings use LXGW WenKai, subset to only the characters currently on the site (`lxgw-wenkai-subset.woff2`). Chinese characters added later are shown in the phone's system font until the subset is regenerated. The shop name 妍手作 is set in Long Cang (`long-cang-yan.woff2`, only those three characters); if the Chinese shop name changes, that file must be regenerated too.

## Before going live

1. `impressum.html`: replace every `[...]` placeholder (name, address, e-mail, VAT note, hosting provider, date). Have it checked if unsure.
2. `index.html`: the shop name (`shopNameEn`, `shopNameZh`) and the WhatsApp number are already set. Optionally fill `wechat` and `instagram` in the `CONFIG` block.

## Publish: private GitHub repo + Cloudflare Pages

1. On GitHub, create a new repository and choose **Private**. Upload all files so that `index.html` sits at the top level (with the `images` and `fonts` folders next to it).
2. In Cloudflare (dash.cloudflare.com): **Workers & Pages › Create application › Pages › Connect to Git**. Authorize GitHub and pick the repository. Choose **Connect to Git** from the start: a project created by direct upload cannot be switched to Git later.
3. Build settings: Framework preset **None**, Build command empty, Build output directory `/`. Deploy.
4. The site is live at `https://<project>.pages.dev` (a custom domain can be added in the project settings).

To update later: upload the changed files to the GitHub repository (Add file › Upload files, same file names). Cloudflare redeploys automatically within about a minute.

## Note on GitHub Pages

GitHub's rules say GitHub Pages is not meant to host an online business or a site mainly for taking orders, so this site is served by Cloudflare instead. The repository stays private.

## Editing content

All products, prices and photos are in the `CONFIG`, `PRICES`, `BASQUE`, `CHIFFON`, `ROLLS`, `PIECES` and `OTHERS` lists near the bottom of `index.html`. A price of `null` shows as 待定. For photos use `photos: [{ src: "images/a.jpg", pos: "center 60%" }]`; the first one shows on the card.
