# Gerenciador-de-Cole-es-Trabalho-POO-
 ________________________________________________________________________________
(Entrega 1)
_______________________________________________________________________________________________


Especificação Detalhada do Sistema
Visão Geral 
O sistema será uma plataforma voltada para colecionadores, permitindo a catalogação, organização e gerenciamento de itens colecionáveis. Haverá um usuário principal (administrador) responsável por registrar e gerenciar os itens e colecionadores dentro da aplicação.
O administrador terá acesso para adicionar novos colecionadores e itens, visualizar e gerenciar os registros existentes, administrar os perfis de usuários que solicitam a inclusão de itens em suas coleções, verificar a disponibilidade para troca, coordenar o processo de trocas entre colecionadores e atualizar os dados de contato dos colecionadores.
Ao adicionar um item ou coleção ao sistema, o administrador será responsável por certificar a autenticidade do produto e confirmar sua existência antes do registro. Esse processo garantirá que apenas itens verificados sejam cadastrados, aumentando a confiabilidade do sistema e garantindo a segurança das transações entre colecionadores.

Requisitos do sistema
Requisitos funcionais

Gerenciamento de Colecionadores:
O administrador deve poder adicionar novos colecionadores ao sistema.
O administrador deve poder editar e atualizar os dados de contato dos colecionadores.
O administrador deve poder excluir colecionadores do sistema.
Cadastro e Gerenciamento de Itens Colecionáveis:
O administrador deve poder adicionar novos itens colecionáveis.
O administrador deve poder editar informações dos itens cadastrados.
O administrador deve poder remover itens do sistema.
O sistema deve permitir o cadastro de informações detalhadas dos itens, incluindo:

Nome do item
Categoria
Data de aquisição
Estado de conservação
Valor estimado
Disponibilidade para troca
Fotos do item (em avaliação)
Trocas registradas 
Controle de Trocas:
O administrador deve poder verificar a disponibilidade de um item para troca.
O administrador deve poder coordenar trocas entre colecionadores.
O sistema deve permitir registrar e acompanhar as trocas realizadas
Pesquisa e Filtros:
O sistema deve permitir buscas por itens cadastrados.
O sistema deve oferecer filtros para facilitar a organização e a visualização dos itens (exemplo: por categoria, disponibilidade para troca, estado de conservação, etc.).
Gestão de Perfis de Usuários (Colecionadores)
O administrador deve poder visualizar e gerenciar os perfis dos colecionadores.
O administrador deve poder aprovar ou rejeitar solicitações de inclusão de itens por colecionadores.

Requisitos não funcionais
Usabilidade:
O sistema deve possuir uma interface usando Java Swing intuitiva e fácil de usar.
A navegação deve ser simples e organizada para que o administrador encontre rapidamente as funcionalidades.
Desempenho:
O sistema deve ser capaz de processar e exibir rapidamente as informações dos itens e colecionadores.
O tempo de resposta para consultas e pesquisas deve ser inferior a 2 segundos.
Segurança:
O sistema deve garantir que apenas o administrador tenha acesso ao gerenciamento de itens e colecionadores.
Os dados dos colecionadores e itens devem ser armazenados de forma segura, protegidos contra acessos não autorizados.
Disponibilidade:
O sistema deve estar disponível 99% do tempo, com mínima interrupção para manutenção.
Caso o sistema fique fora do ar, ele deve se recuperar automaticamente ou emitir alertas para a equipe técnica.
Compatibilidade:
O sistema será apenas em dispositivos desktops com o java jdk instalado e configurado na máquina
Armazenamento e Integridade dos Dados :
Os dados cadastrados devem serão armazenado em arquivos locais cadastrados em arquivos csv 
O sistema deve evitar duplicação de registros e garantir a consistência das informações.
 Regras de Negócio
Apenas o usuário adm pode gerenciar os itens da coleção (visualizar e inserir).
Um item só pode ser marcado como "disponível para troca" se estiver cadastrado corretamente com todas as informações obrigatórias preenchidas.
Itens removidos do sistema não podem ser recuperados sem um backup .
Os itens poderam ser trocado com outros colecionadores cadastrados na aplicação e conforme o requisito dos donos 


Diagrama de Classes


https://drive.google.com/file/d/1m6-WZ0itwd-hGVbT_EBu4F1PZtieoqJS/view?usp=sharing
_______________________________________________________________________________________________
(Entrega 2)
_______________________________________________________________________________________________

