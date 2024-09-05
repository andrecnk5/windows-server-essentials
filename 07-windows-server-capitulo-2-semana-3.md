# Capítulo 2: Active Directory - Semana 3

## 1. Fundamentos de Group Policy

### 1.1 Conceito e propósito das GPOs (Group Policy Objects)
- Definição: Conjunto de configurações que podem ser aplicadas a usuários e computadores em um ambiente Active Directory
- Propósito: Gerenciar e padronizar configurações em larga escala

### 1.2 Hierarquia e herança de políticas
- Ordem de processamento:
  1. Local
  2. Site
  3. Domínio
  4. Unidade Organizacional (OU)
- Herança: Políticas de níveis superiores são herdadas por níveis inferiores
- Bloqueio de herança e forçar aplicação de políticas

### 1.3 Processamento e aplicação de GPOs
- Frequência de atualização: Por padrão, a cada 90 minutos para computadores e 5 minutos para Domain Controllers
- Atualização manual: `gpupdate /force`
- Resultant Set of Policy (RSoP): Ferramenta para visualizar políticas aplicadas

## 2. Criação e gerenciamento de GPOs

### 2.1 Uso do Group Policy Management Console (GPMC)
- Acessando o GPMC: Server Manager > Tools > Group Policy Management
- Criação de uma nova GPO:
  1. Clique com o botão direito em "Group Policy Objects"
  2. Selecione "New"
  3. Nomeie a GPO
  4. Edite as configurações conforme necessário

### 2.2 Configurações de computador vs. usuário
- Computer Configuration: Aplica-se à máquina, independente do usuário logado
- User Configuration: Aplica-se ao usuário, independente da máquina utilizada
- Desabilitando parte não utilizada da GPO para melhorar o desempenho

### 2.3 Templates administrativos e personalização
- Localização dos templates padrão: %SystemRoot%\PolicyDefinitions
- Criação de templates personalizados usando ADMX/ADML files
- Central Store: Armazenamento centralizado de templates administrativos

### 2.4 Filtragem e escopo de GPOs
- Security Filtering: Aplicar GPOs apenas a usuários, grupos ou computadores específicos
- WMI Filtering: Aplicar GPOs com base em critérios específicos do sistema

### 2.5 Backup e restauração de GPOs
- Importância do backup regular de GPOs
- Uso do GPMC para backup e restauração

Exemplo de backup de GPO via PowerShell:
```powershell
Backup-GPO -All -Path "C:\GPOBackups"
```

## 3. Implementação de políticas comuns

### 3.1 Configurações de segurança
- Políticas de senha:
  - Comprimento mínimo
  - Complexidade
  - Histórico de senhas
- Bloqueio de conta:
  - Número de tentativas
  - Duração do bloqueio
- Auditoria de eventos de segurança

Exemplo de configuração de política de senha via PowerShell:
```powershell
Set-ADDefaultDomainPasswordPolicy -Identity contoso.com -MinPasswordLength 14 -ComplexityEnabled $true
```

### 3.2 Mapeamento de drives e impressoras
- Uso de Group Policy Preferences para mapear drives de rede
- Implantação de impressoras via GPO

### 3.3 Distribuição de software via GPO
- Preparação do pacote de software (MSI preferencial)
- Configuração da GPO para distribuição:
  1. Computer Configuration > Policies > Software Settings > Software Installation
  2. Adicionar novo pacote
  3. Escolher entre "Assigned" ou "Published"

### 3.4 Configurações de desktop e Start Menu
- Personalização do papel de parede corporativo
- Restrições de acesso ao Painel de Controle
- Configuração de atalhos padrão

### 3.5 Scripts de logon/logoff e startup/shutdown
- Localização dos scripts: %SystemRoot%\SYSVOL\sysvol\dominio\Policies\GPO_ID\Machine\Scripts
- Tipos de scripts: .bat, .cmd, .vbs, .ps1

## Atividades práticas da Semana 3

1. Crie uma GPO que define uma política de senha forte e aplique-a ao domínio.
2. Implemente uma GPO para mapear um drive de rede para um departamento específico.
3. Use Group Policy Preferences para instalar uma impressora em todos os computadores de uma OU.
4. Crie uma GPO que distribui um software (ex: 7-Zip) para todos os computadores do domínio.
5. Implemente uma GPO que executa um script de logon para usuários de um departamento específico.

## Recursos adicionais
- [Documentação oficial de Group Policy](https://docs.microsoft.com/en-us/windows/client-management/introduction-to-group-policy)
- [Group Policy for Beginners](https://docs.microsoft.com/en-us/windows-server/identity/ad-ds/manage/group-policy/group-policy-for-beginners)
- [Group Policy Planning and Deployment Guide](https://docs.microsoft.com/en-us/windows-server/identity/ad-ds/plan/group-policy-planning-and-deployment-guide)

## Avaliação de conhecimento
Ao final desta semana, você deve ser capaz de:
1. Explicar os conceitos fundamentais de Group Policy, incluindo herança e processamento.
2. Criar e gerenciar GPOs usando o Group Policy Management Console.
3. Implementar políticas comuns para configurações de segurança, mapeamento de recursos e distribuição de software.
4. Utilizar Group Policy Preferences para configurações mais flexíveis.
5. Realizar troubleshooting básico de aplicação de políticas usando ferramentas como gpresult e RSoP.
