# README - CI/CD com GitLab

Este projeto utiliza o GitLab para automatizar o processo de integração contínua (CI) e entrega contínua (CD). Abaixo estão detalhados os estágios do pipeline e como você pode configurar e executar os testes, criar imagens e fazer o deploy utilizando o GitLab CI/CD.

## Estrutura do Pipeline

O pipeline foi configurado com três estágios principais:

1. **Teste**: Executa testes automatizados para validar a integridade do código.
2. **Build**: Criação das imagens ou builds necessárias para o projeto.
3. **Deploy**: Implantação do projeto em um ambiente de produção ou staging.

## Configuração do GitLab CI/CD

### Regras de Execução

O fluxo de trabalho é configurado com as seguintes regras:

```yaml
workflow:
  rules:
    - if: $CI_COMMIT_BRANCH == "main"
      when: never
    - when: always # Para todas as outras branches
sso garante que o pipeline não será executado automaticamente para a branch main, apenas para outras branches.

## Stages e Jobs
1. Teste
Descrição: Este estágio executa testes automatizados para garantir a qualidade do código antes de continuar com os estágios subsequentes.

## Jobs:

executar_teste:

Descrição: Executa testes definidos no script script.sh.
Antes do script: Prepara o ambiente para execução dos testes.
Depois do script: Limpa arquivos temporários após a execução dos testes.
executar_teste2:

Descrição: Executa um segundo conjunto de testes.
Script: Executa um comando simples para simular um teste adicional.
2. Build
Descrição: Este estágio é responsável por criar imagens ou builds necessárias para o projeto.

## Jobs:

criar_imagens:

Descrição: Cria imagens necessárias para o projeto.
push_imagens:

Descrição: Realiza o upload das imagens criadas para um registro de contêineres.
3. Deploy
Descrição: Este estágio realiza a implantação do projeto em um ambiente de produção ou staging.

## Jobs:

kubernetes:
Descrição: Executa o deploy do projeto em um ambiente Kubernetes.
Como Utilizar Este Projeto
Pré-requisitos
GitLab CI/CD configurado para o repositório.
Acesso ao ambiente Kubernetes configurado no GitLab para o deploy.
