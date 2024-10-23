### Tipos fundamentais de memória
- Classes de memória:
	- Primária: RAM
	- Secundária: Discos Magnéticos
- Só a RAM permite acesso direto e aleatório a informação
- Custo RAM é maior se comparado ao disco
- Quantidade de informação armazenada em disco é maior do que em RAM
#### Forma e tempo de acesso
- *Comparativamente aos discos*
- Tempo de aceso a arquivos, menor em RAM se feito copiando-se integralmente o arquivo para RAM
- Tempo de acesso a arquivos, maior em RAM se feito com cópias parciais (swap)
- Custo (tempo) de acesso a RAM ($10^{-9}$), menor do que o custo de acesso ao disco ($10^{-3}$)
- _Complexidade de acesso_ está relacionado ao custo de transferência entre memória primária e secundária
- _Tempo de acesso_ está relacionado ao tempo necessário para encontrar o primeiro setor do arquivo onde está a informação
- Setores subsequentes podem ter o tempo de acesso menor do que o primeiro
#### Redução de complexidade
- _Objetivo_: Minimizar o número de vezes que o arquivo é transferido da memória secundária para a primária
#### Conceitos de endereçamento
- Exemplo de um livro físico;
- _Física_: Capa, contracapa, lombada, orelhas, miolo, folhas
- _Lógica_:Título, autores, editora, ano
- Divisões semelhantes ocorre com os discos

### Estrutura física de um disco
#### Trilhas
![[Pasted image 20241021082903.png]]
- _'A'_= trilha; _'B'_= setor; _'D'_=cluster;
- As trilhas são divisões concêntricas do disco;
- Trilhas têm diâmetros diferentes, então possuem medidas de circunferências distintas;
- Uma trilha interna pode ter comprimento x e uma trilha mais externa pode ter comprimento x+y bytes
#### Trilhas não são a única subdivisão física do disco
- As trilhas armazenam grande quantidade de bytes
- Na prática é necessário subdividir para armazenar
- É necessário atribuir endereços uniformes às partes do disco
#### Setores
- Unidade mínima de armazenamento em disco;
- Subdivisão da trilha;
- Tamanho: tradicionalmente (antes 2011) 512 bytes para HD e 2048 para CD-ROMS
- Cada trilha passa a ter um número definido de setores
- Espaços inutilizáveis são inevitáveis
- Espaços inutilizados podem variar dependendo do tamanho da trilha
- Pela _figura 1_ :
	- _'B'_= Setor, _'C'_= Track setor;
##### Blocos
- Na prática os sistemas operam com _blocos_ de dados
- _Blocos_ são unidades lógicas 
- Um _bloco_ pode corresponder a vários setores
![[Pasted image 20241021085502.png]]
- Como vemos na figura acima o número de setores por trilhas são variáveis dependendo da posição da trilha;
#### Cilindro
![[Pasted image 20241021085851.png]]
- Nos discos existem pelo menos duas cabeças de I/O, uma para cada face do disco.
- _'Cilindro'_= Definido pela posição do braço;
- _'Cabeça'_= Define o prato (lado) do disco;
- _'Setor'_= Define a fração da trilha;

### Estrutura lógica de um disco
- O método de divisão do disco implica em duas abordagens para o mapeamento das sub-regiões das trilhas:
	- _Mapeamento por geometria_$\to$ Físico, os dados são armazenados a partir de endereços físicos;
	- _Mapeamento baseado no bloco_$\to$ Lógico, blocos são abstrações do endereço físico. Cada bloco recebe um número único, esse número é convertido para o endereço baseado na geometria;
#### Bloco x Setor
- Um setor é uma porção física de um disco;
- Geralmente um setor=512bytes;
- Um bloco pode ser um conjunto de setores
- Sistemas de arquivos usam blocos, apontam números de blocos
- Atualmente os blocos 4k são os mais utilizados 
- _Todo arquivo ocupa pelo menos um bloco_