# TRABALHO PRÁTICO - Interconectividade 4.0
ENGENHARIA DE CONTROLE E AUTOMAÇÃO

### OBSERVAÇÕES IMPORTANTES
- O trabalho será individual.
- O projeto entregue antecipadamente terá bonificação de 1% por dia completo de antecipação.
- O projeto entregue atrasado terá a nota geral reduzida em 1% por dia completo de atraso.
- Cada item será considerado realizado com a sua respectiva demonstração no vídeo gravado.
- Utilize o Discord para tirar suas dúvidas.
- Plágios serão anulados.
---

## CONTEXTO

Você foi contratado para implantar uma rede de supervisão de controle para acionamento de chaves comutadoras de energia elétrica. Na fase de projeto, você deverá apresentar um relatório com a divisão lógica do projeto, organizada de forma simplificada em etapas.
Existe uma central de controle em ES. A rede industrial deverá ser implementada em uma IDMZ (Industrial DMZ). Existem 3 plantas locais, que estão em um raio de 5 km². Essas plantas já operam com redes fielbus, mas será necessário ajustar e montar uma integração vertical do chão de fábrica até a rede corporativa. 
A rede de supervisão e gestão de fábrica deverá ficar em uma DMZ de sistemas interna à IDMZ, e apenas o tráfego autorizado entre esta DMZ de sistemas e a rede corporativa deve ser permitido. Além disso, nessa DMZ ficará o acesso remoto da equipe, e uma rede para este fim deve ser aprovisionada com o devido acesso às redes de controle.
Nas redes de controle, cada planta deve estar isolada das demais, provendo conectividade ao respectivo CLP de operação e ao supervisório de forma segura e controlada. Remotamente, a este ambiente, existem outras duas plantas conectadas diretamente à sede que fazem operação remota de chaves de comutação. É necessário prover a conexão segura entre os CLPs remotos e os sistemas locais da sede.
Todos os switches devem ser interconectados de forma a prover pelo menos redundância a 1 falha de link na rede em L2, utilizando convergência rápida. Na DMZ, um switch Ethernet central integra as conexões e conecta os servidores que hospedam os serviços de apoio à produção e supervisão em 2 redes. Cada uma dessas redes precisa suportar pelo menos 40 serviços com endereços diferentes. Não há a necessidade de NAT, pois a rede é totalmente privativa. A redundância da rede deve operar com baixíssimo tempo de recuperação, em L2 (ver Rapid STP).
---

# DEMANDAS IMPLEMENTADAS NO PACKET TRACER
### 1. Montagem da infraestrutura (10%)
- Faça um desenho esquemático e indique a associação de blocos IP e de cada enlace. Identifique todos os equipamentos: Switches Ethernet, Firewalls, Roteadores, Servidores e CLPs, conforme a descrição acima (O esquemático do Packet Tracer pode ser utilizado).
- Destaque cada domínio de broadcast, onde haverá uma rede lógica, e indique a quantidade de dispositivos prevista.
- Implemente a topologia no Packet Tracer, conecte todos os equipamentos necessários para interligar o Supervisório até os CLPs, além de ilustrar os computadores de operadores e usuários.
- Posicione corretamente os switches e respectivas VLANs, roteadores e firewalls necessários.

### 2. Conectividade IP (20%)
- Faça um projeto de endereçamento IPv4 para a solução. Justifique a escolha do bloco.
- Utilize roteamento dinâmico no núcleo da rede. No acesso, utilize anel em L2, quando necessário.
- Implemente a configuração na topologia e verifique a conectividade total entre todos os equipamentos com IP, ou pelo menos com os principais em cada domínio de broadcast, e respectivas VLANs.
- Configure autoconfiguração IPv4 e IPv6 em todas as LANs.

### 3. Plano de conectividade IPv6 (15% - EXTRA)
- Apresente um plano de conectividade com a descrição das VLANs, blocos IP e modificações necessárias para implementação da rede do item 2 em IPv6.

### 4. Política de segurança (15%)
- Configure no Packet Tracer, na referida topologia, uma política de segurança.
- Identifique o posicionamento e o tipo de firewall que será usado. Liste as principais regras de filtragem previstas em cada um desses firewalls.
- Implemente uma DMZ para o supervisório separada da DMZ de serviços de TI.
- Na DMZ de TI, habilite um servidor Web e permita que acessos de uma rede externa e das redes à DMZ interna à IDMZ sejam realizados, a fim de prover acesso aos dados de supervisão ao sistema de gestão da empresa.
- Na DMZ de TO, permita o acesso Web ao supervisório apenas para a rede de operadores. Ainda nesta DMZ, permita que apenas a DMZ de TO acesse a rede interna de operações onde estão os CLPs.
- Usuários na rede de TI não podem ter acesso à DMZ de operações.

### 5. Prática de Socket (15%)
- Implemente um comando de supervisão que acione um equipamento utilizando um Socket Python template disponível no Packet Tracer.
- Esse acionamento deve ser liberado no firewall utilizando uma porta TCP escolhida pelo grupo.
- Deve ser implementado o sensoriamento e a atuação de uma variável analógica e uma digital, pelo menos. (Utilize os elementos de IoT do Packet Tracer)

### 6. Apresentação (40%)
- Agende um horário com o professor para apresentação e arguição do trabalho implementado.
