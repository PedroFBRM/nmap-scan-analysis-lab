# Nmap Scan Analysis Lab

[English](#english) | [Português](#portugues)

---

<a id="english"></a>

## English

### Objective

This project demonstrates basic network reconnaissance and service enumeration in an isolated lab environment using Kali Linux and Metasploitable3.

The goal is to identify exposed services, collect evidence, and analyze the findings from a Blue Team perspective.

### Environment

- VirtualBox
- Kali Linux (Attacker)
- Metasploitable3 (Target)
- Isolated virtual network

### Steps Performed

1. Configured both virtual machines on the same network
2. Identified the target IP address
3. Verified connectivity using ICMP (`ping`)
4. Performed a basic Nmap scan
5. Performed a service version scan using Nmap
6. Saved scan outputs for further analysis

### Commands Used

```bash
ip a
ping -c 4 10.0.2.4
nmap 10.0.2.4 -oN basic_scan.txt
nmap -sV 10.0.2.4 -oN service_scan.txt
```

### Findings

#### Open Ports

- `21/tcp` - FTP - ProFTPD 1.3.5
- `22/tcp` - SSH - OpenSSH 6.6.1p1
- `80/tcp` - HTTP - Apache 2.4.7
- `445/tcp` - SMB - Samba 3.X - 4.X
- `631/tcp` - IPP - CUPS 1.7
- `3306/tcp` - MySQL - Unauthorized
- `8080/tcp` - HTTP - Jetty 8.1.7

### Analysis

The target system exposes multiple services, significantly increasing its attack surface.

The most critical finding is MySQL running on port `3306` without authentication, which could allow unauthorized access to the database.

Additionally, legacy services such as ProFTPD `1.3.5` and Samba are present, both associated with known vulnerabilities, including potential remote code execution.

Several services are outdated, including:

- Apache `2.4.7` (2013)
- OpenSSH `6.6.1p1` (2014)
- Jetty `8.1.7` (2012)

These outdated versions may contain multiple unpatched vulnerabilities.

Overall, the system demonstrates a weak security posture due to exposed services, lack of access control, and outdated software.

### Defensive Perspective

From a Blue Team perspective, the following actions are recommended:

- Restrict access to critical services such as MySQL and SMB
- Disable unnecessary services such as FTP and IPP
- Update outdated software to supported versions
- Implement firewall rules to reduce exposure
- Enforce authentication and encryption where applicable
- Monitor logs for suspicious activity and anomalies

### Evidence

#### Screenshots

- `01-target_ip.png`
- `02-connectivity_test.png`
- `03-basic_nmap_scan.png`
- `04-service_version_scan.png`
- `05-scans.png`

#### Scan Files

- `basic_scan.txt`
- `service_scan.txt`

### Repository Structure

```text
nmap-scan-analysis-lab/
├── README.md
├── basic_scan.txt
├── service_scan.txt
├── 01-target_ip.png
├── 02-connectivity_test.png
├── 03-basic_nmap_scan.png
├── 04-service_version_scan.png
└── 05-scans.png
```

### Conclusion

This lab demonstrates how simple enumeration techniques can reveal critical security issues.

It highlights the importance of minimizing exposed services, maintaining updated systems, and implementing proper defensive controls.

---

<a id="portugues"></a>

## Português

### Objetivo

Este projeto demonstra reconhecimento de rede e enumeração de serviços em um ambiente isolado utilizando Kali Linux e Metasploitable3.

O objetivo é identificar serviços expostos, coletar evidências e analisar os resultados sob a perspectiva de Blue Team.

### Ambiente

- VirtualBox
- Kali Linux (Atacante)
- Metasploitable3 (Alvo)
- Rede virtual isolada

### Etapas Realizadas

1. Configuração das máquinas virtuais na mesma rede
2. Identificação do IP do alvo
3. Validação da conectividade com `ping`
4. Execução de scan básico com Nmap
5. Execução de scan de versão de serviços com Nmap
6. Salvamento dos resultados para análise posterior

### Comandos Utilizados

```bash
ip a
ping -c 4 10.0.2.4
nmap 10.0.2.4 -oN basic_scan.txt
nmap -sV 10.0.2.4 -oN service_scan.txt
```

### Resultados

#### Portas Abertas

- `21/tcp` - FTP - ProFTPD 1.3.5
- `22/tcp` - SSH - OpenSSH 6.6.1p1
- `80/tcp` - HTTP - Apache 2.4.7
- `445/tcp` - SMB - Samba 3.X - 4.X
- `631/tcp` - IPP - CUPS 1.7
- `3306/tcp` - MySQL - Sem autenticação
- `8080/tcp` - HTTP - Jetty 8.1.7

### Análise

O sistema alvo expõe múltiplos serviços, aumentando significativamente sua superfície de ataque.

O achado mais crítico é o MySQL na porta `3306` sem autenticação, o que pode permitir acesso não autorizado ao banco de dados.

Além disso, serviços legados como ProFTPD `1.3.5` e Samba estão presentes, ambos associados a vulnerabilidades conhecidas, incluindo possibilidade de execução remota de código.

Diversos serviços estão desatualizados, incluindo:

- Apache `2.4.7` (2013)
- OpenSSH `6.6.1p1` (2014)
- Jetty `8.1.7` (2012)

Essas versões antigas podem conter múltiplas vulnerabilidades não corrigidas.

No geral, o sistema apresenta uma postura de segurança fraca devido à exposição de serviços, ausência de controle de acesso e uso de software desatualizado.

### Perspectiva Defensiva

Do ponto de vista de Blue Team, as seguintes ações são recomendadas:

- Restringir o acesso a serviços críticos como MySQL e SMB
- Desabilitar serviços desnecessários, como FTP e IPP
- Atualizar softwares desatualizados para versões suportadas
- Implementar regras de firewall para reduzir exposição
- Aplicar autenticação e criptografia quando cabível
- Monitorar logs em busca de atividades suspeitas e anomalias

### Evidências

#### Screenshots

- `01-target_ip.png`
- `02-connectivity_test.png`
- `03-basic_nmap_scan.png`
- `04-service_version_scan.png`
- `05-scans.png`

#### Arquivos de Scan

- `basic_scan.txt`
- `service_scan.txt`

### Estrutura do Repositório

```text
nmap-scan-analysis-lab/
├── README.md
├── basic_scan.txt
├── service_scan.txt
├── 01-target_ip.png
├── 02-connectivity_test.png
├── 03-basic_nmap_scan.png
├── 04-service_version_scan.png
└── 05-scans.png
```

### Conclusão

Este laboratório demonstra como técnicas simples de enumeração podem revelar falhas críticas de segurança.

Também destaca a importância de reduzir a exposição de serviços, manter sistemas atualizados e aplicar controles defensivos adequados.
