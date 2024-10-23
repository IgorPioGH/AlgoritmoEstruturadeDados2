### Tipos de organização
Nem todo arquivo pode ser armazena de maneira sequencial em setores, de acordo com seu tamanho
A desejada continuidade de acesso pode levar a uma alta _fragmentação_
### Organização por setores
#### Organização por setores adjacentes
- Setores são seguimentos com número fixo de bytes (512)
- Leva tempo para processar o dado lido até iniciar a leitura do próximo
- Ordenação contínua não é muito eficiente na prática
#### Organização intercalada
- Setores também possuem tamanho fixo
- A organização é intercalada de acordo com o tempo de processamento do controlador
- Considera que o tempo n de processamento de um setor lido, pode ser próximo ao avanço do controlador em n setores
- Organização intercalada e adjacentes não são mais utilizadas
#### Organização por cluster
- _Cluster_: Conjunto contíguo de setores, é a menor porção lógica de um disco.
- A ideia é que a próxima informação solicitada esteja perto do cabeçote de leitura do disco
- A organização por cluster otimiza estruturas tipo árvore e outras estruturas de dados
- Em um sistema operacional o _file system_ é responsável por mapear as partes lógicas e físicas;
- O FAT (File Allocation Table) relaciona clusters lógicos aos físicos.
- O tamanho do cluster varia entre 1 (512B) e 128 (64KB)

#### Organização por extents
- Os Sistemas de arquivos procuram acomodar um arquivo utilizando o maior número possível de setores contíguos.
- Quando isso ocorre, diz-se que o arquivo consiste de um extent
- Arquivos em um único extent ajudam a reduzir o tempo de acesso ao arquivo (seek)
- Reduz também o custo computacional de acesso ao disco
- Arquivos podem estar contidos em mais de um extent
#### File systems e extents
- Os seguintes file systems suportam extent:
	- Linux ext4
	- Microsoft NTFS 
	- Apple File System (APS), macOS High Sierra
	- HP Multi-Programming Executive File System
### Organização por blocos
- Um bloco é um registro físico de uma quantidade de bytes
- Sistemas baseados em blocos, leem, processam e armazenam blocos nos buffers
- Blocos são utilizados para diminuição de sobrecarga de trabalho do sistema e agilidade no tratamento de fluxos de dados (streams)
- Utilizados em memórias flash tipo NAND
- _Problema_: Fragmentação do disco, pois os arquivos precisam ter tamanhos múltiplos do tamanho do bloco
