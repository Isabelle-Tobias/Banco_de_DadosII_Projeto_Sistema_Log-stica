# Gestão de Estoque e Otimização Logística Híbrida

## 📖 Sobre o Projeto
Projeto desenvolvido para a disciplina de Banco de Dados II (USP). O projeto explora o conceito de **Persistência Poliglota**, utilizando diferentes paradigmas de bancos de dados para resolver problemas específicos de escalabilidade, consistência e performance.

O sistema gerencia desde o recebimento de mercadorias no armazém (foco transacional) até a entrega ao destino final (foco em redes e caminhos).

## 🏗️ Arquitetura e Modelagem de Dados
Para atender aos requisitos da disciplina, a solução utiliza uma arquitetura híbrida:

1.  **Camada Relacional (PostgreSQL):** Focada em integridade referencial e transações ACID. Gerencia o inventário, fornecedores e ordens de serviço.
2.  **Camada de Grafos (Neo4j):** Focada em relacionamentos e topologia de rede. Gerencia a malha de transporte, rotas e centros de distribuição.



## 🚀 Funcionalidades Principais

### 📦 Gestão de Estoque (Relacional)
*   **Recebimento Automatizado:** Registro de entrada de produtos com validação de NF-e e atualização de saldo via *Stored Procedures*.
*   **Inventário Dinâmico:** Suporte a atributos variáveis por categoria de produto (ex: validade para perecíveis, dimensões para móveis) utilizando o tipo `JSONB`.
*   **Controle de Auditoria:** *Triggers* para rastreamento de movimentações (quem moveu o quê e quando).
*   **Gestão de Alertas:** Consultas otimizadas para identificar produtos abaixo do estoque crítico.

### 🚚 Logística de Entrega (Grafos)
*   **Cálculo de Rota Otimizada:** Utilização do algoritmo de Dijkstra (via Cypher) para encontrar o caminho mais curto ou mais barato entre o armazém e o cliente.
*   **Análise de Impacto de Malha:** Identificação de "nós críticos" na rede de distribuição que, se falharem, interrompem o fluxo logístico.
*   **Agrupamento por Proximidade:** Localização do Centro de Distribuição mais próximo de um novo pedido para redução de *Lead Time*.
*   **Rastreamento de Cadeia de Custódia:** Visualização do histórico do produto através dos diversos pontos de transbordo.

## 🛠️ Tecnologias Utilizadas
- **Linguagens:** Java
- **Bancos de Dados:** 
    - PostgreSQL 15+
    - Neo4j 5.x (Graph Data Science library)
- **Containerização:** Docker & Docker Compose
- **Documentação de API:** Swagger (OpenAPI)

## 🎯 Conceitos de Banco de Dados II Aplicados
*   **Normalização vs Desnormalização:** Estratégias para ganho de performance em relatórios.
*   **Índices Complexos:** Uso de índices B-Tree e GIN (para campos JSON).
*   **Transações Distribuídas:** Discussão sobre consistência eventual vs imediata entre as camadas de dados.
*   **Consultas Recursivas:** Comparação de performance entre `WITH RECURSIVE` (SQL) e consultas nativas em grafos.

## 🔧 Como Executar (Em breve)
