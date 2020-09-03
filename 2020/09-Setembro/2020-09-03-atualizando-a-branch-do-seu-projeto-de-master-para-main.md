# Atualizando a branch do seu projeto: de Master para Main

Recentemente, no projeto que eu estou envolvida no trabalho, o time levantou o tópico de modificar a branch da master para main. Achei incrível e, após ser realizado de forma super efetiva e colaborativa dentro do projeto, resolvi fazer isso nos meus projetos pessoais e vi o quão simples foi!

Dado que estou participando do Mega Hack Women, tendo muitas mulheres que estão iniciando na área, surgiu uma conversa em uma das mentorias sobre esta mudança do GitHub e vi uma grande oportunidade para compartilhar este conhecimento, além de trazer a reflexão da importância desta atualização. Precisamos falar e fazer isso!

Para dar mais contexto, seguindo o que foi divulgado na [matéria do Gizmodo](https://gizmodo.uol.com.br/github-planeja-remover-termos-como-master/):

__O CEO do Github, Nat Friedman, afirmou que a companhia está trabalhando para substituir termos como `master` (mestre) e `slave` (escravo) por termos neutros como `main` (principal). A plataforma, que pertence à Microsoft, é utilizada por 50 milhões de desenvolvedores para armazenar e atualizar projetos.__

__A discussão sobre os termos acontece na comunidade de programação há mais de uma década, mas o debate racial levantado nos Estados Unidos após a morte de George Floyd incentivou que algumas lideranças tomassem decisões.__

__Os termos Master/Slave geralmente são utilizados no hardware, arquitetura e códigos para se referir a um dispositivo, base de dados ou processo que controla outro. No Github, o termo `master` é utilizado para apontar o principal ramo de um repositório."__

Dado esse contexto, fiz esta postagem para ajudar você a aproveitar este momento para atualizar a branch principal dos seus projetos para `main`, assim como, para todos os projetos novos que você criar, deixe `main` como sua branch principal.

Segue esse fio bem explicado e simples:

## Tenho projeto no Github e quero mudar a branch da master para main

![](https://github.com/lcnunes09/caminhos-dev/blob/main/images/2020-09-03-main-01.jpg)

Antes de seguir, garanta que seu código está atualizando na branch master no GitHub!

1. Assumindo que você tem o seu projeto utilizando a branch master,  primeiro você cria a branch no seu repositório local e entra nesta branch, digitando o código:
``` 
git branch -m master main
```
2. Depois, manda esta branch main criada para o repositório remoto (GitHub), dando o push:
```
git push -u origin main
```

Agora temos duas branches como podemos ver a seguir:

![](https://github.com/lcnunes09/caminhos-dev/blob/main/images/2020-09-03-main-02.jpg)

3. Ao clicar na branch e visualizar todas as branches clicando em `View all branches`, você irá visualizar a branch `default`, ou seja, a padrão do seu projeto. Para mudar, clica no botão ao lado direito para mudar a branch padrão, mostrado na imagem a seguir:

![](https://github.com/lcnunes09/caminhos-dev/blob/main/images/2020-09-03-main-03.jpg)


4. Na próxima tela, escolha a branch main e clique no botão `Update`:

![](https://github.com/lcnunes09/caminhos-dev/blob/main/images/2020-09-03-main-04.jpg)


5. Na paz, você clica no "I understand, update the default branch.".

![](https://github.com/lcnunes09/caminhos-dev/blob/main/images/2020-09-03-main-05.jpg)


6. Volte na listagem das branches e, também na paz, dê fim a branch master clicando na lixeirinha vermelha do lado direito!

![](https://github.com/lcnunes09/caminhos-dev/blob/main/images/2020-09-03-main-06.jpg)



**E pronto! Só fazer isso nos outros projetos existentes.**


Caso tenha dado algum erro, verifique se você não tem regras definidas para branch nas configurações do repositório. Se tiver, você pode excluir indo em `Branches` dentro das configurações.

![](https://github.com/lcnunes09/caminhos-dev/blob/main/images/2020-09-03-main-07.jpg)


## Altere sua configuração para todos os novos projetos utilizarem a branch main como padrão

1. No seu perfil, vá em Configurações (ou Settings, se tiver em inglês):

![](https://github.com/lcnunes09/caminhos-dev/blob/main/images/2020-09-03-main-08.jpg)



2. Escolha a opção Repositórios (Repositories)

![](https://github.com/lcnunes09/caminhos-dev/blob/main/images/2020-09-03-main-09.jpg)



3. Atualize de master para main e clique no botão Atualizar (Update)
![](https://github.com/lcnunes09/caminhos-dev/blob/main/images/2020-09-03-main-10.jpg)



## Não esqueça de também fazer isso quando criar uma organização!

1. Caso você esteja desenvolvendo com pessoas e crie uma organização para isso, lembre-se de mudar nas configurações de Repositório!

![](https://github.com/lcnunes09/caminhos-dev/blob/main/images/2020-09-03-main-11.jpg)


2. O GitHub já ajuda no processo, é só clicar no botão `Update`!
![](https://github.com/lcnunes09/caminhos-dev/blob/main/images/2020-09-03-main-12.jpg)


## E o mais importante:

Agora, quando você pushar um código, você utiliza o comando:

```
git push origin main
```

Lindeza! :heart:


## É isso gente!
Valeu gente. Tutorial bem simples e espero que bem explicado. Se tiver alguma dúvida ou algo incorreto, por favor, é só falar!


**Lembrando que não é apenas fazer essas ações que tornam você anti racista, mas ações diárias, estimulando pessoas a fazerem isso também, lendo sobre o assunto, seguindo e consumindo o conteúdo de pessoas negras, tirando outros termos racistas do seu vocabulário, entre outras coisas!**


Textos recomendados do Portal Geledes:

[Em boca fechada não entra racismo: 13 expressões racistas que devem sair do seu vocabulário](https://www.geledes.org.br/em-boca-fechada-nao-entra-racismo-13-expressoes-racistas-que-devem-sair-seu-vocabulario/)

[18 expressões racistas que você usa sem saber](https://www.geledes.org.br/18-expressoes-racistas-que-voce-usa-sem-saber/)



Espero ter ajudado! :heart: