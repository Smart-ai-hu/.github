# .github

A Smart-AI org közös alapfájljai (default community health files):

- `profile/README.md` — az org főoldalán megjelenő bemutatkozás
- `ISSUE_TEMPLATE/` — alapértelmezett issue sablonok minden org-repóhoz, ahol nincs saját
- `PULL_REQUEST_TEMPLATE.md` — alapértelmezett PR sablon

Ezeket a fájlokat minden org-repo automatikusan örökli, amelyiknek nincs sajátja.

## Közös GitHub Actions folyamatok

### `n8n-deploy.yml` – n8n-telepítő (workflow_call)

Az n8n-automata repók (`template-n8n` és a belőle indított repók) **ezt hívják**, nem saját másolatot tartanak.
A hívó a saját `.github/workflows/deploy-n8n.yml`-je, ami a triggert, a futás nevét és a concurrency-t adja:

```yaml
jobs:
  deploy:
    uses: Smart-ai-hu/.github/.github/workflows/n8n-deploy.yml@main
    with:
      mod: ${{ inputs.mod || 'eles' }}          # eles | proba (a proba csak olvas)
      sha: ${{ github.event.workflow_run.head_sha || github.sha }}
      n8n-base-url: ${{ vars.N8N_BASE_URL }}
      workflow-ids: ${{ vars.N8N_WORKFLOW_IDS }}
      error-workflow-id: ${{ vars.N8N_ERROR_WORKFLOW_ID }}
    secrets:
      N8N_API_KEY: ${{ secrets.N8N_API_KEY }}
      N8N_HELYKITOLTOK: ${{ secrets.N8N_HELYKITOLTOK }}
```

- A lépések: a hívó repó checkoutja a megadott sha-ra (teljes történettel), Node 22, `node scripts/n8n/telepit.mjs`.
  A szkriptek a hívó repóban vannak (a `smart-ai-ops` template-sync tartja őket azonosan), itt csak a lépések élnek.
- Kimenet: a step summary táblázata és a `deploy-eredmeny` artifact (`deploy-eredmeny.json`, séma
  `smart-ai/n8n-deploy@1`, 90 napig megmarad). A WorkDash a hívó futásának nevéből (`Deploy n8n <sha> · wf=<ID-k>`)
  és ebből az artifactból rakja a telepítést az n8n-workflow mellé; a szerződés a `template-n8n` README-jében.
- Ez a repó **nyilvános**: ide titok, ügyfélnév, workflow-ID nem kerülhet – a hívó csak változó- és titokneveket ad át.
- Változtatás után **minden** n8n-repó következő telepítése az új változattal fut (`@main`). Rögzített változathoz
  a hívók `@n8n-deploy-v1` taggel hivatkozhatnak (a tagot kézzel kell létrehozni).
