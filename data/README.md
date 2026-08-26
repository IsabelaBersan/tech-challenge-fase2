# data/

**Nada aqui é versionado.** O `.gitignore` bloqueia o conteúdo destas pastas de propósito:
datasets em Git incham o repositório e frequentemente violam a licença da fonte.

| Pasta | Conteúdo |
|---|---|
| `raw/` | arquivo original, exatamente como baixado da fonte — nunca editado |
| `processed/` | saída dos notebooks de pré-processamento (`.parquet` ou `.csv`) |

Documente abaixo como obter os dados brutos, para que qualquer pessoa consiga reproduzir o projeto.

## Como obter

1. Baixe em: https://www.kaggle.com/datasets/yasserh/wine-quality-dataset?resource=download
2. Salve como: `data/raw/<!-- WineQT -->`

