# Websocket
F5HLIVE Real-Time WebSocket API SDKs, integrations and examples compatible with the Pusher protocol.  
Includes SDK examples for PHP, Node.js, Next.js, React, Vue, SSE, SockJS and real-time event broadcasting. 
<br>
Built for scalable real-time applications, notifications, live updates, presence channels and WebSocket communication.

# F5HLIVE Realtime API

Realtime multiprotocolo compatível com WebSocket, SockJS, SSE, XHR Streaming e Polling.

Uma infraestrutura desenvolvida para comunicação em tempo real com fallback automático, múltiplos protocolos integrados e compatibilidade com o ecossistema Pusher.

<br>

## 🚀 O que é a F5HLIVE Realtime API?

A F5HLIVE é uma plataforma realtime desenvolvida para entregar comunicação instantânea entre aplicações, navegadores, APIs, sistemas backend e dispositivos conectados.

A plataforma permite criar:

* Chats em tempo real
* Notificações instantâneas
* Atualizações ao vivo
* Sistemas interativos
* Streams de dados
* Comunicação entre aplicações

Tudo isso com baixa latência, fallback automático e alta compatibilidade.

<br>

## ⚡ Diferenciais da plataforma

Diferente de soluções tradicionais focadas apenas em WebSocket, a F5HLIVE trabalha com uma arquitetura multiprotocolo unificada.

Todos os protocolos conseguem se comunicar entre si automaticamente.

Exemplos:

```text
WebSocket envia  → SSE recebe
SSE envia        → SockJS recebe
XHR envia        → WebSocket recebe
HTTP envia       → HTTPS recebe
```

O modo de conexão é irrelevante para a entrega dos eventos.

<br>

## 🌐 Protocolos suportados

| Protocolo     | Descrição                                |
| ------------- | ---------------------------------------- |
| WS / WSS      | WebSocket puro com baixa latência        |
| SockJS        | Compatibilidade com múltiplos transports |
| SSE           | Server-Sent Events                       |
| XHR Streaming | Streaming HTTP persistente               |
| XHR Polling   | Polling HTTP tradicional                 |
| JSONP Polling | Compatibilidade com ambientes antigos    |

<br>

## 🔄 Fallback automático inteligente

O SDK detecta automaticamente:

* HTTP / HTTPS
* WS / WSS
* Melhor transporte disponível
* Portas corretas
* Fallbacks necessários

Na maioria dos casos, basta informar:

* API Key
* Cluster

Sem necessidade de configurar manualmente:

* host
* porta
* protocolo
* fallback
* transportes

<br>

## 📡 SSE / EventSource Support

A infraestrutura F5HLIVE suporta conexões SSE persistentes com gerenciamento automático de reconexão e distribuição unificada de eventos.

Eventos enviados via WebSocket podem ser recebidos normalmente por clientes conectados via SSE/EventSource.

<br>

## 🔐 Segurança flexível

A plataforma suporta diferentes níveis de autenticação.

### 🔹 Modo simples

Ideal para:

* testes rápidos
* MVPs
* chats simples
* aplicações leves

Utiliza apenas a API Key.

<br>

### 🔹 Modo avançado

Adiciona:

* autenticação HMAC SHA256
* validação de origem/domínio
* assinatura de requisição
* controle de publicação
* autenticação private/presence

Compatível com aplicações enterprise.

<br>

## 🧠 Arquitetura desacoplada

Sua aplicação não precisa manter um servidor WebSocket próprio.

O backend pode continuar simples utilizando apenas requisições HTTP para publicar eventos.

A infraestrutura realtime da F5HLIVE gerencia:

* WebSocket
* SockJS
* SSE
* Polling
* Reconexão
* Fallbacks automáticos
* Comunicação entre protocolos

<br>

## 📦 Compatibilidade

Compatível com:

* JavaScript
* PHP
* Node.js
* React
* Next.js
* Vue
* Vite
* Python
* APIs REST
* Aplicações legadas

<br>

# ⚡ Conexão rápida com JavaScript

```html
<script src="https://sdk.f5hlive.com.br/pusher/8.5.0/pusher.min.js"></script>

<script>

  // Debug apenas em desenvolvimento
  Pusher.logToConsole = true;

  // Cria conexão
  var pusher = new Pusher('SUA_API_KEY', {

    // Cluster da aplicação
    cluster: 'custom'

    /*
      Não é necessário informar:
      - wsHost
      - wsPort
      - forceTLS
      - enabledTransports

      O SDK detecta automaticamente:
      - protocolo
      - portas
      - host
      - melhor transporte
      - fallback necessário
    */

  });

  // Inscreve no canal
  var channel = pusher.subscribe('my-channel');

  // Escuta evento
  channel.bind('my-event', function(data) {

    console.log('Evento recebido:', data);

  });

</script>
```

<br>

# 🔄 Forçando um transporte específico (Opcional)

Em cenários específicos é possível forçar transportes manualmente.

⚠ Recomendado apenas para testes ou ambientes controlados.

```javascript
var pusher = new Pusher('SUA_API_KEY', {

  cluster: 'custom',

  enabledTransports: ['ws']

});
```

Transportes disponíveis:

```text
ws
wss
sockjs
xhr_streaming
xhr_polling
sse
```

<br>

# 📡 Envio de evento com PHP

```php
<?php

$payload = [
    "name"    => "my-event",
    "channel" => "my-channel",
    "data"    => json_encode([
        "message" => "Olá realtime!"
    ])
];

$ch = curl_init();

curl_setopt_array($ch, [

    CURLOPT_URL => "https://api-custom.f5hlive.com.br/apps/SEU_APP_ID/events",

    CURLOPT_POST => true,

    CURLOPT_RETURNTRANSFER => true,

    CURLOPT_HTTPHEADER => [
        "Content-Type: application/json",
        "Authorization: Bearer SUA_API_KEY"
    ],

    CURLOPT_POSTFIELDS => json_encode($payload)

]);

$response = curl_exec($ch);

curl_close($ch);

echo $response;
```

<br>

# 🛰 Estrutura da infraestrutura

```text
WS/WSS
→ ws-cluster

SockJS
→ sockjs-cluster

SSE/EventSource
→ sse-cluster

API/Trigger
→ api-cluster
```

Todos os protocolos são tratados de forma unificada dentro do servidor realtime.

<br>

# 📚 Próximas documentações

Documentações detalhadas e SDKs adicionais serão disponibilizados separadamente:

* JavaScript SDK
* PHP SDK
* Node.js SDK
* Next.js
* Python
* Docker
* SSE
* SockJS
* Eventos privados/presence
* Autenticação avançada
* Exemplos práticos
* Ambientes clusterizados

<br>

# 🎯 Objetivo da plataforma

A F5HLIVE foi desenvolvida para ser:

* simples para integrar
* robusta para escalar
* compatível com múltiplos ambientes
* resiliente em diferentes redes
* preparada para aplicações modernas realtime

<br>

# ✅ Conclusão

A F5HLIVE não é apenas um servidor WebSocket.

É uma infraestrutura realtime multiprotocolo desenvolvida para comunicação instantânea com fallback automático, compatibilidade total entre protocolos e integração simplificada para aplicações modernas.
