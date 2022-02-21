package application;

import java.util.ArrayList;
import java.util.List;
import java.util.Locale;

import entities.Product;
import util.ProductPredicate;

/*
 * essa é a primeira possibilidade de implementação de interface.
 */

public class Program {

	public static void main(String[] args) {

		Locale.setDefault(Locale.CANADA);
		List<Product> list = new ArrayList<>();
		
		list.add(new Product("Tv", 900.00));
		list.add(new Product("Mouse", 50.00));
		list.add(new Product("Tablet", 350.50));
		list.add(new Product("HD Case", 80.90));
		
		list.removeIf(new ProductPredicate());
		/*
		 * eu venho aqui e dentro do removeIf eu vou colocar uma instancia da minha classe ProductPredicate() e pronto.
		 * ele excluiu da lista somente quem atendia esse predicado.
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
===========================================================================

package util;

import java.util.function.Predicate;

import entities.Product;

public class ProductPredicate implements Predicate<Product> {

	@Override
	public boolean test(Product p) {
		return p.getPrice() >= 100.0;
		/*
		 * eu quero excluir da lista aqueles produtos que tem o preço maior ou igual a 100.0.
		 * é uma função que retorna um booleano, se a condição for verdadeira, a função tambem vai retornar um valor
		 * verdadeiro.
		 */
	}

}
	
![1](https://user-images.githubusercontent.com/61166475/155022544-d16b41d9-a16d-4dec-98d6-e4cc581b0eb0.png)
![2](https://user-images.githubusercontent.com/6![3![4](https://user-images.githubusercontent.com/61166475/155022556-48a5a15e-9639-4c7b-915c-214d70ba161a.png)
![3](https://user-images.githubusercontent.com/61166475/155022614-21419fb4-677b-43e0-a38b-abc907583cac.png)
![4](https://user-images.githubusercontent.com/61166475/155022619-afb6059a-4acf-4cac-b9fa-db072eb8e6ae.png)
