# Utilizando Single Page Application no seu projeto

PS: Caso não tenha visto as postagens anteriores e queira seguir a linha do pequeno projeto, recomendo dar uma olhada no Readme!

Atualmente, quando criamos páginas separadas como criadas nas postagens anteriores, cada vez que entramos em uma página específica, todos os recursos comuns entre as páginas são recarregados desnecessariamente, fazendo com que a pessoa que está acessando precise esperar este carregamento.

Para evitar que isso aconteça, podemos implantar a ideia de Single Page Application, explicada melhor a seguir:

## Utilizando "Link to" ao invés da tag "a href" quando criando links entre páginas
Uma forma direta e bem simples é:
- Importar o módulo Link do react-router-dom (já falado um pouco na postagem anterior).
- Trocar o a href por Link!

Um exemplo prático:
Imagina que na nossa página Landing, terá um botão para efetuar o cadastro. O código do botão deverá ser:
```
<Link to="/cadastro" className="cadastro">
    Cadastro
</Link>
```

E lembrar de importar o módulo Link nesta página!
```
import { Link } from 'react-router-dom';
```

## É isso! 
Uma postagem breve mas qeu espero que ajude :heart: