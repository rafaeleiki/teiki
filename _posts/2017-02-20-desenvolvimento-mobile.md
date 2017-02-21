---
layout: post
title:  "Desenvolvimento Mobile"
date:   2017-02-20 20:24:36 -0300
tags:
- mobile
- javascript
- react-native
---
Hoje em dia existem diversas alternativas para o desenvolvimento mobile.
Você pode criar um aplicativo nativo, híbrido, um web app ou um 
[Progressive Web App](https://developers.google.com/web/progressive-web-apps/){:target="_blank"}.
Nesse post vou falar um pouco sobre cada um desses tipos de apps e quais
são suas características.

## Aplicativos nativos
Desenvolvidos em Java para Android e Objective-C ou Swift para iOS, eles são
a solução mais utilizada. Usam os recursos nativos de cada sistema e possuem,
no geral, a melhor performance.

### Pros
* Performance
* Uso de APIs nativas
* Mais fácil de se manter atualizado em relação às novidades dos sistemas operacionais
* Suporte amplo

### Contras
* Precisar criar e manter uma versão do app para cada plataforma

### Quando usar
Se você possui equipe dedicada para cada plataforma, pretende lançar só em
um dos sistemas, tem necessidade de se manter muito atualizado quanto
aos recursos novos e/ou possui conhecimento técnico para desenvolvimento nativo.

## Aplicativos híbridos
Pelo uso de tecnologias web e com a possibilidade de usar recursos nativos, o 
desenvolvimento híbrido oferece uma forma rápida de se desenvolver para aqueles
que já possuem experiência com web (principalmente, JavaScript). É possível
gerar aplicativos para diferentes sistemas mantendo apenas uma base de código;
no entanto, para a maioria das aplicações, você vai querer customizar a experiência
do usuário para a plataforma em questão.

Quando usado com Cordova e [Crosswalk](https://crosswalk-project.org/), muitos
aplicativos ficam com desempenho muito bom, não sendo possível diferenciar visualmente
de aplicações nativas. No entanto, isso causa um aumento razoável no tamanho do
package, podendo chegar a vários MB a mais no app.

### Pros
* Multiplataforma
* Usa habilidades que podem ser comuns a desenvolvedores web

### Contras
* Não possuir acesso a todos os recursos do desenvolvimento nativo
de forma fácil
* Depender da atualização do framework para acessar novos recursos dos sistemas

### Quando usar
Se você tem bom domínio de front-end web, possui poucos desenvolvedores,
menos tempo para desenvolvimento, não possui grande necessidade de recursos nativos
e/ou não tem necessidade mútua de app pequeno / performance.

## Web apps
Web apps são sites que possuem adaptação para uso em dispositivos móveis.
Muitas vezes, é a solução mais barata para quem quer reproduzir interações
já existentes em sites. Os web apps, ao contrário dos aplicativos
nativos e híbridos, não se tornam aplicativos que fazem parte do sistema.
É necessário internet para acessá-los, e muitos usuários não estão acostumados
a salvar web apps em suas home screens. Além disso, os web apps dependem
da rede para poder carregar, o que pode ser um problema para conexões mais
lentas ou em uso de dados móveis (principalmente 2G e 3G).

### Pros
* Pode se ter um esforço muito menor para produção caso o site já exista
e os recursos possam ser compartilhados
* Muitas vezes usa a mesma base de código do site voltado para desktop

### Contras
* Performance notavelmente menor
* Necessita de rede para carregar
* Não possuir acesso a todos os recursos nativos

### Quando usar
Quando o desenvolvimento de apps não é uma opção e/ou o app em questão
não possui muitas interações.

## Progressive Web Apps
Considerado uma evolução dos web apps, os PWA cobrem grande parte dos 
problemas dos web apps. Os PWA oferecem experiências muito próximas
de apps nativos, não conseguindo diferenciar um do outro em muitos
casos. O conteúdo dos "sites" é cacheado (evitando a necessidade de internet) 
e o app pode ser adicionado a home screen, fazendo com que a sensação do usuário
seja de uso de um app nativo. Os PWA ainda contam com workers e podem usar 
recursos como notificações web push.

### Pros
* Experiência melhor do que os web apps
* Sem necessidade de download de apps para funcionar offline

### Contras
* Cuidado muito maior com a arquitetura do que os web apps comuns
* Não possuir acesso a todos os recursos nativos

###  Quando usar
**Por enquanto**, quando o desenvolvimento de apps não é uma opção mas
deseja-se uma experiência de usuário melhor do que a de web apps.

## React Native
Eu coloquei esse framework separado porque ele faz algo que é difícil
de encaixar nas outras categorias. Apesar de ele usar JavaScript
e se assemelhar a um aplicativo híbrido, o resultado é um aplicativo
que usa componentes nativos e JS para a lógica. Ele permite que código
nativo seja usado também, e é usado pelo app do Facebook; eles que
mantém a biblioteca, então é confiável.

### Pros
* Desempenho no nível de aplicações nativas
* Multiplataforma
* Caso necessário, é possível usar código nativo, dando acesso a 
todos os recursos

### Contras
* Curva de aprendizado alta: é necessário saber sobre
desenvolvimento mobile, React e as especifidades do React Native

### Quando usar
Semelhante aos casos de uso de aplicações nativas, mas ao invés
de conhecimento em Java / Swift / Objective-C os desenvolvedores
possuem conhecimento em JS / React e pretende-se lançar versões do
app para mais de uma plataforma.
