- Estruturas de dados que armazenam informações (metadados) sobre qualquer arquivo linux
- Descreve um objeto do sistema de arquivo
- Criados juntamente com o file system
- Exemplo:
	- Data de criação do arquivo
	- Dono do arquivo
	- Tamanho
- No Linux cada arquivo é associado a um número chamado de _inode_
- Nome do arquivo não é um metadado armazenado pelo inode
- _Inode é um índice de uma tabla de metadados para cada arquivo_
- ![[Pasted image 20241021152124.png]]
- Arquivos são constituídos por: Nome do arquivo, dados do arquivo e inode
- Diretórios são listas de associações de nome-inode
### Dados armazenados no inode
- Tamanho do arquivo
- Dispositivo no qual o arquivo está armazenado
- IDs de usuário e grupos associados ao arquivo
- Permissões necessárias para acessar o arquivo
- Carimbos de data e hora da criação do arquivo
- Localização dos dados (mas não o caminho do arquivo)
*A quantidade de inodes criados junto com o file system é limitado, assim, pode ser que esgotem e novos arquivos não possam ser criados*
![[Pasted image 20241021152651.png]]
### Hard link
![[Pasted image 20241021153943.png]]
- É um ponteiro para o inode de um arquivo, nunca para diretórios
- Ao deletar o arquivo original, ou o hard link, o outro ainda existe, pois o inode continua existindo
- Ao modificar qualquer link apontando para um mesmo inode, todos os links, incluindo o arquivo original são alterados
- Tem o mesmo número de inode
```
ls -l
```
- Comando mostra todos os hard links
- Remover o link, remove apenas o link
- Se o arquivo original for removido, o link ainda permanecerá
### Soft link
- É outro nome (apelido) para o arquivo. É um arquivo em si
- Um link simbólico (soft link) é uma cadeia de caracteres que aponta para um arquivo ou diretório
- Ao deletar o arquivo original o soft link irá falhar
- Ao deletar o soft link nada irá acontecer com o arquivo original
- tem número de inode diferente
- O soft link tem contém o caminho para o arquivo e não seus dados
- São dependentes do nome

### Mapeamento inode-nome
- Por conta deste mapeamento um arquivo pode ter diferentes 'nomes'
- Dois nomes podem apontar para o mesmo inode

![[Pasted image 20241021154928.png]]
