# 🚀 Consultor de Precios de Criptomonedas

Una aplicación web completa que permite consultar precios en tiempo real de criptomonedas usando Azure Functions y la API de CoinGecko.

## 📋 Características

- 🔍 Consulta precios de 8 criptomonedas populares
- 💱 Precios en USD y MXN
- 🎨 Interfaz moderna y responsiva
- ⚡ Respuesta rápida con Azure Functions
- 🔒 CORS configurado para desarrollo y producción

## 🛠️ Tecnologías Utilizadas

- **Frontend**: HTML5, CSS3, JavaScript (Vanilla)
- **Backend**: Azure Functions con Python 3.9+
- **API**: CoinGecko API v3
- **Despliegue**: Azure Function App

## 📁 Estructura del Proyecto

```
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
```

## 🚀 Instrucciones de Despliegue

### Prerrequisitos

- Azure CLI instalado
- Python 3.9 o superior
- Azure Functions Core Tools v4
- Cuenta de Azure activa

### 1. Preparar Azure Function

#### Crear Function App en Azure

```bash
# Crear grupo de recursos
az group create --name rg-crypto-app --location "East US"

# Crear storage account
az storage account create \
  --name cryptopricestorage \
  --location "East US" \
  --resource-group rg-crypto-app \
  --sku Standard_LRS

# Crear Function App
az functionapp create \
  --resource-group rg-crypto-app \
  --consumption-plan-location "East US" \
  --runtime python \
  --runtime-version 3.9 \
  --functions-version 4 \
  --name crypto-price-function-app \
  --storage-account cryptopricestorage \
  --os-type Linux
```

#### Configurar CORS

```bash
az functionapp cors add \
  --resource-group rg-crypto-app \
  --name crypto-price-function-app \
  --allowed-origins "*"
```

### 2. Desarrollo Local

#### Configurar entorno local

```bash
# Crear directorio del proyecto
mkdir crypto-price-app
cd crypto-price-app

# Inicializar Function App
func init --python

# Crear nueva función HTTP
func new --name GetCryptoPrice --template "HTTP trigger" --authlevel anonymous
```

#### Instalar dependencias

```bash
pip install -r requirements.txt
```

#### Ejecutar localmente

```bash
func start
```

La función estará disponible en: `http://localhost:7071/api/GetCryptoPrice`

### 3. Desplegar a Azure

#### Despliegue directo

```bash
func azure functionapp publish crypto-price-function-app
```

#### Despliegue con GitHub Actions (Opcional)

Crear archivo `.github/workflows/deploy.yml`:

```yaml
name: Deploy Azure Function

on:
  push:
    branches: [ main ]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v2
    
    - name: Setup Python
      uses: actions/setup-python@v2
      with:
        python-version: '3.9'
    
    - name: Install dependencies
      run: |
        pip install -r requirements.txt
    
    - name: Deploy to Azure Functions
      uses: Azure/functions-action@v1
      with:
        app-name: crypto-price-function-app
        package: .
        publish-profile: ${{ secrets.AZURE_FUNCTIONAPP_PUBLISH_PROFILE }}
```

### 4. Configurar Frontend

1. Actualizar la URL en `index.html`:

```javascript
const AZURE_FUNCTION_URL = '├── azure-function/
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
