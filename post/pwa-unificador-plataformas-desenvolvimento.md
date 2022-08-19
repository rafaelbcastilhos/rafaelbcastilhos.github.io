---
title: 'Progressive Web App, o unificador de plataformas de desenvolvimento'
path: /pwa-unificador-plataformas-desenvolvimento
date: 2020-08-28
summary: 'Progressive Web Apps são aplicativos da Web que são carregados em um navegador da Web, como páginas da Web ou sites. Ele oferece uma experiência móvel rica por meio de funcionalidades nativas, como a capacidade de trabalhar offline, notificações push e acessibilidade de hardware do dispositivo.'
---

## Resumo

O recente avanço da web móvel permitiu recursos que anteriormente eram encontrados apenas em aplicativos desenvolvidos nativamente. Assim, foi necessário um desenvolvimento árduo para várias plataformas ou usando abordagens multiplataforma. O romance abordagem, denominada Progressive Web Apps, pode ser implementada através de um conjunto de conceitos e tecnologias em qualquer site que atende a determinados requisitos.

Palavras-chave: Aplicativos, Web, Navegadores, Tecnologia da Informação.


## Introdução

Neste artigo, defendemos os aplicativos da web progressivos como uma ferramenta possivelmente unificadora
tecnologia para aplicativos da web e aplicativos nativos.

No desenvolvimento de aplicativos móveis tradicionais, a reutilização de código entre aplicativos nativos e web é inexistente. Isso ocorre devido ao código não interoperável dos aplicativos nativos bases, resultando em projetos separados, vários ambientes de desenvolvedor e diferentes sistemas operacionais.

De acordo com Heitkotter et al, existem várias abordagens para o desenvolvimento de multiplataforma. Além disso, há uma infinidade de recursos e documentos técnicos com estruturas para apoiar esse desenvolvimento.
Os exemplos de estruturas populares incluem Ionic Framework, PhoneGap, React Native e Xamarin. Coincidentemente essas estruturas representam três abordagens tecnologicamente distintas.

Diante desses fatos, enquanto a indústria mostra investimento e interesse nesse assunto, destaca-se a falta de pesquisa acadêmica sobre o tema. Desse modo, torna-se evidente que ainda há muitos desafios para o desenvolvimento de aplicativos da web progressivos. Com isso, o presente artigo enaltece alguns dos principais tópicos que englobam esse assunto.

## Conceitos

### Manifesto
O objetivo do arquivo manifesto é expor certas configurações modificáveis, como caminho da imagem do logotipo, nome do aplicativo, splash tela e muito mais. Em suma, o manifesto pode ser usado para modificar o comportamento e o estilo dos aplicativos PWA. Para validar esse manifesto, pode ser utilizada a ferramenta manifest-validator.appspot.com, que utiliza a especificação W3C.

### Agnóstico de framework
Existe uma infinidade de frameworks para desenvolvimento web. Entretanto A Google Web Fundamentals demonstrou ser agnóstica ao uso de um determinado, pois realizou a implementação em três diferentes frameworks.

### Shell do aplicativo
O shell do aplicativo é definido pelo Google como:
> (...) o mínimo de HTML, CSS, e JavaScript alimentando uma interface de usuário.
E destacam três critérios para o shell: rápido tempo de carregamento, cache, e exibição de conteúdo dinâmico.

### Service Workers
Os services workers é responsável pela maior parte do núcleo recursos associados a aplicativos da web progressivos. Um PWA não pode funcionar corretamente em navegadores sem suporte do Service Worker. Ele é registrado na primeira visita de página de um usuário. Consiste em um Arquivo JavaScript que incorpora ganchos de ciclo de vida para negócios lógica e controle de cache. Pode ser usado para lidar com tarefas como sincronização em segundo plano, bem como interceptação de requisições pelo intermédio da rede. 

Se o arquivo do service worker for mais velho que 24 horas, Chrome sempre irá na rede e buscará uma versão nova do arquivo do service worker. Isso é para garantir que os desenvolvedores não implementem acidentalmente um arquivo de service worker "quebrado" ou com bugs que fica preso no navegador para sempre

### Segurança com HTTPS
Por motivos de segurança, HTTPS é necessário para um Service Worker se registrar no navegador e agir de acordo sobre eventos, assim torna-se possível a orquestação, fabricação e filtragem de conexões. 

