# Criando componentes em React

Muitas vezes vamos fazer páginas em que terão elementos comuns. Cabeçalhos, Rodapés, botões, cartões para exibir informações similares na tela, etc.

Para isso, uma forma de fazer é usando componentes!

## Estruturando componentes
Similar às páginas, criar a pasta `components` dentro da pasta `src`. Para cada componente, criar uma nova pasta. Por exemplo, vamos construir um cabeçalho, criando dentro da pasta `components` a pasta `PageHeader`. 

Dentro da pasta `PageHeader`, como já sabemos, criamos os arquivos `index.tsx` e `styles.css`.

Dentro do código do componente básico, estruturamos o nosso Header, como por exemplo:
```
<header className="page-header">
    <div className="top-bar-container">
        <Link to="/">
            <img src={backIcon} alt="Voltar"/>
        </Link>
    </div>

    <div className="header-content">
        <strong>Conheça-nos.</strong>
    </div>
</header>
```

E agora, dentro de cada página que for usar este header, chamamos o componente, colocando dentro do return da função:
```
<PageHeader />
```

Não se esqueça de importar o componente!
```
import PageHeader from '../../components/PageHeader';
```

E pronto!

# E se eu precisar mudar o título principal para cada header?
Imagina que cada header pode ter algum título específico de acordo com cada página. Desta forma, para fazermos isso, precisamos usar propriedades e interfaces.

# Mandando uma propriedade pro Header
Para mandar um título para o Header de cada página, é apenas necessário acrescentar um parâmetro, por exemplo, `title`, contendo o título especifico. 
```
<PageHeader title="Que incrível que você quer dar aulas" />
```

Já dentro do PageHeader, precisamos mudar a função para uma constante, ou seja, ao invés de `function PageHeader {`, chamamos:
```
const PageHeader = () => {
```

Precisamos definir o formato das tipagens de um objeto, criando uma interface para ele. 

Basicamente é dizer que nosso PageHeader vai receber uma propriedade `title` que é obrigatória:
``` 
interface PageHeaderProps {
    title: string;
}
```

Dics: 
- Caso não fosse obrigatória, colocaria uma interrogação após o title: `title?: string;`.

## Como fazer com que o componente saiba que precise usar a propriedade?
Precisamos determinar que o componente é uma FunctionalComponent. Mas o que é isso? É apenas dizendo que temos um componente em formato de função :)

E ele precisa receber um parâmetro que é o nosso PageHeaderProps. Desta forma, a chamada do nosso componente ficaria
```
const PageHeader:React.FC<PageHeaderProps> = () => {
```

Tudo certo até aí? Espero que sim! 

Agora precisamos fazer com que nosso componente receba nossas propriedades e trazer a propriedade `title`, exibindo na mensagem do nosso header.

Para isso, nossa chamada recebe `props`:
```
const PageHeader:React.FC<PageHeaderProps> = (props) => {
```

E no local que eu quiser usar a propriedade `title`, eu preciso chamar desta forma:
```
{props.title}
```

Para resumir, no final, nosso PageHeader ficaria:

```
import React from 'react';

import backIcon from '../../assets/images/icons/back.svg';

interface PageHeaderProps {
    title: string;
}

const PageHeader:React.FC<PageHeaderProps> = () => {
    <header className="page-header">
        <div className="top-bar-container">
            <Link to="/">
                <img src={backIcon} alt="Voltar"/>
            </Link>
        </div>

        <div className="header-content">
            <strong>Conheça-nos.</strong>
        </div>
    </header>
    );
}

export default PageHeader;
```

## E é isso!

Espero ter ajudado! :heart: