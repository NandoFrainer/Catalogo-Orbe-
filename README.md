# Orbe — Lista de Preços (HTML estático com login)

Este pacote contém um **index.html** responsivo com:
- Login por senha (cliente-side) — simples para GitHub Pages
- Filtro por **Categoria**
- Busca por texto
- Ordenação por coluna
- Botão **Baixar em PDF** (Print → Salvar como PDF)

## Publicar no GitHub Pages
1. Crie um repositório no GitHub (ex.: `lista-precos-orbe`).
2. Envie **todos os arquivos** desta pasta para a raiz do repositório.
3. Em **Settings → Pages**, configure:
   - **Source**: Deploy from a branch
   - **Branch**: `main` (ou `master`) e pasta `/ (root)`
4. Abra a URL gerada: `https://SEU_USUARIO.github.io/NOME_DO_REPO/`

## Trocar a senha de acesso
- A senha padrão atual é **orbe2025**.
- Para mudar:
  1. Abra `password_hash_helper.html` localmente.
  2. Digite a nova senha; copie o **SHA-256 (hex)** exibido.
  3. No arquivo `index.html`, procure por `const ACCESS_HASH = "..."` e substitua pelo novo hash (entre aspas).
  4. Faça commit/push no GitHub.
- Observação: este login é básico (lado do cliente). Para proteção forte, use um host com autenticação (ex.: Cloudflare Access, Basic Auth no servidor, etc.).

## Dica
- No celular, você pode "Compartilhar → Adicionar à Tela de Início" para um atalho.
