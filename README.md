# Orbe — Lista de Preços (GitHub Pages + Sync)

Este pacote publica uma lista de preços estática no **GitHub Pages**, com:
- **Dois perfis** de acesso: **Master** (edita) e **Representante** (leitura).
- **Imagens** por produto e **atualização de preços** via CSV.
- **Sincronização** opcional via GitHub: o Master publica um `overrides.json` no repositório; todos os dispositivos baixam automaticamente ao abrir.
- **Logo** e **plano de fundo** personalizáveis (Master → botão *Personalizar*).

## Publicar no GitHub Pages
1. Crie um repositório (ex.: `orbe-lista-precos`).
2. Faça upload de **todos** os arquivos deste pacote na raiz do repo.
3. Em **Settings → Pages**:
   - **Source**: *Deploy from a branch*
   - **Branch**: `main` e pasta `/ (root)`
4. Acesse a URL do Pages (ex.: `https://SEU_USUARIO.github.io/orbe-lista-precos/`).

## Senhas (padrão)
- **Master**: `orbe-master`
- **Representante**: `orbe-rep`

### Trocar as senhas
1. Abra `password_hash_helper.html` localmente.
2. Gere o **SHA-256 (hex)** das novas senhas.
3. Edite `index.html` e substitua os valores em:
   ```js
   const ACCESS_HASH_MASTER = "…";
   const ACCESS_HASH_REP = "…";
   ```
4. Faça commit/push.

> Observação: autenticação é **básica** (client-side). Para reforçar, use restrições adicionais no host (ex.: Cloudflare Access) se necessário.

## Sincronização (Master)
1. Crie (ou use) um repositório **público ou privado** onde o arquivo `data/overrides.json` ficará.
2. Gere um **Fine-grained Personal Access Token** no GitHub com permissão **Contents: Read and Write** **apenas** neste repositório.
3. No app (logado como Master), preencha **owner, repo, branch, path e token** e clique **Salvar conexão**.
4. Ao **ajustar imagens** ou **importar CSV de preços**, clique **Publicar alterações (subir)** se não publicar automaticamente. 
   - Por padrão, após importar preços e salvar imagem o app já tenta publicar se a conexão estiver salva.
5. Representantes e demais usuários carregam automaticamente as alterações ao abrir (ou via **Sincronizar agora (baixar)**).

### Estrutura do `overrides.json`
```json
{{
  "updatedAt": "2025-08-13T00:00:00.000Z",
  "images": {{}},              // mapa: codigo -> dataURL ou URL
  "prices": {{}}
}}
```

## Atualizar preços (CSV)
- Clique **“Atualizar preços (CSV)”** e selecione um arquivo `.csv` com delimitador `;` ou `,`:
```
codigo;valor_lista_1;valor_lista_2
0521.1000;156.90;167.00
0433.1000;2231.58;2375.05
```
- Cabeçalhos aceitos (variações): `codigo`/`código`/`cod`, `valor_lista_1` (ou `preco1`, `preço1`, `valor1`), `valor_lista_2` (ou `preco2`, `preço2`, `valor2`).

## Logo e plano de fundo
- (Master) Clique **Personalizar** → informe **URL** ou envie **arquivo**. Salvo no *localStorage* do dispositivo.
- Se quiser sincronizar logo/fundo via GitHub, peça para estendermos o `overrides.json`.

## Observações
- **Imagens**, **preços**, **logo** e **fundo** são guardados localmente e (se configurado) sincronizados via GitHub.
- Este projeto é 100% **estático** e funciona bem em dispositivos móveis.
