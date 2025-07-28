# Banco Web Tests

Este projeto tem como objetivo demonstrar, em portfólio, como automatizar testes de aplicações web utilizando [Cypress](https://www.cypress.io/) com JavaScript. Ele cobre cenários de testes end-to-end para a aplicação [Banco Web](https://github.com/juliodelimas/banco-web), consumindo a API [Banco API](https://github.com/juliodelimas/banco-api).

## Componentes do Projeto

- **Cypress**: Framework principal para automação dos testes.
- **Custom Commands**: Comandos personalizados para reutilização e organização do código de teste.
- **cypress-mochawesome-reporter**: Geração de relatórios detalhados dos testes.
- **Estrutura organizada**: Separação dos testes, fixtures e comandos customizados.

## Pré-requisitos

- [Node.js](https://nodejs.org/) (versão recomendada no `package.json`)
- [npm](https://www.npmjs.com/) ou [yarn](https://yarnpkg.com/)
- Clonar e executar:
  - [Banco API](https://github.com/juliodelimas/banco-api)
  - [Banco Web](https://github.com/juliodelimas/banco-web)

## Instalação

1. Clone este repositório:
   ```sh
   git clone <url-deste-repo>
   cd banco-web-tests
   ```
2. Instale as dependências:
   ```sh
   npm install
   ```

## Execução dos Testes

1. Certifique-se de que a API e a aplicação web estejam rodando localmente.
2. Para rodar os testes em modo headless e gerar o relatório:
   ```sh
   npx cypress run
   ```
3. Para abrir o Cypress em modo interativo:
   ```sh
   npx cypress open
   ```
4. Para visualizar o relatório após a execução:
   - O relatório HTML será gerado em `cypress/reports/html/index.html`.

## Estrutura dos Testes

- `cypress/e2e/`: Contém os arquivos de teste automatizados.
- `cypress/support/commands.js`: Custom Commands para facilitar a escrita dos testes.
- `cypress/fixtures/`: Dados de teste reutilizáveis.

### Exemplos de Custom Commands

No arquivo `cypress/support/commands.js` estão definidos comandos como:

```javascript
// Exemplo de comando customizado para login
Cypress.Commands.add('login', (usuario, senha) => {
  cy.visit('/login')
  cy.get('input[name="usuario"]').type(usuario)
  cy.get('input[name="senha"]').type(senha)
  cy.get('button[type="submit"]').click()
})
```

Utilização no teste:
```javascript
cy.login('usuario_teste', 'senha123')
```

### Cenários de Teste Automatizados

- Login e autenticação de usuários
- Transferências válidas e inválidas

## Relatórios

Os relatórios são gerados automaticamente após a execução dos testes e podem ser encontrados em `cypress/reports/html/index.html`, com detalhes de cada cenário executado.

---