- Sistema Operacional: Coleção de programas que gerenciam e organizam o hardware do computador
- Sistema de Arquivo Distribuído: É um sistema computacional que permite aos programas armazenarem e acessarem arquivos remotos exatamente como se fossem locais. Possibilitam o usuário acessar arquivos a partir de qualquer computador em uma rede
### Requisitos de um SAD
#### Transparência
- Usuário e programador, não devem perceber a separação dos componentes de um SAD (nome, metadados, dados, cópias do arquivo). O sistema do arquivo deve ser compreendido como um todo
- Fazem parte desta transparência:
	- Acesso (programador ou usuário desconhece sua localização)
	- Localização (nome, metadados, dados e servidor são "transparentes")
	- Mobilidade (metadados 'transparentes' durante a mutação de arquivos)
	- Desempenho (transparência na oscilações de cargas)
	- Mudança de escala (file system 'transparente' quanto extensiabilidade)
#### Atualização concorrente
- Alterações feitas em um arquivo por um cliente não devem interferir nas operações de outros clientes, mesmo que estejam manipulando o mesmo arquivo.
#### Replicação de arquivos
- Um arquivo pode ser representado por diferentes cópias de seu conteúdo em diferentes locais
- Permite servidores compartilharem a carga de fornecimento de arquivos
- Pode ser mais tolerante a falhas
#### Heterogeneidade
- Interfaces devem ser desenvolvidas de modo que se possa implementar em diferentes sistemas operacionais e computadores
#### Consistência
- Só deve haver uma versão disponível do arquivo. Se duas pessoas acessarem o mesmo arquivo, devem conseguir ver o mesmo conteúdo
#### Segurança
- O SAD deve ter preocupações com permissão, autenticação, privacidade e integridade.
#### Eficiência
- SAD deve fornecer o desempenho comparável aos sistemas de arquivos padrões

### Generalização gráfica de um SAD
![[Pasted image 20241021164217.png]]
### Vantagens do SAD
- Permitem que vários usuários acessem ou armazenem os dados
- Permite que os dados sejam compartilhados remotamente
- Integridade dos dados mesmo se o servidor ou disco falhar
### Potenciais desvantagens
- Nós e conexões precisam ser protegidos 
- Existe a possibilidade de perda de mensagens ao passar de um nó para outro
- Conexão mais complexa com o Banco de Dados

## Visão global do Google File System
- É um sistema distribuído de arquivos e um sistema de arquivos distribuídos.
- Objetivos:
	- Oferecer escalabilidade, confiabilidade e disponibilidade de serviços
- Deve estar preparado para operações intensas nos arquivos
- Projeto direcionado para as demandas crescentes da empresa
- Monitoramento constante, detecção e suporte a erros, tolerância a falhas são requisitos  funcionais desse _file system_
- 