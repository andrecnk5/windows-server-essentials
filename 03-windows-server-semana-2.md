# Semana 2: Fundamentos do Windows Server

## 1. Instalação e configuração inicial

### 1.1 Requisitos de hardware
- Processador: 1.4 GHz 64-bit
- RAM: 512 MB (Server Core), 2 GB (com Desktop Experience)
- Espaço em disco: 32 GB
- Adaptador de rede: Gigabit Ethernet
- Nota: Requisitos variam conforme a carga de trabalho planejada

### 1.2 Métodos de instalação
- **GUI (Graphical User Interface)**: 
  - Interface gráfica completa
  - Mais fácil para administradores iniciantes
  - Consome mais recursos
- **Server Core**: 
  - Interface de linha de comando
  - Menor superfície de ataque
  - Menor consumo de recursos
  - Requer mais conhecimento em PowerShell

### 1.3 Processo de instalação passo a passo
1. Inicializar o servidor a partir da mídia de instalação
2. Selecionar idioma e configurações regionais
3. Escolher entre "Instalar agora" ou "Reparar o computador"
4. Inserir a chave do produto ou pular para avaliação
5. Selecionar a edição do Windows Server
6. Aceitar os termos de licença
7. Escolher entre instalação limpa ou upgrade
8. Selecionar o disco de instalação e particionamento
9. Aguardar a conclusão da instalação

### 1.4 Configurações iniciais pós-instalação
- Definir senha do administrador
- Configurar rede (IP, máscara de sub-rede, gateway, DNS)
- Atualizar o sistema com Windows Update
- Configurar nome do computador
- Configurar fuso horário
- Ativar Remote Desktop (se necessário)

### 1.5 Ativação do Windows Server
- Ativação online automática
- Ativação por telefone
- Ativação usando Key Management Service (KMS)
- Ativação usando Active Directory-Based Activation (ADBA)

## 2. Interface de gerenciamento

### 2.1 Server Manager
- Visão geral da interface
- Adicionando roles e features
- Gerenciamento de servidores remotos
- Criação e gerenciamento de grupos de servidores
- Configuração de Best Practices Analyzer

### 2.2 PowerShell para administração
- Introdução ao PowerShell
- Cmdlets básicos para administração de servidor:
  - `Get-Command`: lista comandos disponíveis
  - `Get-Help`: obtém ajuda sobre comandos
  - `Get-Service`: lista serviços do sistema
  - `Get-Process`: lista processos em execução
  - `Get-WindowsFeature`: lista roles e features disponíveis
- Executando scripts PowerShell
- Configuração de políticas de execução

### 2.3 Comandos básicos do PowerShell para gerenciamento de servidor
```powershell
# Obter informações do sistema
Get-ComputerInfo

# Listar roles e features instaladas
Get-WindowsFeature | Where-Object {$_.InstallState -eq "Installed"}

# Adicionar uma role ou feature
Install-WindowsFeature -Name Web-Server -IncludeManagementTools

# Reiniciar o servidor
Restart-Computer

# Gerenciar serviços
Get-Service | Where-Object {$_.Status -eq "Running"}
Start-Service -Name "BITS"
Stop-Service -Name "Print Spooler"
```

### 2.4 Configuração de acesso remoto
- Remote Desktop:
  - Habilitando Remote Desktop
  - Configurando firewall para Remote Desktop
  - Conectando-se via Remote Desktop Protocol (RDP)
- Windows Admin Center:
  - Instalação e configuração
  - Gerenciamento de servidores remotos via browser
  - Recursos e limitações

## Atividades práticas da Semana 2

1. Realize uma instalação do Windows Server 2022 (pode ser em máquina virtual).
2. Configure as definições básicas de rede usando tanto a GUI quanto o PowerShell.
3. Instale e remova o role de Web Server (IIS) usando o Server Manager e o PowerShell.
4. Crie um script PowerShell que liste todos os serviços em execução e o salve em um arquivo de texto.
5. Configure o acesso remoto ao seu servidor e conecte-se usando Remote Desktop e Windows Admin Center.

## Recursos adicionais
- [Documentação oficial de instalação do Windows Server](https://docs.microsoft.com/en-us/windows-server/get-started/getting-started-with-server-with-desktop-experience)
- [Guia do PowerShell para iniciantes](https://docs.microsoft.com/en-us/powershell/scripting/learn/ps101/01-getting-started)
- [Tutorial do Windows Admin Center](https://docs.microsoft.com/en-us/windows-server/manage/windows-admin-center/overview)

## Avaliação de conhecimento
Ao final desta semana, você deve ser capaz de:
1. Realizar uma instalação básica do Windows Server.
2. Executar configurações iniciais pós-instalação.
3. Navegar e utilizar o Server Manager para tarefas básicas de administração.
4. Executar comandos básicos do PowerShell para gerenciamento de servidor.
5. Configurar e utilizar opções de acesso remoto ao servidor.
