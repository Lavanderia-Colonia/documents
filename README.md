# 📚 Documentação - Sistema Lavanderia Colônia

> Documentação técnica e artefatos do projeto desenvolvido para a disciplina de Engenharia de Software III

## 🎓 Informações Acadêmicas

**Instituição:** Faculdade de Tecnologia de Mogi das Cruzes (FATEC)  
**Curso:** Análise e Desenvolvimento de Sistemas  
**Disciplina:** Engenharia de Software III  
**Empresa Cliente:** Lavanderia Colônia  

---

## 📁 Estrutura da Documentação

Este diretório contém todos os artefatos de documentação e modelagem do sistema desenvolvido para a Lavanderia Colônia.

```
documents/
│
├── 📊 Lavanderia Colônia.pptx              # Apresentação do projeto
├── 📋 Diagrama_de_Caso_de_Uso.pdf          # Casos de uso do sistema
├── 🗂️ dfd_lavanderia_colonia.drawio.png    # Diagrama de Fluxo de Dados
├── 🔗 modelo_logico_lavanderia.png         # Modelo Lógico do BD
└── 📐 modelo_relacional_lavanderia.png     # Modelo Relacional do BD
```

---

## 📄 Descrição dos Documentos

### 1. 📊 **Apresentação do Projeto** 
**Arquivo:** `Lavanderia Colônia.pptx` (19.7 MB)

Apresentação completa do projeto contendo:
- Visão geral do sistema
- Objetivos e escopo do projeto
- Funcionalidades principais
- Arquitetura e tecnologias utilizadas
- Padrões de projeto implementados (Singleton, Abstract Factory)
- Demonstração das interfaces
- Resultados e conclusões
- Trabalho futuro

**Formato:** Microsoft PowerPoint  
**Última atualização:** 09/11/2025

---

### 2. 📋 **Diagrama de Casos de Uso**
**Arquivo:** `Diagrama_de_Caso_de_Uso.pdf` (26 KB)

Documento que especifica todos os casos de uso do sistema, incluindo:

#### **Atores:**
- 👤 **Usuário (Atendente)**
- 👨‍💼 **Administrador**
- 👔 **Cliente**

#### **Principais Casos de Uso:**

**Gestão de Clientes:**
- UC01: Cadastrar Cliente
- UC02: Consultar Cliente
- UC03: Atualizar Dados do Cliente
- UC04: Ativar/Desativar Cliente
- UC05: Visualizar Histórico de Pedidos

**Gestão de Pedidos:**
- UC06: Criar Novo Pedido
- UC07: Consultar Pedido
- UC08: Atualizar Pedido
- UC09: Finalizar Pedido
- UC10: Cancelar Pedido
- UC11: Excluir Pedido

**Gestão de Produtos:**
- UC12: Consultar Produtos Disponíveis
- UC13: Consultar Cores Disponíveis
- UC14: Consultar Status de Pedidos

**Autenticação e Segurança:**
- UC15: Fazer Login
- UC16: Alterar Senha
- UC17: Gerenciar Perfil de Usuário

**Auditoria:**
- UC18: Visualizar Logs de Auditoria
- UC19: Rastrear Alterações em Pedidos

**Formato:** PDF  
**Última atualização:** 09/11/2025

---

### 3. 🗂️ **Diagrama de Fluxo de Dados (DFD)**
**Arquivo:** `dfd_lavanderia_colonia.drawio.png` (42 KB)

Representação visual do fluxo de informações no sistema.

#### **Principais Processos:**
1. **Processo de Autenticação**
   - Login de usuário
   - Validação de credenciais
   - Geração de token JWT

2. **Processo de Gestão de Clientes**
   - Cadastro de novos clientes
   - Atualização de dados cadastrais
   - Consulta de histórico

3. **Processo de Gestão de Pedidos**
   - Criação de pedidos com itens
   - Atualização de status
   - Finalização/Cancelamento

4. **Processo de Auditoria**
   - Registro automático de operações
   - Armazenamento de logs
   - Consulta de histórico

#### **Fluxos de Dados Principais:**
- Cliente → Sistema → Banco de Dados
- Sistema → Auditoria → Banco de Dados
- Usuário → Autenticação → Token JWT
- Pedido → Validação → Persistência

**Ferramenta:** Draw.io  
**Formato:** PNG  
**Última atualização:** 09/11/2025

---

### 4. 🔗 **Modelo Lógico do Banco de Dados**
**Arquivo:** `modelo_logico_lavanderia.png` (18 KB)

