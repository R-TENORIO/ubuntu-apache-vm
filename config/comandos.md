# Comandos Utilizados no Projeto

Documentação de todos os comandos executados durante a instalação e configuração do servidor web.

---

## 1. Atualização do Sistema

```bash
# Atualizar lista de pacotes
sudo apt update

# Atualizar pacotes instalados
sudo apt upgrade -y
```

---

## 2. Instalação do Apache

```bash
# Instalar Apache HTTP Server
sudo apt install apache2 -y
```

---

## 3. Gerenciamento do Serviço Apache

```bash
# Verificar status do serviço
sudo systemctl status apache2

# Iniciar o serviço
sudo systemctl start apache2

# Parar o serviço
sudo systemctl stop apache2

# Reiniciar o serviço
sudo systemctl restart apache2

# Recarregar configurações
sudo systemctl reload apache2

# Habilitar na inicialização
sudo systemctl enable apache2

# Desabilitar na inicialização
sudo systemctl disable apache2
```

---

## 4. Verificação de Rede

```bash
# Verificar endereços IP
ip addr show

# Versão resumida
ip a

# Verificar portas em uso
sudo netstat -tlnp

# Alternativa com ss
sudo ss -tlnp

# Verificar se a porta 80 está ativa
sudo netstat -tlnp | grep :80
```

---

## 5. Logs do Apache

```bash
# Acompanhar logs de acesso em tempo real
sudo tail -f /var/log/apache2/access.log

# Acompanhar logs de erro em tempo real
sudo tail -f /var/log/apache2/error.log

# Ver últimas 50 linhas do log de acesso
sudo tail -n 50 /var/log/apache2/access.log

# Ver últimas 50 linhas do log de erro
sudo tail -n 50 /var/log/apache2/error.log
```

---

## 6. Firewall (UFW)

```bash
# Permitir tráfego Apache completo
sudo ufw allow 'Apache Full'

# Verificar status do firewall
sudo ufw status

# Ativar firewall
sudo ufw enable
```

---

## 7. Comandos Auxiliares

```bash
# Verificar versão do Apache
apache2 -v

# Verificar versão completa
apache2 -V

# Testar configuração do Apache
sudo apache2ctl configtest

# Listar módulos ativos
apache2ctl -M

# Verificar espaço em disco
df -h

# Verificar uso de memória
free -h

# Verificar hostname
hostname

# Verificar data e hora
date
```

---

## 8. Localização dos Arquivos

| Arquivo/Local | Caminho |
|--------------|----------|
| Página web padrão | `/var/www/html/index.html` |
| Configuração principal | `/etc/apache2/apache2.conf` |
| Logs de acesso | `/var/log/apache2/access.log` |
| Logs de erro | `/var/log/apache2/error.log` |
| Sites disponíveis | `/etc/apache2/sites-available/` |
| Sites habilitados | `/etc/apache2/sites-enabled/` |
| Módulos disponíveis | `/etc/apache2/mods-available/` |
| Módulos habilitados | `/etc/apache2/mods-enabled/` |

---

## 9. Comandos de Diagnóstico

```bash
# Ver journal do systemd para o Apache
sudo journalctl -u apache2

# Ver journal em tempo real
sudo journalctl -f

# Ver informações do sistema
uname -a

# Ver versão do Ubuntu
cat /etc/os-release
```

---

## 10. Reinicialização

```bash
# Reiniciar o sistema
sudo reboot

# Desligar o sistema
sudo shutdown -h now
```
