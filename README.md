package application;

import java.util.ArrayList;
import java.util.List;
import java.util.Locale;

import entities.Product;

/*
 * essa é a quinta versão. com expressão lambda inline, e não declara.
 */

public class Program {

	public static void main(String[] args) {

		Locale.setDefault(Locale.CANADA);
		List<Product> list = new ArrayList<>();
		
		list.add(new Product("Tv", 900.00));
		list.add(new Product("Mouse", 50.00));
		list.add(new Product("Tablet", 350.50));
		list.add(new Product("HD Case", 80.90));
		
		//desse jeito é bacana, por que eu posso inclusive colocar um valor aqui parametizado.
		double min = 100.0;
		
		list.removeIf(p -> p.getPrice() >= min);
		/*
		 * como assim? ao invez de declarar o predicado aqui e depois usar a variavel do predicado, eu vou simplesmente
		 * pegar essa versão lambda aqui: p -> p.getPrice() >= min; e colocar ela diretamente como argumento aqui do
		 * removeIf, e ai eu posso apagar essa decalração do predicado.
		 * aqui na hora de fazer a expressão lambda, eu não precisei declarar aqui essa variavel p, por que ela é do 
		 * tipo product, aqui o proprio compilador fez a inferencia dos tipos, ele deduzio que o tipo desssa variavel 
		 * aqui é do product, então é isso aqui que a gente chamamos de inferencia de tipos.
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

![1](https://user-images.githubusercontent.com/61166475/155023179-0b655598-f435-4e52-b5c7-a64325c1f7db.png)
![2](https://user-images.githubusercontent.com/61166475/155023184-61402c1e-99e3-4af9-baf9-131283679f51.png)
![3](https://user-images.githubusercontent.com/61166475/155023185-d5df809d-b8c5-40eb-944b-ea1f9fe702ab.png)
![4](https://user-images.githubusercontent.com/61166475/155023188-8e31051e-25ca-4ce8-94d5-80a9429263ae.png)
