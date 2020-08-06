# ID de conversa e do Contato

Green API suporta dois tipos de conversas - [conversas pessoais](#cus) e [conversas em grupo](#gus).
O bate-papo privado é usado para enviar mensagens pessoais ao destinatário. O bate-papo em grupo é usado para organizar a comunicação de vários participantes em um grupo. Para trabalhar com bate-papos em grupo, a Gren API fornece métodos
apropriados. Antes de enviar uma mensagem para um bate-papo particular ou em grupo, é necessário obter um ID de conversa.

## ID do contato {#corr}
O identificador de correspondente é usado para identificar o destinatário nas mensagens enviadas e para identificar o remetente nas mensagens recebidas, bem como em quaisquer outros métodos de API nos quais você deseja identificar o contato. O formato do identificador do contato é o mesmo que o identificador de [bate-papo pessoal](#cus).

## Bate-papo privado {#cus}
O formato do identificador de bate-papo pessoal é formado de acordo com o padrão `00000000000@c.us`, onde, em vez dos zeros de` 00000000000`, é necessário usar o número de telefone do destinatário. O telefone deve ser indicado na íntegra, com o código do país e sem espaços. Por exemplo:

```
5521999997777@c.us
```

## Conversas em grupo {#gus}
O ID do bate-papo em grupo é uma sequência no formato `00000000000-XXXXXXXXXX@g.us`. Por exemplo:

```
5521999997777-1581234048@g.us
```

O ID do bate-papo em grupo pode ser obtido usando vários métodos da Green API, por exemplo:

- [Para criar um Grupo](groups/CreateGroup.md)
- [Obter o log de mensagens enviadas](journals/LastOutgoingMessages.md)
- [Obter log da caixa de entrada](journals/LastIncomingMessages.md)
- [Mensagem recebida: Texto](receiving/notifications-format/incoming-message/TextMessage.md)
- e etc.

> **IMPORTANTE**
>
> ID de bate-papo em grupo **NÃO é obrigatório**. É gerado automaticamente pelo sistema e retornado usando vários métodos da Gren API.
