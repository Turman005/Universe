# Universo Observável · Atlas 3D (v3)

Atlas 3D interativo, da Terra (com todos os satélites rastreados publicamente) até o Universo observável.
Site estático: funciona em qualquer hospedagem estática (GitHub Pages, Netlify…) e também aberto direto do disco.

## Publicar no GitHub Pages
1. Crie um repositório (ex.: `universo`) e envie **o conteúdo desta pasta** (`index.html`, `app.js`, `app.css`, `data/`, `offline/`, ícones, `.nojekyll`).
2. Em *Settings → Pages*, escolha *Deploy from a branch*, branch `main`, pasta `/ (root)`.
3. O endereço fica `https://SEU-USUARIO.github.io/universo/`.
4. (Opcional) Para a prévia de link (WhatsApp, X, etc.) usar endereço absoluto, gere de novo com `BASE_URL=https://SEU-USUARIO.github.io/universo/ node build.mjs`.

## Arquivos
- `index.html`, `app.js`, `app.css`: interface e motor 3D (three.js, satellite.js — MIT).
- `data/*.js`: dados carregados sob demanda — `sats` (CelesTrak), `hz` (JPL Horizons), `tex`/`tex-lo` (texturas NASA; `tex-lo` no modo leve), `clouds` (só quando ativadas), `thumbs` (miniaturas com créditos).
- `data/m-*.js`: modelos 3D dos satélites (GLB comprimido), carregados só quando você se aproxima do objeto.
- `offline/universo-v2.html`: versão em arquivo único (tudo embutido), para baixar e abrir sem internet.

Parâmetros de URL: `?perf=1` / `?perf=0` força o modo leve ligado/desligado; `?offline` não tenta atualizar os satélites online.
As fontes, datas de obtenção e licenças de cada conjunto de dados estão no painel **Fontes de dados** do próprio site.

## Satélites em 3D (v3)
- De longe: pontos na GPU. De perto: modelos 3D (até 120 por vez; 26 no modo leve). Chip **“Tamanho exagerado à média distância”** liga/desliga o aumento de tamanho; desligado, tudo fica em escala real.
- **🎥 Visão da câmera**: no cartão de um satélite com modelo, segue a nave em tamanho real (arraste para girar, role para aproximar, Esc ou “Sair ✕” para voltar).
- Cada cartão diz se o modelo é **“Modelo real (NASA)”** ou **“Representação da família …”**. Um modelo de família nunca é apresentado como a nave exata.

### Créditos dos modelos
- **Modelos reais**: [NASA 3D Resources](https://science.nasa.gov/3d-resources/) ([GitHub](https://github.com/nasa/NASA-3D-Resources)). ISS, Hubble, James Webb, Chandra, TESS, Fermi, Swift, Terra, Aqua, Aura, Landsat 8 (usado também para o Landsat 9), Suomi NPP, GPM, ICESat-2, Sentinel-6. Sem copyright (domínio público), sujeitos às [diretrizes de mídia da NASA](https://www.nasa.gov/nasa-brand-center/images-and-media/); a NASA não endossa este site. Os arquivos foram simplificados, comprimidos (meshopt) e tiveram as texturas reduzidas.
- **Modelos procedurais** (gerados no navegador): Starlink v1.5 e V2 Mini (dimensões do registro na FCC), OneWeb, GPS, Galileo (ESA), GLONASS, BeiDou, satélite GEO de comunicações, meteorologia e observação da Terra, CubeSats 1U/3U/6U, estágios de foguete (diâmetro e comprimento por lançador), detritos, Tiangong (CAST/CMSA), NuSTAR (JPL) e Euclid (ESA). Formas aproximadas.
- **Atitude**: ilustrativa. Satélites de observação e estações apontam para a Terra e se alinham à velocidade, com painéis girando para o Sol (na ISS, pelas juntas alfa). Telescópios ficam voltados para o Sol. Detritos e estágios giram.
