# Template Editor

Este projeto fornece uma interface para gerar templates JSON para a configuração de serviços.

## Visão Geral

O Template Editor é uma aplicação web simples que permite aos usuários inserir várias URLs e gerar um arquivo JSON com base nessas entradas. O HTML e o CSS fornecem uma interface limpa e responsiva.

## Como Usar

1. Clone este repositório:
    ```sh
    git clone https://github.com/luiis716/Template-Evolution.git
    ```
2. Abra o arquivo `gerador evo2.html` em um navegador web para acessar o Template Editor.

## Estrutura do Projeto

O projeto consiste em um único arquivo HTML que contém todo o código necessário para a interface do usuário.

### Código HTML

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Template Editor</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            min-height: 100vh;
            background-color: #f5f5f5;
        }
        h1 {
            text-align: center;
            margin-bottom: 20px;
        }
        form {
            display: flex;
            flex-direction: column;
            align-items: center;
            width: 100%;
            max-width: 600px;
            padding: 20px;
            background: #fff;
            box-shadow: 0 0 10px rgba(0,0,0,0.1);
            border-radius: 8px;
        }
        .col-3 {
            position: relative;
            width: 100%;
            margin: 10px 0;
        }
        .effect-21 {
            border: 0;
            padding: 7px 0;
            border-bottom: 1px solid #ccc;
            width: 100%;
            box-sizing: border-box;
            font-size: 18px;
        }
        .effect-21 ~ .focus-border:before,
        .effect-21 ~ .focus-border:after {
            content: "";
            position: absolute;
            top: 0;
            right: 0;
            width: 0;
            height: 2px;
            background-color: #3399FF;
            transition: 0.2s;
            transition-delay: 0.2s;
        }
        .effect-21 ~ .focus-border:after {
            top: auto;
            bottom: 0;
            right: auto;
            left: 0;
            transition-delay: 0.6s;
        }
        .effect-21 ~ .focus-border i:before,
        .effect-21 ~ .focus-border i:after {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            width: 2px;
            height: 0;
            background-color: #3399FF;
            transition: 0.2s;
        }
        .effect-21 ~ .focus-border i:after {
            left: auto;
            right: 0;
            top: auto;
            bottom: 0;
            transition-delay: 0.4s;
        }
        .effect-21:focus ~ .focus-border:before,
        .effect-21:focus ~ .focus-border:after,
        .has-content.effect-21 ~ .focus-border:before,
        .has-content.effect-21 ~ .focus-border:after {
            width: 100%;
            transition: 0.2s;
            transition-delay: 0.6s;
        }
        .effect-21:focus ~ .focus-border:after,
        .has-content.effect-21 ~ .focus-border:after {
            transition-delay: 0.2s;
        }
        .effect-21:focus ~ .focus-border i:before,
        .effect-21:focus ~ .focus-border i:after,
        .has-content.effect-21 ~ .focus-border i:before,
        .has-content.effect-21 ~ .focus-border i:after {
            height: 100%;
            transition: 0.2s;
        }
        .effect-21:focus ~ .focus-border i:after,
        .has-content.effect-21 ~ .focus-border i:after {
            transition-delay: 0.4s;
        }
        .effect-21 ~ label {
            position: absolute;
            left: 0;
            top: -18px;
            font-size: 12px;
            color: #3399FF;
            transition: 0.3s;
            z-index: 1;
            pointer-events: none;
        }
        .button {
            --background: #275efe;
            --rectangle: #184fee;
            --success: #4BC793;
            --text: #fff;
            --arrow: #fff;
            --checkmark: #fff;
            --shadow: rgba(10, 22, 50, .24);
            display: flex;
            justify-content: center;
            align-items: center;
            margin-top: 20px;
            padding: 10px 20px;
            text-decoration: none;
            background: var(--background);
            border-radius: 8px;
            box-shadow: 0 2px 8px -1px var(--shadow);
            transition: transform .2s ease, box-shadow .2s ease;
        }
        .button:active {
            transform: scale(.95);
            box-shadow: 0 1px 4px -1px var(--shadow);
        }
        .button span {
            color: var(--text);
            font-size: 16px;
            font-weight: 500;
        }
        .link-dica {
            margin-top: 10px;
            font-size: 14px;
            text-align: center;
        }
        .link-dica a {
            color: #275efe;
            text-decoration: none;
        }
        .link-dica a:hover {
            text-decoration: underline;
        }
    </style>
