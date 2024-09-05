# Semana 1: Fundamentos do Windows Server

## 1. Arquitetura do Windows Server

### 1.1 História e evolução do Windows Server
- Windows NT Server (1993) - primeiro servidor dedicado da Microsoft
- Windows 2000 Server (2000) - introdução do Active Directory
- Windows Server 2003, 2008, 2012, 2016, 2019, 2022 - evolução contínua

### 1.2 Arquitetura de 32-bit vs. 64-bit
- 32-bit: limite de 4 GB de RAM
- 64-bit: suporte para mais de 4 GB de RAM, melhor desempenho
- Windows Server moderno é exclusivamente 64-bit desde o Server 2008 R2

### 1.3 Componentes principais do sistema operacional
- Kernel: núcleo do sistema, gerencia recursos de hardware
- HAL (Hardware Abstraction Layer): interface entre hardware e software
- Executive: gerenciamento de processos, memória, E/S
- Subsistemas de ambiente: Win32, POSIX
- Drivers de dispositivo: interface com hardware específico

### 1.4 Diferenças entre Windows Server e Windows Desktop
- Funcionalidades de servidor (roles e features)
- Licenciamento e modelo de atualização
- Interface do usuário (Server Core vs GUI completa)
- Limites de hardware suportado (RAM, CPUs)

## 2. Edições e licenciamento

### 2.1 Edições disponíveis
- **Standard**: para ambientes físicos ou levemente virtualizados
- **Datacenter**: para ambientes altamente virtualizados ou cloud
- **Essentials**: para pequenas empresas (até 25 usuários, 50 dispositivos)

### 2.2 Modelos de licenciamento
- **Por núcleo**: baseado no número de núcleos físicos do servidor
  - Mínimo de 16 licenças de núcleo por servidor
  - Vendido em pacotes de 2 ou 16 núcleos
- **CAL (Client Access License)**: necessário para cada usuário ou dispositivo que acessa o servidor

### 2.3 Comparação de recursos entre as edições
| Recurso                    | Standard | Datacenter | Essentials |
|----------------------------|----------|------------|------------|
| Direitos de virtualização  | 2 VMs    | Ilimitado  | 1 VM       |
| Storage Replica            | Limitado | Completo   | Não        |
| Shielded Virtual Machines  | Não      | Sim        | Não        |
| Software-Defined Networking| Não      | Sim        | Não        |

### 2.4 Escolhendo a edição adequada para diferentes cenários
- Pequenas empresas: Essentials
- Empresas médias com virtualização limitada: Standard
- Grandes empresas ou provedores de serviços em nuvem: Datacenter

## Atividades práticas da Semana 1

1. Pesquise e crie uma linha do tempo visual da evolução do Windows Server.
2. Compare as especificações de hardware recomendadas para Windows Server 2022 Standard e Datacenter.
3. Utilize a calculadora de licenciamento da Microsoft para determinar as licenças necessárias para um servidor com 24 núcleos físicos.
4. Crie um documento comparando as características das edições Standard, Datacenter e Essentials do Windows Server 2022.

## Recursos adicionais
- [Documentação oficial do Windows Server](https://docs.microsoft.com/en-us/windows-server/)
- [Guia de licenciamento por volume da Microsoft](https://www.microsoft.com/en-us/licensing/product-licensing/windows-server)
- Livro: "Windows Server 2022 Inside Out" de Orin Thomas

## Avaliação de conhecimento
Ao final desta semana, você deve ser capaz de:
1. Explicar a evolução do Windows Server e suas principais versões.
2. Diferenciar entre arquiteturas de 32-bit e 64-bit.
3. Identificar os componentes principais do sistema operacional Windows Server.
4. Distinguir entre as diferentes edições do Windows Server e seus modelos de licenciamento.
5. Selecionar a edição apropriada do Windows Server para cenários específicos.
