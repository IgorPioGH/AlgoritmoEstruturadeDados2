## Leitura por campos (lógica)
- Seja um arquivo chamado _data1.txt_
```
1234 Carla
1235 Carolina
1236 Ian
1237 Marcos
1238 Vini
```
- Código "alto nível"
	- Para ler o arquivo em campos
```
#include <stdio.h>
int main(void){
	int num; char pal[10]; FILE *tf;

	tf = fopen("data1.txt", "r");
	if(tf==NULL){
		perror("Erro na abertura do arquivo");
		return 1;
	}

	while (fscan(tf,"%d %10s", &num, pal)==2){
		fprint(stdout, "%d %s\n", num, pal);
	}
	fclose(tf);
	return 0;
}
```
### Ligações
- Stream:
	- Conceitualmente C trabalha com streams e não com arquivos em diretamente
	- stream é uma entidade lógica, um fluxo de dados idealizado que é canalizado para uma saída, ou entrada de dados.
- _stdout_ é uma stream de saída de dados.
- O comando _fopen()_ basicamente liga um arquivo lógico a um arquivo físico.
	- O Sistema Operacional (S.O.) realiza um série de operações para abrir o arquivo associado ao descritor (tf).
## Leitura Byte a Byte
- Código para ler um arquivo byte a byte
```
#include <stdio.h>
int main(void){
	char c;
	FILE *tf;

	tf=fopen("data1.txt","r");
	while(!feof(tf)){
		fread(&c,sizeof(char),1,tf);
		fwrite(&c, sizeof(char),1,stdout);
	}
	fclose(tf);
	return 0;
}
```
- _fread( )_ lê uma quantidade específica de bytes a partir do tamanho especificado $\to$ é uma função mais específica, o que implica em ser de mais baixo nível
## Tratando de busca
- Retorna o tamanho do arquivo
```
#include <stdio.h>
int main(void){
int cont; FILE *tf;

tf=fopen("data1.txt","r");
fseek(tf, OL, SEEK_END);
cont=ftell(tf);
printf("Comprimento do arquivo: %d\n", cont);
fclose(tf);
return 0;
}
```
- Saída: Comprimento do arquivo: 56.
- Obs. No OSX o final de linha é representado pelo caractere LF.

- Posicionando-se no arquivo, e escrevendo
```
#include <stdio.h>
int main(void){
FILE *tf;
tf=fopen("texto.txt", "w+");
fputs("O melhor programa do mundo!", tf);
fseek(tf, 10, SEEK_SET); //No arquivo tf, andará com o ponteiro 10 posições
fputs("pijama", tf); //"Coloca" no arquivo tf, a palavra pijama
fclose(tf);
return 0;
}
```
- Conteúdo do arquivo: O melhor ppijamao do mundo!

### "Segredos" da busca em arquivos
- SEEK_SET, SEEK_CUR, SEEK_END são constantes declaradas na linguagem C;
- SEEK_SET ajusta o apontador para o início do arquivo;
- SEEK_END ponteiro vai para o final do arquivo;
- SEEK_CUR move o ponteiro para uma posição específica.
- A função `fseek()` define o indicador de posição do arquivo para o fluxo apontado por *stream*. A nova posição é medida em bytes.

## Marcando um 'x' a cada 5 bytes
```
#include <stdio.h>
int main(void){
	FILE *tf; int i;
	tf=fopen("data1.txt", "r+");
	for(i=0;i<=55;i++){
		if((i%5)==0){
			fseek(tf,i, SEEK_SET);
			fprint(tf,"%c",'x');
		}
	}
	fclose(tf);
	return 0;
}
```

## Alterando um arquivo
- No OSX o final da linha  é representado pelo caractere LF; Se o caractere LF for trocado por outro as linhas serão juntadas
### Algoritmo para marcar 'x' a cada 5 bytes
```
#include <stdio.h>
int main(void){
	FILE *tf; int i;
	tf=fopen("data1.txt", "r+");
	for(i=0;i<=55;i++){
		if((i%5)==0){
			fseek(tf,i, SEEK_SET);
			fprint(tf,"%c",'x');
		}
	}
	fclose(tf);
	return 0;
}
```

