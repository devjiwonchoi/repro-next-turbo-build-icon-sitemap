### Steps to Reproduce

1. Install the dependencies.
2. Run `pnpm build`.
3. Open `.next/server/middleware-manifest.json`.
4. `functions['/dynamic/[id]/icon/route'].files` exists.
5. Run `pnpm build-turbo`.
6. Open `.next/server/middleware-manifest.json`.
7. `functions['/dynamic/[id]/icon/route'].files` DOES NOT exist.