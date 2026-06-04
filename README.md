# Clone Disney+

Projeto front-end que recria a interface da landing page do Disney+ com HTML, Sass, JavaScript e automação de build com Gulp.

O objetivo deste repositório é praticar organização de estilos com Sass, interação com JavaScript puro e geração de arquivos otimizados para uso no navegador.

## Visão geral

Este projeto renderiza uma página estática inspirada no Disney+, com foco em:

- layout responsivo;
- organização de estilos em arquivos Sass parciais;
- troca de abas na seção de atrações;
- accordion na seção de perguntas frequentes;
- alteração do cabeçalho durante o scroll;
- pipeline de build para CSS, JavaScript e imagens.

Os arquivos-fonte ficam dentro de `src` e os arquivos processados são gerados em `dist`.

## Tecnologias utilizadas

- HTML5
- Sass
- JavaScript vanilla
- Gulp 4
- gulp-sass
- gulp-uglify
- gulp-imagemin

## Estrutura do projeto

```text
.
|-- assets/
|   `-- fonts/
|-- dist/
|   |-- css/
|   |-- images/
|   `-- js/
|-- src/
|   |-- images/
|   |-- scripts/
|   |   `-- main.js
|   `-- styles/
|       |-- main.scss
|       |-- _available-devices.scss
|       |-- _faq.scss
|       |-- _footer.scss
|       |-- _header.scss
|       |-- _hero.scss
|       |-- _plans.scss
|       |-- _shows.scss
|       `-- _variaveis.scss
|-- gulpfile.js
|-- index.html
`-- package.json
```

## Como o projeto funciona

### HTML

O arquivo principal da aplicação é o `index.html`.

Ele consome os arquivos compilados gerados em `dist`:

- `dist/css/main.css`
- `dist/js/main.js`
- `dist/images/...`

Isso significa que, antes de abrir a página com o resultado final esperado, é necessário executar o processo de build ou o modo de desenvolvimento.

### Estilos com Sass

O ponto de entrada dos estilos é `src/styles/main.scss`.

Esse arquivo importa os parciais responsáveis por cada seção da página, como cabeçalho, hero, planos, shows, FAQ e rodapé. O Gulp compila esses arquivos para `dist/css/main.css`.

### JavaScript

O comportamento da interface está em `src/scripts/main.js`.

As interações implementadas são:

- esconder e mostrar o cabeçalho com base no scroll;
- alternar as abas da seção de shows;
- abrir e fechar respostas da FAQ.

### Imagens

As imagens-fonte ficam em `src/images` e são processadas para `dist/images` durante o build.

## Pré-requisitos

Antes de rodar o projeto, você precisa ter instalado:

- Node.js
- npm

Para confirmar a instalação, você pode usar:

```bash
node -v
npm -v
```

## Instalação

Clone o repositório e instale as dependências:

```bash
git clone https://github.com/PauloHenrique993940/clone_disneyplus-main.git
cd clone_disneyplus-main
npm install
```

## Scripts disponíveis

Os scripts estão definidos em `package.json`.

### Desenvolvimento

```bash
npm run dev
```

Esse comando:

- compila Sass para CSS;
- minifica o JavaScript;
- otimiza as imagens;
- inicia o modo watch para recompilar automaticamente quando houver alteração nos arquivos de `src`.

Use esse modo durante a edição do projeto.

### Build

```bash
npm run build
```

Esse comando executa a build completa uma vez, gerando os arquivos finais em `dist`.

### Testes

```bash
npm test
```

Atualmente não há uma suíte de testes implementada. Esse script está apenas como placeholder no projeto.

## Fluxo recomendado para rodar localmente

1. Instale as dependências com `npm install`.
2. Execute `npm run dev` para gerar os arquivos da pasta `dist` e manter o watch ativo.
3. Abra o `index.html` no navegador.

Se preferir apenas gerar os arquivos processados sem manter o watch ligado, use `npm run build`.

## Pipeline de build

O arquivo `gulpfile.js` define três tarefas principais:

- `styles`: compila os arquivos `.scss` e gera `dist/css/main.css`;
- `scripts`: minifica os arquivos JavaScript de `src/scripts` e gera `dist/js`;
- `images`: otimiza as imagens de `src/images` e gera `dist/images`.

Além disso:

- a tarefa padrão executa `styles`, `scripts` e `images` em paralelo;
- a tarefa `watch` executa primeiro a compilação inicial e depois observa alterações em estilos, scripts e imagens.

## Organização dos estilos

Os estilos foram divididos por responsabilidade para facilitar manutenção:

- `_variaveis.scss`: variáveis globais de cores;
- `_header.scss`: cabeçalho;
- `_hero.scss`: seção principal;
- `_shows.scss`: seção com abas de conteúdo;
- `_plans.scss`: área de planos;
- `_available-devices.scss`: seção de dispositivos;
- `_faq.scss`: perguntas frequentes;
- `_footer.scss`: rodapé;
- `main.scss`: ponto central que reúne tudo.

## Funcionalidades da interface

### Cabeçalho dinâmico

O cabeçalho muda de estado conforme a posição da rolagem da página.

### Abas de conteúdo

Na seção de atrações, os botões alternam entre listas diferentes usando atributos `data-tab-button` e `data-tab-id`.

### FAQ com accordion

As perguntas frequentes usam clique para abrir e fechar respostas, adicionando ou removendo classes CSS no item correspondente.

## Saída gerada em dist

Após rodar `npm run dev` ou `npm run build`, a pasta `dist` passa a conter:

- CSS compilado;
- JavaScript minificado;
- imagens otimizadas.

Esses são os arquivos efetivamente consumidos pelo HTML.

## Problemas comuns

### O Sass não compilou

Garanta que as dependências foram instaladas:

```bash
npm install
```

Depois execute:

```bash
npm run dev
```

Esse comando já faz a compilação inicial antes de entrar em modo watch.

### A página abriu sem estilo

Normalmente isso acontece quando a pasta `dist` ainda não foi gerada. Rode:

```bash
npm run build
```

ou:

```bash
npm run dev
```

### As imagens não aparecem

Verifique se o build foi executado e se os arquivos foram gerados em `dist/images`.

## Possíveis melhorias futuras

- adicionar um servidor local com live reload;
- criar uma suíte de testes para interações da interface;
- melhorar acessibilidade com foco em navegação por teclado e atributos ARIA;
- separar melhor os dados do conteúdo em estruturas reutilizáveis;
- adicionar validação e lint para HTML, CSS e JavaScript.

## Autor

Projeto baseado em estudo prático de front-end com foco em clone visual e automação de assets.
