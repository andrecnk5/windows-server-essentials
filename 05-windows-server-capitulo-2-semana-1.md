# Capítulo 2: Active Directory - Semana 1

## 1. Conceitos fundamentais do Active Directory

### 1.1 Definição e propósito do Active Directory
O Active Directory (AD) é um serviço de diretório desenvolvido pela Microsoft para redes de domínio Windows. Seus principais propósitos são:

- Fornecer um armazenamento centralizado para informações de rede
- Autenticar e autorizar usuários e computadores
- Facilitar a administração de recursos de rede
- Permitir a aplicação de políticas em larga escala

### 1.2 Estrutura lógica: domínios, árvores e florestas

#### Domínios
- Unidade básica de estrutura lógica no AD
- Contém objetos como usuários, grupos e computadores
- Compartilha políticas, relações de confiança e autenticação

#### Árvores
- Hierarquia de domínios que compartilham um namespace contíguo
- Exemplo: root.contoso.com, sub.root.contoso.com

#### Florestas
- Coleção de uma ou mais árvores de domínio
- Compartilham um esquema comum, catálogo global e configurações
- Permitem confiança entre domínios de diferentes árvores

### 1.3 Estrutura física: sites, domain controllers e replicação

#### Sites
- Representam localizações físicas na rede
- Usados para otimizar tráfego de replicação e autenticação

#### Domain Controllers (DCs)
- Servidores que executam o AD Domain Services (AD DS)
- Armazenam uma cópia completa do diretório para seu domínio
- Processam solicitações de login e buscas no diretório

#### Replicação
- Processo de sincronização de dados entre DCs
- Garante consistência das informações em toda a rede
- Usa topologia otimizada baseada em sites

## 2. Planejamento de uma infraestrutura AD

### 2.1 Design de domínios e florestas
- Considere a estrutura organizacional
- Avalie requisitos de segurança e autonomia
- Determine o número necessário de domínios e florestas

#### Estratégias comuns:
- Domínio único para organizações menores
- Múltiplos domínios para estruturas complexas ou distribuídas geograficamente
- Florestas separadas para isolamento de segurança

### 2.2 Planejamento de sites e replicação
- Mapeie locais físicos da organização para sites do AD
- Configure links de site baseados na conectividade de rede
- Otimize a replicação para economizar largura de banda

#### Melhores práticas:
- Crie sites para locais com 100 ou mais usuários
- Use compressão de replicação para links lentos
- Configure horários de replicação para períodos de baixo tráfego

### 2.3 Considerações de naming e DNS
- Escolha um namespace de domínio (ex: contoso.com)
- Planeje a estrutura de DNS interna
- Considere o uso de sufixos DNS adicionais para subdomínios

#### Dicas:
- Use nomes de domínio internos que não conflitem com nomes públicos
- Implemente zonas DNS integradas ao AD para melhor gerenciamento
- Configure encaminhadores DNS para resolução de nomes externos

## 3. Instalação e configuração inicial do AD DS

### 3.1 Pré-requisitos para instalação do AD DS
- Sistema operacional Windows Server (2016 ou posterior recomendado)
- Configuração de rede estática
- Servidor DNS instalado e configurado

### 3.2 Promoção de um servidor a Domain Controller
Passos básicos:
1. Instale o role AD DS usando Server Manager ou PowerShell
2. Execute a promoção do DC usando o assistente ou PowerShell
3. Escolha entre criar uma nova floresta ou adicionar a um domínio existente
4. Configure o NetBIOS name e o nível funcional do domínio/floresta
5. Especifique a localização da base de dados, logs e SYSVOL
6. Revise as opções e complete a instalação

Exemplo de comando PowerShell para instalar AD DS:
```powershell
Install-WindowsFeature -Name AD-Domain-Services -IncludeManagementTools
```

### 3.3 Configuração pós-instalação
- Verifique a saúde do DC usando dcdiag
- Configure zonas DNS reversas
- Ajuste as políticas de grupo padrão
- Implemente uma estratégia de backup para o AD

## Atividades práticas da Semana 1

1. Desenhe um diagrama da estrutura lógica e física do AD para uma empresa fictícia com três locais físicos.
2. Use uma máquina virtual para instalar o Windows Server e promovê-lo a Domain Controller de um novo domínio.
3. Configure um site do AD correspondente ao seu DC e simule um link de site para um local remoto.
4. Use o comando dcdiag para verificar a saúde do seu novo DC e interprete os resultados.

## Recursos adicionais
- [Documentação oficial do AD DS](https://docs.microsoft.com/en-us/windows-server/identity/ad-ds/get-started/virtual-dc/active-directory-domain-services-overview)
- [Planejamento da topologia do AD DS](https://docs.microsoft.com/en-us/windows-server/identity/ad-ds/plan/designing-the-site-topology)
- [Guia passo a passo de instalação do AD DS](https://docs.microsoft.com/en-us/windows-server/identity/ad-ds/deploy/install-active-directory-domain-services--level-100-)

## Avaliação de conhecimento
Ao final desta semana, você deve ser capaz de:
1. Explicar os conceitos fundamentais do Active Directory, incluindo sua estrutura lógica e física.
2. Planejar uma infraestrutura básica de AD, considerando domínios, sites e nomenclatura.
3. Instalar e configurar o AD DS em um servidor Windows, promovendo-o a Domain Controller.
4. Realizar verificações básicas de saúde em um novo Domain Controller.
