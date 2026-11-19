# Repertório digital do COMVIDA — EEPJFCA

Site institucional estático para registrar, organizar e preservar a memória ambiental da Comissão de Meio Ambiente e Qualidade de Vida na Escola (COMVIDA), da Escola Estadual Professor José Félix de Carvalho Alves. Slogan: **“Cuidar, transformar e agradecer.”**

## Estrutura

- `index.html`, `sobre.html`, `projetos.html`, `acoes.html`, `repertorio.html`, `galeria.html`, `equipe.html`, `contato.html`: páginas públicas.
- `admin.html`: painel de edição ligado à API do GitHub.
- `CSS/style.css`, `js/script.js`, `js/admin.js`: estilos e funcionalidades.
- `data/*.json`: conteúdo público editável; começa vazio intencionalmente.
- `imagens/`: identidade visual e imagens do acervo.

## Publicar gratuitamente no GitHub Pages

1. No repositório, abra **Settings → Pages**.
2. Em **Build and deployment**, selecione **Deploy from a branch**.
3. Selecione a branch `main` e a pasta `/ (root)`, depois salve.
4. Aguarde a publicação indicada na página Pages e acesse o endereço apresentado pelo GitHub.
5. Faça um commit no repositório para atualizar o site. Não é necessário processo de build.

## Conteúdo e repertório

Projetos, ações, fotos, integrantes e registros históricos são mantidos em `data/projects.json`, `data/actions.json`, `data/gallery.json`, `data/team.json` e `data/history.json`. Os arquivos estão vazios para evitar inventar datas, pessoas ou atividades. O repertório apresenta espaços para 2021–2026 e aceita novos anos. Filtros de pesquisa, ano e categoria são montados a partir dos registros publicados.

Registros podem ser adicionados pelo painel ou por edição direta dos JSON. Cada registro aceita `id`, `title`, `year`, `category`, `date` (formato `AAAA-MM-DD`), `description`, `image` e `details`. Para a galeria, use ao menos `title`, `year` e `image`; para equipe, `title` recebe o nome confirmado e `category` pode indicar a função. Exemplo de objeto (apenas modelo, não é conteúdo publicado):

```json
{
  "id": "id-unico",
  "title": "Título confirmado",
  "year": 2026,
  "category": "Educação ambiental",
  "date": "2026-01-30",
  "description": "Descrição validada pela escola.",
  "image": "imagens/registros/foto.jpg",
  "details": "Informações complementares"
}
```

## Painel administrativo e segurança

O GitHub Pages serve apenas arquivos estáticos e não oferece banco de dados ou autenticação de servidor. O painel implementado usa a API oficial do GitHub para gravar commits diretamente nos arquivos do repositório. Para editar, abra `admin.html` no endereço publicado e autentique com um **fine-grained personal access token** do GitHub, limitado a este repositório, com **Contents: Read and write**. A autenticação usa o token fornecido e o mantém somente na memória da página; não há senha padrão, token embutido, `localStorage` ou salvamento falso no navegador. A gravação produz um commit real. A imagem pode ser enviada pelo próprio painel (máximo 1 MB; formatos JPG, PNG, WebP e GIF).

**Atenção:** este modelo é apropriado somente para administradores confiáveis. O navegador precisa enviar o token à API GitHub, então o token não é um segredo protegido por um servidor da aplicação: não compartilhe token, não o incorpore no código e encerre a sessão ao terminar. Configure expiração curta e permissões mínimas, mantenha apenas pessoas confiáveis com acesso de escrita ao repositório e proteja a conta GitHub com autenticação em dois fatores. Para vários editores ou controle de acesso mais forte, use um CMS com OAuth mediado por servidor (ou outro backend autenticado); GitHub Pages sozinho não consegue proteger credenciais de forma equivalente.

O painel está vinculado a este repositório e branch `main`. Se a branch de publicação mudar, atualize `BRANCH` em `js/admin.js`.

## Acessibilidade e compatibilidade

HTML semântico, navegação por teclado, foco visível, rótulos de formulário, texto alternativo, controles acessíveis e menu responsivo. O conteúdo é carregado sob demanda dos JSON; imagens da galeria usam carregamento tardio. O site funciona sem build e utiliza apenas HTML, CSS e JavaScript, com uma dependência CDN para fonte legível da API GitHub no painel.
