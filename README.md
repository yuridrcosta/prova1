# Sistema de Gerenciamento de Projetos
## Funcionalidades:
 1. **Gerenciar projetos:**<br/>
	- Adicionar projeto<br/>
  - Definir coordenador<br/>
	- Alterar status de andamento do projeto<br/>
	- Adicionar novo membro<br/>
	- Adicionar nova atividade<br/>
	- Adicionar/remover nova informação<br/>
  - Listar todas as informações<br/>
  - Listar atividades associadas ao projeto<br/>
			
 2. **Gerenciar atividades:**<br/>
	- Adicionar participante em atividadebr/>
	- Adicionar tarefa de participante<br/>
	- Listar membros<br/>
  
 3. **Gerenciar membros:**<br/>
	- Adicionar aluno de graduação, mestrado e doutorado<br/>
	- Adicionar professor<br/>
	- Adicionar pesquisador<br/>
	- Adicionar profissional desenvolvedor, testador e analista <br/>
  - Adicionar técnico <br/>
  - Mostrar informações completas de cada membro <br/>
  - Registrar/remover projeto a um membro <br/>
  - Listar projetos coordenados por um professor ou pesquisador<br/>
  
 4. **Relatórios**<br/>
	 - Gerar relatório geral<br/>
	 - Listar membros em específico<br/>

 

## Classes

 1. **Person**<br/>
	 - Motivação: Todas as pessoas tem dados em comum.<br/>
	 - Vantagens: Grande número de métodos não precisam ser reescritos.<br/>
	 -  Desvantagens: Maior dificuldade de lidar com a grande quantidade de subclasses, como por exemplo, para receber objetos, passar objetos entre os métodos.<br/>
 2. **Responsible** - Subclasse de Person<br/>
	-  Motivação: Era necessário que tanto pesquisadores como professores fossem responsáveis por projetos. Em breve poderia surgir novos responsáveis<br/>
	-  Vantagens: Listar os projetos em que este membro coordena sem precisar identificar se é um pesquisador ou professor.<br/>
	- Desvantagens: Semelhante as desvantagens da classe Person.<br/>
 3. **Student** - Subclasse de Person<br/>
	 - Motivaçao: Representar os estudantes, não era necessário no momento a criação de classes separadas para cada estudante, porém caso necessário, a implementação será simples.<br/>
	 - Vantagens: Facilidade em criar classes que herdam essa classe, caso seja necessário gerar especificidades.<br/>
 4. **Professional** - Subclasse de Person<br/>
	-  Motivação: Poderia ser necessário futuramente associar atividades aos profissionais e assim, gerar novas classes que herdassem a classe Professional.<br/>
	- Vantagens: Ditas na motivação.<br/>
 5. **Technical** - Subclasse de Person<br/>
	 - Motivação: Caso seja necessário adicionar mais dados sobre os técnicos e funções específicas, a classe está criada.<br/>
	 -  Vantagens: Manutenção mais fácil após código ter sido desenvolvido com essa classe preparada.
 6. **Professor** - Subclasse de Responsible<br/>
	- Motivação: Caso seja necessário adicionar mais dados sobre os professores e funções específicas, a classe está criada.<br/>
	-   Vantagens: Manutenção mais fácil após código ter sido desenvolvido com essa classe preparada, pode por exemplo, adicionar agora dados sobre o estilo de jogo do treinador.<br/>
 7. **Researcher** - Subclasse de Responsible<br/>
	- Motivação: Caso seja necessário adicionar mais dados sobre os professores e funções específicas, a classe está criada.<br/>
 8. **Register**br/>
	  - Motivação: Manejar todos os registros (ArrayLists).<br/>
	 -  Vantagens: Mantém a classe Main "limpa".<br/>
 9. **Data**<br/>
	 - Motivação: Projetos e atividades tem dados em comum.<br/>
	 -  Vantagens: Facilidade em adicionar novas características em comum pra projetos e atividades.<br/>
 10. **Project** - Subclasse de Data<br/>
	 -  Motivação: Necessário gerenciar projetos.<br/>
	 -  Vantagens: Com uma classe para projetos, fica mais fácil trabalha-los como objetos, podendo guardar em Array Lists, passar como métodos.<br/>
 11. **Activity** - Subclasse de Data<br/>
	 -  Vantagens: Com uma classe para atividades, fica mais fácil trabalha-las como objetos, podendo guardar em Array Lists, passar como métodos.<br/>
 12. **Task** - Subclasse de Data<br/>
		- Motivação: Necessidades de criar tarefas associadas a cada tipo de membro.<br/>
		-  Vantagens: Com uma classe para tarefas, fica mais fácil trabalha-las como objetos, podendo guardar em Array Lists, passar como métodos.<br/>
 13. **Information**
		- Motivação: Possível necessidade de alterar o tipo de informação.<br/>
		- Vantagens: Facilidade em alterar as informações adicionais<br/>

