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
