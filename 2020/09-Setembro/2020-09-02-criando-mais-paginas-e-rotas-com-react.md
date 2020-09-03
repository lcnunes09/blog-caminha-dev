# Criando mais páginas e rotas usando React!

Depois de criarmos a Landing page, o que acontece se precisarmos criar mais páginas para o nosso projeto?

É isso que vamos fazer hoje! Se está aqui e não sabe criar um projeto usando React, recomendo dar uma olhada na postagem [Iniciando com React](https://github.com/lcnunes09/caminhos-dev/blob/main/2020/08-Agosto/2020-08-31-iniciando-com-react-primeira-aplicacao.md)!

## Criando a estrutura

Dentro da pasta `pages`, criar pasta com sua nova página. Por exemplo `Cadastro`.

Dentro dessa pasta, criar o arquivo `index.tsx`, contendo:

```
import React from 'react';

function Cadastro() {
    return (
        <h1>Cadastro</h1>
    )
}

export default Cadastro;
``` 

Todas as páginas vão utilizar essa estrutura básica! 

## Adicionando CSS
Caso queira adicionar CSS específico para página, na mesma pasta `Cadastro`, criar arquivo `styles.css` e colocar o estilo que queira utilizar!

Não se esqueça de importar o `styles.css` no arquivo `Cadastro/index.tsx`, como foi feito na página Landing:
```
import './styles.css';
```

## Criando as Rotas

Agora que temos nossas páginas, vamos criar as rotas. Para isso, vamos instalar o módulo `react-router-dom` para fazer as navegações.

``` 
yarn add react-router-dom
```

Após instalar, dentro da pasta `src` vamos configurar as rotas criando um arquivo novo chamado `routes.tsx`.

Dentro desse arquivo, vamos importar o React e o React Router Dom.
```
import React from 'react';

import { BrowserRouter, Route } from 'react-router-dom'
```

Caso algum erro apareça ao importar o React Router Dom, já existe uma indicação para instalar utilizando @types/react-router-dom. Pode fazer isso que vai dar certo! Lembrando que esta dependência pode ser instalada como dependência de desenvolvimento, para isso, é só colocar o -D no fim do comando.
```
yarn add @types/react-router-dom -D
``` 

## Adicionando as rotas
Dado que agora temos duas páginas, a Landing Page e a página de Cadastro, precisamos adicionar essas rotas.

A rota é basicamente a URL que a pessoa usuária irá acessar e qual conteúdo irá mostrar ao abrir a página, baseado na pasta / conteúdo que criou.

Por exemplo, caso eu queira que a pessoa usuária, ao acessar minhapagina.com.br/cadastro ela acesse o que está no arquivo Cadastro/index.tsx, esta é a rota que deve ser criada:
``` 
<Route path="/cadastro" component={Cadastro} />
```

Quando digitamos o componente, dependendo da sua configuração, ele pode ser importado automaticamente, a medida que o auto complete aparecer. Se não tiver acontecido, não se esqueça de importar na parte superior:
```
import Cadastro from './pages/Cadastro';
```

Dica:
- Não precisa colocar especificamente o arquivo index.tsx pois o React já reconhece automaticamente!
- Para a página principal do projeto, ou seja, quando a pessoa acessar minhapagina.com.br ela visualizar a página "Landing", basta colocar o path como "/" e direcionando qual página será visualizada. Porém, para não confundir o navegador e mostrar tanto o cadastro quanto a Landing quando entrarmos em /cadastro, dado que tem uma "/" no link, precisamos colocar o atributo `exact` para apenas aparecer a página Landing caso o usuário acesse exatamente a página principal do nosso projeto, por exemplo, minhapagina.com.br. 

Se ficou difícil de entender, faça o teste sem o atributo `exact` e entre na página localhost:3000/cadastro. Deve exibir as duas páginas, Landing e Cadastro.

Para finalizar, nosso arquivo de rotas ficaria assim:
```
import React from 'react';

import { BrowserRouter, Route } from 'react-router-dom';

import Landing from './pages/Landing';
import Cadastro from './pages/Cadastro';

function Routes() {
    return (
        <BrowserRouter>
            <Route path="/" exact component={Landing} />
            <Route path="/cadastro" component={Cadastro} />
        </BrowserRouter>
    )
}

export default Routes;
```

## Chamando as Rotas!
E agora, como fazer as rotas funcionar?

Vamos lembrar da nossa página principal, `App.tsx`. Antes, estávamos apenas chamando a Landing page. Agora, precisamos atualizar para utilizar Rotas, assim como importar o arquivo routes!
```
import React from 'react';

import Routes from './routes';

import './assets/styles/global.css';

function App() {
  return (
    <Routes />
  );
}

export default App;
```

## E é isso!
Prontinho! Agora você tem seu projetinho com as páginas funcionando separadamente.

Agora você pode focar no seu HTML / CSS e fazer suas páginas, porém, usando React!

Aguarde mais postagens :heart: