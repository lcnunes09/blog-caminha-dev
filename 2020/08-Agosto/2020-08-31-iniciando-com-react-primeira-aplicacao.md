
# Iniciando uma aplicação React

## Assumindo que você já tem instalado
Se não tiver, clique aqui.
```
- yarn create react-app web --template typescript
```

ou 
```
- npx create-react-app web --template typescript
```

No meu computador, aparece um erro dependendo da pasta que eu esteja se eu estiver usando yarn. Desta forma, pode utilizar o comando npx.

Obs: Mesmo usando npx, é possível utilizar os comandos do yarn depois :)


## Para visualizar a aplicação React rodando
```
yarn start
```

E agora tem um servidor frontend React rodando! Acesse: http://localhost:3000/

## Limpar a estrutura
- Deletar README: podemos criar um readme depois, melhor estruturado.
- Dentro da pasta src, deletar os arquivos CSS, Testes, Service Worker, Logo: dado que não precisamos utilizar agora no início.

No arquivo index.tsx, deletar as chamadas dos arquivos CSS e Service worker que não estão mais utilizados.

- index.tsx
```
import React from 'react';
import ReactDOM from 'react-dom';
import App from './App';

ReactDOM.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>,
  document.getElementById('root')
);
```

No arquivo App.tsx, deletar chamadas CSS e logo, assim como apagar HTML e deixar apenas um Hello World :D
import React from 'react';

- App.tsx
```
function App() {
  return (
    <div className="App">
      <h1>Hello Word</h1>
    </div>
  );
}

export default App;
```

Na pasta public, apenas deixar o index.html. Neste index.html, deletar as chamadas CSS e favicon. Deixar o body apenas com a tag do noscript e a div root.

Dentro de web/src, criar pasta assets. Dentro da pasta assets:
- Criar pasta images.
- Criar pasta styles e arquivo global.css.

## Configurando CSS e HTML com estilo inicial

No arquivo global.css, já deixar um setup padrão para as páginas, por exemplo:
```
:root {
    font-size: 60%;

    --color-background: #F0F0F7;
    --color-primary-lighter: #9871F5;
    --color-primary-light: #916BEA;
    --color-primary: #8257E5;
    --color-primary-dark: #774DD6;
    --color-primary-darker: #6842C2;
    --color-secundary: #04D361;
    --color-secundary-dark: #04BF58;
    --color-title-in-primary: #FFFFFF;
    --color-text-in-primary: #D4C2FF;
    --color-text-title: #32264D;
    --color-text-complement: #9C98A6;
    --color-text-base: #6A6180;
    --color-line-in-white: #E6E6F0;
    --color-input-background: #F8F8FC;
    --color-button-text: #FFFFFF;
    --color-box-base: #FFFFFF;
    --color-box-footer: #FAFAFC;
}

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

html, body, #root {
    height: 100vh;
}

body {
    background: var(--color-background);
}

#root {
    display: flex;
    align-items: center;
    justify-content: center;
}

body, 
input,
button,
textarea {
    font: 500 1.6rem Poppins;
    color: var(--color-text-base);
}

.container {
    width: 90vw;
    max-width: 700px;
}

@media (min-width: 700px) {
    :root {
        font-size: 62.5%;
    }
}
```

No arquivo App.tsx, chamar o global.css, adicionando linha
```
import './assets/styles/global.css';
```

No arquivo public/index.html, colocar o link para a fonte que vou utilizar, pegando no site google fonts.

Dica CSS: 
- Trabalhar em unidade de rem  para trabalhar mais fácil com porcentagem no font-size.

## Estruturando primeira página!

Dicas :: Componentes React:
- Nome do componente sempre em letra maiúscula
- Sempre que criar um componente, importar React

Dentro de src, criar pasta pages e dentro dela a pasta Landing, para iniciar a estrutura da Landing Page. 
Dentro dessa pasta, criar arquivo index.tsx.

### Criando a primeira página
Exemplo de como iniciar um código index.tsx para exibir a primeira página

```
import React from 'react';

function Landing() {
    return <h1>Landing</h1>
}

export default Landing;
```

Não esquecer de chamar ela no App.tsx!
```
import Landing from './pages/Landing';
```

Assim como, chamar a página dentro do return da função App():
```
<Landing />
```

## E como começa a brincadeira?
Dentro do return da função da página criada, agora é só usar HTML!

### Alguns pontos importantes:
- A imagem sempre precisa ser importada no topo da página, junto com os outros imports:

```
import logoImg from '../../assets/images/logo.svg';
```

E depois chamada na tag img, atributo src, do código, entre chaves. Exemplo:

```
<img src={logoImg} alt="Proffy"/>
```

 - O atributo class do HTML é agora className. Exemplo:
```
<div className="buttons-container">
```
