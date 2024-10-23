- Definição de superbloco: é um metadado do file system, estrutura básica do ext2, ocupa 1024 bytes e é responsável pelo boot do sistema

### ext2
- Espaço em disco divididos em blocos
- Blocos são organizados em grupos de blocos
- Sempre que possível um arquivo é armazenado em um único grupo de blocos
- Feito para minimizar o número de buscas de disco
- Todo grupo de bloco possui:
	- O block bitmap
	- O inode bitmap
	- Uma tabela de inode
	- Os blocos de dados que efetivamente armazenam dados
- O volume ext2 é dividido em grupos de blocos do mesmo tamanho
- Não há _extent_ que é uma área contínua na memória reservada para um único arquivo. Este recurso pode diminuir a fragmentação de discos, neste modo o inode aponta apenas

### ext3
- É o FS padrão para muitos tipos de Unix, por exemplo o BSD
- Criado para manter compatibilidade com o ext2
- Usa B-tree com hash para manter estrutura de diretórios
- É um file system com _journaling_ (registro de ocorrência)
- _journaling_ foi a principal inovação
- Melhora confiabilidade
- Elimina a necessidade de verificação do file system depois de um shutdown problemático
#### Registro de ocorrências
- _Journal_: Menor risco, tanto os metadados quanto o conteúdo do arquivo são registrados antes de serem efetivados no FS.
- _Ordenado_: Risco médio, os metadados são registrados, mas o conteúdo do arquivo não. No entanto o conteúdo do arquivo é escrito no disco antes de efetuar seu registro. Em caso de pane podemos ter 2 arquivos . É o modo padrão do Linux.
- _Writeback_: Maior risco, apenas os metadados são registrados. O conteúdo do arquivo pode ser escrito antes ou depois da atualização no journal. Arquivos modificados podem ser corrompidos
#### Desvantagens
- Não é tão atualizado para novas características de FS.
- O ext3 é resistente a fragmentação externa, mas não é imune
- Com o tempo ext3 fica fragmentado e não há desfragmentação para ext3
- Não existe verificação de erros por checksum no registro de ocorrências

### Ext4
- Compatível com ext3 e ext2
- Planejado para utilizar com processadores 64bits
- Introduz _extents_ e elimina mapas de blocos
- Tem registro de journal com checksum
- Pode estabelecer quota de espaço em disco para projetos
- Criptografia transparente ao usuário
- Defragmentação
#### Mais vantagens
- Pode ser utilizado em outros S.O.
- Suporta volumes de até 1EB (Hexabite)
- Arquivo de até 16TB
- Máximo de 4 bilhões de arquivos
- Número ilimitado de subdiretórios