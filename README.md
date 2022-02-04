# Solução Desafio de código da Novatics!

## Problema 1

<details>
<summary>Manipulando listas</summary>
Crie uma função que receba uma lista de números inteiros como parâmetro. Essa função deverá primeiramente ordenar os elementos em ordem crescente e após isso, deverá remover os elementos duplicados da lista, mantendo a ordem anterior.

````
 import java.util.Arrays;
public class Lista {
    public static void main(String[] args) {
        int[] listas = new int[] {8, 5, 8,10, 5, 2, 4, 4, 5, 3};
        Arrays.sort(listas);
        for (int lista: listas){
        System.out.print(lista + ", ");
    }
     System.out.println(""); 
     int[] w= removerDuplicados(listas);
        System.out.println(Arrays.toString(w)); 
    }            
    private static int[] removerDuplicados(int[] listas) {
        int n = listas.length;
        int[] w =  Arrays.copyOf(listas,n);
        for(int i = 0; i < n; i++){
    int k = i+1;
    int removidos = 0;
    for (int j = i+1; j < n; j++){
        if(w[j] == w[i])
            removidos ++;
        else
            w[k++] = w[j];
    }
    n = n-removidos;
    }
    w = Arrays.copyOf(w,n);
    return w;
}
}

````

</details>

## Problema 2

<details>
<summary>Validando Sudoku</summary>

```

```

```

```

</details>

