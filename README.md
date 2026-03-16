# DESAFIO-QA-BEEDOO-2026  
## Analista de Qualidade de Software Júnior

Este repositório contém a documentação dos testes realizados na aplicação de gestão de cursos, conforme proposto no desafio de QA 2026. O objetivo principal foi validar os fluxos de cadastro, listagem e exclusão, garantindo que as regras de negócio e a integridade dos dados fossem respeitadas.

## Tecnologias e Ferramentas

* **Aplicação Alvo:** [Acessar Site](https://creative-sherbet-a51eac.netlify.app/)
* **Navegador:** Google Chrome
* **Documentação:** [Planilha de Testes](https://docs.google.com/spreadsheets/d/1m6cJc-gJsyxEqW_lx8piJSCGa4WqfpMLVR0VJ67-5oI/edit?gid=22151257#gid=22151257)
* **Ferramentas de Inspeção:** Chrome DevTools (Console, Network, Application/LocalStorage)

---

## Planejamento e Estratégia de Testes

A estratégia adotada seguiu o ciclo de vida de teste (STLC):
* **Testes Exploratórios:** Para entender o comportamento do sistema e mapear funcionalidades.
* **Testes de Caminho Feliz (Happy Path):** Validar se a funcionalidade principal opera conforme o esperado.
* **Testes de Exceção e Negativos:** Validar como o sistema reage a entradas inválidas ou inconsistentes.
* **Análise de Fronteira:** Testar limites de campos numéricos e datas.
* **Verificação Técnica:** Inspeção de requisições HTTP e persistência em LocalStorage.

---

| ID | Cenário | Objetivo | Status |
| :--- | :--- | :--- | :--- |
| **CT-001** | Cadastrar novo curso | Validar fluxo principal de cadastro. | [❌ Falhou](evidencias-BUG001) |
| **CT-002** | Excluir curso selecionado | Validar remoção de registro da lista e do banco. | [❌ Falhou](evidencias-BUG002) |
| **CT-003** | Validação de regra cronológica | Impedir data de término anterior à data de início. | [❌ Falhou](evidencias-BUG003) |
| **CT-004** | Validação de campos obrigatórios | Impedir cadastro de formulário vazio. | [❌ Falhou](evidencias-BUG004) |
| **CT-005** | Integridade de dados (Vagas) | Impedir números negativos ou decimais em vagas. | [❌ Falhou](evidencias-BUG005) |

---

## Relatório de Bugs Encontrados
Durante a execução, foram identificados 5 defeitos críticos que impactam a experiência do usuário e a integridade do sistema.

**Destaques Técnicos:**
* **BUG-002 (Erro 405):** Identificada tentativa de deleção em endpoint estático (`/courses/1`) com método HTTP não permitido, indicando código chumbado (*hardcoded*).
* **BUG-003/005 (Tipagem):** Detectado que campos numéricos e de data estão sendo tratados como `Strings` no LocalStorage, o que impossibilita validações lógicas automáticas.
* **BUG-004 (UX/Validação):** Ausência total de validação de formulário no Front-end, permitindo registros vazios.

> **Nota:** O detalhamento completo de cada bug (Passos para reproduzir, Resultado Atual vs Esperado e Evidências) está disponível na documentação técnica anexada.

---

## Análise e Tomada de Decisão (Etapa 2)

### **Metodologia de Investigação**
Utilizei o **Chrome DevTools** para realizar o *troubleshooting* das falhas encontradas. O objetivo foi realizar uma análise de causa raiz, distinguindo erros no Front-end de falhas estruturais de comunicação e persistência.

### **Investigação do BUG-002 (Falha na Exclusão)**
Ao validar o cenário de exclusão (CT-002), identifiquei que a operação não era persistida. Através da aba **Network**, constatei dois problemas críticos:
1. **Erro de Método:** A aplicação dispara uma requisição com o método **HTTP DELETE**, porém o servidor retorna o status **405 (Method Not Allowed)**.
2. **Parâmetro Estático (Hardcoded):** A URL da requisição utiliza um **ID estático (/courses/1)** independentemente do curso selecionado, impedindo a exclusão de outros registros.

*Nota Técnica: A ausência de uma documentação de API (como Swagger ou OpenAPI) impossibilitou a validação do contrato esperado.*

### **Vulnerabilidades e Integridade de Dados**
Identifiquei que o sistema não possui validações de entrada no Front-end para campos obrigatórios, datas ou valores numéricos.
* **Risco:** A falta de tipagem (armazenamento como `String` no `LocalStorage`) representa um risco à integridade, permitindo valores negativos ou datas inconsistentes que podem causar quebras de layout.

### **Priorização de Correções**
Classifiquei os bugs de **Exclusão** e **Falta de Validação** com prioridade **ALTA**, pois impedem o gerenciamento básico dos dados (CRUD) e comprometem a confiabilidade da base de dados.

---



## Contato
**João Carlos Moreira Rodrigues** 
[LinkedIn](https://www.linkedin.com/in/joaocmr) |  [GitHub](https://github.com/joao-cmr)  |  contatojoaocmr@gmail.com
