Configuração do systemd para o Partido Pirata
===

Arquivos de configuração residentes no diretório `/lib/systemd/system/` para os serviços do [partido pirata](http://partidopirata.org).

Tarefas comuns
---

### Instalar serviços na máquina

Presumindo que o sistema é Debian

```bash
$ git clone https://github.com/piratas/systemd.d.git
# rsync -avhP systemd.d/*.service /lib/systemd/system/
```

### Habilitar serviço na inicialização do sistema

Isto deve ser feito para cada serviço. Para habilitar todos, faça um loop em bash ou outra linguagem de script.  
Usando o serviço `apoio.service` como exemplo:

```bash
# systemctl enable apoio.service
```

### Iniciar serviço

```bash
# systemctl start apoio.service
```

### Verificar estado do serviço

```bash
# systemctl -l status apoio.service
```

### Monitorar serviço e reiniciar em caso de queda


```bash
# crontab -e
```

Adicionar linha na crontab do root:

```cron
*/5 * * * * /bin/systemctl is-active apoio.service || /bin/systemctl start apoio.service
```

Isto vai testar o serviço de 5 em 5 minutos. É possível usar `@daily` ou `@hourly` no lugar de `*/5 * * * *` para verificar diariamente e horariamente, respectivamente.

