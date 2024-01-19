# Go Expert - Desfio Clean Architecture
# terceiroDesafioGoExpert

Go | gRPC | graphQL | REST | Wire | MySQL | Docker | Rabbitmq | Evans



### Para executar o projeto sega os seguintes passos:


1. `git clone https://github.com/michelpessoa/terceiroDesafioGoExpert`
2. `go mod tidy` para instalar todas as dependências
3. `docker-compose up` tenho o docker instalado, para iniciar os serviços mysql, evans e rabbitmq
4. `go run main.go wire_gen.go` execute o comando para iniciar os serviços 


### Para testar o serviço REST

1. `abra a pasta api e utilize o httpClient 'create_order.http'`

### Para testar o serviço GraphQL

1. `abra o navegador no endereço 'http://localhost:8080'` para acessar o playground o GraphQL
2. `utilize a mutation 
    'mutation createOrder {
  createOrder (input: {id:"xxx", Price: 100.1, Tax: 1.1}) {    
    id
    Price
    Tax  
    FinalPrice
  }
}'` para criação
3. `utilize a query 
    'query queryOrders {
  listOrders {
    id
    Price
    FinalPrice
    Tax
  }
}'` para listagem das ordens de seviço

### Para testar o serviço gRPC

1. `tenho gRPC Client Evans instalado` [gRPC client - Evans](https://github.com/ktr0731/evans)
2. `evans -r repl` para acessar o client
3. `package pb` para acessar o pacote 
4. `service OrderService` para acessar o serviço
5. `call CreateOrder` para acessar o registro de uma nova ordem de serviço, com inserção dos dados
6. `call ListOrders` para acessar a listagem de ordens registradas

#### Para visualizar as mensagens no RabbitMQ

1. `http://localhost:15672` para acessar o serviço
2. `usuário e senha 'guest'` para logar no serviço 
3. `acesse a aba _Queues_ / _Add a new queue_ / _Name: orders_ / clicar _Add queue_` para cria uma nova queue (fila)
4. `acesse a fila _orders_ / _Bidings_ / _Add binding to this queue_ / _From exchange: amq.direct_ / clicar _Bind_` para criar um bind de recepção
5. `acesse _Get messages_ / clicar _Get Message(s)_` para visualizar as mensagens recebidas, mas antes execute o registro de alguma ordem de serviço. 