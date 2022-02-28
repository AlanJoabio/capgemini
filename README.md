#           Academia Técnica Capgemini:school:

##                        Academia Java Capgemini

####                                            Desafio de Programação

# Questão 01**

## :pencil:Resolução:

```
package br.com.capgemini.desafio.funcoes;

import java.util.Scanner;

public class QuestaoUm {

public static void main(String[] args) {
	
	int numero;
	String escadaMontada;
	Scanner scanner = new Scanner(System.in);

	System.out.print("Digite um tamanho numérico para forma sua escada: ");
	numero = scanner.nextInt();
	escadaMontada = montaEscada(numero);

	System.out.println(escadaMontada);

}

public static String montaEscada(int numero) {
	
	int a;
	String escada = "";

	for (a = 1; a <= numero; a++) {
		escada += " ".repeat(numero - a) + "*".repeat(a) + "\n";
	}

	return escada;
    }
    }
```

# Questão 02

## :pencil:Resolução:

```
package br.com.capgemini.desafio.funcoes;

import java.util.Scanner;
import java.util.regex.Pattern;

public class QuestaoDois {

public static void main(String[] args) {

	String senha;
	int valor;
	Scanner scanner = new Scanner(System.in);

	System.out.print("Escreva sua senha: ");
	senha = scanner.next();
	valor = validaSenha(senha);

	System.out.println(valor);

}

public static Integer validaSenha(String senha) {
	int tamanho = senha.length();
	int x = 0;
	int y;
	boolean senhaMinuscula = Pattern.matches("^(?=.*[a-z]).+$", senha),
			senhaMaiuscula = Pattern.matches("^(?=.*[A-Z]).+$", senha),
			senhaDigito = Pattern.matches("^(?=.*\\d).+$", senha),
			senhaEspecial = Pattern.matches("^(?=.*[-+_!@#$%^&*.,?]).+$", senha);

	if (senhaMinuscula == false) {
		x += 1;
	}
	if (senhaMaiuscula == false) {
		x += 1;
	}
	if (senhaDigito == false) {
		x += 1;
	}
	if (senhaEspecial == false) {
		x += 1;
	}

	if (tamanho + x >= 6) {
		return x;
	} else {
		y = (6 - tamanho);
		return y;
	}

    }
}
```



# Questão 03

:pencil:Resolução:

```
package br.com.capgemini.desafio.funcoes;

import java.util.Arrays;
import java.util.HashMap;
import java.util.Scanner;

public class QuestaoTres {

public static void main(String[] args) {

	String palavra;
	int valor;
	Scanner scanner = new Scanner(System.in);

	System.out.print("Digite uma palavra qualquer: ");
	palavra = scanner.next();
	valor = montaParesAnagrama(palavra);

	System.out.println(valor);
}

public static Integer montaParesAnagrama(String palavra) {

	HashMap<String, Integer> map = new HashMap<>();
	int a, b, tamanho = palavra.length();

	for (a = 0; a < tamanho; a++) {
		for (b = a; b < tamanho; b++) {
			char[] arrayPalavra = palavra.substring(a, b + 1).toCharArray();
			Arrays.sort(arrayPalavra);
			String chaveArrayPalavra = new String(arrayPalavra);
			if (map.containsKey(chaveArrayPalavra))
				map.put(chaveArrayPalavra, map.get(chaveArrayPalavra) + 1);
			else
				map.put(chaveArrayPalavra, 1);
		}
	}

	int paresAnagrama = 0;
	for (String chave : map.keySet()) {
		int x = map.get(chave);
		paresAnagrama += (x * (x - 1)) / 2; 
	}
	return paresAnagrama;
}
}
```

s
