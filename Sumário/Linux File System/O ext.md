- ext sigla para: _extended file system_ 
- _Primeiro sistema de arquivos criado especificamente para Linux_
- Era um VFS que aumentava o tamanho das partições para 2GB e o número de caracteres para nome de arquivos para 255
- Introduziu conceitos de design de sistemas de arquivos do Unix:
	- _Árvore hierárquica de diretórios_
	- _inodes_
	- Sistema de permissões baseado em usuários e grupos
- Lançado inicialmente como um _Virtual File System_ (VFS)
	- A principal vantagem do VFS é servir uma interface genérica para outros sistemas de arquivos
#### Exemplo de aplicação no OSX
```
cp -R Documents /Volumes/USB
```
- Usuário comanda a cópia de toda hierarquia de diretórios do diretório Documents para uma memória flash montada como um drive externo
- O VFS inibe os detalhes de file system e deixa o comando único independente do sistema utilizado
### Componentes de um sistema de arquivos
![[Pasted image 20241021142805.png]]
- O diagrama mostra uma versão simplificada de um sistema de arquivos do Linux
- Percebe-se que o Linux aceita diversos File Systems:
	- _Ext3_ Uma evolução do ext
	- _jfs_ Um journaled filesystem projetado pela IBM para sistemas de alto desempenho
	- _reiserfs_ Outro sistema de arquivo robusto pelo uso do journaling 
### Ext modificado
- Em 1993 surgem duas inovações para o ext:
	- O _xifas_ (hoje obsoleto), com poucas modificações no ext
	- _ext2_ um f.s. totalmente remodelado que incorpora muitas ideias do Berkeley Fast File System, BSD
- Planejado para ser _extensível_
- Atualmente muito utilizado para boot usando memória flash
- Como não é _journaling file system_, sistema com registro de ocorrências, escreve poucos dados no disco comparado ao _ext3_
