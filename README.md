<p align="center"> <img width="1140" height="300" alt="gradeflow-logo" src="https://github.com/user-attachments/assets/f81dbb80-71cd-4cad-895f-f915282f1a88" />

 ##
<p align="center"> <img width="6000" height="3375" alt="Blue and White Modern Mobile App Mockup Presentation Presentation (3)" src="https://github.com/user-attachments/assets/6cb7d2b3-8d8d-42e9-af17-f248e2f02fec" />

## ✨ Funcionalidades
- **Gestão de disciplinas** por período/semestre, com média mínima configurável.
- **Controle de atividades**: pendente, em andamento e concluída, com prazo e peso.
- **Registro de notas** com média ponderada automática e **nota necessária** nas avaliações restantes.
- **Painel de desempenho**: cabeçalho de boas-vindas, cartões por disciplina com barra de média parcial (marca na média mínima) e situação por cor (Aprovado, No caminho, Atenção, Em risco, Reprovado), próximos prazos e sugestões de estudo/reforço.
- **CRUD completo** persistido em banco relacional (SQLite).
- **Temas (versão web)**: padrão *Azul*, além de Preto e branco, Verde, Roxo, Rosa e cor personalizada, cada um em **modo claro e escuro**, escolhidos na barra lateral.
- **Sugestões de estudo** para todas as disciplinas (não só as em alerta), com atrasos e prazos da semana.

## 📚 Tabela / Resumo do Site

> **Critério de Aprovação:** Nota mínima `6.0` por disciplina.

| Disciplina | Atividade | Tipo | Data de Entrega | Status | Peso | Nota |
| :--- | :--- | :---: | :---: | :---: | :---: | :---: |
| Compiladores | Análise Léxica e Sintática | Projeto | 23/11/2026 | ⏳ Em andamento | 3.0 | - |
| Compiladores | Lista de Gramáticas Livres de Contexto | Lista | 30/11/2026 | 📅 Pendente | 2.0 | - |
| Inteligência Artificial | Algoritmos de Busca (A* e Heurísticas) | Trabalho | 26/11/2026 | 📅 Pendente | 2.5 | - |
| Inteligência Artificial | Redes Neurais e Classificação | Projeto | 04/12/2026 | 📅 Pendente | 2.5 | - |

## 📊 Estrutura e Dados do Sistema (Contexto para README / Copilot)

### 1. Mapeamento de Telas e Componentes

| Seção / Aba | Componentes Principais | Funcionalidades |
| :--- | :--- | :--- |
| **Barra Lateral** | Aparência (Claro/Escuro), Cores do tema (`Azul`), Seletor de Aluno (`João (#1)`), Formulário `Novo aluno` e checkbox `Habilitar exclusão do aluno` | Alterna temas, seleciona o perfil ativo, cadastra novos alunos (Nome e E-mail opcional) e libera a opção de exclusão. |
| **Painel** | Banner de boas-vindas (`Olá, João`), 4 Cards de Resumo (`Disciplinas`, `Atividades em aberto`, `Próximo prazo`, `Disciplinas em alerta`), `Desempenho por disciplina`, `Próximos prazos` e `Sugestões de estudo` | Exibe visão geral do semestre, barras de progresso de notas, tabela cronológica de entregas e recomendações automáticas de estudo. |
| **Disciplinas** | Formulário de cadastro (`Disciplina`, `Período`, `Média mínima`), Tabela de disciplinas cadastradas e seção `incluir ou excluir` | Permite adicionar novas matérias com suas respectivas médias de corte e gerenciar registros existentes. |
| **Atividades e notas** | Seletor de disciplina, 3 Cards de Indicadores (`Média parcial`, `Nota necessária`, `Situação`), Tabela de atividades, Formulário de nova atividade e `incluir ou excluir` | Calcula médias em tempo real, lista tarefas com prazos/pesos/notas e permite cadastrar ou avaliar atividades. |

---

### 2. Regras de Negócio e Estados de Situação

| Estado / Indicador | Condição / Lógica Aplicada | Comportamento na Interface |
| :--- | :--- | :--- |
| **Sem notas** | Nenhuma atividade da disciplina possui nota lançada (`Status: Pendente`) | `Média parcial` exibe `—`; `Nota necessária` exibe o valor da média mínima (`6,0`); card de sugestão orienta a priorizar a próxima entrega. |
| **Aprovado** | `Média parcial >= Média mínima` (ex: Compiladores com `8,0 >= 6,0` ou IA com `(9,0 + 3,0) / 2 = 6,0`) | `Nota necessária` exibe `—`; badge verde `Aprovado` é exibido; sugestão recomenda revisão leve e foco nas demais matérias. |
| **Reprovado** | Todas as atividades concluídas e `Média parcial < Média mínima` (ex: IA com `(9,0 + 2,0) / 2 = 5,5 < 6,0`) | `Situação` exibe `Reprovado`; `Nota necessária` exibe `—`. |
| **Próximos 7 dias** | Atividades pendentes com vencimento em até 7 dias a partir da data atual (`18/11/2026`) | Destaca alertas no topo de `Sugestões de estudo` listando as tarefas urgentes. |

---

### 3. Dados de Exemplo (Seed / Testes — Período `2026.2`)

