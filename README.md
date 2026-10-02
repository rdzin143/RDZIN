# Página de vendas — Acervo Pedagógico

Página única (`public/index.html`), sem dependências externas: CSS e JS inline, ilustrações em SVG, fontes do sistema.

## Antes de publicar
Tudo o que precisa ser editado fica no bloco `PAGE_CFG`, no `<head>` do `public/index.html`:
- `PIXEL_ID` — ID do Pixel da Meta (vazio = Pixel desligado).
- `CHECKOUT_BASICO` / `CHECKOUT_PREMIUM` — links de checkout.
  Os parâmetros da URL (`sck`, `utm_*`, `fbclid`…) são repassados automaticamente ao checkout.
- `PRECO_BASICO` / `PRECO_PREMIUM` — valores enviados nos eventos do Pixel.

Confira também preços, bônus e garantia na seção `#planos` e troque os depoimentos de exemplo por depoimentos reais (com autorização).

## Eventos enviados ao Pixel
| Evento | Quando |
|---|---|
| `PageView` | ao carregar |
| `ViewContent` | quando a seção de planos aparece na tela |
| `InitiateCheckout` | clique em um botão de checkout (com plano e valor) |
| `Scroll50`, `Scroll75`, `Engaged30s` (custom) | rolagem de 50%/75% e 30s na página |

Para a otimização de campanha, use **Compra** (disparada pela plataforma de checkout, via integração/CAPI).
Se ainda houver poucas compras, `InitiateCheckout` serve como evento intermediário.

## Publicar na Netlify
**Opção rápida (arrastar e soltar):** acesse app.netlify.com/drop e arraste a pasta `public/` (ou o `pagina-netlify.zip`).

**Opção conectada ao GitHub (republica a cada push):**
1. Em app.netlify.com → **Add new site → Import an existing project → GitHub** e escolha este repositório.
2. Deixe o build command vazio; o `netlify.toml` já define a pasta `public/`.
3. **Deploy**. Em **Domain management** você conecta seu domínio.

## Publicar na Vercel
1. Em vercel.com → **Add New… → Project**, importe este repositório do GitHub.
2. Framework Preset: **Other**. Não precisa de build: o `vercel.json` já aponta para a pasta `public/`.
3. Clique em **Deploy**. Cada push na branch escolhida republica a página automaticamente.
4. (Opcional) Em **Settings → Domains**, conecte seu domínio.

Imagens próprias vão em `public/img/` e são referenciadas como `/img/nome.webp` (prefira WebP, até ~150 KB cada).
O cache de longa duração já está configurado para essa pasta.