O que foi feito até agora


Nesta etapa do trabalho, foi iniciada a construção da interface gráfica da aplicação, utilizando a biblioteca javax.swing. O foco principal foi estruturar a navegação entre as janelas e organizar o controle da interface de maneira centralizada.
A aplicação é iniciada de forma segura através do método SwingUtilities.invokeLater, garantindo que todos os componentes gráficos sejam criados na Event Dispatch Thread (EDT), conforme as boas práticas do Swing. A tela de login é exibida pelo método login(), e, após a autenticação, ocorre a transição para a tela principal (JanelaControle) por meio do método painelControle(). A confirmação de acesso é feita pelo método getConfirmaAcesso(String nome), que realiza a troca de janelas de forma segura, mantendo a aplicação responsiva e estável.
Dois atributos principais sustentam o fluxo da interface: nome_adm, que armazena o nome do administrador autenticado, e janelaAtiva, que mantém referência à janela atualmente exibida. Esse controle centralizado garante uma navegação segura entre as telas, evitando sobreposição e conflitos visuais.
Logo após o início da aplicação, a main chama a janela de login, definida na classe Login, que intermedia o processo de autenticação do usuário administrador. Essa classe é responsável por construir e exibir a interface de login. Ela herda de Componentes, uma classe que provavelmente contém métodos reutilizáveis para facilitar a criação dos elementos gráficos. No método getLogin(), é criado um JFrame contendo um JPanel com imagem de fundo, rótulos, campos de entrada para usuário e senha, e um botão para realizar o login. Todos os elementos são posicionados manualmente com o método setBounds(), proporcionando maior controle visual sobre o layout.
A funcionalidade de autenticação está encapsulada na classe interna Funcionalidades, que trata o evento de clique no botão "Logar". Ao ser acionado, o botão coleta os dados inseridos, verifica se os campos estão preenchidos e, em seguida, utiliza o método authAdm() da classe Registros para validar o acesso. Caso a autenticação seja bem-sucedida, a interface é redirecionada para o painel principal com a chamada de getConfirmaAcesso(), que fecha a janela atual e, novamente utilizando o invokeLater, abre a JanelaControle. Essa abordagem centraliza a lógica de acesso na própria classe Login, facilitando a manutenção e a compreensão do código.
Ressaltamos também que os dados gravados na aplicações estão disponíveis nos arquivos csv alocado junto as pasta src , onde estão armazenado as classes do java.
A edição de arquivos CSV no projeto é realizada principalmente pela função setAtualizarDadoLinha, que localiza uma linha com base em um índice. Caso o parâmetro recebido seja "delet", a linha correspondente é removida. Caso contrário, ela é substituída por uma nova. Isso permite tanto a atualização quanto a exclusão de dados diretamente no arquivo.
O acesso aos dados dos arquivos CSV ocorre por meio das classes FileReader e BufferedReader, que leem o conteúdo linha a linha. Essas linhas são separadas por ; e organizadas em listas ou matrizes para facilitar a manipulação.
Para adicionar ou salvar modificações, é utilizado o BufferedWriter com FileWriter. Quando o objetivo é adicionar conteúdo sem apagar o que já existe, o modo de adição é ativado. Já para sobrescrever o arquivo, a gravação é feita normalmente. Isso garante operações seguras de leitura, escrita e atualização.
A aplicação consta com 3 arquivos csv 
com as seguintes estruturas 
file.csv ( Para adm e autenticação )
Login_usuario ; Dados Senha ; nome ; telefone ; endereço
file2.csv ( Para colecionadores cadastrado )
Cpf ou Cnpj ; Nome ; Email ; Endereço ; Data da última Edição Colecionador
itens.csv  ( Para itens cadastrados )
cod_item ; Nome ; Descrição ; Valor Avaliado ; /Nome_Do no ; CPF ou CNPJ ; categoria ; Estado ; Data de atualização; Troca ou não ; Caminho interno de onde está a foto do produto 

Diagrama de classe Interface



https://drive.google.com/file/d/1EyximmcBKwdBrnLjhDIWQGyM76QiN4jb/view?usp=sharing 


Codigos do Projeto criado até o momento 

https://drive.google.com/file/d/120l2zViiKTlrAZXiYciLO9s1R6iAZyy3/view?usp=sharing (LInk dos códigos estrias até o momento )

