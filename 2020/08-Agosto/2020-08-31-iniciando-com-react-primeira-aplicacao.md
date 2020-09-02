
# Iniciando uma aplicação React
Olá! Criei essa postagem para ajudar vocês nos primeiros passos com um projeto React. Minha motivação maior foi que eu iniciei como dev tendo experiências em hackathons, porém apenas utilizando HTML, CSS e JavaScript. O que foi muito bom, porém entender de React trouxe outras possibilidades e facilidades que espero compartilhar com vocês! Muito do que está aqui eu aprendi participando das Next Level Week (houveram duas até o momento dessa postagem) e também assistindo videos no youtube. Espero ajudar e que você veja o quão simples é ter sua aplicação em React!

## Preparação do ambiente
Uma forma que pode ajudar a instalação do Node na sua máquina é utilizar gerenciadores de pacotes. [Nesta página](https://nodejs.org/en/download/package-manager/) é possível encontrar várias plataformas diferentes e como instalar. 

Caso esteja utilizando Windows, o meu caso, eu instalei o [Chocolatey](https://chocolatey.org/install) para me ajudar na instalação de 3 coisas: NPM, Yarn e Node.

### Para instalar o Chocolatey: 
1) Abrir o PowerShell do Windows como Administrador;
2) Rode o comando ```Get-ExecutionPolicy```. Se retornar ```Restricted```, rode o comando ```Set-ExecutionPolicy AllSigned``` ou o comando ```Set-ExecutionPolicy Bypass -Scope Process```.
3) Confirme que o Get-ExecutionPolicy não está Restricted.
4) Rode o comando ```Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))```.
5) Digite ```choco``` para ver se o Chocolatey foi instalado e veja a versão instalada.

#### Para instalar o Node e NPM
Rode o comando abaixo para instalar o Node junto com NPM utilizando o Chocolatey: 
```
cinst nodejs.install
```

#### Para instalar o Yarn
```
choco install yarn
```

NPM e Yarn são gerenciadores de pacotes para javascript que vão te ajudar a instalar dependências necessárias no seu projeto e, espero, contribuir no desenvolvimento. Yarn é mais aprimorado que o NPM: mais rápido e tem algumas funcionalidades mais avançadas.

Para concluir, eu precisei reiniciar minha máquina para verificar que tudo estava funcionando conforme esperado. Para confirmar, rode os comandos para saber a versão que está instalada no seu computador:

```
node -v
npm -v
yarn -v
```

Não se esqueça que precisa ter o GIT instalado na sua máquina! :)

## Assumindo que você já tem instalado
Para criar sua primeira aplicação React é tão simples quanto uma linha de código, literalmente! Primeiro, vá para pasta que você queira criar o seu repositório.
```
yarn create react-app web --template typescript
```

ou 
```
npx create-react-app web --template typescript
```

No meu computador, aparecia um erro dependendo da pasta que eu estivesse rodando o comendo utilizando yarn. Desta forma, pode utilizar o comando npx para a criação da apliação React, sem problemas.

Obs: Mesmo usando npx, é possível utilizar os comandos do yarn depois :)


## Para visualizar a aplicação React rodando
```
yarn start
```

E agora você tem um servidor frontend React rodando! Acesse para visualizar essa lindeza: http://localhost:3000/

## Limpar a estrutura
O React instala por padrão diversos arquivos que, para essa aplicação mais simples, não iremos utilizar. Então, segue as dicas:
- Deletar README: podemos criar um readme depois, melhor estruturado e específico para o projeto.
- Dentro da pasta src, deletar os arquivos de CSS, Testes, Service Worker, Logo: dado que não precisamos utilizar agora no início.

No arquivo index.tsx, deletar as chamadas dos arquivos CSS e Service worker que não estão mais utilizados.

- `index.tsx`
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

- `App.tsx`
```
import React from 'react';

function App() {
  return (
    <div className="App">
      <h1>Hello Word</h1>
    </div>
  );
}

export default App;
```

Na pasta public, apenas deixar o arquivo `index.html`. Neste arquivo, deletar as chamadas CSS e favicon. Deixar o body apenas com a tag do noscript e a div root.

Dentro de web/src, criar pasta assets. Dentro dessa pasta:
- Criar pasta images.
- Criar pasta styles e arquivo global.css.

Segue abaixo nossa estrutura final de arquivos:
```
> web
>> node_modules
>> public
>>> index.html
>> src
>>> assets
>>>> images
>>>> styles
>>>>> global.css
>>> App.tsx
>>> index.tsx
>> .gitignore
>> package.json
>> tsconfig.json
>> yarn.lock
```

## Configurando CSS e HTML com estilo inicial

No arquivo global.css, já deixar um setup padrão para as páginas, por exemplo:
```
:root {
    font-size: 60%;

    --color-background: #F0F0F7;
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

No arquivo `public/index.html`, colocar o link para a fonte que vai utilizar. Você pode utilizar o site [Google Fonts](https://fonts.google.com/) pode ajudar muito.

O exemplo de fonte utilizada neste código é a fonte Poppins, que você pode importar com o link abaixo, colocando no `public/index.html`:
```
<link href="https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap" rel="stylesheet">
```

Dicas: 
- Em CSS, recomendo utilizar em unidade de rem ao invés de pixels. Isso facilita aumentar e diminuir a fonte utilizando porcentagem no font-size, principalmente no caso de desenvolvimento Mobile / Website. 
- Ao efetuar a importação da fonte, caso utilize Google Fonts, priorize a importação da fonte através da tag link, ao invés de @import, pois pode causar problemas mirabolantes não identificáveis no futuro. 

## Estruturando primeira página!

Dicas | Componentes React:
- Nome do componente sempre em letra maiúscula.
- Sempre que criar um componente, importar React na primeira linha.

Suponha que você vai construir uma página inicial principal, a qual chamamos Landing Page.

Dentro da pasta `src`, criar pasta `pages` e dentro dela a pasta `Landing`, para iniciar a estrutura da Landing Page. 

Dentro dessa pasta, criar arquivo `index.tsx`.

### Criando a primeira página
Exemplo de como iniciar um código `index.tsx` para exibir a primeira página:

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

Assim como, chamar a página dentro do return da função App(). Ficando no final:
```
import React from 'react';

import Landing from './pages/Landing';

import './assets/styles/global.css';

function App() {
  return (
    <Landing />
  );
}

export default App;
```

## E como começa a brincadeira?
Dentro do return da função da página criada, agora é só usar HTML! 

Para criar o estilo desta página, dentro da pasta `Landing` criar arquivo `style.css` e é só alegria!

### Alguns pontos importantes:
A imagem sempre precisa ser importada no topo da página, junto com os outros imports:

```
import logoImg from '../../assets/images/logo.svg';
```

E depois chamada na tag `img`, atributo `src`, do código, entre chaves. Exemplo:

```
<img src={logoImg} alt="Proffy"/>
```

O atributo class do HTML é agora `className`. Exemplo:
```
<div className="buttons-container">
```


### Final!

No final, você já consegue ter uma estrutura básica para começar seu projeto usando React!

![](https://github.com/lcnunes09/caminhos-dev/blob/main/images/2020-08-31-landing-page-react.jpg)

Para mais informações e dar uma olhada no código em desenvolvimento, acessem [esse repositório](https://github.com/lcnunes09/nlw2-proffy). Projeto realizado durante a Next Level Week #2, pela Rocketseat, onde estou refazendo e atualizando!

Qualquer dúvida, conte comigo!