Representação lógica da estrutura do banco de dados, mostrando:

#### **Entidades Principais:**

**👥 CLIENT (Cliente)**
- PK: id (INTEGER)
- name (VARCHAR)
- telephone (VARCHAR)
- street, number, district (VARCHAR)
- zip_code (VARCHAR)
- complement (VARCHAR)
- active (BOOLEAN)
- created_at, updated_at (DATE)

**📦 ORDER (Pedido)**
- PK: id (INTEGER)
- FK: client_id → CLIENT
- FK: status_id → ORDER_STATUS
- finish_type (ENUM: ENTREGA, RETIRAR)
- finish_deadline (VARCHAR)
- delivery_date (DATETIME)
- created_at, updated_at (DATE)

**🛍️ ORDER_ITEM (Item do Pedido)**
- PK: id (BIGINT)
- FK: order_id → ORDER
- FK: product_id → PRODUCT
- FK: color_id → ORDER_ITEM_COLOR
- brand (VARCHAR)
- quantity (INTEGER)
- price (DECIMAL)
- observation (VARCHAR)
- created_at, updated_at (DATE)

**📋 PRODUCT (Produto)**
- PK: id (BIGINT)
- code (VARCHAR)
- description (VARCHAR)
- created_at, updated_at (DATE)

**🎨 ORDER_ITEM_COLOR (Cor)**
- PK: id (BIGINT)
- name (VARCHAR)
- created_at, updated_at (DATE)

**📊 ORDER_STATUS (Status)**
- PK: id (BIGINT)
- name (VARCHAR)
- created_at, updated_at (DATE)

**📝 AUDIT (Auditoria)**
- PK: id (INTEGER)
- description (VARCHAR 4000)
- change_date (DATE)
- created_at, updated_at (DATE)

**👤 USER (Usuário)**
- PK: id (BIGINT)
- name (VARCHAR)
- password (VARCHAR)
- role (ENUM: USER, ADMIN)
- created_at, updated_at (DATE)

#### **Relacionamentos:**
- CLIENT (1) ←→ (N) ORDER
- ORDER (1) ←→ (N) ORDER_ITEM
- PRODUCT (1) ←→ (N) ORDER_ITEM
- ORDER_ITEM_COLOR (1) ←→ (N) ORDER_ITEM
- ORDER_STATUS (1) ←→ (N) ORDER

**Formato:** PNG  
**Última atualização:** 09/11/2025

---

### 5. 📐 **Modelo Relacional do Banco de Dados**
**Arquivo:** `modelo_relacional_lavanderia.png` (35 KB)

Diagrama ER (Entidade-Relacionamento) detalhado mostrando:

#### **Características:**
- ✅ Chaves primárias (PK) identificadas
- ✅ Chaves estrangeiras (FK) mapeadas
- ✅ Cardinalidades dos relacionamentos
- ✅ Tipos de dados especificados
- ✅ Restrições de integridade
- ✅ Índices sugeridos

#### **Relacionamentos Detalhados:**

```
CLIENT ||--o{ ORDER : "faz"
ORDER ||--o{ ORDER_ITEM : "contém"
PRODUCT ||--o{ ORDER_ITEM : "é usado em"
ORDER_ITEM_COLOR ||--o{ ORDER_ITEM : "define"
ORDER_STATUS ||--o{ ORDER : "categoriza"
```

#### **Regras de Negócio Implementadas:**
1. Um cliente pode ter vários pedidos
2. Um pedido deve ter pelo menos um item
3. Um pedido pertence a apenas um cliente
4. Todo pedido deve ter um status válido
5. Itens removidos geram registro de auditoria
6. Todas as operações críticas são auditadas

**Formato:** PNG  
**Última atualização:** 09/11/2025

---

## 🎯 Metodologia de Desenvolvimento

### **Processo Utilizado**
O projeto foi desenvolvido seguindo metodologias ágeis com as seguintes fases:

1. **📋 Levantamento de Requisitos**
   - Entrevistas com stakeholders
   - Análise de processos da lavanderia
   - Definição de escopo

2. **🎨 Modelagem**
   - Criação de casos de uso
   - Modelagem do banco de dados
   - Diagramas de fluxo de dados

3. **💻 Desenvolvimento**
   - Implementação do backend (Spring Boot)
   - Aplicação de padrões de projeto
   - Integração com banco de dados

