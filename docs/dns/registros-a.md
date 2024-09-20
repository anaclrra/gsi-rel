# Registros de Recurso do DNS
## Configuração DNS

Antes de adicionar registros DNS, é essencial que o samba-tool esteja corretamente configurado e que o Samba esteja funcionando como um controlador de domínio, permitindo a gestão de DNS.
- [Instalação do SAMBA](../samba/instalacao.md)

Use o seguinte comando para listar todos os registros de sua zona:

- samba-tool dns query 127.0.0.1 "alagoas.lab" @ ALL -U administrator

    - ![saída](/docs/dns/assets/samba-tool-dns-query.png)

Adicione os registros A, cada um associando um nome de host a um endereço IP específico.

 - ![saída](/docs/dns/assets/samab-tool-dns-add-penedo.png "Adiciona Host Penedo")
 - ![saída](/docs/dns/assets/samba-tool-dns-add-maragogi.png "Adiciona Host Maragogi")
 - ![saída](/docs/dns/assets/samba-tool-dns-add-piranhas.png "Adiciona Host Piranhas")

  Os registros A criados permitem que dispositivos na sua rede local resolvam nomes de host em seus respectivos endereços IP. Isso facilita a comunicação entre máquinas, pois os usuários podem usar nomes amigáveis em vez de memorizar endereços IP.

 - ![saída](/docs/dns/assets/samba-tool-dns-query_2.png "Verifica hosts adicionados")

 ---
 Com os registros adicionados, agora é possível que qualquer máquina na rede que consulte o DNS do servidor Samba consiga resolver os nomes especificados para os endereços IP correspondentes, permitindo um gerenciamento mais fácil e eficiente da rede.