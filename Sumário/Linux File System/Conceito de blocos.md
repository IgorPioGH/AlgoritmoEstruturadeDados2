### Revisão sobre Blocos
- Menor unidade de escrita e leitura de um dispositivo de memória secundária que pode ser endereçável
- Objetivo do bloco é facilitar o acesso ao fluxo de dados na programação
- Dados nos blocos são lidos como um todo
- _File Systems_ utilizam blocos como estruturas de abstração para I/O
- Bloco lógico corresponde a vários setores

### A página
- _Memory page_ é um bloco de _memória virtual contínua de tamanho fixo_
- É a quantidade de memória trocada pela RAM e  o disco
- Transferência de memória entre disco e RAM é o que chamamos de _swapping_ ou _paging_
- A utilização de paginamento pelo s.o cria a memória virtual de um sistema
- Uma tabela de páginas é a estrutura usada pela memória virtual que mapeia essa memória na memória física

### Bloco x Página
- Bloco (dados no disco):
	- Menor unidade de dado que o f.s. pode ler ou escrever
	- Sequência de setores
	- Discos podem ter blocos de tamanhos diferentes
	- Dados trocados entre disco e RAM são blocos
- Página (dados na RAM):
	- Menor unidade que o s.o. manipula
	- Página é uma sequencia de blocos
	- Páginas tem tamanho fixo
	- Páginas sempre têm o mesmo tamanho
	- Dados na RAM são formados de páginas
- A página é um tamanho de memória física contínua endereçável pelo s.o., ou seja, memória acessada pela RAM