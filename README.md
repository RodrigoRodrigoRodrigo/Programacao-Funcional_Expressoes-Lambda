package application;

import java.util.ArrayList;
import java.util.List;
import java.util.Locale;
import java.util.function.Predicate;

import entities.Product;

/*
 * essa é a quarta versão. com expressão lambda declarada.
 */

public class Program {

	public static void main(String[] args) {

		Locale.setDefault(Locale.CANADA);
		List<Product> list = new ArrayList<>();
		
		list.add(new Product("Tv", 900.00));
		list.add(new Product("Mouse", 50.00));
		list.add(new Product("Tablet", 350.50));
		list.add(new Product("HD Case", 80.90));
		
		Predicate<Product> pred = p -> p.getPrice() >= 100.0;
		/*
		 * eu vou criar um Predicate do tipo product com o nome de pred, e ai eu vou falar que esse predicado aqui vai
		 * receber uma expressão lambdaque expressão lambda que é essa? é uma função anonima que recebe como argumento
		 * um produto p, e ai ela vai me resultar(->) no booleano que vai ser o p.getPrice() maior ou igual(>=) a 100.0.
		 */
		
		list.removeIf(pred);
		/*
		 * eu vou apagar o que está dentro do removeIf, que era (Product::nonStaticProductPredicate) da 3º versão do predicado.
		 * e vou colocar no lugar uma variavel que vou criar emcima dele, do list.removeIf().
		 * qual vai ser o tipo dessa variavel? um predicado.
		 * 
		 */
		
		for (Product p : list) {
			System.out.println(p);
		}
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

![1](https://user-images.githubusercontent.com/61166475/155023101-c5d13dee-c5ad-4a04-9fb6-2d0ed7d74594.png)
![2](https://user-images.githubusercontent.com/61166475/155023105-919843f6-fdfb-4b1a-a16c-34ac1df9732c.png)
![3](https://user-images.githubusercontent.com/61166475/155023107-123fa488-cadc-4e2d-aefb-4f31d5445877.png)
![4](https://user-images.githubusercontent.com/61166475/155023108-59e3ed8d-cb1b-4d20-8295-55d5010d8c95.png)
