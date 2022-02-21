package application;

import java.util.ArrayList;
import java.util.List;
import java.util.Locale;
import java.util.function.Consumer;

import entities.Product;

/*
 *  essa é a quarta possibilidade, com expressão lambda declarada.
 */
public class Program {

	public static void main(String[] args) {

		Locale.setDefault(Locale.CANADA);
		List<Product> list = new ArrayList<>();
			
		list.add(new Product("Tv", 900.00));
		list.add(new Product("Mouse", 50.00));
		list.add(new Product("Tablet", 350.50));
		list.add(new Product("HD Case", 80.90));
		
		double factor = 1.1;
		/*
		 * aqui vamos declarar uma variavel do tipo consumer parametizado com o Product chamado cons, ele vai receber uma
		 * função que vai receber um produto p, e vai fazer a atualização do preço.
		 * 
		 * esse 1.1 agora nesse contexto do programa, ele pode ir para outra variavel, assim fica legal porque fica mais
		 * flexivel, o valor de atualização de preço pode vim de uma variavel que ta fora, que pode ser inclusive lida
		 * pelo usuario.
		 */
		Consumer<Product> cons = p -> { // as chaves são opcionais, eu posso apagar se quiser, funciona tambem.
			p.setPrice(p.getPrice() * factor); 
		};
		
		list.forEach(cons);
		/*
		 * Como que eu faço para percorrer essa minha lista, e aumentar o preço de cada produto em 10%, como que eu faço isso?
		 * bom, vamos falar agora de um metodo default na interface List chamado forEach, e esse forEach, ele recebe um
		 * Consumer como argumento, esse forEache é um default method, que ele vai percorrer a coleção e ele vai executar um 
		 * consumer dessa coleção pra cada elemento.
		 * 
		 * O Consumer<T> ele é um cara que vai ter um metodo accept(T t);
		 * então vamos criar uma classe para implementar essa interface Consumer.
		 * 
		 */
		list.forEach(System.out::println);
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

![1](https://user-images.githubusercontent.com/61166475/155024730-a4ba2c1c-2b66-422e-b87f-6f6ef72086a2.png)
![2](https://user-images.githubusercontent.com/61166475/155024733-9d229bb6-ab07-4b98-b404-72fe9c29b5ee.png)
![3](https://user-images.githubusercontent.com/61166475/155024734-25ebec82-822b-4f57-9b10-58f34a48f213.png)
