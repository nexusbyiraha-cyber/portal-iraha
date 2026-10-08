# Portal Iraha

Portal interno da Iraha Contabilidade: avisos, sistemas, calendário fiscal, ferramentas e documentos.
O site é publicado pelo GitHub Pages a partir deste repositório.

## Como editar

Todo o conteúdo editável fica em **`dados.json`**. Para mudar:

1. Abra `dados.json` no GitHub e clique no lápis (**Edit this file**).
2. Faça a alteração seguindo os exemplos abaixo.
3. Clique em **Commit changes**. O site atualiza em 1 a 2 minutos.

Atualize também o campo `"atualizado"` com a data do dia (formato `AAAA-MM-DD`).

### Novo aviso
```json
{"id": "reuniao-sexta", "titulo": "Reunião geral na sexta", "texto": "Às 9h, na sala 2.", "prioridade": "normal", "ate": "2026-10-16", "criadoEm": "2026-10-08"}
```
- `prioridade`: `"normal"` ou `"importante"` (importantes aparecem primeiro, destacados).
- `ate`: data em que o aviso some do mural. Use `null` para não expirar.

### Novo sistema (link)
```json
{"id": "webmail", "nome": "Webmail", "descricao": "E-mail do escritório", "categoria": "Geral", "url": "https://..."}
```

### Novo sistema ou documento (arquivo para baixar)
1. Envie o arquivo para a pasta `arquivos/` (**Add file → Upload files**).
2. Cadastre usando `"arquivo"` no lugar de `"url"`:
```json
{"id": "mapear-rede", "nome": "Mapear rede", "descricao": "Script de acesso à rede", "categoria": "Geral", "arquivo": "arquivos/mapear-rede.bat"}
```
PDFs e imagens abrem no navegador; os demais formatos são baixados.

### Cuidados com o JSON
- Separe os itens de uma lista com vírgula, mas **não** coloque vírgula depois do último.
- Use aspas duplas `"` em todos os textos.
- Cada `id` deve ser único, sem espaços (ex.: `nfse-nacional`).

## Calendário fiscal
As regras de vencimento ficam no próprio `index.html` (listas `FED` e `UFS`). Elas são revisadas todo dia 1º por uma tarefa agendada no Claude, que corrige as regras quando a legislação muda e publica avisos de prorrogação em `dados.json`.

> Atenção: no plano gratuito do GitHub, o site do GitHub Pages é público para quem tiver o endereço.
