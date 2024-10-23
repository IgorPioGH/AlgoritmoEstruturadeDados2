### Arquivos
- Coleção de dados armazenados em memória não volátil
- A biblioteca padrão <stdio.h> da linguagem C oferece recursos para operações em arquivos
- Essas operações ajudam a entender o acesso a esses arquivos na memória secundária
### Operações Básicas sobre Arquivos
- Open (Abrir), Close (Fechar):
	- Abrir:
		- Read only (Apenas leitura)
		- Write only (Apenas escrita)
		- Leitura e escrita
		- Append: Inclusão de dados
- Read (ler) e Write (Escrever)
- End of file (EOF): Testar o final do arquivo
- Seek: Posicionar o apontador do arquivo em alguma posição específica
### Acesso à um arquivo pode ser:
- Sequencial: Dados são lidos sequencialmente, um após o outro
- Aleatório: Posiciona-se o apontador para a leitura de apenas um dado;
- *Ou uma combinação de ambos acima*
- _Como regra geral todo arquivo deve ser fechado_
