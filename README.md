# Sample API – Manual DTO Mapping (.NET 10)

Projeto completo do artigo **Como Mapear DTOs Manualmente em .NET – Parte 2**.

## Executar localmente
```bash
dotnet restore
dotnet run --project src/SampleApi
```

## Docker
```bash
docker build -t sample-api .
docker run -p 8080:8080 sample-api
```

## CI
Pipeline GitHub Actions configurado em `.github/workflows/ci.yml`.
