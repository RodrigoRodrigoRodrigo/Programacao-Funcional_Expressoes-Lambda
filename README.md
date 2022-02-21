package application;

import java.util.ArrayList;
import java.util.List;
import java.util.Locale;

import entities.Product;
import util.PriceUpdate;

/*
 *  essa é a primeira possibilidade de implementação de interface.
 */
public class Program {

	public static void main(String[] args) {

		Locale.setDefault(Locale.CANADA);
		List<Product> list = new ArrayList<>();
			
		list.add(new Product("Tv", 900.00));
		list.add(new Product("Mouse", 50.00));
		list.add(new Product("Tablet", 350.50));
		list.add(new Product("HD Case", 80.90));
		
		list.forEach(new PriceUpdate());
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
		
		/*
		 * ta funcionando perfeitamente, adicionamos aqui o nosso consumer(PriceUpdate) com a função para atualizar o preço
		 * p.setPrice(p.getPrice() * 1.1);, e ai foi so chamar ela dentro do forEach que ele atualizou o preço de todos os 
		 * produtos.
		 */
		
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

import java.util.function.Consumer;

import entities.Product;

public class PriceUpdate implements Consumer<Product> {

	@Override
	public void accept(Product p) {
		p.setPrice(p.getPrice() * 1.1);
	}

}

  
![1](https://user-images.githubusercontent.com/61166475/155024441-689395cb-c3ca-4141-be64-4e540294712f.png)
![2](https://user-images.githubusercontent.com/61166475/155024442-32685c5f-3571-44ab-9cf1-b136b4a7d70d.png)
![3](https://user-images.githubusercontent.com/61166475/155024444-c950103b-1c17-447b-a1a0-0361a0451c00.png)
