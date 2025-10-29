# Gerador de Base de Conhecimento (Gemini)

Descrição curta
Cria e expande automaticamente uma base de conhecimento em JSON adicionando, em cada execução, 25 novas entradas únicas sobre tecnologias (linguagens, frameworks, ferramentas, bancos de dados, metodologias). A lógica usa a API Gemini para gerar conteúdo estruturado e valida/mescla o resultado com o arquivo local `baseDeConhecimento.json`.

O que ele faz (resumido)
- Gera exatamente 25 novas entradas em formato JSON.
- Evita repetir nomes já presentes na base.
- Faz validação básica da resposta (garante que seja um ARRAY com 25 objetos).
- Realiza tentativas com backoff exponencial em caso de falhas.
- Atualiza (sobrescreve) o arquivo `baseDeConhecimento.json` com a base combinada.

Pré-requisitos
- Node.js instalado (v16+ recomendado).
- Chave da Gemini API.

Como executar (resumido)
1. Instale dependências:
   ```js
   npm install
   ```

3. Crie um arquivo `.env` na raiz com:
   GEMINI_API_KEY="SUA_CHAVE_AQUI"

4. Execute:
   ```js
   npm start
   ```

O que esperar
- Ao finalizar, o arquivo `baseDeConhecimento.json` será atualizado com as entradas antigas + 25 novas geradas.
- Logs no console informam sucesso, número de itens e possíveis erros.

Onde ajustar comportamento
- Para alterar a quantidade gerada, edite a constante `TOTAL_ITEMS` em [gerador.js](gerador.js) (`TOTAL_ITEMS`).
- Função responsável pela geração: [`generateNewKnowledge`](gerador.js).
- Fluxo principal: [`main`](gerador.js).

Arquivos principais
- [gerador.js](gerador.js) — script principal que chama a API e atualiza a base.
- [baseDeConhecimento.json](baseDeConhecimento.json) — arquivo de dados que será atualizado.
- [package.json](package.json) — configuração do projeto e script de start.
- Crie [.env](.env) na raiz com a variável GEMINI_API_KEY.

Avisos rápidos
- O arquivo `baseDeConhecimento.json` será sobrescrito ao final do processo.
- Verifique limites e custos da API Gemini antes de executar em escala.
