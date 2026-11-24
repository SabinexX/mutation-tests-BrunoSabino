# Testes unitários e testes de mutação — Bruno Sabino

Atividade de Mutation Tests — SATC, professor Leandro Antunes Ugioni.
Projeto baseado no trabalho anterior de testes unitários em JavaScript com Jest.

[![Mutation Tests](https://github.com/SabinexX/prova1-unit-tests-BrunoSabino/actions/workflows/mutation.yml/badge.svg)](https://github.com/SabinexX/prova1-unit-tests-BrunoSabino/actions/workflows/mutation.yml)

## Objetivo

Avaliar a capacidade dos testes unitários existentes de identificar alterações artificiais no código-fonte. O Stryker Mutator modifica temporariamente expressões, operadores e condições e executa os testes Jest para verificar se eles detectam essas alterações.

## Execução local

Requisito: Node.js 22 LTS e npm.

```bash
npm install
npm test
npm run coverage
npm run test:mutation
```

Use `npm install` na primeira execução para atualizar o lockfile com as novas dependências. Depois disso, registre o package-lock.json atualizado no Git.

## Estrutura

- `src/`: os 12 módulos originais em JavaScript.
- `test/`: os 12 arquivos de testes unitários originais.
- `stryker.config.json`: configuração do Stryker com Jest e análise de cobertura por teste.
- `.github/workflows/mutation.yml`: execução automática no GitHub Actions.
- `reports/mutation/`: relatórios gerados pelo Stryker.

## Relatório

O Stryker analisa os arquivos `src/**/*.js`, sem alterar permanentemente os fontes. O relatório HTML é gerado em `reports/mutation/mutation.html` e o relatório JSON em `reports/mutation/mutation.json`.

No GitHub, abra **Actions → Mutation Tests → execução mais recente → Artifacts → mutation-report**. Extraia o arquivo baixado e abra o HTML no navegador.

- Killed: mutação detectada por um teste.
- Survived: mutação não detectada pelos testes.
- No coverage: mutação em código não executado pelos testes.
- Timeout: execução excedeu o limite de tempo.
- Mutation score: proporção de mutações detectadas entre as mutações válidas.

Os limites de referência são 80% (alto) e 60% (baixo). O resultado efetivo será produzido pela execução da ferramenta; nenhum valor foi preenchido manualmente.

## Exemplo de mutação

Uma operação de soma pode ser substituída por uma subtração. Se os testes verificarem o resultado correto para entradas que distinguem as operações, o mutante será detectado. Caso contrário, a mutação pode sobreviver, indicando uma oportunidade de melhorar as verificações.

## Referências

- [Stryker Mutator](https://stryker-mutator.io/)
- [Integração com Jest](https://stryker-mutator.io/docs/stryker-js/jest-runner/)
- [Jest](https://jestjs.io/)
