PRIMEIROS PASSOS

  - criando o projeto
    - vamos fazer com yarn por conta de algumas extensoes especificas
    - yarn init -y
      - para criar o json das configurações
    - yarn add next react react-dom
      - coloca todas essas dependencias no projeto
      - adicionando os scripts que estao na documentacao no json
  
  - otimização SPA
    - criamos uma pasta pages
      - todo arquivo dentro dela se transforma em uma rota
    - utilizamos o import do Link do próprio next que otimiza âncoras como SPA -> vimos que para aplicar igual o video precisamos utilizar um
    Link mais antigo

  - entendendo o build
    - SSR - server side render
      - o usuário recebe somente o html necessário na página
      - colocar para hostiar em um servidor
        - o nosso código é lido pela máquina a qual colocamos o host
      - rodamos os arquivos de forma estática: pega somente o js, html e css da página e serve para o cliente
        - quando o usuário acessa, o servidor interpreta que teve uma requisição e manda os arquivos necessários
        - não tem o processamento de gerar o arquivo
      - o Next faz mais ou menos isso de SSR, mas ele gerar diversos arquivos estáticos
    - atalho no json: "export": "next build && next export"
      - ao rodar gera a pasta out
      - dentro dele gera os arquivos
        - esses são os arquivos estáticos -> a pessoa só abre ele e ele carrega aquela página por completo

  - Começar a estilização
    - CSS in JS
      - fazemos um class dinâmico onde fazemos o css dentro do prórpio escopo do componente
      - com o <style jsx>
      - deixamos todo o componente o máximo genérico possível -> utilizamos o as por exemplo
      - elimina o dead code
      - próprio do Next
    - Estilos "globais"
      - fizemos um estilo global, mas global dentro do próprio componente
      - ta tudo no arquivo index.js
    - Estilo GLOBAL
      - podemos fazer um global de fato
      - vamos fazer um centralizador - MIDDLEWARE - meio de campo entre qualquer página que o usuário acesse e qualquer componente que vamos renderizar
      - fizemos então esse arquivo _app.js -> funciona como um layout
      - criamos uma pasta theme/GlobalStyle.js -> nele colocamos todos os temas que queremos renderizar globalmente
      - puxamos esse componente GlobalStyle para o _app.js -> aplica em toda aplicação
    - Esse tipo de estilização ajuda na otimização -> não temos que fazer mais arquivos ou nos preocuparmos com o className

  - Componentes do layout
    - yarn add @fortawesome/fontawesome-svg-core @fortawesome/free-solid-svg-icons @fortawesome/react-fontawesome
      - instalando algumas fontes e icones
    - estruturação dos componentes da página da home

  - Arquivos estáticos
    - tudo que é renderizado passa pelo arquivo app.js
    - SFS - static file serving - pegar as imagens estáticas para utilizar no projeto - baixar no projeto
    - libs de requisições serão aproveitadas
      - o Next tem funções a mais que auxiliam na performance
      - enquanto o react faz algo menos otimizado -> tem um certo loading
        - o Next possibilita o particionamento do loading da aplicação -> vai mandando por pedaços
        - contorna esse problema de otimização que impactio no SEO
      - fazemos as tags já entrarem preenchidas
        - getStaticProps: next sincroniza todos os dados do objeto e joga o dado na página
        - tira o tempo de load
        - foca em perfomance -> consegue controlar o que vai ser carregado antes -> LCP (largest contentful paint) loading
        - serve para publicar sites staticos, em github pages ou algo do gênero
        - o estático chega mais rápido para o usuário, não precisa de dinamicidade

        - getServerSideProps: o build é feito diferente
          - roda sempre que o usuário carrega a página, não carrega somente uma vez como é feito no static
          - todo acesso do usuário ele roda de novo
          - só fazemos o uso dessa propriedade quando queremos uma página mais dinâmica que precisa ser atualizada com interação do usuário

      - SSG (STATIC SITE GERENATION)
      - SSR (SERVER SIDE RENDERING)

  - next Head
    - componente do next para lidar com o cabeçalho das páginas
    - import Head from 'next/head'
      - conseguimos colocar o título da página com:
        <Head>
          <title>Home - Alura Case Campanha</title>
        </Head>
    - podemos importar as fonts do google fonts também com o link

  - scripts externos
    - google analytics
    - tem um jeito certo de escrever script dentro do jsx com a propriedade dangerousHTML 

  - Trailing slashs e redirects
    - criamos o arquivo next.config.js
      - comfigurações gerais de como o next deve funcionar
      - colocamos o trailingSlash: true
        - faz com que independete da url que estamos tenha uma barra no final da url
        - trabalhar com análise de dados pode ser necessária ter essa barra
      - fizemos um redirecionamento -> se a pessoa digitar "perguntas" é redirecionada para o FAQ
