# biostat-kb

Personal knowledge base of a biostatistician, published with [Quartz v4](https://quartz.jzhao.xyz/) at **https://pzhang724.github.io/biostat-kb/**.

## Layout

```
biostat-kb/
├── wiki/        # Knowledge base content (markdown with [[wiki-links]]) — this is what gets published
├── site/        # Quartz v4 static site generator (framework code, not content)
└── .github/     # Deploy workflow: push to main → build wiki/ → GitHub Pages
```

## Local preview

```bash
cd site
npm ci
npx quartz build --directory ../wiki --output public --serve
```
