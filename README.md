package application;

import java.util.ArrayList;
import java.util.List;
import java.util.Locale;

import entities.Product;

/*
 * essa é a segunda possibilidade de implementação de interface, a segunda possibilidade diferente vai ser o Reference Method
 * ou seja, uma referencia para metodo utilizando metodo estatico.
 * essa foi a segunda versão da implementação do predicado
 */

public class Program {

	public static void main(String[] args) {

		Locale.setDefault(Locale.CANADA);
		List<Product> list = new ArrayList<>();
		
		list.add(new Product("Tv", 900.00));
		list.add(new Product("Mouse", 50.00));
		list.add(new Product("Tablet", 350.50));
		list.add(new Product("HD Case", 80.90));
		
		list.removeIf(Product::staticProductPredicate);
		/*
		 * eu vou colocar aqui a classe product, usso :: para referência ao método, e ai o nome do metodo.
		 * isso daqui é o que a gente chama de MethodReference, isso aqui tambem é aceito no sistema lambda do JAVA.
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
	
	public static boolean staticProductPredicate(Product p) {
		return p.getPrice() >= 100.0;
		/*
		 * eu vou mostrar agora que aqui no JAVA, ele tambem aceita uma referencia para o metodo, ao invez de aceitar apenas
		 * um objeto instanciado da minha classe.
		 * 
		 * metodo estatico ele trabalha com o produto que você passa como argumento pra ele, o metodo não estatico, é o 
		 * metodo da instancia, então ele vai trabalhar com o proprio objeto onde eu estou. 
		 */
	}

	@Override
	public String toString() {
		return name + ", " + String.format("%.2f", price);
	}
}

