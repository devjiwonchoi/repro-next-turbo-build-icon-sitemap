> [!NOTE]
> This issue occurs at next build turbopack

## Issue 1

### Summary

The `runtime` set on the layout is not passed correctly to the Metadata File `icon.tsx`.

### Steps to Reproduce

1. Install the dependencies.
2. Run `pnpm build`.
3. Open `.next/server/middleware-manifest.json`.
4. `functions['/icon/route'].files` exists.
5. Run `pnpm build-turbo`.
6. Open `.next/server/middleware-manifest.json`.
7. `functions['/icon/route'].files` DOES NOT exist.

## Issue 2

### Summary

Setting `sitemap.ts` tries to read the path as: `.next/server/app/sitemap/route/app-paths-manifest.json`, but is `.next/`server/app/sitemap.xml/route/app-paths-manifest.json`

### Steps to Reproduce

1. Install the dependencies.
2. Add `sitemap.ts` anywhere inside the app dir.

```ts
import type { MetadataRoute } from 'next';

export default function sitemap(): MetadataRoute.Sitemap {
  return [
    {
      url: 'https://acme.com',
      lastModified: new Date(),
      changeFrequency: 'yearly',
      priority: 1,
    },
    {
      url: 'https://acme.com/about',
      lastModified: new Date(),
      changeFrequency: 'monthly',
      priority: 0.8,
    },
    {
      url: 'https://acme.com/blog',
      lastModified: new Date(),
      changeFrequency: 'weekly',
      priority: 0.5,
    },
  ];
}
```

3. Run `pnpm build-turbo`.
4. See the error log.
