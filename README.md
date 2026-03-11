# DESAFIO-QA-BEEDOO-2026  
## Analista de Qualidade de Software Júnior

Este repositório contém a documentação dos testes realizados na aplicação de gestão de cursos, conforme proposto no desafio de QA 2026. O objetivo principal foi validar os fluxos de cadastro, listagem e exclusão, garantindo que as regras de negócio e a integridade dos dados fossem respeitadas.

## Tecnologias e Ferramentas

**Aplicação Alvo:** https://creative-sherbet-a51eac.netlify.app/

**Navegador:** https://www.google.com/chrome/ 

**Documentação:** https://docs.google.com/spreadsheets/d/1m6cJc-gJsyxEqW_lx8piJSCGa4WqfpMLVR0VJ67-5oI/edit?gid=22151257#gid=22151257

**Ferramentas de Inspeção:** Chrome DevTools (Console, Network, Application/LocalStorage)

----

## Planejamento e Estratégia de Testes

A estratégia adotada seguiu o ciclo de vida de teste (STLC)
Testes exploratórios para entender o comportamento do sistema e suas funcionalidades
Testes de Caminho Feliz (Happy Path): Validar se a funcionalidade principal opera conforme o esperado.
Testes de Exceção e Negativos: Validar como o sistema reage a entradas inválidas ou inconsistentes.
Análise de Fronteira: Testar limites de campos numéricos e datas.
Verificação Técnica: Inspeção de requisições HTTP e persistência em LocalStorage.

----
| ID | Cenário | Objetivo | Status |
| :--- | :--- | :--- | :--- |
| **CT-001** | Cadastrar novo curso | Validar fluxo principal de cadastro. | [❌ Falhou](evidencias-BUG001) |
| **CT-002** | Excluir curso selecionado | Validar remoção de registro da lista e do banco. | [❌ Falhou](evidencias-BUG002) |
| **CT-003** | Validação de regra cronológica | Impedir data de término anterior à data de início. | [❌ Falhou](evidencias-BUG003) |
| **CT-004** | Validação de campos obrigatórios | Impedir cadastro de formulário vazio. | [❌ Falhou](evidencias-BUG004) |
| **CT-005** | Integridade de dados (Vagas) | Impedir números negativos ou decimais em vagas. | [❌ Falhou](evidencias-BUG005) |
