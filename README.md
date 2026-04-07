# ubuntu-apache-vm

[![GitHub license](https://img.shields.io/github/license/R-TENORIO/ubuntu-apache-vm)](https://github.com/R-TENORIO/ubuntu-apache-vm/blob/main/LICENSE)
[![Ubuntu](https://img.shields.io/badge/Ubuntu-24.04-orange)](https://ubuntu.com/)
[![Apache](https://img.shields.io/badge/Apache-2.4-blue)](https://httpd.apache.org/)

## Descrição

Projeto acadêmico da Unidade 4 - Atividade 1 (U4-A1) do curso de Engenharia de Software. Este repositório documenta a virtualização de um servidor web utilizando Ubuntu Server e Apache, criado como parte dos estudos em DevOps e infraestrutura.

## Arquitetura

```
┌─────────────────────────────────────┐
│         VirtualBox / VMware         │
│  ┌───────────────────────────────┐  │
│  │      Ubuntu Server 24.04      │  │
│  │  ┌─────────────────────────┐  │  │
│  │  │   Apache HTTP Server    │  │  │
│  │  │      (Port 80)          │  │  │
│  │  └─────────────────────────┘  │  │
│  └───────────────────────────────┘  │
└─────────────────────────────────────┘
```

## Pré-requisitos

- [VirtualBox](https://www.virtualbox.org/) ou [VMware Workstation](https://www.vmware.com/products/workstation-pro.html)
- ISO do [Ubuntu Server 24.04 LTS](https://ubuntu.com/download/server)
- Mínimo de 4GB de RAM disponível no host
- Mínimo de 20GB de armazenamento livre

## Passo a Passo

### 1. Criação da VM

1. Abra o VirtualBox e clique em **"Novo"**
2. Nome: `ubuntu-server`
3. Tipo: **Linux**
4. Versão: **Ubuntu (64-bit)**
5. Memória RAM: **4096 MB**
6. Disco rígido: **25 GB** (VDI, alocação dinâmica)

### 2. Instalação do Ubuntu Server

1. Monte a ISO do Ubuntu Server nas configurações de Armazenamento
2. Inicie a VM
3. Siga o assistente de instalação:
   - Idioma: Português (Brasil)
   - Teclado: Português (Brasil)
   - Configuração de rede: DHCP (padrão)
   - Usuário: seu nome de usuário
   - Instalação do OpenSSH Server: **Sim**
   - Software adicional: **Sem pacotes extras**

### 3. Instalação do Apache

```bash
# Atualizar repositórios
sudo apt update && sudo apt upgrade -y

# Instalar Apache
sudo apt install apache2 -y

# Verificar status do serviço
sudo systemctl status apache2

# Habilitar Apache na inicialização
sudo systemctl enable apache2

# Verificar IP da máquina
ip addr show
```

### 4. Testar Acesso

No navegador do host, acesse:
```
http://<IP_DA_VM>
```

Você deve ver a página padrão do Apache.

## Comandos Úteis

| Ação | Comando |
|------|---------|
| Iniciar Apache | `sudo systemctl start apache2` |
| Parar Apache | `sudo systemctl stop apache2` |
| Reiniciar Apache | `sudo systemctl restart apache2` |
| Recarregar config | `sudo systemctl reload apache2` |
| Ver logs | `sudo tail -f /var/log/apache2/access.log` |
| Ver erros | `sudo tail -f /var/log/apache2/error.log` |

## Troubleshooting

### Apache não inicia
```bash
sudo systemctl status apache2
sudo journalctl -xe
```

### Porta 80 já em uso
```bash
sudo netstat -tlnp | grep :80
```

### Problema de firewall
```bash
sudo ufw allow 'Apache Full'
sudo ufw status
```

## Evidências

As evidências do projeto (prints da instalação e configuração) estão na pasta `docs/evidencias/`.

## Autor

**Rodrigo Tenorio** - @R-TENORIO
Estudante de Engenharia de Software | DevOps & Automação

## Licença

Este projeto está sob a licença MIT - veja o arquivo [LICENSE](LICENSE) para mais detalhes.
