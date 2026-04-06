# Projeto Final: Modelagem Física de Dados - Clube do Livro (Curso 2)

Este projeto apresenta a transição do modelo lógico para o modelo físico do e-commerce Clube do Livro.

## 🛠️ Especificações do Modelo Físico

Abaixo estão as tabelas estruturadas com seus respectivos domínios (tipos de dados) e restrições de integridade.

### 1. Tabela: Tb_CLIENTE
| Coluna | Tipo | Restrição |
| :--- | :--- | :--- |
| id_cliente | INTEGER | Primary Key (PK) |
| nome_cliente | VARCHAR(100) | NOT NULL |
| email_cliente | VARCHAR(50) | NOT NULL |
| cpf_cnpj | VARCHAR(14) | UNIQUE / NOT NULL |

### 2. Tabela: Tb_LIVRO
| Coluna | Tipo | Restrição |
| :--- | :--- | :--- |
| id_livro | INTEGER | Primary Key (PK) |
| titulo_livro | VARCHAR(150) | NOT NULL |
| preco_livro | DECIMAL(10,2) | NOT NULL |
| fk_id_editora | INTEGER | Foreign Key (FK) |

### 3. Tabela: Tb_ITEM_PEDIDO (Entidade Associativa)
*Resolve o relacionamento N:M entre Pedido e Livro.*
| Coluna | Tipo | Restrição |
| :--- | :--- | :--- |
| fk_id_pedido | INTEGER | PFK (Primary Foreign Key) |
| fk_id_livro | INTEGER | PFK (Primary Foreign Key) |
| qtd_item | INTEGER | NOT NULL |
| valor_unitario | DECIMAL(10,2) | NOT NULL |

### 4. Tabela: Tb_ESTOQUE (Entidade Fraca)
| Coluna | Tipo | Restrição |
| :--- | :--- | :--- |
| fk_id_livro | INTEGER | PFK (Primary Foreign Key) |
| qtd_estoque | INTEGER | NOT NULL |

---

## 🔑 Decisões Técnicas de Modelagem

1. **Nomenclatura**: Adotado o prefixo `Tb_` para identificar tabelas físicas e nomes em snake_case (letras minúsculas com underline).
2. **Tipagem (Domínios)**: 
   - `VARCHAR` para campos de texto (nomes, e-mails).
   - `DECIMAL(10,2)` para valores monetários (garante precisão de centavos).
   - `INTEGER` para chaves e quantidades.
3. **Integridade**: Uso de `NOT NULL` em campos obrigatórios para evitar dados inconsistentes.
4. **Relacionamentos**: Implementação de Relacionamentos Identificadores em entidades fracas e associativas (resultando em PFKs).

---
*Projeto desenvolvido como parte do curso de Modelagem de Dados Relacional.*
