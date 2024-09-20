<!--  # Instalação do SAMBA

Pontuação: [30 pontos] 

Documente a instalação do Samba no Alpine Linux

Dica: 

1. Use o [aplicativo ChatGPT do Celular](https://play.google.com/store/apps/details?id=com.openai.chatgpt&hl=pt_BR)
2. Copie a resposta (Formato Markdown)
3. Cole em uma conversa do WhatsApp com seu colega de grupo
4. Abra o [WhatsApp Web](https://web.whatsapp.com/) em um PC/Notebook
5. Copie o conteúdo da conversa, que deve estar no formato Markdown, e cole em sua documentação.

!!! note "Dica de *prompt* para o [ChatGPT](https://chatgpt.com)" 

- Como instalar um servidor Samba como contraldor de domínio do ActiveDirectory. O sistema operacional é o Alpine Linux. O domínio "<estado>.lab".
 -->

# Instalação do SAMBA

Instalar um servidor Samba como controlador de domínio do Active Directory no Alpine Linux envolve várias etapas. Aqui está um guia passo a passo:

1. Instalar Pacotes Necessários

Primeiro, você precisa instalar os pacotes necessários. Abra o terminal e execute:

``` apk update  ```   
```apk add samba samba-client openrc```


2. Configurar o Samba

Crie um diretório para os arquivos de configuração:

```mkdir /etc/samba```

3. Configurar o arquivo smb.conf

Edite o arquivo de configuração do Samba:

```vi /etc/samba/smb.conf```

Adicione as seguintes linhas:

```
[global]
   workgroup = ALAGOAS
   realm = alagoas.lab
   netbios name = MACEIO
   server role = active directory domain controller
   dns forwarder = 8.8.8.8  ; (ou outro servidor DNS de sua escolha)
   idmap config * : backend = tdb
   idmap config * : range = 10000-99999

[netlogon]
   path = /var/lib/samba/sysvol/alagoas.lab/scripts
   read only = no

[sysvol]
   path = /var/lib/samba/sysvol
   read only = no
```

4. Inicializar o Samba

Execute o comando para provisionar o domínio:

```samba-tool domain provision --use-rfc2307 --interactive```

Durante a execução, você será solicitado a fornecer informações como o nome do domínio, nome do administrador e senha.

5. Configurar o DNS

Após o provisionamento, configure o Samba para fornecer serviços DNS. Verifique se o serviço named (BIND) está instalado e configurado corretamente.

Adicione a configuração do DNS no /etc/samba/smb.conf se necessário.

6. Criar Diretórios Necessários

Crie os diretórios necessários para o Sysvol e Netlogon:

```mkdir -p /var/lib/samba/sysvol/alagoas.lab/scripts```

7. Iniciar os Serviços

Ative e inicie o Samba:

```rc-update add samba default
service samba start```

8. Verificar o Status

Verifique se o Samba está rodando corretamente:

```samba-tool domain level show```

9. Testar a Configuração

Verifique se o DNS e o controlador de domínio estão funcionando corretamente. Você pode usar o comando:

```nslookup alagoas.lab```

10. Conectar Clientes ao Domínio

Agora você pode adicionar máquinas clientes ao domínio .lab configurando-as para usar o servidor DNS do Samba.

Observações Finais

Certifique-se de que as portas necessárias (como 53, 88, 135, 139, 389, 445 e 464) estejam abertas no firewall. Além disso, faça backups regulares de suas configurações e dados.