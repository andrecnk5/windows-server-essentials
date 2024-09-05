# Capítulo 2: Active Directory - Semana 4

## 1. FSMO roles e operações de domínio

### 1.1 Compreendendo as FSMO roles (Flexible Single Master Operation)
- Schema Master: Gerencia mudanças no schema do AD
- Domain Naming Master: Gerencia adição/remoção de domínios na floresta
- RID Master: Aloca pools de Relative Identifiers (RIDs) para DCs
- PDC Emulator: Sincroniza tempo, processa alterações de senha
- Infrastructure Master: Atualiza referências a objetos entre domínios

### 1.2 Transferência e apreensão de roles
- Transferência (recomendada):
```powershell
Move-ADDirectoryServerOperationMasterRole -Identity "DC02" -OperationMasterRole PDCEmulator
```
- Apreensão (em caso de falha do detentor atual):
```powershell
Move-ADDirectoryServerOperationMasterRole -Identity "DC02" -OperationMasterRole PDCEmulator -Force
```

### 1.3 Manutenção e recuperação de domain controllers
- Promoção de um servidor a DC
- Rebaixamento de um DC
- Remoção forçada de um DC falho:
```powershell
Remove-ADDomainControllerPasswordReplicationPolicy -Identity "DC01"
```

## 2. Replicação e troubleshooting

### 2.1 Funcionamento da replicação do AD
- Replicação intra-site vs. inter-site
- Topologia de replicação automática
- Compressão de replicação para links lentos

### 2.2 Monitoramento da saúde da replicação
- Uso do Replication Diagnostics Tool (repadmin):
```cmd
repadmin /showrepl
```
- Active Directory Replication Status Tool (adreplstatus)

### 2.3 Resolução de problemas comuns de replicação
- Verificação de conectividade de rede
- Resolução de conflitos de replicação
- Reinício forçado da replicação:
```cmd
repadmin /syncall
```

## 3. Backup e recuperação do AD

### 3.1 Estratégias de backup para o Active Directory
- System State Backup
- Full Server Backup
- Backup do AD usando Windows Server Backup

Exemplo de backup do System State via PowerShell:
```powershell
Wbadmin start systemstatebackup -backupTarget:E: -quiet
```

### 3.2 Recuperação de objetos excluídos
- Lixeira do Active Directory:
  - Habilitando a Lixeira do AD:
  ```powershell
  Enable-ADOptionalFeature 'Recycle Bin Feature' -Scope ForestOrConfigurationSet -Target 'contoso.com'
  ```
  - Recuperando objetos da Lixeira:
  ```powershell
  Get-ADObject -Filter {displayName -eq "John Doe"} -IncludeDeletedObjects | Restore-ADObject
  ```

### 3.3 Restauração do Active Directory em diferentes cenários
- Restauração não autoritativa: Restaura um DC sem sobrescrever alterações mais recentes
- Restauração autoritativa: Força a replicação de dados restaurados para outros DCs
- Restauração de todo o domínio em caso de desastre

## 4. Manutenção e otimização do AD

### 4.1 Limpeza de metadados do AD
- Remoção de objetos obsoletos
- Limpeza de registros DNS antigos
- Uso do comando `netdom` para limpeza de metadados

### 4.2 Desfragmentação do banco de dados do AD
- Redução do tamanho do arquivo ntds.dit
- Execução do utilitário ntdsutil:
```cmd
ntdsutil
activate instance ntds
files
compact to C:\temp\ntds.dit
```

### 4.3 Monitoramento de desempenho do AD
- Uso do Performance Monitor
- Contadores importantes para o AD:
  - LDAP Client Sessions
  - DS Directory Reads/sec
  - DS Directory Writes/sec

## Atividades práticas da Semana 4

1. Identifique os detentores atuais das FSMO roles em seu domínio de laboratório e transfira uma role para outro DC.
2. Configure a replicação entre dois sites e monitore o processo usando repadmin.
3. Realize um backup completo do System State em um DC e pratique a restauração em um ambiente de teste.
4. Habilite a Lixeira do AD e pratique a recuperação de um objeto excluído.
5. Use o Performance Monitor para coletar dados de desempenho do AD por 24 horas e analise os resultados.

## Recursos adicionais
- [Understanding FSMO Roles](https://docs.microsoft.com/en-us/windows-server/identity/ad-ds/plan/understanding-active-directory-site-topology)
- [Active Directory Replication Concepts](https://docs.microsoft.com/en-us/windows-server/identity/ad-ds/get-started/replication/active-directory-replication-concepts)
- [Active Directory Backup and Restore](https://docs.microsoft.com/en-us/windows-server/identity/ad-ds/manage/advanced-ad-ds-management-using-the-command-line)

## Avaliação de conhecimento
Ao final desta semana, você deve ser capaz de:
1. Explicar as FSMO roles e realizar transferências quando necessário.
2. Monitorar e solucionar problemas de replicação do AD.
3. Implementar estratégias de backup e recuperação para o Active Directory.
4. Realizar tarefas de manutenção e otimização do AD, como limpeza de metadados e desfragmentação do banco de dados.
5. Usar ferramentas de linha de comando e PowerShell para administração avançada do AD.