### SEO
Qualquer aplicativo precisa ter um modelo de engajamento mais profundo para criar histórias de sucesso. É difícil manter o mesmo nível de taxa de engajamento depois que o aplicativo é baixado. Com o tempo de carregamento notavelmente mais rápido, funcionalidade de execução offline, design responsivo, estrutura segura e menor uso de dados, é muito fácil otimizar com palavras-chave necessárias para colher os benefícios de uma presença online. Para realizar testes de SEO, performance, melhores práticas e acessibilidade deve-se utilizar o Lighthouse, disponível nas opções de ferramentas do desenvolvedor.

## Unificação das experiências web e mobile

Uma diferença evidente entre aplicativos da web e aplicativos móveis comuns é sua explorabilidade. Um aplicativo comum requer pesquisa e instalação por meio de um mercado de aplicativos. Os aplicativos da web progressivos permitem o melhor de ambas abordagens, onde os usuários finais podem facilmente experimentar um
aplicativo por meio do navegador da Web e, em seguida, escolher instalá-lo por meio de um pop-up "Adicionar à tela inicial".

## Tabela de comparação 

|  | Aplicativo nativo | Aplicativo web normal | PWA | 
|----|----|----|----|
| **Instalação** | Necessário ir até AppStore ou PlayStore | Instalação não necessária | Apenas clicar no botão de adicionar à página inicial (apenas em Android) |
| **Atualização** | Necessário ir até a loja e submeter o download | Instantâneo | Instantâneo |
| **Tamanho** | Médio/Grande | Pequeno e rápido | Pequeno e rápido |
| **Acesso Offline** | Disponível | Indisponível | Necessário usar o aplicativo uma vez previamente online para conseguir acessar o cache |
| **Experiência do usuário** | Excelente quando bem projetado | Confuso por causa dos menus duplos | Confuso por causa dos menus duplos |
| **Notificação Push** | Disponível porém necessário trabalhar intervenção da loja de aplicativos | Indisponível | Disponível |

## Caso de sucesso

O case de sucesso mais famoso dos Progressive Web Apps é o do Flipkart, que é o maior e-commerce da India. A experiência na construção do Flipkart Lite (que é a versão PWA do aplicativo) resultou em um aumento de 70% em conversões de vendas. Além disso, o Flipkart Lite teve outros números impressionantes, aumentando o tempo de permanência dos usuários em 3 vezes, 40% maior engajamento e consumo de dados quase 3 vezes menor.

## Desvantagens

Os PWAs ainda não tem o controle total sobre o hardware do device. Além disso, o uso de cache não é desenvolvido da melhor maneira pelos desenvolvedores. Outro ponto a ser destacado é que apesar de Google, Microsoft e Mozilla estarem apostando alto nos PWAs, a Apple ainda não está. Ainda existem duas features importantes não suportadas pelo Safari: push notifications e funcionamento offline.

## Conclusão

A indústria está investindo recursos em web apps (PWA) juntamente com materiais didáticos. Entretanto a falta de envolvimento acadêmico denota uma significativa lacuna de conhecimento, mas ao mesmo tempo oferece potencial de pesquisa. 

O estado atual dos aplicativos da web progressivos envolve a falta de certas APIs e recursos de hardware e plataforma que apenas (certos) aplicativos nativos e de plataforma cruzada podem acessar. Os recentes avanços do navegador foram forças de unificação para a experiência do aplicativo do usuário final, incluindo, mas não limitado a, aplicativos da Web instaláveis ​​e com aparência nativa por meio de PWAs.

Portanto, há muito potencial para os PWAs tornar-se um unificador para o desenvolvimento nativo da web sem
o uso de frameworks multiplataforma. Como usuário final, o processo de instalação do PWA se torna mais semelhante para aplicativos regulares por meio de novos avanços nos aspectos da experiência do usuário.

## Referências Bibliográficas

- HUME, DEAN. A BIG list of Progressive Web App tips & tricks. Personal Blog Dean Hume. Disponível em:<https://deanhume.com/a-big-list-of-progressive-web-app-tips/> Acesso em 02 ago. 2020.
- Biørn-Hansen, Andreas & Majchrzak, Tim A. & Grønli, Tor-Morten. (2017). Progressive Web Apps: The Possible Web-native Unifier for Mobile Development. 344-351. 10.5220/0006353703440351. 
- Tandel, Sayali & Jamadar, Abhishek. (2018). Impact of Progressive Web Apps on Web App Development. 10.15680/IJIRSET.2018.0709021.