| Disciplina | Período | Média Mínima | Atividade | Descrição | Prazo | Peso | Status | Nota (Cenários) |
| :--- | :---: | :---: | :--- | :--- | :---: | :---: | :---: | :---: |
| **Compiladores** | 2026.2 | 6,0 | Atividade 1 – Análise Léxica e Sintática | Compreender como um compilador identificar os tokens e verificar a estrutura sintática de um programa. | 23/11/2026 | 1,00 | Pendente | `—` |
| **Compiladores** | 2026.2 | 6,0 | Atividade 2 – Construção de um Analisador Léxico Simples | Desenvolver um pequeno programa capaz de refletir os principais elementos de uma linguagem de programação. | 27/11/2026 | 1,00 | Pendente | `—` |
| **Inteligência artificial** | 2026.2 | 6,0 | Atividade 1 – Fundamentos da Inteligência Artificial | Compreender os conceitos fundamentais da Inteligência Artificial e suas aplicações na sociedade. | 24/11/2026 | 1,00 | Concluída | `9,0` |
| **Inteligência artificial** | 2026.2 | 6,0 | Atividade 2 – Criando uma Inteligência Artificial na Prática | Explorar o funcionamento de uma aplicação de Inteligência Artificial e compreender como ela pode resolver problemas reais. | 26/11/2026 | 1,00 | Concluída | `3,0` (Aprovado) / `2,0` (Reprovado) |

## 
<p align="center"> <img width="1916" height="841" alt="Captura de tela 2026-11-18 085727" src="https://github.com/user-attachments/assets/3adb44b4-be05-44ce-8be6-01f4ef348513" /> </p>

## 
<p align="center"> <img width="1917" height="841" alt="Captura de tela 2026-11-18 085710" src="https://github.com/user-attachments/assets/c03a464e-581c-405d-a620-ebf84a992589" /> </p>

##
<p align="center"> <img width="1917" height="886" alt="Captura de tela 2026-11-18 085350" src="https://github.com/user-attachments/assets/832942a8-e737-4aa7-8561-2908d3ef677b" /> </p>

##
<p align="center"> <img width="1916" height="867" alt="Captura de tela 2026-11-18 085409" src="https://github.com/user-attachments/assets/a5087593-1a13-4847-baa9-29bac61e0a39" /> </p>

##

### 📊 Painel de Indicadores
* **Atividades em Aberto:** `4`
* **Disciplinas em Alerta (Nota < 6.0):** `0`
* **Próximo Prazo:** `23/11/2026` *(Compiladores - Análise Léxica e Sintática)*
* **Nota Mínima Exigida:** `6.0`
* **Legenda de Status:** ✅ Concluído | ⏳ Em andamento | 📅 Pendente | ⚠️ Atrasado

## 🛠️ Tecnologias
Python 3.10+ · Streamlit · Pandas · SQLite · Tkinter (versão desktop) · Git & GitHub

## ▶️ Como executar
```bash
git clone https://github.com/cauapaivadecarvalho85-cmyk/Acompanhamento-de-Atividades-e-Notas.git
cd Acompanhamento-de-Atividades-e-Notas
pip install -r requirements.txt
streamlit run streamlit_app.py
```
No Linux, se faltar o Tkinter: `sudo apt install python3-tk`. O banco `academico.db` é criado automaticamente na primeira execução.


## 🌐 Versão web (Streamlit)
A versão web roda no navegador (`streamlit_app.py`) e compartilha as regras de cálculo e a camada SQLite com a versão desktop.

**No seu computador**
```bash
python -m streamlit run streamlit_app.py
```

**Dentro do GitHub (Codespaces)** — Code → Codespaces → *Create codespace on main*. O ambiente instala tudo e abre o app sozinho (porta 8501).

**Publicar online (Streamlit Community Cloud)** — em [share.streamlit.io](https://share.streamlit.io) escolha este repositório e o arquivo `streamlit_app.py`.

> ⚠️ O GitHub Pages não executa Python. No Streamlit Community Cloud, o armazenamento local não deve ser tratado como permanente: o arquivo `academico.db` pode ser perdido quando o ambiente for recriado. Para uso contínuo online, configure um banco externo persistente (por exemplo, PostgreSQL). Esta versão não possui autenticação: não publique dados acadêmicos pessoais em um app público. No computador e no Codespace, os dados ficam no arquivo local `academico.db`.

## 🧪 Testes
```bash
python -m unittest discover -s tests -t . -v
```

## ⚙️ Esquema do banco
| Tabela | Campos principais |
|---|---|
| `alunos` | id, nome, email |
| `disciplinas` | id, aluno_id → alunos, nome, periodo, media_minima |
| `atividades` | id, disciplina_id → disciplinas, titulo, descricao, prazo, peso, status |
| `notas` | id, atividade_id → atividades (única), valor (0–10) |

Todas as relações usam `ON DELETE CASCADE`.

## 🧮 Regras de cálculo
- **Média parcial** = Σ(nota × peso) ÷ Σ(peso das atividades já avaliadas).
- **Nota necessária** = (média mínima × Σ peso total − Σ pontos obtidos) ÷ Σ peso das atividades sem nota.
- Os pesos de todas as atividades cadastradas formam o total da disciplina; cadastre todas as avaliações previstas para a projeção ficar correta.
- **Em risco**: nota necessária > 10 · **Atenção**: nota necessária > 8 ou média parcial abaixo da mínima.

## 📁 Estrutura
```
main.py        ponto de entrada
ui.py          interface desktop (Tkinter)
streamlit_app.py  interface web (Streamlit, com temas claro/escuro)
.streamlit/config.toml  tema base (Azul)
database.py    esquema e CRUD (SQLite)
calculos.py    médias, nota necessária e situação
tests/         testes unitários
.github/       CI (Actions) e instruções do Copilot
```

## 👥 Colaboradores

- **Cauã Paiva**
- **Arthur Ferreira**
- **Josielly Macedo**
