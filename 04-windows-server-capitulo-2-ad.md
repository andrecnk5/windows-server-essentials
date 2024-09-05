# Capítulo 2: Active Directory (3-4 semanas)

## Semana 1: Introdução ao Active Directory

### 1. Conceitos fundamentais do Active Directory
- Definição e propósito do Active Directory
- Estrutura lógica: domínios, árvores e florestas
- Estrutura física: sites, domain controllers e replicação

### 2. Planejamento de uma infraestrutura AD
- Design de domínios e florestas
- Planejamento de sites e replicação
- Considerações de naming e DNS

### 3. Instalação e configuração inicial do AD DS
- Pré-requisitos para instalação do AD DS
- Promoção de um servidor a Domain Controller
- Configuração pós-instalação

## Semana 2: Gerenciamento de Objetos do AD

### 1. Usuários e grupos
- Criação e gerenciamento de contas de usuário
- Tipos de grupos (segurança vs. distribuição, escopo)
- Estratégias de nomeação e organização

### 2. Unidades Organizacionais (OUs)
- Propósito e design de OUs
- Delegação de controle administrativo
- Melhores práticas para estrutura de OUs

### 3. Computadores e outros objetos
- Adição de computadores ao domínio
- Gerenciamento de contas de computador
- Objetos de contato, impressora e compartilhamento

## Semana 3: Políticas de Grupo (Group Policy)

### 1. Fundamentos de Group Policy
- Conceito e propósito das GPOs
- Hierarquia e herança de políticas
- Processamento e aplicação de GPOs

### 2. Criação e gerenciamento de GPOs
- Uso do Group Policy Management Console (GPMC)
- Configurações de computador vs. usuário
- Templates administrativos e personalização

### 3. Implementação de políticas comuns
- Configurações de segurança
- Mapeamento de drives e impressoras
- Distribuição de software via GPO

## Semana 4: Tópicos Avançados e Manutenção

### 1. FSMO roles e operações de domínio
- Compreendendo as FSMO roles
- Transferência e apreensão de roles
- Manutenção e recuperação de domain controllers

### 2. Replicação e troubleshooting
- Funcionamento da replicação do AD
- Monitoramento da saúde da replicação
- Resolução de problemas comuns de replicação

### 3. Backup e recuperação do AD
- Estratégias de backup para o Active Directory
- Recuperação de objetos excluídos
- Restauração do Active Directory em diferentes cenários

## Atividades Práticas do Capítulo

1. Configure um ambiente de laboratório com dois domain controllers em um único domínio.
2. Crie uma estrutura de OUs, usuários e grupos seguindo as melhores práticas.
3. Implemente GPOs para configurar papéis de parede, mapeamento de drives e restrições de segurança.
4. Simule uma falha de domain controller e realize um processo de recuperação.
5. Use ferramentas como dcdiag e repadmin para diagnosticar e resolver problemas de replicação.

## Recursos Adicionais
- [Documentação oficial do Active Directory](https://docs.microsoft.com/en-us/windows-server/identity/ad-ds/active-directory-domain-services)
- Livro: "Active Directory: Designing, Deploying, and Running Active Directory" por Brian Desmond et al.
- [Curso online: Microsoft 70-742 Identity with Windows Server 2016](https://www.microsoft.com/en-us/learning/exam-70-742.aspx)

## Avaliação de Conhecimento do Capítulo
Ao final deste capítulo, você deve ser capaz de:
1. Explicar a estrutura e os conceitos fundamentais do Active Directory.
2. Planejar e implementar uma infraestrutura básica de AD.
3. Gerenciar eficientemente usuários, grupos e outros objetos do AD.
4. Criar e aplicar Group Policies para controlar configurações de usuários e computadores.
5. Realizar tarefas básicas de manutenção e troubleshooting no Active Directory.
