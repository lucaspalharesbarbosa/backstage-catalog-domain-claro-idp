# Catálogo Backstage — domínio Claro IDP

Repositório de **descritores YAML** do [Software Catalog](https://backstage.io/docs/features/software-catalog/) do Backstage para o domínio **Claro IDP** (plataforma interna para desenvolvedores, catálogo de software, automações e self-service).

Este projeto **não** contém o aplicativo Backstage em si — apenas entidades do catálogo (`Component`, `System`, `Domain`, `API`, `Resource`) e um agregador de **Location** para ingestão remota.

## Estrutura

| Pasta | Conteúdo |
|-------|----------|
| `domains/` | Domínio de negócio (ex.: `claro-idp`) |
| `systems/` | Sistemas que agrupam componentes e recursos |
| `components/` | Serviços, bibliotecas, workers, pipelines, etc. |
| `apis/` | Contratos e APIs documentadas |
| `resources/` | Infraestrutura (buckets, clusters, observabilidade, etc.) |
| `locations/` | Arquivo `Location` apontando para todas as entidades no GitHub |

## Uso no Backstage

### Opção 1 — registrar o arquivo de locations (recomendado)

No `app-config.yaml` do seu Backstage, inclua uma entrada que carregue o descritor `Location` deste repositório (ele lista todos os `targets`):

```yaml
catalog:
  locations:
    - type: url
      target: https://github.com/lucaspalharesbarbosa/backstage-catalog-domain-claro-idp/blob/main/locations/github-locations.yaml
```

Se o processador de URL do seu ambiente exigir conteúdo bruto, use o equivalente em `raw.githubusercontent.com` para o mesmo caminho.

### Opção 2 — clonar e apontar para arquivos locais

Após clonar o repositório, registre pastas ou arquivos com `type: file` conforme a [documentação de locations](https://backstage.io/docs/features/software-catalog/configuration#catalogrules--cataloglocations).

## Contribuir

1. Adicione ou edite o YAML na pasta adequada ao [kind](https://backstage.io/docs/features/software-catalog/descriptor-format) da entidade.
2. Atualize `locations/github-locations.yaml` para incluir o novo arquivo, se for uma entidade nova.
3. Valide nomes, `apiVersion`, relacionamentos (`spec.owner`, `spec.system`, `dependsOn`, etc.) para manter o grafo do catálogo consistente.

## Referências

- [Formato dos descritores](https://backstage.io/docs/features/software-catalog/descriptor-format)
- [Modelo de entidades](https://backstage.io/docs/features/software-catalog/system-model)
