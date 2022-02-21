package application;

/*
 * esse function vai ser de que tipo? o Function ele tem dois tipos, o de entrada e o de saida.
 * no caso aqui como eu quero transformar objetos Product em nomes de produto, o tipo de entrada vai ser Product e o tipo
 * de saida vai ser String, por que? por que eu quero mecher no que ta na classe Product e quero ter de saida o nome deles
 * em caixa alta, ou seja, saida de String
 */

import java.util.ArrayList;
import java.util.List;
import java.util.Locale;
import java.util.stream.Collectors;

import entities.Product;

/*
 *  essa é a quarta possibilidade de implementação de interface, com expressão lambda inline.
 */

public class Program {

	public static void main(String[] args) {

		Locale.setDefault(Locale.CANADA);
		List<Product> list = new ArrayList<>();
			
		list.add(new Product("Tv", 900.00));
		list.add(new Product("Mouse", 50.00));
		list.add(new Product("Tablet", 350.50));
		list.add(new Product("HD Case", 80.90));
		
		/*
		 * agora aqui no nosso programa nos vamos ter que fazer algo para aplicar aquela função UpperCaseName para
		 * todo os elementos daqui da minha lista. pra fazer isso eu vou usar uma função chamada map, (não confunda com a estrutura de dados Map)
		 * A função "map" é uma função que aplica uma função a todos elementos de uma stream. o que é uma stream?
		 * ela é uma sequencia de dados. Mas o que é importante entender tambem? é que a função map ela não funciona 
		 * apartir de uma lista, ela funciona apartir de uma .stream, e ai então eu vou ter que converter a minha lista
		 * para .stream, aplicar esse map, e depois eu vou ter que converter esse .stream devolta para lista.
		 * 
		 * pra eu converter uma lista para .stream, eu vou ter que chamar .stream apartir da lista.
		 * e para converter uma stream pra uma lista, eu vou ter que chamar .collect(collectors.toList()); apartir 
		 * da .stream
		 */
		
		List<String> names = list.stream().map(p -> p.getName().toUpperCase()).collect(Collectors.toList());
		/*
		 * o .map ele aplica a função que estiver dentro dela: .map( Product::nonStaticUpperCaseName ) a cada elemento da lista.
		 * lembrando que a operação map ela só funciona para .stream, ela n funciona para List, por isso que eu tive
		 * que primeiro converter a minha Lista para stream chamando ->(list.stream()), e depois convertendo a minha
		 *  stream divolta pra lista, chamando ->( .collect(Collectors.toList()) ), e toda essa sequencia  de chamadas
		 *  list.stream().map(Product::nonStaticUpperCaseName).collect(Collectors.toList()); vai produzir a minha nova lista de 
		 *  nomes -> List<String> names =, olha que interesante
		 */
		
		names.forEach(System.out::println);
		//aqui eu estou usando um Reference Method para o println.
		
	}

}

===========================================================================

package entities;

public class Product {

	private String name;
	private Double price;
	
	public Product() {
	}

	public Product(String name, Double price) {
		this.name = name;
		this.price = price;
	}

	public String getName() {
		return name;
	}

	public void setName(String name) {
		this.name = name;
	}

	public Double getPrice() {
		return price;
	}

	public void setPrice(Double price) {
		this.price = price;
	}
	
	@Override
	public String toString() {
		return name + ", " + String.format("%.2f", price);
	}
}

![1](https://user-images.githubusercontent.com/61166475/155024336-d9a812d8-ad9b-4959-8b5c-94a003477a8c.png)
![2](https://user-images.githubusercontent.com/61166475/155024339-7c5ffbf6-6399-4033-bba9-0678c4d76939.png)
![3](https://user-images.githubusercontent.com/61166475/155024340-883f6eeb-cfe1-4f68-a316-1a0146529538.png)
![4](https://user-images.githubusercontent.com/61166475/155024341-dfebd196-063e-43e8-bb22-437c71608e17.png)
