# Hello World com o Google Cloud Function

Este repositório contém um exemplo básico de uma ```Cloud Function HTTP``` escrita em ```Node.js``` e implantada no **Google Cloud Platform**.

Objetivo é demonstrar como criar, implantar e executar uma função simples que responde com `"Olá, mundo!"` ao ser acessada via HTTP.

# Pré-requesitos:

- Conta no [Google Cloud Platform](https://console.cloud.google.com/)
- Node.js instalado (use `node -v` para verificar)
- Google Cloud SDK instalado: [instalar aqui](https://cloud.google.com/sdk/docs/install)
- VS Code instalado
- Projeto criado no GCP
- Conta de faturamento vinculada ao projeto (mesmo para uso gratuito)

# Estrutura do projeto

```bash
gcp-cloud-function-hello-world/
├── index.js         # Código principal da função
├── package.json     # Dependências e metadata do projeto


<br>

```

# Arquivos:

1 - Nesse repositório contém os arquivos ```index.js``

```
// Exporta a função chamada 'olaMundo'
// Essa função será usada como ponto de entrada na Google Cloud Function

exports.olaMundo = (req, res) => {
  res.send("Olá, mundo! Esta função está rodando no Google Cloud 🎉");      #Envia uma resposta HTTP simples
};


```

2 - Arquivo ```package.json``

```
{
    "name": "ola-mundo-com-gcloud-function",  # Nome do projeto (sem espaços)
    "version": "1.0.0",                        # Versão inicial do projeto
    "main": "index.js"                          # Arquivo principal da função
  }
  
```


# Instalação e execução

1 - Faça o clone do repositório ```gcp-cloud-function-hello-world```

git clone <https://github.com/diegorodriguescsilva/gcp-cloud-function-hello-world>

2 - Abra o terminal e execute:

```
gcloud auth login

```

3 - Selecione o projeto onde deseja implantar a função:

```
gcloud config set project SEU_ID_DO_PROJETO

````
4 - Faça a verificação se a conta e o nome do projeto estão certos:

````

gcloud config list

```
# Ativando a API Cloud Functions

1 - No terminal digite: 

```
gcloud services enable cloudfunctions.googleapis.com

```
# Fazer o deploy da função

1 - No terminal execute:

```

gcloud functions deploy olaMundo \
  --runtime=nodejs20 \                      # define a versão do Node.js
  --trigger-http \                          # ativa a função por URL HTTP
  --allow-unauthenticated \                 # permite chamadas públicas
  --entry-point=olaMundo                    # nome da função exportada no código

```

# Acessando a função no navegador

1- Após o deploy, o terminal vai mostrar algo como:

```
httpsTrigger:
  url: https://REGIAO-PROJETO.cloudfunctions.net/olaMundo

```

2 - Abra essa URL no navegador para ver ```Olá, mundo!```

# Deletar a função

1 - No terminal digite:

```

gcloud functions delete olaMundo

```