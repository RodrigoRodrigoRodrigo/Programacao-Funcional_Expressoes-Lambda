package application;

import java.util.ArrayList;
import java.util.List;
import java.util.Locale;

import entities.Product;

/*
 *  essa é a segunda possibilidade de implementação de interface. o reference method com o metodo estatico.
 */
public class Program {

	public static void main(String[] args) {

		Locale.setDefault(Locale.CANADA);
		List<Product> list = new ArrayList<>();
			
		list.add(new Product("Tv", 900.00));
		list.add(new Product("Mouse", 50.00));
		list.add(new Product("Tablet", 350.50));
		list.add(new Product("HD Case", 80.90));
		
		list.forEach(Product::staticPriceUpdate);
		//usando o reference method.
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

	public static void staticPriceUpdate(Product p) {
		p.setPrice(p.getPrice() * 1.1);
	}
	
	@Override
	public String toString() {
		return name + ", " + String.format("%.2f", price);
	}
}

![1](https://user-images.githubusercontent.com/61166475/155024544-4a95a2d2-328a-4cce-aa5d-b5bf504b8db9.png)
![2](https://user-images.githubusercontent.com/61166475/155024548-c6d58a7d-f668-4ebc-a6c9-420a23b1f795.png)
![3](https://user-images.githubusercontent.com/61166475/155024550-39c990fa-2710-4e1c-a80a-b4fe078ac172.png)
