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
O objetivo do projeto é fazer com que o rastro da movimentação da tartaruga forme um quadrado. <br>
A função principal do código é a que faz a movimentação da tartaruga, sendo ela: <br>
    `def move_turtle(self):`<br>
Ela comporta blocos iguais que permitem a movimentação da tartaruga, sendo eles: <br>
        `self.twist_msg_.linear.x = 2.0
        self.twist_msg_.angular.z = 0.0
        self.publisher_.publish(self.twist_msg_)
        time.sleep(2.0)` <br>
Este bloco é responsável pela regulação da velocidade linear. Quando a velocidade linear possui um valor, a tartaruga se movimenta de forma retílinea. Nesse caso, como está positivo no eixo x, ela se movimentará inicialmente para a direita. <br>
E o outro bloco: <br> 
`    self.twist_msg_.linear.x = 0.0
        self.twist_msg_.angular.z = 1.57
        self.publisher_.publish(self.twist_msg_)
        time.sleep(2.0)`
Este bloco é responsável pela regulação da velocidade angular da tartaruga, ou seja, faz com que ela mude o ângulo que está andando. Para atingir o objetivo do projeto, é necessário que ela se movimente em 90º 3 vezes. Para isso, transforma-se o ângulo de 90 graus em radianos, para que possa ser utilizado como valor no código. Para encontrarmos o valor de 90º em radianos, multiplica-se esse número por pi e divide-se o resultado por 180, obtendo, assim, 1.57 (valor utilizado no código).<br>
Para a tartaruga formar o quadrado, é necessário repetir o movimento linear 4 vezes e o angular 3 vezes, de maneira intercalada. Após isso, para impedir com que a tartaruga se movimente, utilizamos o comando da biblioteca time: <br>
`self.timer_.cancel()` <br>
Já era! agora é só diversão.
