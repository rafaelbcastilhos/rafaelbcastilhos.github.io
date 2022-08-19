---
title: 'Troca de chaves com TLS utilizando criptografia pós quântica'
path: /troca-chaves-tls-pq
date: 2022-07-28
summary: 'Experimento de algoritmos pós quânticos utilizando o protocolo TLS na troca de chaves.'
---

## Introdução
Desde que se descobriu o potencial de criptoanálise do computador quântico,
especialmente com o algoritmo de Shor, criou-se a idéia de que a criptografia
moderna se tornaria inútil assim que esse tipo de computador começasse a ser
desenvolvido em larga escala. Com isso, todas as mensagens trocadas com o
uso de algoritmos criptográficos atuais seriam facilmente interceptáveis.

Desse modo, a troca de chaves que é um método de criptografia para trocas de chaves de maneira segura em canal público. Entretanto, deixaria de ser pois estaria utilizando um protocolo que poderia ser descriptografado por um computador quântico.

Em resposta a isso, surgiu a criptografia pós-quântica, ramo da criptografia que estuda classes de algoritmos criptográficos resistentes à criptoanálise quântica. Como exemplos de classes de algoritmos, podemos mencionar os baseados em hash, os baseados em látice, os baseados em códigos, entre outros. Estes algoritmos demorariam um tempo exponencial para serem quebrados, mesmo em computadores quânticos.

O TLS (Transport Layer Security) assim como o seu antecessor SSL(Secure Sockets Layer) é um protocolo de segurança projetado para fornecer segurança nas comunicações sobre uma rede de computadores. O protocolo TLS, que atualmente está na versão 1.2, visa principalmente fornecer privacidade e integridade de dados entre dois ou mais aplicativos de computador que se comunicam. Entretanto, com o surgimento da computação quântica, uma nova ameaça ao problemas de segurança surge.

Contextualizado os itens acima, em sequência será apresentado e experimentado a troca de chaves utilizando o protocolo TLS, será utilizado o projeto de código aberto Open Quantum Safe (OQS) que fornece algoritmos finalistas no NIST empacotados na biblioteca liboqs.

## Conceitos

A troca de chave hı́brida refere-se ao uso de vários algoritmos de troca de
chave simultaneamente e à combinação do resultado com o objetivo de forne-
cer segurança, mesmo que todos os algoritmos do componente, exceto um, es-
tejam quebrados. É motivado pela transição para a criptografia pós-quântica.
Denominado como Transport Layer Security (TLS) versão 1.3.

Troca de chave ”hı́brida”, significa o uso de dois, ou mais algoritmos de troca de chave com base em diferentes suposições criptográficas, por exemplo, um algoritmo tradicional e um algoritmo de última geração. O principal objetivo é facilitar o estabelecimento de um segredo compartilhado que permaneça seguro enquanto um dos mecanismos de troca de chave permanecer intacto.

### Encapsulamento
Os algoritmos de troca de chaves são formulados como mecanismos de en-
capsulamento de chaves, sendo eles:
- KeyGen: Geração probabilı́stica, chave pública pk e chave secreta sk.
- Encaps: Encapsulamento probabilı́stico, recebe como entrada uma chave
pk, e gera um texto cifrado ct e segredo compartilhado ss.
- Decaps: Desencapsulamento que recebe como entrada uma chave sk e
texto cifrado ct, gerando um texto compartilhado ss.

### Construção da troca
- Negociação: Para cada combinação particular de algoritmos em um
troca de será representada por um grupo nomeado. Cada valor que
representa uma troca de chave corresponderá a um par ordenado de
dois algoritmos.
- Transmissão: As mensagens serão concatenadas e transmitidas como
um único valor.
- Cálculo de segredo compartilhado: Os dois segredos compartilhados são
concatenados. Inserindo no cronograma de chave no local do segredo
compartilhado (EC)DHE.

A biblioteca liboqs fornece os principais mecanismos para encapsulamento
de chaves, conforme citado no item 2.1, sendo denotadas como:

- OQS KEM keypar: Gera um par de chaves pública/privada para
troca de chaves.
- OQS KEM encaps: Gera uma chave pública para a outra parte e um
segredo compartilhado para o requisitante.
- OQS KEM decaps: Gera um valor secreto compartilhado usando a
chave pública da outra parte e sua própria chave privada.

