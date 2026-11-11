# Simulado-Sistemas-em-Nuvem

# Simulado Pratico de Computacao em Nuvem

## Identificacao

- **Aluno:** Mayran Juvenal Milani 
- **Turma:** 4° Semestre
- **Data:** 11/11/2026
- **Ambiente:** Killercoda
- **Tecnologia:** Kubernetes

## 1. Objetivo

Este projeto tem como objetivo demonstrar conhecimentos praticos
sobre computacao em nuvem e orquestracao de containers utilizando
Kubernetes.

Foram realizadas atividades de configuracao de cluster, namespace,
ConfigMap, Secret, ServiceAccount, RBAC, Deployment, Service,
probes, escalabilidade, autorrecuperacao, atualizacao, rollback,
Job e CronJob.

## 2. Atividades realizadas

- Verificacao do cluster Kubernetes.
- Criacao do namespace simulado-nuvem.
- Criacao e atualizacao de ConfigMaps.
- Configuracao de Secret e ServiceAccount.
- Configuracao de permissoes RBAC.
- Criacao de Deployment com duas replicas.
- Exposicao da aplicacao por meio de Service.
- Configuracao de Readiness e Liveness Probes.
- Testes de comunicacao HTTP.
- Escalabilidade de duas para tres replicas.
- Teste de autorrecuperacao apos exclusao de Pod.
- Atualizacao da pagina para a versao 2.
- Simulacao de falha com imagem inexistente.
- Recuperacao por meio de rollback.
- Criacao de CronJob e execucao de Job.

## 3. Perguntas teoricas

### 1. Qual e a diferenca entre container, Pod e Deployment?

**Container:** e o ambiente que executa a aplicacao e suas
dependencias.

**Pod:** e a menor unidade de execucao do Kubernetes. Pode conter
um ou mais containers que compartilham recursos de rede e
armazenamento.

**Deployment:** e o recurso responsavel por gerenciar os Pods,
manter a quantidade desejada de replicas e controlar atualizacoes
da aplicacao.

### 2. Por que ConfigMap e Secret tem finalidades diferentes?

O ConfigMap armazena configuracoes que nao sao confidenciais,
como arquivos HTML, parametros e variaveis de ambiente.

O Secret e destinado a informacoes sensiveis, como senhas,
tokens e credenciais.

O Secret deve ser protegido com controles de acesso e criptografia
adequada, pois sua existencia nao garante confidencialidade
automaticamente.

### 3. Qual a diferenca entre Readiness e Liveness?

A Readiness Probe verifica se a aplicacao esta pronta para receber
requisicoes. Se falhar, o Pod deixa de receber trafego pelo Service.

A Liveness Probe verifica se a aplicacao continua funcionando.
Se falhar repetidamente, o Kubernetes pode reiniciar o container.

### 4. O que ocorreu apos a exclusao do Pod?

Apos a exclusao manual de um Pod, o Deployment identificou que
a quantidade de replicas estava abaixo do valor desejado.

O Kubernetes criou automaticamente outro Pod para manter
a quantidade configurada de duas replicas.

Esse comportamento demonstra a autorrecuperacao do Kubernetes.

### 5. O que o rollback recuperou? A pagina voltou a versao 1?

O rollback recuperou a revisao anterior do Deployment, incluindo
a imagem valida utilizada antes da atualizacao com a imagem
inexistente.

A pagina nao voltou automaticamente para a versao 1.

Isso aconteceu porque o ConfigMap e o Deployment sao recursos
independentes. O rollback do Deployment nao restaura
automaticamente o conteudo do ConfigMap.

Como o ConfigMap continuou na versao 2, a aplicacao voltou
a funcionar utilizando a pagina da versao 2.

### 6. Qual a diferenca entre Deployment, Job e CronJob?

**Deployment:** gerencia aplicacoes que precisam permanecer
em execucao, mantendo a quantidade desejada de replicas.

**Job:** executa uma tarefa ate que ela seja concluida com sucesso.

**CronJob:** agenda a execucao de Jobs em horarios ou intervalos
definidos, utilizando uma expressao cron.

## 4. Estrutura do repositorio

```text
simulado-nuvem-nome-sobrenome/
├── README.md
├── manifests/
│   ├── 01-configmap-v1.yaml
│   ├── 02-configmap-v2.yaml
│   ├── 03-rbac.yaml
│   ├── 04-web.yaml
│   └── 05-cronjob.yaml
├── scripts/
│   └── comandos.sh
└── evidencias/
    └── resultados.md
```

## 5. Evidencias

As evidencias da execucao pratica estao documentadas
em `evidencias/resultados.md`.

O arquivo apresenta as saidas dos comandos utilizados
para comprovar as atividades realizadas.

## 6. Conclusao

O laboratorio proporcionou experiencia pratica com os principais
recursos do Kubernetes.

Foi possivel compreender como o Kubernetes gerencia aplicacoes,
controla replicas, realiza atualizacoes, recupera falhas e executa
tarefas programadas.

O projeto demonstra a importancia da orquestracao de containers
para a disponibilidade, escalabilidade e manutencao de aplicacoes
em ambientes de computacao em nuvem.
