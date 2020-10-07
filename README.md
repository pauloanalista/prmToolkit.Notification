# prmToolkit

# Notification
Classe responsável por validar argumentos, sem levantar exceções, com ela é possível adicionar mensagens em várias camadas do projeto e obter essas notificações de forma centralizada. Também é possível saber se a requisição é válida.

OBS: A classe trabalha de forma estática, ou seja, se tiver várias sessões utilizando a classe, poderá ter problemas de ter notificações de outros usuários.

Recomendo o uso da prmToolkit.NotificationPattern ou prmToolkit.ArgumentsValidator

### Installation - Notification

Para instalar, abra o prompt de comando Package Manager Console do seu Visual Studio e digite o comando abaixo:

Para adicionar somente a referencia a dll
```sh
Install-Package prmToolkit.Notification
```

Para adicionar somente as classes
```sh
Install-Package prmToolkit.Notification-Source
```
### Exemplo de como usar

```sh
            //Iniciar o monitoramento das mensagens, normalmente ficara em um base da controller da api
            NotificationManager.Start();

            //Validacoes que irao ocorrer em várias camadas do sistema
            string nome = string.Empty;
            int idade = 35;
            string variavel = "123455";

            //Camada de serviços de aplicacao
            //O último parametro é opcional, ele pega o nome do método que está executando a validação automaticamente, caso queira 
            //customizar o nome, é só informar no parametro
            AddNotification.IfEmpty(nome, "Nome é obrigatório", "Nome do método que está executando a validação");

            //Camada de serviços (Dominio)
            AddNotification.IfNotGreaterThan(idade, 100, "Idade deve ser maior que 100");

            //Camada de infra
            AddNotification.IfNotGuid(variavel, "Nao é um guid válido");

            //Verifica se todas as validações estão de válidas
            bool valid = NotificationManager.IsValid();

            //Obtém a lista de mensagens para apresentar para o usuário
            var lista = NotificationManager.GetNotifications();

            //Limpa lista de notificações, usado quando você finaliza seu request
            NotificationManager.End();

       
```

# VEJA TAMBÉM
## Grupo de Estudo no Telegram
- [Participe gratuitamente do grupo de estudo](https://t.me/blogilovecode)

## Cursos baratos!
- [Meus cursos](https://olha.la/udemy)

## Fique ligado, acesse!
- [Blog ILoveCode](https://ilovecode.com.br)

## Novidades, cupons de descontos e cursos gratuitos
https://olha.la/ilovecode-receber-cupons-novidades
