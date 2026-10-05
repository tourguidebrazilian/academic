# 📄 DOCX to Markdown & GitHub Publisher

Uma aplicação web *client-side* (100% no navegador) desenvolvida para converter artigos e documentos no formato **Microsoft Word (`.docx`)** para **Markdown Semântico**, renderizar equações matemáticas (**LaTeX/KaTeX**) e publicar o conteúdo convertido juntamente com suas imagens diretamente em um repositório do **GitHub**.

---

## 🚀 Funcionalidades

- **🔒 Privacidade Total:** Todo o processamento ocorre no navegador. Nenhum arquivo ou token é enviado para servidores intermediários.
- **📁 Leitura Real de DOCX:** Extração completa de parágrafos, títulos, listas, tabelas e estilos usando [Mammoth.js](https://m242.github.io/mammoth.js/) e [JSZip](https://stuk.github.io/jszip/).
- **🧮 Suporte a Fórmulas Matemáticas:** Extração automática de marcas de equação do Word (`<m:oMath>`) e conversão para LaTeX renderizado em tempo real com [KaTeX](https://katex.org/).
- **🖼️ Extração e Upload de Imagens:** Extrai imagens embutidas no `.docx` e as envia para o diretório de assets (`docs/imagens/`) no GitHub.
- **🐙 Integração Direta com GitHub API:**
  - Autenticação via **Personal Access Token (PAT)**.
  - Carregamento e seleção dinâmica dos seus repositórios.
  - Commit automático do arquivo `.md` e das imagens associadas.
- **🎨 Interface Moderna:** Layout limpo com suporte a Drag & Drop (arrastar e soltar), visualização dividida (Código Markdown vs. Pré-visualização Renderizada).

---

## 🛠️ Tecnologias Utilizadas

- **HTML5 / CSS3 / JavaScript (ES6+)**
- **[Mammoth.js](https://github.com/m242/mammoth.js)** — Conversão de `.docx` para HTML/Markdown.
- **[JSZip](https://stuk.github.io/jszip/)** — Leitura da estrutura interna XML e extração de mídias do documento Word.
- **[KaTeX](https://katex.org/)** — Renderização rápida de equações LaTeX.
- **[GitHub REST API v3](https://docs.github.com/en/rest)** — Comunicação com repositórios e criação de commits.

---

## 📥 Como Usar

### 1. Requisitos Prévios
Você precisará de um **GitHub Personal Access Token (PAT)** com permissão de escrita em repositórios (`repo` ou `public_repo`).

> **Como criar um PAT no GitHub:**
> 1. Vá em **Settings** > **Developer Settings** > **Personal Access Tokens** > **Tokens (classic)**.
> 2. Clique em **Generate new token**.
> 3. Marque o escopo `repo` (para repositórios privados) ou `public_repo` (para públicos).
> 4. Copie o token gerado.

---

### 2. Passo a Passo de Uso

1. **Abrir a Aplicação:**
   - Abra o arquivo `index.html` em qualquer navegador moderno.

2. **Conectar ao GitHub:**
   - Insira o seu **Personal Access Token (PAT)** no campo indicado no cabeçalho.
   - Clique em **Conectar**. O sistema validará o token, exibirá seu usuário do GitHub e listará seus repositórios.

3. **Carregar o Documento `.docx`:**
   - Arraste e solte o arquivo `.docx` na área de upload ou clique na caixa para selecionar o arquivo.
   - O documento será processado instantaneamente em memória.

4. **Revisar e Editar:**
   - Utilize a guia **Código Markdown** para editar o texto gerado manualmente, se necessário.
   - Utilize a guia **Pré-visualização** para checar a formatação final, tabelas e equações KaTeX.

5. **Publicar no GitHub:**
   - Selecione o **Repositório** de destino na lista suspensa.
   - Ajuste o **Caminho do Arquivo** (ex: `docs/artigo.md`).
   - Insira uma **Mensagem de Commit**.
   - Clique em **🚀 Publicar no GitHub**.

---

## 📁 Estrutura de Arquivos do Commit

Quando você clica em publicar, o app realiza as seguintes ações no seu repositório:

```text
seu-repositorio/
├── docs/
│   ├── artigo.md            # Arquivo Markdown convertido
│   └── imagens/
│       ├── imagem_1.png     # Imagens extraídas do .docx
│       └── imagem_2.jpg