# Página de vendas — Acervo Pedagógico

Página única (`index.html`), sem dependências externas: CSS e JS inline, ilustrações em SVG, fontes do sistema.

## Antes de publicar
Tudo o que precisa ser editado fica no bloco `PAGE_CFG`, no `<head>` do `index.html`:
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
