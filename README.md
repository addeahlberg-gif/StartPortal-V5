# Startportal V5 med Cloudflare D1

V5 lagrar kategorier, länkar, RSS-flöden och väderort centralt i D1. Din befintliga `startportal-backup.json` importeras från portalens gränssnitt efter första publiceringen.

## Publicering

1. Skapa en D1-databas i Cloudflare med namnet `startportal-v5`.
2. Kopiera databasens ID till `wrangler.jsonc` och ersätt `REPLACE_WITH_YOUR_D1_DATABASE_ID`.
3. Installera beroenden med `npm install`.
4. Logga in med `npx wrangler login`.
5. Kör migreringen: `npm run db:remote`.
6. Skapa en administratörsnyckel: `npx wrangler secret put ADMIN_TOKEN`.
7. Publicera: `npm run deploy`.
8. Öppna portalen, välj **Lås upp**, ange administratörsnyckeln och importera din befintliga JSON-backup.

## GitHub

Ladda upp hela projektets innehåll till repots rot. För automatisk deploy behöver Cloudflare-projektet använda Workers Builds, eller så kan du först publicera med Wrangler enligt stegen ovan.

## Säkerhet

Läsning av portalens data är publik på Worker-adressen. Skrivning kräver `ADMIN_TOKEN`. För privata arbetslänkar rekommenderas Cloudflare Access framför hela Worker-adressen.
