# Encurtador de URLs Serverless - Redirecionamento 🚀

Este projeto faz parte de um curso gratuito da [Rocketseat](https://github.com/Rocketseat) ministrado pela especialista [Fernanda Kipper](https://github.com/Fernanda-Kipper) utilizando Java.

É um **sistema de encurtamento de URLs** desenvolvido utilizando uma arquitetura **serverless** com serviços da AWS. 

O objetivo é oferecer uma solução escalável, de fácil manutenção e com custos operacionais reduzidos, eliminando a necessidade de servidores dedicados.

## 🎯 Objetivos do Projeto

- Criar um **sistema de encurtamento de URLs** eficiente e funcional.
- Implementar uma **arquitetura serverless**, explorando serviços da AWS como:
  - AWS Lambda
  - Amazon API Gateway
  - Amazon S3
  - Amazon CloudaWatch
  - Amazon IAM
- Oferecer **escalabilidade automática**, reduzindo custos operacionais sem comprometer o desempenho.
- Garantir **facilidade na manutenção e evolução do sistema**.

## 🛠️ Tecnologias e Ferramentas Utilizadas

- **AWS Lambda**: Funções serverless para processar requisições.
- **API Gateway**: Exposição de endpoints HTTP para o sistema.
- **S3**: Armazenamento eficiente das URLs originais e encurtadas.
- **AWS CloudaWatch**: Monitoramento e coleta dados de eventos, métricas e logs em tempo real para otimizar a manutenção de aplicações e a infraestrutura.
- **Amazon IAM**: Controle o acesso aos recursos da AWS de forma segura.
- **Java**: Linguagem para a implementação das funções Lambda.

## 📂 Estrutura de arquivos do Projeto

**CreateUrlLambda**
```
. 
├── src/ 
│   ├── main/ 
│   │   ├── java/ 
│   │   │   ├── com.rocketseat.createUrlShortner/ 
│   │   │   │   ├── Main.java                   <--- Classe com método Handler para encurtar URLs
│   │   │   │   ├── UrlData.java        <--- CLasse contém a biblioteca lombok para trabalhar a String das informações enviadas (url e tempo)
│    
├── pom.xml                                     <--- Gerenciamento de dependências Maven

```

**RedirectUrlShortener**
```
. 
├── src/ 
│   ├── main/ 
│   │   ├── java/ 
│   │   │   ├── com.rocketseat.redirectUrlShortener/ 
│   │   │   │   ├── Main.java                   <--- Classe com método Handler para encurtar URLs
│   │   │   │   ├── OriginalUrlData.java        <--- Classe contém a biblioteca lombok processar os dados (url e tempo)
│    
├── pom.xml                                     <--- Gerenciamento de dependências Maven

```

## 🚀 Endpoints

**URL**: https://uw0782y11d.execute-api.us-east-1.amazonaws.com

### Criando URL Encurtada
- **Método**: `POST`
- **Endpoint**: `/create`
- **Body**:  
  ```
  {
  "originalUrl": "https://exemplo.com",
  "expirationTime": "1732225506"
  }
  ```
  - **Resposta**:
    - `200: { "code": "273206e1"}`
    - `500: {"message": "Internal Server Error"}`
- **Função**:
    1. Coleta a url e tempo (data) fornecidos.
    2. Processa as informações e armazena em S3.
    3. Gera um código de referencia do armazenamento.
  
### Redirecionar URL
- **Método**: `GET`  
- **Endpoint**: `/{shortUrlCode}`
- **Resposta**:
    - `302: Redireciona para a URL original.`
    - `410: Indica que a URL expirou.`
- **Função**:
    1. Recupera os metadados para o código curto fornecido.
    2. Verifica o tempo de expiração.
    3. Redireciona ou retorna um erro caso a URL esteja expirada.

## 🌟 Diferenciais

- **Custos otimizados**: Sem servidores dedicados, os custos são proporcionais ao uso.
- **Alto desempenho**: Escalabilidade automática para atender a picos de demanda.
- **Foco na simplicidade**: Arquitetura modular e de fácil manutenção.
              
