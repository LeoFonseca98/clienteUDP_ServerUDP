# Cliente e Servidor UDP - Comunicação Básica

Este projeto demonstra a comunicação básica entre um **cliente** e um **servidor** usando o protocolo **UDP**, como parte da aula de **Segurança da Informação** da **DIO (Digital Innovation One)**.

## Como Funciona

- **Cliente**: Envia uma mensagem para o servidor e aguarda a resposta.
- **Servidor**: Recebe a mensagem do cliente e envia uma resposta de volta.

## Código

### Cliente (`clienteUDP.py`)

```python
import socket

s = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)

print('Cliente Socket criado com sucesso!')

host = 'localhost'
porta = 5433
mensagem = 'Ola Servidor!'

try:
    print('Cliente: ' + mensagem)
    s.sendto(mensagem.encode(), (host, 5432))

    dados, servidor = s.recvfrom(4096)
    dados = dados.decode()
    print('Cliente: ' + dados)
finally:
    print('Cliente: Fechando a conexão')
    s.close()
Servidor (servidorUDP.py)
python
Copiar código
import socket

s = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)

print('Socket Criado com Sucesso!')

host = 'localhost'
port = 5432

s.bind((host, port))
mensagem = '\n Servidor: Olá Cliente e aí?'

while 1:
    dados, end = s.recvfrom(4096)

    if dados:
        print('Servidor enviando mensagem...')
        s.sendto(dados + (mensagem.encode()), end)
Como Rodar
Execute o servidor:

bash
Copiar código
python servidorUDP.py
Execute o cliente:

bash
Copiar código
python clienteUDP.py
O cliente envia uma mensagem ao servidor, que responde de volta, e a conexão é encerrada.

Conclusão
Este código ilustra uma comunicação simples usando UDP, onde o cliente envia uma mensagem e o servidor responde. É uma demonstração de como funciona a troca de dados em redes, abordando conceitos básicos de Sockets e Segurança da Informação.

arduino
Copiar código

Esse **README** é direto ao ponto, explicando rapidamente o funcionamento do projeto e o código, com instruções claras para executar tanto o servidor quanto o cliente.





