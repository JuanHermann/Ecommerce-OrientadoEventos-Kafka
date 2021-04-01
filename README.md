# Ecommerce-OrientadoEventos-Kafka
Projeto e-commerce com a arquitetura de microsserviços, orientação de eventos com Apache Kafka e compatibilidade entre a comunicação dos microsserviços com Schema Registry.


Esse projeto foi desenvolvido juntamente com o professor @hatanakadaniel em uma aula da Digital Innovation One. Além das tecnologias já citadas nós utilizamos o Spring e Docker para acelerar o desenvolvimento da aplicação e o Apache Avro que serve como um sistema de serialização de dados, e também o Schema Registry.

O funcionamento do projeto consiste em 3 partes, primeiramente temos o ecommerce-checkout-frontend que é onde inserimos as informações do pagamento que são enviadas para a segunda parte que é o ecommerce-checkout-api, na qual vai inserir as informações do pagamento do banco e gerar uma mensagem administrada pelo krafka, essa mensagem fica na fila para que nosso terceiro serviço, ecommerce-payment-api, receba a mesma para executar o pagamento com os dados do banco e gerar outra mensagem com o resultado da execução.

Um ótimo exemplo de vantagem em utilizar um serviço com mensageria são as empresas que no tempo de black friday possuem muito mais fluxo de compra do que o normal e precisam que os servidores aguentem a nova sobrecarga, com a mensageria fica muito mais facil de escalor no serviço de checkout para que não trave nessa parte. Como o serviço de mensageria é assincrono, podemos manter o servidor de payment para que ele trabalhe conforme a fila criada pelos varios microsserviços de checkout.
