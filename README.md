# Teste MQTT

Esse aplicativo é destinado a testes de conectividade do RabbitMQ com o protocolo MQTT
Nesse estágio, é necessário fazer um _port-fowared_ do _kubernetes_ para funcionamento.

## Configuração de Pod e Service

Na pasta `k8s` está disponibilizado o arquivo yaml para a construção do _service_ e _pod_ 
do RabbitMQ com suporte ao MQTT.

### Port Forward

Está exposto em forma de _service_ as seguintes portas:

|Protocolo|Porta|Descrição|
|:--------|:----|:--------|
|amqp|5672|Comunicação AMQP|
|http|15672|Manager Web|
|http/web-mqtt|15675|Websocket MQTT|
|mqtt|1883|Fila MQTT|

Para fazer o acesso a cada porta, via _port-forward_ do _kubernetes_, rode o seguinte comando:

`kubectl port-forward service/rabbitmq <port>`

#### Exemplos

 - `kubectl port-forward service/rabbitmq 15672`
 - `kubectl port-forward service/rabbitmq 1883`