Aplicando essas funcionalidades da biblioteca, é possı́vel encontrar o seguinte fluxo:

![Fluxograma](https://raw.githubusercontent.com/rafaelbcastilhos/rafaelbcastilhos.github.io/main/post/images/troca-chave-tls-pq-fluxo.png)

## Experimento
O experimento será executado em um notebook com sistema operacional Linux Ubuntu, todos os procedimentos citados a seguir também poderão ser executados em outros sistemas operacionais, porém haverá diferença em alguns comandos que são especiais do Linux. Preambularmente, iremos precisar realizar o download do programa Wireshark que é um programa que analisa o tráfego da rede e organiza por protocolos. Também iremos precisar baixar a biblioteca liboqs e a biblioteca wolfSSL.

### Instalação e construção 

Para baixar o Wireshark é necessário executar:
```
sudo apt-get install wireshark
```
Após instalado, deve ser iniciado, executando o comando:
```
sudo wireshark
```
Para realizar download e construção do liboqs, execute:
```
wget https://github.com/open-quantum-safe/liboqs/archive/refs/tags/0.7.0.tar.gz

tar xf 0.7.0.tar.gz

cd liboqs-0.7.0

mkdir build

cd build

cmake -DOQS_USE_OPENSSL=0 ..

make all

sudo make install
```

Para realizar download e construção do wolfSSL, execute:
```
git clone https://github.com/wolfssl/wolfssl

cd wolfssl

./autogen.sh

./configure --with-liboqs

make all

sudo make install
```

### Execução

Em seguida, vamos estabelecer uma comunicação TLS entre um exemplo de servidor e um exemplo de cliente. Para isso, é necessário abrir duas janelas no terminal, uma para o servidor, outra para o cliente. Nesse momento, certifique-se que o Wireshark está aberto e clique no botão para iniciar captura de pacotes.

Agora é necessário especificar o inı́cio do servidor para troca de chaves
hı́bridas ECC-P521 e Kyber Level 5, em uma janela do terminal:
```
./examples/server/server -v 4 --pqc P521_KYBER_LEVEL5
```
Na outra janela do terminal, execute a conexão do cliente:
```
./examples/client/client -v 4 --pqc P521_KYBER_LEVEL5
```

O servidor e o cliente realizam uma conexão TLS e uma comunicação com mensagem de ida e volta. Cada janela exibe informações de conexão TLS 1.3 com as seguintes mensagens:

![Servidor](https://raw.githubusercontent.com/rafaelbcastilhos/rafaelbcastilhos.github.io/main/post/images/troca-chave-tls-pq-servidor.png)

![Cliente](https://raw.githubusercontent.com/rafaelbcastilhos/rafaelbcastilhos.github.io/main/post/images/troca-chave-tls-pq-cliente.png)

Após realizar a conexão, é possı́vel verificar os pacotes no Wireshark, filtrando apenas os pacotes que utilizam TLS, de acordo com a figura abaixo:

![Wireshark](https://raw.githubusercontent.com/rafaelbcastilhos/rafaelbcastilhos.github.io/main/post/images/troca-chave-tls-pq-wireshark.png)

E também constatar o acontecimento do handshake, Client Hello e Server Hello, na imagem abaixo é demonstrado com detalhes as propriedades do TLS no pacote Server Hello:

![Pacote Wireshark](https://raw.githubusercontent.com/rafaelbcastilhos/rafaelbcastilhos.github.io/main/post/images/troca-chave-tls-pq-pacote.png)

## Análise e conclusões
Portanto, após realizar testes e executar o programa de benchmark disponibilizado pela wolfSSL por meio do comando:
```
./wolfcrypt/benchmark/benchmark
```
Se torna possı́vel constatar que os tempos de processamento desses algoritmos
estão entrando em um intervalo comparável aos algoritmos atuais, mas ainda
não são iguais ou inferiores.

É possı́vel concluir que os segredos compartilhados calculados na troca
de chave hı́brida devem ser calculados de uma maneira que atinja a propriedade ”hı́brida”: o segredo resultante é seguro desde que pelo menos um dos algoritmos de troca de chave componente esteja intacto.

