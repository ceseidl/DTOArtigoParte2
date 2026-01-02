# Sample API – Mapeamento Manual de DTOs em .NET 10

Este repositório acompanha o artigo:

**Como Mapear DTOs Manualmente em .NET – Parte 2**

Ele demonstra uma abordagem **simples, explícita e arquiteturalmente correta** para mapear DTOs em APIs ASP.NET Core, **sem AutoMapper**, mantendo serviços e domínio desacoplados da camada HTTP.

O foco deste projeto **não é banco de dados, autenticação ou infraestrutura complexa**, e sim **arquitetura, responsabilidades e fluxo de dados**.

---

## 🎯 Qual problema este projeto resolve?

Em muitas APIs, o mapeamento de DTOs acaba indo parar na **camada de serviço**:

- serviços passam a depender de DTOs
- regras de negócio se misturam com apresentação
- mudanças na API impactam o core da aplicação
- reutilização de serviços se torna difícil

Este projeto propõe uma alternativa mais limpa:

> **Serviços retornam domínio.**  
> **DTOs são responsabilidade da borda da aplicação.**

---

## 🧠 A ideia central (bem simples)

Toda a aplicação segue uma regra clara:

> **O domínio não deve saber nada sobre HTTP.**  
> **A API é que se adapta ao domínio.**

---

## 🔁 Fluxo da requisição

```
Controller
   ↓
Service
   ↓
Domínio
   ↓
Filtro de saída
   ↓
DTO
   ↓
Response HTTP
```

---

## 🗂 Estrutura do Projeto

```
SampleApiSolution
├── SampleApiSolution.sln
├── README.md
├── Dockerfile
├── .github/
│   └── workflows/
│       └── ci.yml
└── src/
    └── SampleApi/
        ├── Api/
        ├── Application/
        ├── Domain/
        ├── Infrastructure/
        └── SampleApi.csproj
```

---

## ▶️ Executando localmente

```bash
dotnet restore
dotnet run --project src/SampleApi
```

---

## 🐳 Docker

```bash
docker build -t sample-api .
docker run -p 8080:8080 sample-api
```

---

## 🤖 GitHub Actions

O pipeline configurado em `.github/workflows/ci.yml` executa automaticamente:

- restore
- build
- docker build

---

## ✅ Quando usar este padrão?

Use quando:

- você quer proteger o domínio
- serviços precisam ser reutilizáveis
- DTOs são próximos do domínio

Evite quando:

- DTOs são muito diferentes do domínio
- múltiplos formatos de resposta por endpoint

---

## 🧑‍💻 Autor

Carlos Eduardo Seidl
