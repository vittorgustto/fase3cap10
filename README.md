# Projeto de Análise de Dados Agro

Este projeto visa criar um sistema de análise de dados agrícolas no Brasil, com foco em produção, produtividade e área plantada. Através de um banco de dados SQL e consultas SQL relevantes, o sistema permite explorar informações sobre diferentes culturas em vários estados, oferecendo uma visão detalhada e histórica dos dados.

## Objetivos

- **Analisar dados agrícolas** para entender a produção e produtividade de diferentes culturas.
- **Fornecer um ranking** dos estados com maior produtividade por cultura.
- **Examinar a evolução** da área plantada ao longo dos anos para cada cultura.

## Estrutura do Banco de Dados

O banco de dados contém três tabelas principais: `Área_Brasil`, `Produção_Brasil` e `Produtividade_Brasil`. Cada uma possui informações detalhadas sobre diferentes aspectos das culturas agrícolas.

### Tabela `Área_Brasil`
| Coluna             | Tipo       | Descrição                              |
|--------------------|------------|----------------------------------------|
| `estado`           | VARCHAR(50)| Nome do estado                         |
| `cultura`          | VARCHAR(50)| Nome da cultura                        |
| `safra`            | VARCHAR(20)| Ano da safra                           |
| `area_plantada_ha` | INT        | Área plantada em hectares              |

### Tabela `Produção_Brasil`
| Coluna             | Tipo       | Descrição                              |
|--------------------|------------|----------------------------------------|
| `estado`           | VARCHAR(50)| Nome do estado                         |
| `cultura`          | VARCHAR(50)| Nome da cultura                        |
| `safra`            | VARCHAR(20)| Ano da safra                           |
| `producao_ton`     | INT        | Produção em toneladas                  |

### Tabela `Produtividade_Brasil`
| Coluna              | Tipo       | Descrição                              |
|---------------------|------------|----------------------------------------|
| `estado`            | VARCHAR(50)| Nome do estado                         |
| `cultura`           | VARCHAR(50)| Nome da cultura                        |
| `safra`             | VARCHAR(20)| Ano da safra                           |
| `produtividade_kg_ha` | DECIMAL  | Produtividade em kg/ha                |

## Consultas SQL Relevantes

Aqui estão algumas consultas SQL criadas para explorar o banco de dados:

 **Produção total de uma cultura por estado em uma safra específica**:

    SELECT estado, SUM(producao_ton) AS producao_total
    FROM Produção_Brasil
    WHERE cultura = 'Soja' AND safra = '2023/2024'
    GROUP BY estado;

**Evolução da área plantada de uma cultura ao longo dos anos**:

    SELECT safra, SUM(area_plantada_ha) AS total_area
    FROM Área_Brasil
    WHERE cultura = 'Milho'
    GROUP BY safra
    ORDER BY safra;

**Ranking dos estados com maior produtividade em uma cultura específica**:

SELECT estado, AVG(produtividade_kg_ha) AS media_produtividade
FROM Produtividade_Brasil
WHERE cultura = 'Café'
GROUP BY estado
ORDER BY media_produtividade DESC;


**Configuração e Importação dos Dados**
Criação das Tabelas:

No MySQL, execute os comandos SQL para criar as tabelas Área_Brasil, Produção_Brasil e Produtividade_Brasil conforme especificado na seção Estrutura do Banco de Dados.
Importação dos Dados:

Carregue os arquivos CSV (Área_Brasil.csv, Produção_Brasil.csv, Produtividade_Brasil.csv) no MySQL utilizando o recurso de importação do phpMyAdmin ou via comandos SQL.
Executar Consultas:

Após a configuração e importação dos dados, execute as consultas SQL fornecidas para verificar e explorar os dados.
Demonstração
Assista ao vídeo de demonstração do projeto para ver a análise dos dados agrícolas em ação.

**Estrutura do Repositório**
README.md: Documentação do projeto.
sql/: Scripts SQL para criação e importação do banco de dados.
csv/: Arquivos CSV contendo os dados das tabelas.
docs/: Documentação do projeto.
video/: Link para o vídeo de demonstração do projeto.

