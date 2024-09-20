# Explicação de seu DN do LDAP no IFRN

>Em uma máquina Window do IFRN, execute, no CMD, o comando `whoami /fqdn`.

Na árvore *DIT (Directory Information Tree)* do LDAP, cada entrada é identificada por um *DN* (Distinguished Name). O *DN* representa o caminho completo para a entrada dentro da árvore, começando pela raiz e descendo até a entrada específica. Vamos detalhar os principais componentes com base no exemplo fornecido:

### DN (Distinguished Name)
O *DN* é o identificador único de uma entrada na árvore LDAP. Ele é composto por uma sequência de RDNs (Relative Distinguished Names), que descrevem o caminho até a entrada. No exemplo:

| CN           | OU   | OU  | OU    | OU     | DC   | DC   |
|--------------|-------|------|--------|---------|-------|-------|
| 20221148060012 | Alunos | DG-PAR | RE | IFRN | ifrn  | local |



Este é o DN completo da entrada que estamos referenciando.

### RDN (Relative Distinguished Name)
O *RDN* é a parte do DN que descreve a entrada em relação ao seu pai direto na árvore. É o identificador da entrada em um determinado nível do LDAP. No exemplo, o *RDN* mais específico é:


| CN            |
|---------------|
| 20221148060012|  



Aqui, CN (Common Name) é o atributo e 20221148060012 é o valor desse atributo.

### DC (Domain Component)
O *DC* indica os componentes de um domínio DNS e é utilizado para identificar o domínio ao qual a entrada pertence. No exemplo:


| DC    | DC    |
|-------|-------|
| ifrn  | local |



Isso representa o domínio ifrn.local.

### OU (Organizational Unit)
A *OU* é uma Unidade Organizacional, usada para organizar entradas em subgrupos dentro da árvore LDAP. No exemplo, temos várias *OUs*:


| OU     | OU     | OU  | OU   |
|------- |--------|-----|-------
| Alunos | DG-PAR | RE  | IFRN |


Cada uma dessas *OUs* representa uma categoria dentro da hierarquia da organização.

### CN (Common Name)
O *CN* é o nome comum da entrada, que geralmente é usado para identificar pessoas ou objetos. No exemplo:


| CN            |
|---------------|
| 20221148060012|  



Aqui, 20221148060012 é o identificador único da entrada, que pode ser um código associado a um aluno.

---

Em resumo, o *DN* descreve a localização exata de uma entrada dentro da árvore LDAP, enquanto os componentes *RDN, **DC, **OU, e **CN* ajudam a organizar e identificar essa entrada dentro de um contexto hierárquico e estruturado.

!!! tip " Manuscrito digitalizado para [PDF](https://drive.google.com/file/d/12CZjSWiZXpsoIbzvlHm8UznKoGIhKwKt/view?usp=drivesdk)"