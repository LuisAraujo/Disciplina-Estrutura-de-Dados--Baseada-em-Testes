# Estrutura de Dados I

Esse texto tem por objetivo apoiar o processo de ensino-aprendizagem de Estrutura de Dados. O texto tem como base os códigos no repositório. Não há restrições para a ordem da leitura, mas - se você for um estudante que ainda não conhecem os tópicos apresentados - recomenda-se ler um capítulo e partir para a implementação na seção *overview*. 

**Licença**: O material está disponível sob licença: **Creative Commons BY**

![CC BY](https://upload.wikimedia.org/wikipedia/commons/thumb/1/16/CC-BY_icon.svg/88px-CC-BY_icon.svg.png)
 
**Requisitos**: conhecer o Paradigma Orientado a Objeto (POO) e Linguagem em Java. 

**Obs:** *Esse documento está em construção, deixe-me saber se há algum erro: luisaraujo.ifba@gmail.com*

# 1 - Estrutura de Dados

O que é uma estrutura de dados? Como o próprio nome diz, é uma forma de organizar informações. Ou seja, passamos de um patamar que usávamos tipos primitivos como Inteiro, Caractere e outros para tipos mais complexos, como Pilha, Fila, Árvore e outros. Sim, esses tipos complexos utilizam tipos primários, mas estamos interessados agora nesses mais complexos.

Como disciplina Estrutura de Dados, embora usemos os tipos primitivos, tem como objetivo apresentar estruturas já consolidadas da área de computação que buscam resolver diversos problemas recorrentes.  

É importante ressaltar que uma Estrutura de Dados é formada por Dados (organizados segundo alguma lógica) e operações permitidas, vinculadas a essas dados.

Formalizando:

> Estrutura de Dados envolve dados organizados de alguma forma e operações vinculadas aos dados que garantem que os mesmos permaneçam com a mesma organização após inserções e deleções.

Assim, algumas estruturas são utilizadas como forma de facilitar o armazenamento de informações, permitindo a recuperação de modo mais rápido. Logicamente que tudo depende do contexto do problema. Por exemplo, não é recomendável utilizar uma Pilha para um problema que envolve o conceito de Fila, como uma fila de Banco por exemplo.

### 1.1 - Modelagem Computacional

Modelagem Computacional é um área da Computação que visa modelar computacionalmente alguns cenários ou problemas. Basicamente, buscamos transpor elementos do mundo real para o computador e para isso precisamos usar a "abstração". Logicamente que não iremos modelar algo da natureza em sua perfeição, e muitas vezes não precisamos. Assim, muitas vezes, modelamos apenas os elementos essenciais, arte proveniente da abstração: poder de focar em elementos principais, ignorando elementos eventuais ou menos importantes (para um contexto específico).

Desse modo, podemos criar classe - quando falamos em POO - com seus métodos que simulem um determinado elemento a ser modelado. Por exemplo: Carro possui uma marca, placa, modelo, ano de fabricação, motor e pode acelerar, frear, virar à esquerda, entre outros. 

Em Estrutura de Dados, faremos constantemente esse exercício, modelaremos elementos do mundo real, eliminando suas características eventuais, focando apenas nos elementos principais. Isso ocorre com Pilhas, Filas, Árvore entre outras estruturas. 

### 1.2 - Revisão POO com Java

Uma condição essencial para criar estruturas de dados, no modelo que vamos apresentar, é saber os conceitos de POO e Java. Caso esse não seja o seu caso, recomendamos parar a leitura e fazer um curso ou ler materiais específicos sobre POO. 

Então, assumindo que você já conhece POO, vamos relembrar.

**Classe**

Classes são elementos no qual podemos implementar modelos, tal como uma forma de bolo que usaremos para fazer vários bolos: chocolate, cenoura e outros. Não importa os ingredientes utilizados, a forma sempre será a mesma. 

Com classes podemos definir como serão os nossos objetos. Fazendo outra analogia, classes são como gabarito. Através das classes podemos definir os atributos e métodos dos objetos.

Vamos ver um exemplo em Java. A seguir temos uma classe de nome *AlgumaClasse*, com dois atributos: um do tipo inteiro, chamado número, e outro do tipo string, chamado nome:

```java
public class AlgumaClasse{

     int numero;
	 String nome;
}

```

**Objetos**

Objetos são copias das Classes, dizemos ainda que quando instanciamos um objeto, estamos consolidando a classe. Ou seja, estamos de fato utilizando a classe como modelo para criar um objeto. Esse objeto terá os atributos e métodos estipulados na Classe. Mas é importante saber que: *dois objetos da mesma classe podem ter comportamentos diferentes, dado o seu estado* (os valores nos atributos). Como o exemplo do bolo, chocolate e cenoura foram implementados com ingredientes diferentes, mas ainda são bolos. 

Em Java, um objeto é criado da seguintes forma, declara-se um local para armazená-lo (como uma variável) estipulando o seu tipo (AlgumaClasse) e depois o seu nome. Do lado direto da igualdade, temos o operador *new* acompanhado do nome da Classe e de parênteses:

```java
public static void main(){
	AlgumaClasse ac = new AlgumaClasse();
}

```

Como disse antes, elas podem ter valores diferentes (estado). Vejamos:



```java
public static void main(){
	AlgumaClasse ac = new AlgumaClasse();
	ac.numero = 10;
	ac.nome = "AC 1";

	AlgumaClasse ac2 = new AlgumaClasse();
	ac.numero = 20;
	ac.nome = "AC 2";

}

```

Assim, ac e ac2 são objetos diferentes que possuem seus próprios valores. Mas, ainda assim, são objetos de AlgumaClasse.


**Construtor**

Mas o que faz o *new*? Bem, ele 'chama' o construtor da classe para que seja instanciado o objeto (o objeto é colocado dentro da variável *ac*). Esse construtor é um método diferenciado, pois ele não possui retorno. Isso não quer dizer que ele é um *void*, ele literalmente não possui retorno. O Java saberá que ele é um construtor, pois não colocamos o tipo de retorno (*void, Integer, String ...*). Vejamos a diferença entre os métodos *setNumero*, *getNumero* e o Construtor.

```java
public class AlgumaClasse{

    [...] //trecho inibido

	public AlgumaClasse(){
		nome = "";
	}

	public int getNumero(){
		return this.numero;
	}

	public void setNumero(int numero){
		this.numero = numero
	}	

```


**Atributos**

Atributos são variáveis (primitivas ou objetos) que são inerentes ao Objeto instanciado. Ou seja, os atributos são estipulados no modelo (a Classe). No exemplo anterior, já vimos o uso de atributos (*nome e número*). Os valores nos atributos definem o estado do objeto, que podem influenciar as suas ações (os métodos).

**Métodos**

Como vimos, os métodos são as ações dos objetos. O que isso significa? Significa que são eles os responsáveis por executar as operações, como obter um valor ou inserir um valor. Vimos um exemplos do Método (*getNúmeros*). 

Métodos podem retornar um tipo ou não (void). Vejamos dois exemplos:

```java
public class AlgumaClasse{

    [...] //trecho inibido

	public void setNumero(int numero){
		this.numero = numero
	}

	public int getNumero(){
 		return numero;
	}

```

**Herança**

Herança é uma forma de compartilhar atributos e métodos, de modo a eliminar a duplicidade de código. Assim, o processo de Herança consiste em agrupar atributos e métodos gerais em uma classe, que chamamos de Pai e reaproveitá-los nos Filhos.

Em Java, a Herança é implementada com a palavra-chave *extends*. Todos os atributos e métodos públicos (public) e protegidos (protected) serão herdados pelos filhos. Vejamos:

A classe Pai:

```java
public class ClassePai{

    protected int valor1;

	protected void getValor1(){
		return valor1;
	}

```

A classe Filha:

```java
public class ClasseFilha extends ClassePai{

    protected int valor2;

	protected void getValor2(){
		return valor2;
	}

	// usando o método do Pai
	protected void exibeValor(){
		System.out.println(  getValor1()  + "  " +  getValor2());
	}

```

Através da Herança podemos utilizar o Polimofirmos para agregar dados de vários tipos e tratá-los como iguais. Por exemplo: Um lista de Funcionários tem objetos do tipo Operador, Gerente e Supervisor. Poderíamos tratá-los como Funcionários e assim utilizar os métodos e atributos em comum.

### 1.3 - Tipos Abstratos em Java

Já que relembramos os conceitos básicos de POO, buscaremos agora entender como implementar algo que funcione para uma variedade de tipos, eliminando a necessidade de implementar várias estrutura (uma para cada tipo). Afinal nosso objetivo é criar estruturas que possam ser utilizadas em vários contextos.

**Classe Object**

Como já falamos sobre Herança, podemos então definir a Classe Object. Basicamente, todos as Classes em Java são filhas de Object, mesmo sem o uso de *extends*. Ou seja, nativamente, todas as classes são filhas de Object. 

Object é uma super classe, logo podemos tratar todas as classes como Objects. O problema é que precisamos saber os seus tipos, quando formos utilizar os atributos e métodos. Então, nem sempre isso é uma vantagem. 


```java

public class EstruturaQualquer (){

	Object[] vetor;

	public EstruturaQualquer(int tamanho){
		vetor = new Object[tamanho];
	} 
	
	public void getItem(int i, Object valor){
		vetor[i] = valor;
	}
	public Object getItem(int i){
		retunr vetor[i];
	}

}
```
	   
Agora vamos utilizar essa estrutura. Como ela foi implementada com Object, podemos inserir todos tipo de objeto, pois todos são filhos de Object.

```java

	public static void main(Strings[] args){

		EstruturaQualquer est1 = new EstruturaQualquer(10);
		est1.setItem(0, "Teste");
		est1.setItem(1, "Teste 2");

		EstruturaQualquer est2 = new EstruturaQualquer(10);
		est2.setItem(0, new Gerente() );
		est2.setItem(1, new Gerente() );


}
   
```

Mas do que se trata isso? Bem, estamos tentando esboçar uma forma de implementar nossas estrutura apenas uma vez de modo que ela sirva para uma ampla gama de contextos. O uso do Object funciona, criamos apenas uma estrutura e podemos inserir vários tipos, mas isso possui uma dificuldade: precisamos sempre fazer o *cast* para usar métodos específicos.


```java

	public static void main(Strings[] args){

		[...]

		EstruturaQualquer est2 = new EstruturaQualquer(10);
		est2.setItem(0, new Gerente() );
		est2.setItem(1, new Gerente() );

		double sal = est2.getItem(0).getSalario(); //isso possui um erro


}
```

Então vamos lá:


```java
	
		public static void main(Strings[] args){
	
			[...]

			EstruturaQualquer est2 = new EstruturaQualqyer(10);
			est2.setItem(0, new Gerente() );
			est2.setItem(1, new Gerente() );

			Gerente g = (Gerente) est2.getItem(0).getSalario(); //cast
			double sal = g.getSalario();

	
	}
	   
```

Agora que já entendemos a limitação, vamos ao próximo tópico.

**Classes Genéricas**

Classes Genéricas são muito boas para o que estamos querendo fazer. É comum que aqui você fique um pouco confuso, mas tenha uma coisa em mente: queremos criar estruturas que sejam implementadas um única vez e que sirva para String, Inteiro, Classes criadas por nós e outras. 

Basicamente Classes Genéricas postergam a definição do tipo de dados. Assim, ao invés de definirmos na implementação (Classe) o tipo a ser utilizado, vamos definir no instanciamento do objeto. As classes Genérias recebem um termo (T) que será substituída em tempo de execução, pelo tipo passado por parâmetro. Certamente você já utilizou algo similar como ArrayList, mas não sabia o motivo. 


```java

public class EstruturaQualquer<T>(){

	T[] vetor;

	public EstruturaQualquer(int tamanho){
		vetor = (T[]) new Object[tamanho];
	} 
	
	public void getItem(int i, T valor){
		vetor[i] = valor;
	}
	public T getItem(int i){
		retunr vetor[i];
	}

}
```
	   
Pare um pouco, observe esse código e compare com a implementação da subseção anterior sobre Object. O que mudou?


Certamente você percebeu que as referências do Object sumiram (menos a de instanciar o vetor, pois em Java não podemos criar diretamente um vetor genérico: *new T[tamanho]*. 

Ao usar essa estrutura, vamos dizer no instanciamento o tipo que desejamos:


```java

	public static void main(Strings[] args){

		EstruturaQualquer<String> est1 = new EstruturaQualquer<String>(10);
		est1.setItem(0, "Teste");
		est1.setItem(1, "Teste 2");

		EstruturaQualquer<Gerente> est2 = new EstruturaQualquer<Gerente>(10);
		est2.setItem(0, new Gerente() );
		est2.setItem(1, new Gerente() );


}
   
```

Vamos ao exemplo do uso de métodos específicos:

	
```java

	public static void main(Strings[] args){

		[...]

		EstruturaQualquer<Gerente> est2 = new EstruturaQualquer<Gerente>(10);
		est2.setItem(0, new Gerente() );
		est2.setItem(1, new Gerente() );

		double sal = est2.getItem(0).getSalario(); //isso NÃO possui erro


}
  
```

Pronto, chegamos ao nosso objetivo. Por se tratar de um assunto novo e abstrato, é recomendado que você implemente os exemplos com Object e Classes Genéricas para internalizar os conceitos. Vamos utilizar esse tipo de codificação para as estruturas a seguir: Pilha, Fila, Listas e Árvores.


# 2 - Pilha

A primeira estrutura de dados que vamos ver é a Pilha. A pilha é uma estrutura bastante simples que tem a seguinte característica: 

> Um elemento entra sempre pelo topo. Ao remover um elemento, só podemos removê-lo pelo topo. 

Essa característica significa dizer que não podemos remover imediatamente qualquer elementos desejado, é necessário obedecer esta ordem. Pense em uma pilha de pratos de louça que a nossa mãe tanto ama. Já pensou em remover um prato que está no meio da pilha e, por essa decisão, deixar cair os pratos de cima? Não queremos nem imaginar o problemão, em?

Logicamente que o mais pudente é retirar os pratos de cima um a um e colocar em algum outo lugar, até que possamos - com segurança - pegar o prato desejado. Então, vamos criar um algoritmo simples para modelar isso:

- Pega a pilha de pratos
- Remove o prato que está no topo desta pilha
- Coloca o prato do lado

Bem, isso deve se repetir até que cheguemos ao prato desejado, então...

- Pega a pilha de pratos
- Até chegar ao prato desejado
	- Remove o prato que está no topo desta pilha
	- Coloca o prato do lado

Quando chegar ao prato, devemos retirá-lo e usá-lo, além de recolocar os pratos no local (sim, somos organizados)! 

- Pega a pilha de pratos
- Até chegar ao prato desejado
	- Remove o prato que está no topo desta pilha
	- Coloca o prato do lado
- Pega o prato desejado
- Até que a pilha do lado seja esvaziada
	- Remover o prato que está no topo desta segunda pilha
	- Coloca o prato na pilha principal novamente

> Ufa! Não quebramos nenhum prato, pois seguimos o protocolo correto para a remoção segura. 

Basicamente esta é a ideia de pilha, você já deve ter entendido. Podemos então usar uma modelagem para essa situação. Como já conhecemos bem POO e gostamos de criar objetos, vamos pensar que o prato pode ser uma objeto do tipo Prato, ou de modo mais geral, um Item.  Outra coisa que devemos ter em mente é: *"devemos usar um vetor para armazenar muitos elementos, pois uma variável não daria conta!"*.

Então, temos:

- Uma classe Item;
- Um vetor.


Mas uma estrutura de dados não é formada apenas por locais onde podemos armazenar coisas ou objetos soltos no ar. Devemos criar operações que **garantam uma certa organização**, neste caso a organização da pilha: entra no topo, sai do topo. É interessante observar, caso ainda não tenha pensado nisso, que o elemento que entra do último é o primeiro a sair e o primeiro a entrar é o último a sair. Por esse motivo, a pilha é chamada de FILO (*First In, Last Out*).

Então, além dos dados, temos:

- Operação de inserir
- Operação de remover


### 2.1 - Inserindo dados em uma Pilha**

Mas como controlar que vou inserir no topo? Bem isso é simples, vamos pensar que temos um vetor de 10 elementos e no início todos são nulos. 

    [null, null, null, null, null, null, null, null, null, null]

Eu posso inserir na posição 0, ela será nosso topo.

    ["Prato A", null, null, null, null, null, null, null, null, null]

Se desejo inserir novamente, eu coloco todos os elemento para a a próxima posição e insiro na posição 0 novamente.

	["Prato B", "Prato A", null, null, null, null, null, null, null, null]


Você certamente já percebeu que eu precisaria transpor os elementos, posição por posição até disponibilizar um local vazio no início:

	int i = tamanho_pilha-1;
	while( (i > 0) && (pilha[i] = null) && (pilha[i-1] != null) )
		pilha[i] = pilha[i-1];
		i = i-1
 
	pilha[0] = "Prato C";


Nossa!!! Mas isso é muito custoso, não acha? Pense em uma Pilha de  1 milhão de dados. Quando tivermos ao menos 50% da Pilha com dados, teremos 500 mil alocações. No final, teremos 999.999 alocações, apenas para inserir um único elemento. **Nossa!!**.

**Usando um Topo**

Uma solução para esse problema é: criar uma variável que armazenará o valor (índice) do topo e assim, poderemos sempre inserir em uma posição vazia. No primeiro caso que apresentamos, o topo poderia ser -1 (pois a Pilha está vazia). Você deve pensar: "Mas na outra solução, se a inserção for no fundo, teríamos o mesmo resultado!". Não! Ainda seria preciso achar a posição vazia. 
	
	topo = -1
	[null, null, null, null, null, null, null, null, null, null]

Seguiremos:

	//inserindo o Prato A
	topo = 0
	["Prato A", null, null, null, null, null, null, null, null, null]
	//inserindo o Prato B
	topo = 1
	["Prato A", "Prato B", null, null, null, null, null, null, null, null]

Mas como ficaria esse algoritmo?

	topo++;
	pilha[topo] = "Prato C";

Só isso? Sim!!! Além de ter menos linhas, há menos necessidade de acesso aos dados. Agora, quando a pilha estiver com 50% de dados, teremos a mesma quantidade de operação que ele como 100% dos dados. **Que legal!!!**

### 2.2 - Removendo dados na Pilha

Analogicamente, na solução antiga precisaríamos percorrer todo o vetor até encontrar uma posição onde o próximo elemento é nulo, guardar este valor e colocar um valor nulo no local.

	["Prato A", "Prato B", "Prato C", "Prato D", null, null, null, null, null, null]

Vejamos:

- pilha na posição 0 é null?  // Não
- pilha na posição 1 é null?  // Não
- pilha na posição 2 é null?  // Não
- pilha na posição 3 é null?  // Não
- pilha na posição 4 é null?  // Sim
- guarde o valor da posição 3
- coloque null na posição 3
	
	["Prato A", "Prato B", "Prato C", null, null, null, null, null, null, null]

Sim, podemos usar o loop;
- n = 0
- Enquanto pilha na posição (n + 1)for diferente de null
	- n++
- Se n < tamanho da pilha
	- guarde o valor da posição n 
	- coloque null na posição n 


Já percebemos que essa solução não é ideal, por motivos claros e sabemos que o uso de uma variável de controle como o topo é ideal. Mas como ficaria esse código? Vamos ver:

	String item = pilha[topo]
	topo--
	return item

Pois é, só isso!!! Assim como a inserção, a remoção é muito simples. Logicamente que isso deve ser inserido em uma função, mas isso veremos mais a frente. 


**Verificações, porque não?**

>  You have a error of type 'StackOverflow' on line 4 - Pilha.java

Sim, ninguém quer ver um erro similar no seu mega projeto que demorou 10 dias para ser implementado, horas antes de vencer o prazo de envio ao professor da disciplina. Certamente o papo de "O cachorro comeu minha atividade" não vai colar. Então, precisamos fazer verificações no nosso projeto, para eliminar de uma vez por todas esses erros. 

Um pilha pode ser implementada com vetor ou com lista, neste caso estamos aprendendo como implementá-la em vetor e isso trás algumas limitações como por exemplo um tamanho máximo fixo de elementos que ele aceita. Como foi dito na Seção 2, existem dois motivos para verificarmos uma pilha baseada em vetor: *inserir em uma pilha cheia e remover em uma pilha vazia*.

A condição para um pilha está vazia é simples e já vimos aqui, é justamente o estado inicial dela, onde o topo é -1. 

	if(topo == -1)
		pilhavazia = true

Já a condição para ela está cheia ainda não vimos e vou dizer agora: basta que o topo seja igual ao tamanho do vetor - 1. Isso porque inserimos no vetor na posição "topo" e se topo é igual a o tamanho do vetor ou maior, não poderíamos inserir, pois é uma posição inválida.

	topo = 3
	["Prato A", "Prato B", "Prato C", "Prato D"]

Podemo inserir no topo? Vejamos:

- O topo será incrementado, ou seja virará 4
- Inserimos no vetor na posição 4 //Erro 

Isso certamente ocorrerá em erro, pois em um vetor de 4 posições (tamanho igual a 4), temos a primeira posição válida, a posição 0 e a última a 3. Ou seja, achamos um limite que é justamente quando o topo é igual à 3 (tamanho - 1).

	if(topo == tamanho_pilha - 1)
		pilhacheia = treu


**Observações**

Alguns exemplos aqui são didáticos, no sentido de que você entenda o problema. O código a seguir pode apresentar algumas diferenças, mas isso não impacta na solução do problema. Caso ainda ache que um algoritmo pode ser solucionado de apenas uma única forma, espero que reflita sobre isso. Esse é o momento! 


### 2.4 - Overview

Agora você está pronto para consultar o código da Pilha.java que implementamos.

```java
public class PilhaV<T> {

	/**
	* Array da Pilha 
	*/
	private T[] arrayPilha;
	/**
	* Atributo para armazenar o indice do topo da pilha
	*/
	private int topo;
	
	/**
	* Contrutor da Pilha
	* @param max Tamanho da pilha
	*/
	public PilhaV(int max){
		//instanciando um vetor genérico (cria um vetor do tipo Objetc e faz o cast (conversão) para o tipo T
		arrayPilha = (T[]) new Object[max];
		topo = -1;
	}
	
	/**
	* Insere um elemento se a pilha não estiver cheia
	* @param elemento Elemento a ser inserido na pilha
	* @return retora true se a operação foi bem sucedida
	*/
	public boolean inserir(T elemento) {		
		if(!this.estaCheia()) {
		topo++;
		arrayPilha[topo] = elemento;
		return true;
	}
	
	return false;
	}
	
	/**
	* Remove um elemento da pilha, se ela não esiver vazia
	* @return retorna o elemento se a operação foi bem sucedida
	*/
	public T remover() {		
	
	
	if(!this.estaVazia()) {			
		return arrayPilha[topo--];
	}
	
	return null;
	
	}
	
	/**
	* Verifica se a pilha está vazia
	* @return retorna true se a pilha estiver vazia
	*/
	public boolean estaVazia() {		
		return topo == -1;
	}
	
	/**
	* Verifica se a pilha está cheia
	* @return retorna true se a pilha estiver cheia
	*/
	public boolean estaCheia() {		
		return topo == arrayPilha.length-1;
	}
}
```


Link aqui: [PilhaV.java](https://github.com/LuisAraujo/Disciplina-Estrutura-de-Dados/blob/master/Pilha/PilhaV.java)



# 3 - Fila

Bem, chegamos a nossa segunda estrutura de dados: a Fila. Quando falamos em fila, já pensamos em filas de banco, atendimento e etc. Você irá se espantar se eu lhe disser que é justamente isso. Lembra que falamos sobre "Modelagem Computacional"? Pois é, aqui vamos modelar uma Fila. Intuitivamente a Fila tem a seguinte característica:

> Um elemento entra sempre no final. Ao remover um elemento só podemos remover o elemento no início.

Isso quer dizer que não podemos remover um elemento se ele não for o elemento que está no início (o próximo a ser atendido). Já pensou se você está em uma Fila, esperando cerca de 30 minutos, é o próximo a ser atendido, e alguém passa na sua frente, sem nenhuma justificativa? É realmente indignante! 

Como fizemos com a Pilha, faremos um algoritmo informal para atender pessoas em Fila. Imagine esse cenário: Uma pessoa D chega ao Banco e verifica que a fila para o atendimento que deseja já possui a pessoa A, B e C.

 
* A pessoa D entra no final da fila
* A pessoa A é atendida!
	* *A pessoa B é a próxima a ser atendida*.
* A pessoa B é atendida!
	* *A pessoa C é a próxima a ser atendida*.
* A pessoa C é atendida!
	* *A pessoa D é a próxima a ser atendida*.
* A pessoa D é atendida!

Bem, há uma repetição aqui, então vamos ajustar usando loop:

* A pessoa D entra no final da fila
* Atá que a pessoa C seja atendida!
	* *Atender Próxima pessoa*
* A pessoa D é atendida!

> Ok, garantimos que a pessoa 'D' será atendida conforme sua posição, assim uma pessoa 'E' não será atendida antes dela.

Assim como fizemos com Pilha, vamos também implementar algo mais formal usando a linguagem de programação Java para isso. Como queremos usar POO, vamos criar algumas classes para serem a "forma" dos nossos objetos. Vamos criar o elemento, um Item que será colocado na Fila e a própria fila, para isto usaremos um simples vetor.

Então:

* Uma classe item (sim, podemos usar a mesma da pilha, copie para o seu novo projeto).
* Um vetor.

Além dos locais de armazenamento, precisamos garanti as operações da Fila. A Fila - diferentemente da Pilha - é uma estrutura onde o último elemento a entrar será também o último a sair, isso quer dizer que o primeiro a entrar será o primeiro a sair, por isso ela é conhecida como FIFO (*First Input First Output*).

Então, além dos dados temos:

* Operação de inserir
* Operação de remover


### 3.1 - Inserindo dados na Fila

Mas como controlar que vou inserir no início? Ok, se você pensou "vou usar o mesmo que fiz na pilha", você está no caminho certo. Vamos pensar que temos um vetor de 10 elementos e no inicio todos são nulos.

	[null, null, null, null, null, null, null, null, null, null]

Eu posso inserir na posição com menor índice que possui o valor null, ela será o nosso final.

	["Pessoa A", null, null, null, null, null, null, null, null, null]

Se desejo inserir novamente, eu coloco na próxima posição com menor índice que esteja vazia (null).

	["Pessoa A", "Pessoa B", null, null, null, null, null, null, null, null]

Você certamente já percebeu que eu precisaria verificar, posição por posição até chegar a uma vazia:

	int pos_vazia = 0;
	while( (i< tamanho_fila) && (fila[i] != null) )
		pos_vazia++;
	
	if(pos_vazia < tamanho_fila)
		fila[i] = "Prato C";

**Nossa!!!** Mas isso é muito custoso! Pense em uma Fila de 1 milhão de lugares. Quando tivermos que inserir o primeiro elemento, faremos 999.999 comparações apenas para inserir um único elemento. 


**Usando o fim** (um primo distante do topo)

Uma solução para esse problema é criar uma variável que armazenará o valor (índice) do fim, assim como o topo. Com isso, poderemos sempre inserir em uma posição vazia. No primeiro caso que apresentamos, o fim inicial poderia ter o valor 0.

	fim = 0
	[null, null, null, null, null, null, null, null, null, null]

Seguiremos:
	
	//Inserir Pessoa A
	fim = 1
	["Pessoa A", null, null, null, null, null, null, null, null, null]
	//Inserir Pessoa B
	fim = 2
	["Pessoa A", "Pessoa B", null, null, null, null, null, null, null, null]

Mas como ficaria esse algoritmo?

	//Inserir Pessoa C
	fila[fim] = "Prato C";
	fim++


Só isso? Sim!!! Como na Pilha, além de ter menos linhas, temos menos acesso aos dados. Agora, quando a Fila estiver com 50% de dados, teremos a mesma quantidade de operações que ela como 100% dos dados. **Que legal!!!**


### 3.2 - Removendo Dados na Fila

Para remover um dado na fila, precisaríamos apenas remover o elemento no início, que naquele caso inicial é o 0. Isso é muito simples, mas há o fator complicador que é a realocação de todos os elementos em suas novas posições.

Vetor inicial:
	
	["Pessoa A", "Pessoa B", "Pessoa C", "Pessoa D", null, null, null, null, null, null]

Removendo o primeiro elemento:

	[null, "Pessoa B", "Pessoa C", "Pessoa D", null, null, null, null, null, null]

Realocando os elementos:

	["Pessoa B", "Pessoa C", "Pessoa D", null, null, null, null, null, null, null]


Um algoritmo informal para a realocação seria:

* Remover a posição 0 do vetor;
* A posição 1 é diferente de null?
	* Mova o elemento 1 para 0
* A posição 2 é é diferente de null?
	* Mova o elemento 2 para 1
* A posição 3 é é diferente de null?
	* Mova o elemento 3 para 2

Usando loops:

* i = 0
* Remover a posição i do vetor;
* Enquanto a posição i + 1 for diferente de null
	* Mova o elemento i + 1 para i


Já percebemos que essa solução não é ideal! Poderíamos então usar outra variável  chamada início pra controlar a remoção:

	String item = fila[inicio]
	inicio++
	return item

**Verificações, porque não?**

>  OMG!!! You have YET a error of type 'StackOverflow' on line 4 - Fila.java

Já falei sobre a estória do "O cachorro comeu minha atividade" não é? Então vamos evitar isso fazendo as verificações necessárias no nosso projeto.

Assim como uma pilha, a fila pode ser implementada com vetor ou com lista, estamos implementando com vetor, neste momento.  Chegará o momento de usarmos lista, mais a frente. Bem, usar vetor torna o processo mais básico e agrega algumas limitações como por exemplo um tamanho máximo fixo de elementos que ele aceita. Assim, existem dois motivos para verificarmos uma fila baseada em vetor: inserir em uma fila cheia e remover em uma fila vazia.

As condições para verificar a fila é um pouco mais complexa, mas nada que não possamos aprender. Bem, uma fila não pode está vazia quando o final é 0, isso porque o final e o início caminham ao longo dela. Então, mesmo o final sendo 0, pode ser que o início seja 10, em uma fila com 15 posições. Logo, temos elementos na posição 10, 11, 12, 13 e 14. *Isso impede o desperdício de locais no vetor*. Mas vamos focar nas condições, por hora aceite que a fila vazia pode ser identificada quando o início for igual ao fim.

	if(inicio == fim)
		filavazia = true 


A condição para ela está cheia é também diferente da Pilha. Uma Fila está cheia quando  a subtração do fim pelo início for igual  à 1 (fim - início == 1) ou (fim = início - 1). Como dito antes, o índice do final e do início caminham ao longo da fila. Logo quando o fim for igual ao tamanho da fila e início for 0, ela também está cheia


	if(fim == tamanho_fila) && (inicio == 0) ) || (fim == inicio-1)
			filacheaia = true 



**Explorando mais sobre o início e o fim**


Como dizia Raul Seixas: "eu sou o início, o fim e o meio". Logicamente que ele não estava falando de uma fila, mas poderia. O fim e o início em uma fila não funcionam como o topo de uma Pilha. O topo em uma pilha varia de -1 até o tamanho da pilha. Na Fila isso não seria muito bom. Vamos pensar em uma fila com capacidade para 8 elementos e inicialmente com 4 elementos:

	    inicio                                      fim 
	      |                                          |
	      v                                          v
		    
	["Pessoa A", Pessoa B", "Pessoa C", "Pessoa D", null, null, null, null]


Ao remover os elementos teríamos:

 			     inicio   fim 
				|       |
				v       v
		    
	[null, null, null, "Pessoa D", null, null, null, null]

Adicionando mais 4 elementos teríamos

			   inicio    					              fim 
			     |                                                         |
			     v                                                         v
		    
	[null, null, null, "Pessoa D", "Pessoa E", "Pessoa F", "Pessoa G", "Pessoa H"]


Ok, até ai nada de novo. Mas o que aconteceria se eu removesse 4 elementos?


				                    inicio    fim 
			                              |        |
				                      v        v
		    
	[null, null, null, null, null, null, null, "Pessoa H"]


Sim, temos 7 posições vazias (*nulls*) e não podemos inserir, pois o fim já chegou ao seu limite. Inserir na posição do fim, nessa situação, nos levaria para um erro por acesso à local não permitido. #stackoverflow 

Por esse motivo que, quando vamos inserir e verificamos que o fim chegou no seu limite, ele é transportado para o índice 0, para que possamos inserir mais elementos: 

	if(fim ==tamanho_fila)
			fim = 0;

Como exercício desenhe uma fila de 10 posições, insira elementos e remova-os. Deixando a fila cheia no primeiro momento e depois vazia. Faça isso ao menos 3 vezes na mesma pilha e verá como essa transição funciona.  

**Observações**

Como na Seção anterior, alguns exemplos aqui são didáticos, no sentido de que você entenda o problema. O código a seguir pode apresentar algumas diferenças, mas isso não impacta na solução do problema. Como já dito anteriormente, não há uma solução fechada para um algoritmo. 

**Overview**

Agora você está pronto para consultar o código da Fila.java que implementamos.
	
```java 
public class FilaV<T>{
	private T[] arrayFila;
	private int inicio;
	private int fim;
	
	public FilaV(int size){
		inicio = fim = 0;
		arrayFila = (T[]) new Object[size];
	}
	
	public boolean estaCheia(){
		return ((fim == arrayFila.length-1) && (inicio == 0) )
				|| (fim == inicio-1);
	}
	
	public boolean estaVazia(){
		return inicio == fim;
	}
	
	public T remover(){
		if(!estaVazia()){
			T e = arrayFila[inicio];
			inicio++;
			return e;
		}
		
		return null;
	}
	
	public boolean inserir(T e){
		if(fim == arrayFila.length)
			fim = 0;
		
		if(!estaCheia()){
			arrayFila [fim++] = e;
			System.out.println("inserindo - " + fim);
			return true;
		}
		
		return false;
	}
	
	@Override
    public String toString(){
		
        String s = "[";
        int i = inicio; 
        while(i != fim){
        	System.out.println(s);
            if(i == arrayFila.length)
                i = 0;
            
            if(i == fim-1) 
                s+=arrayFila[i];
            else 
                s+=arrayFila[i] + " , ";
        
            i++;
    		
        }
        
        return s + "]";  
    }
}
```


Link aqui: [FilaV.java](https://github.com/LuisAraujo/Disciplina-Estrutura-de-Dados/blob/master/Fila/FilaV.java)


# 4 - Listas Simplesmente Encadeada

Parabéns, espero que até aqui vocês tenha aprendido sobre Pilha e Fila. Caso contrário eu lhe deixo uma máxima que sempre digo: 

> Não importa o quanto você veja, leia ou ouça, você só aprenderá de fato se tentar. O erro nesta fase é normal, mas você deve lidar com ele, verificá-lo, analisá-lo, testar o seu código e assim chegará ao topo, não só da pilha (rs), mas da montanha. Onde habitam os *programadores(as)-ninjas*! 

Assim, Lista Simplesmente Encadeada é uma estrutura multifacetada, ela possui variações dos métodos de inserção e remoção. Diferentemente da Fila e Pilha que só permitiam a entrada e saída de dados de um único local. Existem muitos tipos de Lista, mas aqui, nesta Seção, falaremos apenas da Simplesmente Encadeada, assim sempre que mencionarmos o termo Lista, nesta Seção, estamos nos referindo à Lista Simplesmente Encadeada.

A Lista está mais próxima de um Vetor do que das estruturas que fizemos até aqui, por isso mesmo é que ela pode ser utilizada em substituição dos vetores, nas Pilhas e Filas, eliminando os problemas de limitação e de desperdício de espaço de memória. Assim, as Listas alocam memória quando necessário e despejam quando não precisam mais. 

**Saindo de Vetor e indo para lista**


### 4.1 - A Lista

**O Nó**

[TEXTO]

**A lista, uma cadeia de Nós**

[TEXTO]

### 4.2 -Inserindo na Lista

### 4.3 -Removendo da Lista

### 4.4 -Buscando na Lista