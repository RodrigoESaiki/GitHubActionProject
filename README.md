# iOSGitHubActionProject
Esse projeto tem como objetivo mostrar como configurar sua CI utilizando o GithubActions em um projeto iOS ("Hello Word", buildar projeto e rodar testes).

## GitHub Actions
GitHub Actions ajuda você a automatizar tarefas dentro de seu ciclo de vida de desenvolvimento de software. GitHub Actions são orientados por eventos, o que significa que você pode executar uma série de comandos após um evento especificado ocorrer. Por exemplo, cada vez que alguém cria um pull request para um repositório, você pode executar automaticamente um comando que executa um script de teste do software.

## Criar um fluxo de trabalho
1. Adicione uma Action ao seu projeto criando uma pasta oculta .github e dentro dela uma outra pasta chamada workflows.
2. Dentro da pasta workflows crie um arquivo AlgumaCoisa.yml e ele será a Action. As actions podem ter qualquer nome, desde que sejam arquivos YAML.
3. Adicione o código a seguir.
`````
name: Run CI
on: [push, pull_request]

jobs:
  say_hello:
    name: Hello World
    runs-on: ubuntu-latest
    steps:
      - run: echo "Hello World"
`````
4. Faça commit dessas alterações e faça push para o seu repositório do GitHub. Seu novo arquivo de fluxo de trabalho de GitHub Actions agora está instalado no seu repositório e será executado automaticamente toda vez que alguém fizer push de uma alteração no repositório.

## Entendendo o arquivo de fluxo de trabalho
Para ajudar você a entender como a sintaxe de YAML é usada para criar um arquivo de fluxo de trabalho, esta seção explica cada linha do exemplo. Para mais exemplos de sintaxe acesse [Sintaxe de fluxo de trabalho para GitHub Actions](https://docs.github.com/en/actions/reference/workflow-syntax-for-github-actions#onpushpull_requestpaths)

| Sintaxe | Descrição |
| -------------| -----------|
| name: Run CI | Opcional - Como o nome do fluxo de trabalho irá aparecer na aba Ações do repositório de GitHub. |
| on: [push, pull_request] | Especifica o evento que aciona automaticamente o arquivo do fluxo de trabalho. Este exemplo usa o evento push e quando abre um pull request para que os trabalhos sejam executados toda vez que alguém fizer uma alteração no repositório. É possível definir o fluxo de trabalho para ser executado somente em determinados branches, caminhos ou tags. |
|jobs: | Agrupa todos os trabalhos executados no arquivo de fluxo de trabalho Run CI.|
|runs-on: ubuntu-latest | Configura o trabalho a ser executado em um executor do Ubuntu Linux. Isto significa que o trabalho será executado em uma nova máquina virtual hospedada pelo GitHub.|
|steps: | Agrupa todos os passos são executados no trabalho say_hello |

### Referencias
1. [GitHubActions](https://docs.github.com/pt/actions/learn-github-actions)
2. [Github Actions em um projeto iOS](https://ma-vasconcelos98.medium.com/github-actions-em-um-projeto-ios-f313d6b96d6f)
