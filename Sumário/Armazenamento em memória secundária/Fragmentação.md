### Conceito
- Falta de continuidade do armazenamento de dados.
- Decorrente do uso ineficiente de memória do sistema operacional
- Causa redução da memória utilizável
#### Fragmentação interna
- Para muitos file system, os blocos (menor unidade de armazena) possuem o mesmo tamanho
- Memória é fragmentada em espaços prefixados 
- É conveniente ajustar o tamanho do _cluster_ ao espaço ocupado pelos registros
- Registro ocorre através de _clusters_
![[Pasted image 20241021131345.png]]
- File Systems um arquivo começa no inicio do cluster, porém acaba antes do final do cluster;
- Inutilizando o espaço restante (_file slack_ ou _slack space_)
- _Fragmentação interna é difícil de recuperar_
- Tipo antigo de fragmentação interna: Codificação ASCII 8 bits: maioria dos caracteres usava somente 7 bits

#### Fragmentação Externa
- _Oferta de memória não contínua_
- Apagar um arquivo significa liberar o espaço ocupado pelo arquivo
- Alguns sistemas de alocação de espaço físico permitem muitos setores livres espalhados pelo disco
- Normalmente estes espaços livres são pequenos
- Estes blocos livres espalhados configuram a fragmentação externa
- O nome _externa_ vem das regiões pouco úteis que estão fora das regiões a serem alocadas
- _Ocorre em sistemas que trabalham intensamente com arquivos de tamanhos diferentes_
![[Pasted image 20241021132140.png]]
#### Fragmentação de Dados 
- _Ocorre quando uma estrutura de dados é dividida em partes que não estão próximas_
- Geralmente ocorre ao tentar alocar um arquivo grande em um sistema que já sofreu _fragmentação externa_

#### Exercício
![[Pasted image 20241021132926.png]]
#### Resolução
```
Capacidade da trilha: 840*512=430.080
Capacidade do cilindro: 430.080*11=4.730.880 Bytes
Tamanho do arquivo: 20.000*256=5.120.000 Bytes
Resposta: 2 cilindros
```