### Conceitos básicos
- É muito comum a gravação, em arquivos, de dados vinculados. Chamamos esse tipo de dado de _"registro"_ 
- Por exemplo:
		![[Pasted image 20241020181405.png]]

#### Tipos de consulta em registros
- **Consulta simples**: Especifica-se um valor de um atributo do registro;
- **Consulta por intervalo**: Especifica-se o intervalo de valor de um atributo do registro;
- **Consulta funcional**: Especifica-se uma função a um ou mais atributos;
	- Exemplo: Funcionários com média salarial acima de, soma entre dois valores
- **Consulta booleana**: Utiliza conectivos lógicos (AND, OR, NOT) para todos os tipos de consulta;

#### Organização de arquivos
- Toda consulta eficiente a arquivos demanda uma certa organização dos dados;
- Uma forma elementar de organização é a _ordenação_;
- _Problema_: Em muitos casos os dados (registros) podem estar dispostos em arquivos diferentes
- Um método comum é a _organização por intercalação_;
- A _intercalação_ pressupõe dois arquivos ordenados por algum campo em comum, juntando-os em um único arquivo final, também ordenado;
	- Processo também conhecido como _merge_
- _Merge_ é o processo de formar uma lista de saída contendo todos os itens de duas (ou mais) listas de entrada;

### Intercalação
- Sejam dois arquivos, _ordenados_ por ordem alfabética. A _ordenação_ ocorre pelo atributo 'Nome' e a _intercalação_ também.
		![[Pasted image 20241020182631.png]]

#### Sugestão de algoritmo de intercalação (merge)
- procedure merge(X,Y,Z);
- X e Y são arquivos de entrada, ambos ordenados;
- Z é o arquivo de saída, também ordenado;
- x $\in$ X, x é um registro de X, assim como, y $\in$ Y;
- O algoritmo, abre os arquivos X e Y e a cada registro insere em Z o 'menor' registro entre os dois;
##### Pseudocódigo
```
procedure merge(X,Y,Z)
Leia registro x de X 
Leia registro y de Y 
while (not X.EOF() and not Y.EOF())do 
if x.key < y.key 
then Escreva x em Z 
Leia x do arquivo X 
else 
Escreva y em Z 
Leia y do arquivo Y 
endif 
endwhile

while not X.Eof() do 
Escreva x em Z 
Leia x do arquivo X 
endwhile 
while not Y.Eof() do 
Escreva y em Z 
Leia y do arquivo Y 
endwhile 
end merge
```

#### Mais sobre intercalação
- A _ordenação por intercalação_ é a mais comum em dispositivos com memória secundária;
- Esse método tem duas fases:
	- _Distribuição_: Os segmentos dos arquivos de entrada são organizados na memória principal, esses segmentos recebem o nome de _runs_. Que serão gravados na memória secundária a medida que são gerados.
	- _Intercalação_: As runs geradas são intercaladas até esgotarem as corridas
#### Intercalação na prática
- Problemas:
	- Ordenar um arquivo com 4.500 registros
	- Na memória ram só cabem 750 registros
- Solução:
	- Considerar cada um dos blocos de 750 registros como uma run
	- 6 * 750 =4.500
	- Ordenar cada uma das runs, segmentos do futuro arquivo
	- Usar o algoritmo de intercalação
- Exemplo:
	![[Pasted image 20241020184130.png]]

### Modelo Cossequencial
- Operações cossequenciais são muito comuns em arquivos
- A intercalação é um exemplo de operação _cossequencial_ de processamento de arquivos
- Envolvem o _processamento coordenado de duas ou mais entradas sequenciais_, de modo a _produzir um ou mais arquivos de saída_
- Cada arquivo é ordenado sobre um ou mais campos chave, e todos os arquivos são ordenados do mesmo modo sobre esses campos
- Registros são ordenados de acordo com a ordem lógica
- A ordem física não é relevante ao modelo, mas pode ser impactante para a eficiência da operação
- Os registros são manipulados somente em memória principal, já que não se pode alterar um registro diretamente no arquivo em disco

### Intercalação em vias múltiplas
