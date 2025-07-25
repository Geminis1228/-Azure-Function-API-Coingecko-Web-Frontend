# -Azure-Function-API-Coingecko-Web-Frontend🚀 Consultor de Precios de Criptomonedas
Una aplicación web completa que permite consultar precios en tiempo real de criptomonedas usando Azure Functions y la API de CoinGecko.
📋 Características

🔍 Consulta precios de 8 criptomonedas populares
💱 Precios en USD y MXN
🎨 Interfaz moderna y responsiva
⚡ Respuesta rápida con Azure Functions
🔒 CORS configurado para desarrollo y producción

🛠️ Tecnologías Utilizadas

Frontend: HTML5, CSS3, JavaScript (Vanilla)
Backend: Azure Functions con Python 3.9+
API: CoinGecko API v3
Despliegue: Azure Function App

📁 Estructura del Proyecto
crypto-price-app/
├── frontend/
│   └── index.html              # Aplicación web completa
├── azure-function/
│   ├── GetCryptoPrice/
│   │   ├── __init__.py         # Función principal
│   │   └── function.json       # Configuración de binding
│   ├── requirements.txt        # Dependencias Python
│   ├── host.json              # Configuración del host
│   └── local.settings.json    # Configuración local
└── README.md                  # Este archivo
🚀 Instrucciones de Despliegue
Prerrequisitos

Azure CLI instalado
Python 3.9 o superior
Azure Functions Core Tools v4
Cuenta de Azure activa
