# Central de Atendimento — Desafio Final

Este projeto é um sistema simples de atendimento de chamados via linha de comando (CLI) desenvolvido em Python. Ele simula uma central de suporte técnico aplicando conceitos fundamentais de estruturas de dados e algoritmos (Filas, Pilhas, Ordenação Estável, Busca Binária e Recursão).

---

## 📑 Sumário

- [Visão Geral](#-visão-geral)
- [Funcionalidades e Conceitos](#-funcionalidades-e-conceitos)
- [Estrutura do Projeto](#-estrutura-do-projeto)
- [Pré-requisitos](#-pré-requisitos)
- [Como Executar](#-como-executar)
  - [Executando os Testes Automáticos](#1-executando-os-testes-automáticos)
  - [Executando a Aplicação](#2-executando-a-aplicação)
- [Níveis de Implementação](#-níveis-de-implementação)

---

## 🔍 Visão Geral

O sistema gerencia o ciclo de vida dos chamados de suporte abertos pelos usuários (ex: *"minha internet caiu"*, *"servidor parou"*). Permite cadastrar chamados, atendê-los por ordem de chegada, desfazer atendimentos incorretos, listar pendentes ordenados por prioridade e pesquisar chamados rapidamente por número de protocolo.

---

## 🛠️ Funcionalidades e Conceitos

| Funcionalidade | Conceito / Estrutura de Dados |
| :--- | :--- |
| **Atender por ordem de chegada** | Fila / Queue (FIFO - *First In, First Out*) |
| **Desfazer último atendimento** | Pilha / Stack (LIFO - *Last In, First Out*) |
| **Listar pendentes por prioridade** | Algoritmo de Ordenação Estável (*Bubble Sort*) |
| **Buscar chamado por protocolo** | Busca Binária (*Binary Search*) |
| **Contar chamados por prioridade** | Recursão |

---

## 📁 Estrutura do Projeto

```text
.
├── desafio_final.py         # Código-fonte principal com funções e menu CLI
└── desafio_final_testes.py  # Suíte de testes automáticos (9 testes)
```

---

## ⚙️ Pré-requisitos

- Python 3.7 ou superior instalado no seu sistema.

Não é necessária a instalação de dependências externas (o projeto utiliza apenas bibliotecas padrão do Python como `collections.deque`).

---

## 🚀 Como Executar

### 1. Executando os Testes Automáticos

Antes de rodar a aplicação principal, certifique-se de que todas as funções estão operando corretamente rodando a suíte de testes:

```bash
python desafio_final_testes.py
```

Se tudo estiver correto, você verá a confirmação de que todos os 9 testes passaram:

```text
[OK]    Nivel 1: abrir chamado gera protocolos 1, 2, 3...
[OK]    Nivel 1: atender segue a ordem de chegada (FIFO)
[OK]    Nivel 1: atender com fila vazia devolve None
[OK]    Nivel 2: desfazer devolve o chamado para a FRENTE da fila
[OK]    Nivel 2: desfazer sem historico devolve None
[OK]    Nivel 3: ordena por prioridade (3 primeiro), estavel
[OK]    Nivel 3: ordenar NAO altera a fila original
[OK]    Nivel 4: busca binaria acha e nao acha protocolos
[OK]    Nivel 4: contagem recursiva por prioridade

Resultado: 9/9 testes passaram.
```

### 2. Executando a Aplicação

Para iniciar o menu interativo no terminal:

```bash
python desafio_final.py
```

**Opções disponíveis no menu:**
1. **Abrir chamado:** Registra um novo chamado com nome, descrição e prioridade (1-Baixa, 2-Média, 3-Alta).
2. **Atender próximo:** Remove o primeiro da fila e altera seu status para `atendido`.
3. **Desfazer último atendimento:** Retorna o último chamado atendido para a **frente da fila**.
4. **Listar pendentes por prioridade:** Exibe chamados pendentes da maior prioridade (3) para a menor (1), mantendo a ordem de chegada entre prioridades iguais.
5. **Buscar por protocolo:** Encontra rapidamente o chamado pelo número identificador.
6. **Relatório:** Exibe o total de chamados e a contagem por prioridade via recursão.
0. **Sair:** Encerra a aplicação.

---

## 🎯 Níveis de Implementação

- **Nível 1 (Fila - FIFO):** Implementação de `abrir_chamado` e `atender_proximo` usando `deque` da biblioteca padrão.
- **Nível 2 (Pilha - LIFO):** Implementação de `desfazer_atendimento` empilhando/desempilhando do histórico e retornando o chamado ao topo da fila (`appendleft`).
- **Nível 3 (Ordenação):** Implementação manual do *Bubble Sort* sem utilizar métodos nativos (`sorted()` ou `.sort()`), respeitando a estabilidade da ordem de chegada.
- **Nível 4 (Busca e Recursão):** 
  - `buscar_protocolo`: Algoritmo $O(\log n)$ de busca binária.
  - `contar_por_prioridade`: Algoritmo recursivo (sem o uso de laços `for`/`while` ou `sum()`).