## Distribuição de Métodos

 1. **Métodos buscadores e de listagem:**<br/>
- find(MemberClass)() e list(MemberClass).<br/><br/>
	- Motivação: Buscam/listam objetos de cada classe. Foram colocados todos na classe Register devido a localização dos ArrayLists de registro, como por exemplo o ArrayList de registro de todos os estudantes.<br/>

 2. **addNewMember()**<br/>
	- Motivação: Método colocado na classe Register devido a localização dos registros.<br/>

3. **readNumber()**<br/>
	- Motivação: Função que lê inteiros com tratamento de exceções.<br/>
	- Vantagens: Caso seja necessário alterar o que é feito após capturar uma exceção ao ler inteiros, ao alterar este método, toda a leitura de inteiros do sistema está atualizada.<br/>
4. **readFloat()**<br/>
	- Motivação: Função que lê números reais (floats) com tratamento de exceções.<br/>
	- Vantagens: Caso seja necessário alterar o que é feito após capturar uma exceção ao ler floats, ao alterar este método, toda a leitura de floats do sistema está atualizada. 
 

## Herança<br/>


  - Motivação: Aproveitar atributos em comum foi necessário na maioria das classes onde a herença foi usada. Nas classes derivadas da classe Person, é interessante pensar que o projeto pode ter mais funções e uma melhor distribuição das classes facilita a implementação e manutenção, após o código ter sido desenvolvido. Era necessário também uma classe Responsible por motivos explicados anteriormente na seção em que fala sobre essa classe.<br/>
  - Solução: Criar classes para possíveis responsáveis por projetos, e outras para cada tipo de membro.
  - Vantagens: Deste modo, a manutenção fica mais fácil e o surgimento de novas funções para o sistema também.<br/>
 - Desvantagem: As classes ainda não estão sendo muito bem utilizadas, nesta concepção inicial do sistema.<br/>
 
## Polimorfismo <br/>
  - Motivação: O método showInformations() mostra as informações contidas nos atributos da classe em que está e nas superclasses, logo foi necessário usar de polimorfismo.

## Tratamento de Exceções<br/>
1. **readNumber()** - Tratamento InputMismatchException<br/>
	- Motivação: O sistema lê muitos inteiros e caso o usuário digite algo diferente quando o sistema espera esse tipo, aparece um erro ao qual o usuário comum dificilmente irá entender.<br/>
	- Solução: Criar um método de leitura para inteiros com tratamento de exceções.<br/>
	- Vantagens: Com a utilização de métodos, caso seja necessário alterar o que é feito após capturar uma exceção ao ler inteiros, ao alterar este método, toda a leitura de inteiros do sistema está atualizada e uma mensagem amigável irá aparecer ao usuário caso ele não digite um inteiro.<br/>
2. **readFloat()** - Tratamento InputMismatchException<br/>
	-  Motivação: O sistema lê valores reais e caso o usuário digite algo diferente quando o sistema espera esse tipo, aparece um erro ao qual o usuário comum dificilmente irá entender.<br/>
	- Solução: Criar um método de leitura para inteiros com tratamento de exceções.<br/>
	- Vantagens: Com a utilização de métodos, caso seja necessário alterar o que é feito após capturar uma exceção ao ler floats, ao alterar este método, toda a leitura de floats do sistema está atualizada e uma mensagem amigável irá aparecer ao usuário caso ele não digite um float.<br/>

## Extensibilidade<br/>

1. **Novos tipos de estudante** - Classe Student<br/>
	- Motivação: Pode ser necessário a implementação de novos tipos de estudantes.<br/>
	- Vantagens: A classe Students deverá ter todos os dados básicos e métodos básicos e permitirá que qualquer tipo de função possa ser adicionada ao sistema extendendo a essa classe.<br/>
	
2. **Novos tipos de pessoas** - Classe Person<br/>
	- Motivação: A clase Person vem sendo extendida pois tem vários dados em comum, e poderá ser extender mais classes que tenham esses dados em comum.<br/>
	- Solução: A classe Person não tem dados que não sejam pertinentes a Responsible e Student ao mesmo tempo.<br/>

