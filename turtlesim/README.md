# Turtlesim: simulando um ambiente robótico integrado no ROS
Para esta atividade, espera-se a capacidade demonstrável de interagir com o sistema operacional de robôs, criando um nó de comunicação com uma solução pré-existente. A entrega deve ser um vídeo demonstrando o funcionamento do projeto, um texto conciso descrevendo como foi feita a implementação e o link para o repositório público no github onde foi feita a implementação. O enunciado da atividade encontra-se no link anexado ao card.
## Dependências
Os primeiros passos são a instalação do WSL (Windows Subsystem for Linux) que permite a utilização do Linux nativamente no Windows, e o ROS (Robot Operating System) que é uma plataforma de desenvolvimento de software. <br>
É necessário fazer a instalação do arquivo que comporta todas as outras dependências que permitem o funcionamento correto do código utilizando o seguinte comando no terminal com o diretório correto aberto: <br>
`pip install -r requirements` <br>
## Procedimentos para a execução do código
É necessário a abertura de 2 terminais (pode-se utilizar o terminator para isso) ou 2 guias caso esteja utilizando o terminal do windows, como foi utilizado nos testes deste projeto. <br>
Em um dos terminais, deve-se executar a linha de comando: <br>
`ros2 run turtlesim turtlesim_node` <br>
Já no outro: <br>
`python3 main.py`<br>
Espera-se obter a simulação como resultado.
## Entendimento do código
Para esse projeto, utilizamos os conceitos de node, tópico e publisher. <br>
No código é criado primeiramente um node Turtle Controller, e criamos um objeto publisher que publica mensagens twist (que fazem a movimentação linear e angular) no tópico 'turtle1/cmd_vel'.
O objetivo do projeto é fazer com que o rastro da movimentação da tartaruga forme um triângulo de cabeça pra baixo dentro de um triângulo maior. <br>
Para conseguir implementar, é necessário dividir o código em 2 partes, de movimentação e rotação do ângulo. A movimentação escolhida foi de valor 2.0 no linear. Já os ângulos foram escolhidos para conseguir modelar o formato desejado. Basta transformar o valor dos graus em radianos. Após isso, para impedir com que a tartaruga se movimente, utilizamos o comando da biblioteca time: <br>
`self.timer_.cancel()` <br>
Já era! agora é só diversão.
