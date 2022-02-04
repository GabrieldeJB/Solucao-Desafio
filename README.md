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

````````
public class Sudoku {
  private static final int TamanhoGrade = 9;
  public static void main(String[] args) {
    
    int[][] tabuleiro = {
        {5, 3, 0, 0, 7, 0, 0, 0, 0},
        {6, 0, 0, 1, 9, 5, 0, 0, 0},
        {0, 9, 8, 0, 0, 0, 0, 6, 0},
        {8, 0, 0, 0, 6, 0, 0, 0, 3},
        {4, 0, 0, 8, 0, 3, 0, 0, 1},
        {7, 0, 0, 0, 2, 0, 0, 0, 6},
        {0, 6, 0, 0, 0, 0, 2, 8, 0},
        {0, 0, 0, 4, 1, 9, 0, 0, 5},
        {0, 0, 0, 0, 8, 0, 0, 7, 9} 
      };
    
    printTabuleiro(tabuleiro);
    
    if (resolverTabuleiro(tabuleiro)) {
      System.out.println("Resolvido com sucesso!");
    }
    else {
      System.out.println("Não resolvido :(");
    }
    
    printTabuleiro(tabuleiro);
    
  }
  
  private static void printTabuleiro(int[][] tabuleiro) {
    for (int linha = 0; linha < TamanhoGrade; linha++) {
      if (linha % 3 == 0 && linha != 0) {
        System.out.println("-----------");
      }
      for (int coluna = 0; coluna < TamanhoGrade; coluna++) {
        if (coluna % 3 == 0 && coluna != 0) {
          System.out.print("|");
        }
        System.out.print(tabuleiro[linha][coluna]);
      }
      System.out.println();
    }
  }


  private static boolean numeroNaLinha(int[][] tabuleiro, int numero, int linha) {
    for (int i = 0; i < TamanhoGrade; i++) {
      if (tabuleiro[linha][i] == numero) {
        return true;
      }
    }
    return false;
  }
  
  private static boolean numeroNaColuna(int[][] tabuleiro, int numero, int coluna) {
    for (int i = 0; i < TamanhoGrade; i++) {
      if (tabuleiro[i][coluna] == numero) {
        return true;
      }
    }
    return false;
  }
  
  private static boolean numeroNaCaixa(int[][] tabuleiro, int numero, int linha, int coluna) {
    int linhaCaixa = linha - linha % 3;
    int colunaCaixa = coluna - coluna % 3;
    
    for (int i = linhaCaixa; i < linhaCaixa + 3; i++) {
      for (int j = colunaCaixa; j < colunaCaixa + 3; j++) {
        if (tabuleiro[i][j] == numero) {
          return true;
        }
      }
    }
    return false;
  }
  
  private static boolean posicaoValida(int[][] tabuleiro, int numero, int linha, int coluna) {
    return !numeroNaLinha(tabuleiro, numero, linha) &&
        !numeroNaColuna(tabuleiro, numero, coluna) &&
        !numeroNaCaixa(tabuleiro, numero, linha, coluna);
  }
 
  private static boolean resolverTabuleiro(int[][] tabuleiro) {
    for (int linha = 0; linha < TamanhoGrade; linha++) {
      for (int coluna = 0; coluna < TamanhoGrade; coluna++) {
        if (tabuleiro[linha][coluna] == 0) {
          for (int tentativaNumero = 1; tentativaNumero <= TamanhoGrade; tentativaNumero++) {
            if (posicaoValida(tabuleiro, tentativaNumero, linha, coluna)) {
              tabuleiro[linha][coluna] = tentativaNumero;
              
              if (resolverTabuleiro(tabuleiro)) {
                return true;
              }
              else {
                tabuleiro[linha][coluna] = 0;
              }
            }
          }
          return false;
        }
      }
    }
    return true;
  }
}
````````

</details>