</head>
<body>
    <h1>Template Editor</h1>
    <form id="templateForm">
        <div class="col-3 input-effect">
            <input class="effect-21" type="text" id="input1" required placeholder="">
            <label>Imagem</label>
            <span class="focus-border">
                <i></i>
            </span>
        </div>
        <div class="link-dica">
            <a href="https://hub.docker.com/r/atendai/evolution-api/tags" target="_blank">Veja a última versão no Docker Hub</a>
        </div>
        <div class="col-3 input-effect">
            <input class="effect-21" type="text" id="input2" required placeholder="">
            <label>Domínio</label>
            <span class="focus-border">
                <i></i>
            </span>
        </div>
        <div class="col-3 input-effect">
            <input class="effect-21" type="text" id="input3" required placeholder="">
            <label>URL Conexão Postgres</label>
            <span class="focus-border">
                <i></i>
            </span>
        </div>
        <div class="col-3 input-effect">
            <input class="effect-21" type="text" id="input4" required placeholder="">
            <label>URL Conexão Redis</label>
            <span class="focus-border">
                <i></i>
            </span>
        </div>
        <div class="col-3 input-effect">
            <input class="effect-21" type="text" id="input5" placeholder="">
            <label>URL Postgres Chatwoot</label>
            <span class="focus-border">
                <i></i>
            </span>
        </div>
        <div class="col-3 input-effect">
            <input class="effect-21" type="text" id="input6" placeholder="">
            <label>URL S3</label>
            <span class="focus-border">
                <i></i>
            </span>
        </div>
        <a href="" class="button" onclick="generateJSON(event)">
            <span>Tudo Ok</span>
        </a>
    </form>

    <script>
        function generateJSON(event) {
            event.preventDefault();

            const input1 = document.getElementById('input1').value;
            const input2 = document.getElementById('input2').value;
            const input3 = document.getElementById('input3').value;
            const input4 = document.getElementById('input4').value;
            const input5 = document.getElementById('input5').value;
            const input6 = document.getElementById('input6').value;

            if (!input1 || !input2 || !input3 || !input4) {
                alert('Por favor, preencha todos os campos obrigatórios.');
                return;
            }

            const envString = `
                SERVER_URL=${input2}
                DEL_INSTANCE=false
                DEL_TEMP_INSTANCES=false
                PROVIDER_ENABLED=false
                PROVIDER_HOST=127.0.0.1
                PROVIDER_PORT=5656
                PROVIDER_PREFIX=evolution_v2
                DATABASE_ENABLED=true
                DATABASE_PROVIDER=postgresql
                DATABASE_CONNECTION_URI=${input3}
                DATABASE_CONNECTION_CLIENT_NAME=evolution_v2
                CACHE_REDIS_ENABLED=true
                CACHE_REDIS_URI=${input4}
                CACHE_REDIS_PREFIX_KEY=evolution_v2
                CACHE_REDIS_SAVE_INSTANCES=false
                CACHE_LOCAL_ENABLED=false
                S3_ENABLED=false
                S3_ACCESS_KEY=
                S3_SECRET_KEY=
                RABBITMQ_ENABLED=false
                RABBITMQ_URI=amqp://admin:admin@rabbitmq:5672/default
                RABBITMQ_EXCHANGE_NAME=evolution_v2
                RABBITMQ_GLOBAL_ENABLED=false
                RABBITMQ_EVENTS_APPLICATION_STARTUP=false
                RABBITMQ_EVENTS_INSTANCE_CREATE=false
                RABBITMQ_EVENTS_INSTANCE_DELETE=false
                RABBITMQ_EVENTS_QRCODE_UPDATED=false
                RABBITMQ_EVENTS_MESSAGES_SET=false
                RABBITMQ_EVENTS_MESSAGES_UPSERT=true
                RABBITMQ_EVENTS_MESSAGES_EDITED=false
                RABBITMQ_EVENTS_MESSAGES_UPDATE=false
                RABBITMQ_EVENTS_MESSAGES_DELETE=false
                RABBITMQ_EVENTS_SEND_MESSAGE=false
                RABBITMQ_EVENTS_CONTACTS_SET=false
                RABBITMQ_EVENTS_CONTACTS_UPSERT=false
                RABBITMQ_EVENTS_CONTACTS_UPDATE=false
                RABBITMQ_EVENTS_PRESENCE_UPDATE=false
                RABBITMQ_EVENTS_CHATS_SET=false
                RABBITMQ_EVENTS_CHATS_UPSERT=false
                RABBITMQ_EVENTS_CHATS_UPDATE=false
                RABBITMQ_EVENTS_CHATS_DELETE=false
                RABBITMQ_EVENTS_GROUPS_UPSERT=false
                RABBITMQ_EVENTS_GROUP_UPDATE=false
                RABBITMQ_EVENTS_GROUP_PARTICIPANTS_UPDATE=false
                RABBITMQ_EVENTS_CONNECTION_UPDATE=true
                RABBITMQ_EVENTS_CALL=false
                RABBITMQ_EVENTS_TYPEBOT_START=false
                RABBITMQ_EVENTS_TYPEBOT_CHANGE_STATUS=false
                SQS_ENABLED=false
                SQS_ACCESS_KEY_ID=
                SQS_SECRET_ACCESS_KEY=
                SQS_ACCOUNT_ID=
                SQS_REGION=
                WEBSOCKET_ENABLED=false
                WEBSOCKET_GLOBAL_EVENTS=false
                WA_BUSINESS_TOKEN_WEBHOOK=evolution
                WA_BUSINESS_URL=https://graph.facebook.com
                WA_BUSINESS_VERSION=v20.0
                WA_BUSINESS_LANGUAGE=pt_BR
                WEBHOOK_GLOBAL_URL=''
                WEBHOOK_GLOBAL_ENABLED=false
                WEBHOOK_GLOBAL_WEBHOOK_BY_EVENTS=false
                WEBHOOK_EVENTS_APPLICATION_STARTUP=false
                WEBHOOK_EVENTS_QRCODE_UPDATED=true
                WEBHOOK_EVENTS_MESSAGES_SET=true
                WEBHOOK_EVENTS_MESSAGES_UPSERT=true
                WEBHOOK_EVENTS_MESSAGES_EDITED=true
                WEBHOOK_EVENTS_MESSAGES_UPDATE=true
                WEBHOOK_EVENTS_MESSAGES_DELETE=true
                WEBHOOK_EVENTS_SEND_MESSAGE=true
                WEBHOOK_EVENTS_CONTACTS_SET=true
                WEBHOOK_EVENTS_CONTACTS_UPSERT=true
                WEBHOOK_EVENTS_CONTACTS_UPDATE=true
                WEBHOOK_EVENTS_PRESENCE_UPDATE=true
                WEBHOOK_EVENTS_CHATS_SET=true
                WEBHOOK_EVENTS_CHATS_UPSERT=true
                WEBHOOK_EVENTS_CHATS_UPDATE=true
                WEBHOOK_EVENTS_CHATS_DELETE=true
                WEBHOOK_EVENTS_GROUPS_UPSERT=true
                WEBHOOK_EVENTS_GROUPS_UPDATE=true
                WEBHOOK_EVENTS_GROUP_PARTICIPANTS_UPDATE=true
                WEBHOOK_EVENTS_CONNECTION_UPDATE=true
                WEBHOOK_EVENTS_LABELS_EDIT=true
                WEBHOOK_EVENTS_LABELS_ASSOCIATION=true
                WEBHOOK_EVENTS_CALL=true
                WEBHOOK_EVENTS_TYPEBOT_START=false
                WEBHOOK_EVENTS_TYPEBOT_CHANGE_STATUS=false
                WEBHOOK_EVENTS_ERRORS=false
                WEBHOOK_EVENTS_ERRORS_WEBHOOK=
                CONFIG_SESSION_PHONE_CLIENT=Evolution API V2
                CONFIG_SESSION_PHONE_NAME=Chrome
                CONFIG_SESSION_PHONE_VERSION=2.2413.51
                QRCODE_LIMIT=30
                TYPEBOT_ENABLED=false
                TYPEBOT_API_VERSION=latest
                CHATWOOT_ENABLED=false
                CHATWOOT_MESSAGE_READ=true
                CHATWOOT_IMPORT_DATABASE_CONNECTION_URI=${input5 ? `${input5}?sslmode=disable` : ''}
                CHATWOOT_IMPORT_PLACEHOLDER_MEDIA_MESSAGE=true
                S3_BUCKET=evolution
                S3_PORT=443
                S3_ENDPOINT=${input6 ? input6 : ''}
                S3_USE_SSL=true
                AUTHENTICATION_API_KEY=429683C4C977415CAAFCCE10F7D57E11
                AUTHENTICATION_EXPOSE_IN_FETCH_INSTANCES=true
                LANGUAGE=pt_BR
            `.replace(/^\s+|\s+$/gm, '');

            const jsonTemplate = {
                "services": [
                    {
                        "type": "app",
                        "data": {
                            "projectName": "evolution",
                            "serviceName": "evolution",
                            "source": {
                                "type": "image",
                                "image": input1
                            },
                            "domains": [
                                {
                                    "host": "$(EASYPANEL_DOMAIN)",
                                    "port": 8080
                                }
                            ],
                            "env": envString,
                            "mounts": [
                                {
                                    "type": "volume",
                                    "name": "evolution_instances",
                                    "mountPath": "/evolution/instances"
                                }
                            ]
                        }
                    }
                ]
            };

            if (!input5) {
                delete jsonTemplate.services[0].data.env["CHATWOOT_IMPORT_DATABASE_CONNECTION_URI"];
            }
            if (!input6) {
                delete jsonTemplate.services[0].data.env["S3_ENDPOINT"];
            }

            const jsonString = JSON.stringify(jsonTemplate, null, 2);
            const blob = new Blob([jsonString], { type: "application/json" });
            const url = URL.createObjectURL(blob);
            const a = document.createElement("a");
            a.href = url;
            a.download = "template.json";
            a.click();
            URL.revokeObjectURL(url);
        }
    </script>
</body>
</html>
