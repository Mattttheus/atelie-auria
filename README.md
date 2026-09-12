# Ateliê Auria — Alta Costura

Site institucional estático (HTML/CSS/JS puro) do Ateliê Auria.

## Estrutura

- `index.html` — marcação da página.
- `style.css` — estilos.
- `hero-mockup.webp` / `hero-mockup.jpg` — imagem principal, otimizada (WebP com fallback JPEG).
- `assets/originals/` — arquivo de imagem original em alta resolução, mantido como referência e **não** usado pela página em produção.

## Otimizações aplicadas

- Imagem principal convertida de PNG (~1,9 MB) para WebP/JPEG (~140 KB / ~225 KB), com `<picture>` + `image-set()` para servir o melhor formato suportado pelo navegador.
- `preload` com `fetchpriority="high"` da imagem do hero para melhorar o carregamento inicial (LCP).
- `loading="lazy"` e `decoding="async"` na imagem abaixo da dobra.
- `content-visibility: auto` nas seções abaixo da dobra para reduzir custo de layout/pintura inicial.
- Animações limitadas a `transform`/`opacity` (compositor), com `will-change`/`backface-visibility` nos elementos animados e `will-change` removido após a transição para não desperdiçar memória.
- Suporte a `prefers-reduced-motion` para desativar animações quando o usuário preferir.

## Publicar no GitHub Pages

Este repositório já inclui um workflow (`.github/workflows/deploy.yml`) que publica o site automaticamente a cada push na branch `main`.

1. Crie um repositório novo e vazio no GitHub (sem README/gitignore).
2. Conecte este projeto local a ele e envie o código (veja instruções passadas pelo assistente).
3. No GitHub, vá em **Settings → Pages** e em "Build and deployment" selecione **Source: GitHub Actions**.
4. Após o primeiro push, o workflow publica o site automaticamente. A URL final aparece em **Settings → Pages** e no resumo da Action, no formato `https://<usuario>.github.io/<repositorio>/`.
