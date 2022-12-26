> **Aviso 1**: Esse blog post provavelmente vai ser atualizado no futuro.

> **Aviso 2**: Tentei adicionar o máximo de referências em português(Brasil), mas infelizmente a maior parte está escrita em inglês.

## Só pra recapitular, o que é o Terraform mesmo?
Baseado na definição da Hashicorp (em uma tradução literal):

> O Terraform é uma ferramenta de infraestrutura como código criado pela Hashicorp que permite definir recursos locais e/ou em nuvem em arquivos de configuração legíveis por humanos que você pode versionar, reutilizar e compartilhar. Você pode então usar um fluxo de trabalho consistente para provisionar e gerenciar todo ciclo de vida da sua infraestrutura.

A linguagem usada para escrever esses arquivos é o HCL (_Hashicorp Configuration Language_), mas também pode ser usado JSON.

Mais detalhes e a definição completa, você pode ver [aqui](https://developer.hashicorp.com/terraform/intro).

## Por onde começar?
É possível começar com os tutoriais oficiais na [plataforma da Hashicorp](https://developer.hashicorp.com/terraform/tutorials), ao menos para casos de uso mais comuns (com provedores de nuvem) tem bastante coisa:
* [Terraform com AWS](https://developer.hashicorp.com/terraform/tutorials/aws-get-started)
* [Terraform com Azure](https://developer.hashicorp.com/terraform/tutorials/azure-get-started)
* [Terraform com Google Cloud](https://developer.hashicorp.com/terraform/tutorials/gcp-get-started)

Também existem alguns cursos/tutoriais gratuitos no Youtube em português(Brasil), como:
* [Terraform 1.0 - do básico a módulos via Caio Delgado](https://www.youtube.com/watch?v=b7vbsx-pPJg)
* [Terraform 101 - Instalação e Deploy na AWS via Caio Delgado](https://www.youtube.com/watch?v=bYvdJKTwx_I)
* [Curso completo - do básico ao menos básico via Igor Sousa](https://www.youtube.com/watch?v=JayShFpuRdY&list=PLVGIivuHGmJpyciRgdZ-x4avdzlsdCTmH)

Outras recomendações no Youtube, em inglês:
* [Learn Terraform (and AWS) by Building a Dev Environment vi FreeCodeCamp](https://www.youtube.com/watch?v=iRaai1IBlB0)
* [Learn Terraform with Azure by Building a Dev Environment via FreeCodeCamp ](https://www.youtube.com/watch?v=V53AHWun17s)

E por último, e não menos importante, para quem gosta de livros, deixo a recomendação do [Terraform Up & Running](https://www.terraformupandrunning.com/).

## Agora que já sei usar (ao menos o básico), onde posso aprender as melhores práticas?
A forma de uso do Terraform muitas vezes varia de organização pra organização, mas existem alguns guias que valem a pena serem seguidos (ou ao menos adaptados para a criação de uma melhor prática interna):
* [Práticas recomendadas para usar o Terraform via Google Cloud](https://cloud.google.com/docs/terraform/best-practices-for-terraform?hl=pt-br#operational-best-practices)
* [Livro aberto com recomendações de melhores práticas](https://www.terraform-best-practices.com/v/ptbr/)
* [Guia completo de uso do Terraform via GruntWork](https://blog.gruntwork.io/a-comprehensive-guide-to-terraform-b3d32832baca)¹ 
     
¹Valeu pelo lembrete desse link [Pablo](https://www.linkedin.com/in/pmmenezes/).

Aqui também é importante citar que existem dois grandes grupos em uma discussão infinita quando se fala em organização dos projetos no Terraform:
* [time organiza por workspaces (me refiro a workspace no Terraform OSS, que é diferente do Terraform Cloud)](https://developer.hashicorp.com/terraform/cli/workspaces)
* [time organiza por diretórios, com Terragrunt](https://terragrunt.gruntwork.io/)

Recomendo ler sobre as duas opções e escolher a que traz mais benefícios para o seu cenário.

## Se Terraform é infra como código, quais opções eu tenho para testar meu código?

O tópico testes de infraestrutura como código ainda tem muito a ser discutido/melhorado, mas até agora, as opções que temos disponíveis são:
* [Terratest](https://terratest.gruntwork.io/): Framework de testes para Terraform, os testes devem ser escritos em Golang.
* [Kitchen Terraform](https://newcontext-oss.github.io/kitchen-terraform/getting_started.html): Plugins do Test Kitchen para testar código Terraform, testes devem ser escritos em Ruby.
* [Módulo Experimental de Testes](https://developer.hashicorp.com/terraform/language/modules/testing-experiment): Recurso builtin experimental do Terraform que permite que os testes sejam escritos em HCL e executados com o comando `terraform test`.

Deixo aqui também um artigo bem interessante da Hashicorp sobre o assunto: https://www.hashicorp.com/blog/testing-hashicorp-terraform.

## Existem ferramentas de segurança para fazer análise estática (ou algum outro tipo) do meu código Terraform?
Existem algumas ferramentas opensource que fazem análise estática e de erros de configuração no código e lint.
As mais usadas:
* [tfsec](https://github.com/aquasecurity/tfsec): ferramenta para análise de código estático e erros de configuração em código Terraform.
* [checkov](https://github.com/bridgecrewio/checkov): ferramenta para análise de código estático de IaC (infra como código), serve também para CloudFormation, Kubernetes e outros.
* [tflint](https://github.com/terraform-linters/tflint): Linter para Terraform, serve para avisar sobre problemas com sintaxe, erros nos principais provedores de nuvem, garantir boas práticas e outras coisas.

## Algum material de referência relacionado a Terraform no pipeline de CI/CD?
Falando das plataformas mais usadas, todas tem workflows reutilizáveis para Terraform.

Para Github Actions:
* https://developer.hashicorp.com/terraform/tutorials/automation/github-actions

Para Gitlab:
* https://docs.gitlab.com/ee/user/infrastructure/iac/

Para CircleCI:
* https://developer.hashicorp.com/terraform/tutorials/automation/circle-ci

## E caso eu já tenha recursos criados (manualmente), consigo importar para código HCL?
Esse normalmente é um processo doloroso (dependendo da quantidade de recursos), mas existem alguns utilitários que podem ajudar nisso:
* [Terraformer](https://github.com/GoogleCloudPlatform/terraformer): tem suporte para os maiores provedores de nuvem (GCP, AWS e Azure) e outros serviços (como PagerDuty).
* [Aztfy](https://github.com/Azure/aztfy): importa especificamente recursos da Azure.

## Comandos interessantes da CLI do Terraform
* [terraform console](https://developer.hashicorp.com/terraform/cli/commands/console): abre uma CLI interativa pra validar expressões.
* [terraform graph](https://developer.hashicorp.com/terraform/cli/commands/graph): gera uma visualização da configuração ou de um `plan`.

## Outras ferramentas que podem ser úteis
* [Atlantis](https://www.runatlantis.io/): Automação de Terraform via Pull Requests.
* [Infracost](https://github.com/infracost/infracost): Estimativas de custos nos Pull Requests.
* [Pre-commit Terraform](https://github.com/antonbabenko/pre-commit-terraform): git hooks com uma série de plugins pra Terraform.
* [Conftest](https://www.conftest.dev/): ferramenta para escrever testes estruturados usando Open Policy Agent.
* [Tfswitch](https://github.com/warrensbox/terraform-switcher): ferramenta de CLI pra gerenciar versões do Terraform.
* [Terraboard](https://github.com/camptocamp/terraboard): dashboard web para inspecionar states do Terraform.
* [Terraform Visual](https://github.com/hieven/terraform-visual): ferramenta para ter visualização interativa das mudanças em um `plan`.
* [Terraform-docs](https://terraform-docs.io/)²: utilitário para gerar documentação para os módulos Terraform.
* [K2tf](https://github.com/sl1pm4t/k2tf)³: utilitário para converter arquivos yaml do kubernetes para HCL.
* [IAM JSON para Terraform HCL](https://flosell.github.io/iam-policy-json-to-terraform/)³: utilitário para converter políticas IAM (AWS) em .json para HCL.

²: Valeu pelo lembrete [Arielson](https://www.linkedin.com/in/arielson-oliveira-91a73b1b1)   
³: Valeu pelo lembrete [Isac](https://www.linkedin.com/in/isaccavalcante)

---
Por agora é isso, provavelmente mais informações serão adicionadas no futuro :)


