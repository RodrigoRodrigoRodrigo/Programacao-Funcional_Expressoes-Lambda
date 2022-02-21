package application;

import java.util.ArrayList;
import java.util.List;
import java.util.Locale;

import entities.Product;

/*
 * essa é a terceira versão, eu vou fazer o reference method, só que o metodo comum, não estatico.
 */

public class Program {

	public static void main(String[] args) {

		Locale.setDefault(Locale.CANADA);
		List<Product> list = new ArrayList<>();
		
		list.add(new Product("Tv", 900.00));
		list.add(new Product("Mouse", 50.00));
		list.add(new Product("Tablet", 350.50));
		list.add(new Product("HD Case", 80.90));
		
		list.removeIf(Product::nonStaticProductPredicate);
		/*
		 * e vou trocar aqui para o nonStaticProductPredicate
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
	
	public boolean nonStaticProductPredicate() {
		return price >= 100.0;
		/*
		 * aqui, como ele é um metodo não estatico, ele é um metodo que vai trabalhar com o proprio produto aonde eu estou,
		 * e não com o produto que vai vim como argumento, então eu vou apagar o argumento(Product p). 
		 * metodo estatico ele trabalha com o produto que você passa como argumento pra ele, o metodo não estatico, é o 
		 * metodo da instancia, então ele vai trabalhar com o proprio objeto onde eu estou.
		 * no caso aqui, eu vou trocar o  p.getPrice() por apenas price,
		 */
	}

	@Override
	public String toString() {
		return name + ", " + String.format("%.2f", price);
	}
}

![1](https://user-images.githubusercontent.com/61166475/155023015-1a819759-2179-4c8d-87dc-44a766908a75.png)
![2](https://user-images.githubusercontent.com/61166475/155023018-cc05293c-8de9-48d8-b4f2-a3293733c225.png)
![3](https://user-images.githubusercontent.com/61166475/155023021-702fa7d3-d02f-43d8-9224-a911ece8ced1.png)
![4](https://user-images.githubusercontent.com/61166475/155023022-a285271f-dc75-452e-ab4a-d31de5affc92.png)
