# Capítulo 2: Active Directory - Semana 2

## 1. Usuários e grupos

### 1.1 Criação e gerenciamento de contas de usuário

#### Criação de contas de usuário
- Usando o Active Directory Users and Computers (ADUC)
- Usando PowerShell

Exemplo de criação de usuário com PowerShell:
```powershell
New-ADUser -Name "João Silva" -GivenName "João" -Surname "Silva" -SamAccountName "joao.silva" -UserPrincipalName "joao.silva@contoso.com" -AccountPassword (ConvertTo-SecureString "P@ssw0rd" -AsPlainText -Force) -Enabled $true
```

#### Propriedades importantes de usuários
- Nome completo, nome de login (SAM Account Name)
- UPN (User Principal Name)
- Senha e políticas de senha
- Grupos de associação
- Local de armazenamento (OU)

#### Gerenciamento de contas
- Habilitar/desabilitar contas
- Redefinição de senha
- Configuração de expiração de conta

### 1.2 Tipos de grupos

#### Grupos de segurança
- Usados para atribuir permissões
- Podem conter usuários, computadores e outros grupos

#### Grupos de distribuição
- Usados principalmente para listas de e-mail
- Não podem ser usados para atribuir permissões

#### Escopos de grupo
1. Domain Local
   - Podem conter membros de qualquer domínio na floresta
   - Usados para atribuir permissões dentro do domínio
2. Global
   - Podem conter membros apenas do domínio em que são criados
   - Usados para agrupar objetos com características similares
3. Universal
   - Podem conter membros de qualquer domínio na floresta
   - Listados no Catálogo Global

### 1.3 Estratégias de nomeação e organização
- Use nomes descritivos e consistentes
- Considere prefixos para indicar função ou departamento
- Implemente uma estratégia de grupo aninhado para facilitar o gerenciamento

Exemplo de convenção de nomenclatura:
- SG_TI_Admins (Grupo de Segurança para Administradores de TI)
- GG_Vendas (Grupo Global para o departamento de Vendas)

## 2. Unidades Organizacionais (OUs)

### 2.1 Propósito e design de OUs
- Organizar objetos do AD logicamente
- Facilitar a aplicação de Group Policies
- Delegar controle administrativo

### 2.2 Criação e gerenciamento de OUs
- Usando ADUC
- Usando PowerShell

Exemplo de criação de OU com PowerShell:
```powershell
New-ADOrganizationalUnit -Name "Departamento de TI" -Path "DC=contoso,DC=com"
```

### 2.3 Delegação de controle administrativo
- Conceder permissões específicas a usuários ou grupos sobre OUs
- Usar o "Delegation of Control Wizard" no ADUC

### 2.4 Melhores práticas para estrutura de OUs
- Baseie a estrutura em requisitos administrativos, não na estrutura organizacional
- Mantenha a hierarquia simples e rasa quando possível
- Considere o impacto na aplicação de Group Policies

Exemplo de estrutura de OU:
```
Contoso
├── Computadores
│   ├── Desktops
│   └── Servidores
├── Usuários
│   ├── Funcionários
│   └── Contratados
└── Grupos
```

## 3. Computadores e outros objetos

### 3.1 Adição de computadores ao domínio
- Processo de ingresso no domínio
- Contas de computador no AD

Exemplo de adição de computador com PowerShell (executado no computador cliente):
```powershell
Add-Computer -DomainName "contoso.com" -Credential (Get-Credential) -Restart
```

### 3.2 Gerenciamento de contas de computador
- Redefinição de conta de computador
- Movimentação entre OUs
- Desativação e exclusão de contas de computador

### 3.3 Objetos de contato, impressora e compartilhamento
- Criação e gerenciamento de contatos
- Publicação de impressoras no AD
- Objetos de compartilhamento para facilitar o acesso a recursos

Exemplo de criação de contato com PowerShell:
```powershell
New-ADObject -Type "contact" -Name "Fornecedor XYZ" -DisplayName "Fornecedor XYZ" -Path "OU=Contatos,DC=contoso,DC=com"
```

## Atividades práticas da Semana 2

1. Crie uma estrutura de OUs para uma empresa fictícia com pelo menos três departamentos.
2. Adicione usuários e grupos a estas OUs, seguindo uma convenção de nomenclatura consistente.
3. Use PowerShell para criar um script que adicione múltiplos usuários de uma só vez, baseado em um arquivo CSV.
4. Configure a delegação de controle para permitir que um usuário não-administrador gerencie as contas em uma OU específica.
5. Adicione um computador ao domínio e mova sua conta para a OU apropriada.

## Recursos adicionais
- [Gerenciamento de contas de usuário no AD](https://docs.microsoft.com/en-us/windows-server/identity/ad-ds/manage/manage-user-accounts-in-active-directory)
- [Melhores práticas para design de OU](https://docs.microsoft.com/en-us/windows-server/identity/ad-ds/plan/planning-ou-design)
- [Gerenciamento de grupos no AD](https://docs.microsoft.com/en-us/windows-server/identity/ad-ds/manage/manage-groups-in-active-directory)

## Avaliação de conhecimento
Ao final desta semana, você deve ser capaz de:
1. Criar e gerenciar contas de usuário e grupos no Active Directory.
2. Entender e implementar diferentes tipos e escopos de grupos.
3. Projetar e implementar uma estrutura eficiente de Unidades Organizacionais.
4. Realizar tarefas de gerenciamento de objetos do AD usando tanto a interface gráfica quanto o PowerShell.
5. Adicionar e gerenciar contas de computador no domínio.