4. **🧪 Testes**
   - Testes unitários
   - Testes de integração
   - Validação com usuários

5. **📊 Documentação**
   - Documentação técnica
   - Manual de uso
   - Apresentação final

---

## 🛠️ Ferramentas Utilizadas na Documentação

| Ferramenta | Uso | Arquivo |
|------------|-----|---------|
| **Microsoft PowerPoint** | Apresentação do projeto | `Lavanderia Colônia.pptx` |
| **Draw.io** | Diagramas UML e DFD | `dfd_lavanderia_colonia.drawio.png` |
| **MySQL Workbench** | Modelagem de BD | `modelo_logico_lavanderia.png` |
| **dbdiagram.io** | Diagrama ER | `modelo_relacional_lavanderia.png` |
| **Astah UML** | Casos de uso | `Diagrama_de_Caso_de_Uso.pdf` |

---

## 📊 Padrões e Convenções

### **Nomenclatura do Banco de Dados:**
- Tabelas: `snake_case` (ex: `order_item`)
- Colunas: `snake_case` (ex: `created_at`)
- Chaves estrangeiras: `{tabela}_id` (ex: `client_id`)

### **Padrões UML:**
- Atores representados por stick figures
- Casos de uso em elipses
- Relacionamentos com setas direcionadas
- <<include>> e <<extend>> quando aplicável

---

## 🔍 Como Utilizar esta Documentação

### **Para Desenvolvedores:**
1. Consulte o **modelo relacional** para entender a estrutura do BD
2. Use o **DFD** para compreender o fluxo de dados
3. Revise os **casos de uso** para implementar funcionalidades

### **Para Avaliadores:**
1. Inicie pela **apresentação** para visão geral
2. Analise os **casos de uso** para validar requisitos
3. Verifique a **modelagem do BD** para avaliar design

### **Para Stakeholders:**
1. Revise a **apresentação** para entender o projeto
2. Consulte os **casos de uso** para validar funcionalidades
3. Use o **DFD** para compreender processos

---

## 📈 Estatísticas do Projeto

- **Total de Casos de Uso:** 19
- **Entidades no Banco:** 8
- **Relacionamentos:** 5 principais
- **Páginas de Documentação:** 50+ (incluindo apresentação)
- **Diagramas Criados:** 5

---

## 🎓 Aprendizados

Este projeto permitiu aplicar conceitos fundamentais de Engenharia de Software:

### **Modelagem:**
- ✅ Diagramas de Caso de Uso (UML)
- ✅ Modelagem de Dados (Lógico e Relacional)
- ✅ Diagramas de Fluxo de Dados (DFD)

### **Padrões de Projeto:**
- ✅ Singleton Pattern (Sistema de Auditoria)
- ✅ Abstract Factory (Criação de OrderItems)
- ✅ Repository Pattern (Acesso a dados)

### **Boas Práticas:**
- ✅ Normalização de banco de dados (3FN)
- ✅ Nomenclatura consistente
- ✅ Documentação completa
- ✅ Versionamento de artefatos

---

## 📝 Atualizações e Versionamento

| Data | Versão | Mudanças |
|------|--------|----------|
| 09/11/2025 | 1.0 | Versão inicial de todos os documentos |

---

## 🤝 Contribuidores

- Bianca Nunes Codo - RA: 1840482412013
- Diogo Santana de Almeida - RA: 1840482412001
- Felipe Kenji Oizumi - RA: 1840482412024
- João Paulo Akira Sigue - RA: 1840482412005
- Luciano Akihiro Tokuno - RA: 1840482412017
- Luana Mika Maruyama - RA: 1840482412016
- Marcos Guilherme Tasato - RA: 1840482412006

**Equipe de Desenvolvimento**  
Alunos do curso de Análise e Desenvolvimento de Sistemas  
FATEC Mogi das Cruzes - Engenharia de Software III



## 📋 Checklist de Documentação

- [x] Diagrama de Casos de Uso
- [x] Diagrama de Fluxo de Dados
- [x] Modelo Lógico do Banco de Dados
- [x] Modelo Relacional (ER)
- [x] Apresentação do Projeto
- [x] README de Documentação
- [x] README do Sistema (Backend)

---

## 🔗 Links Relacionados

- [📁 Repositório do Backend](../../../backend)
- [📋 Repositório do Frontend](../../../frontend)
---

**Desenvolvido com 📚 e ☕ na FATEC Mogi das Cruzes**

*Projeto acadêmico - Engenharia de Software III - 2025*
