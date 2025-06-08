//Bibliotecas
#include <stdio.h>
#include <stdlib.h>
#include <locale.h>

//Constante
#define tamanho 5

//Variaveis e Estruturas
struct tlivro {
    int codigo;
    char titulo[50];
    char autor[50];
};

struct tpilha {
    struct tlivro livro[tamanho];
    int fim;
};

struct tpilha pilha;
int op;
int i;

//prototipação
void mostrar_pilha();
void mostrar_menu();
void push();
void pop();
void listar_livros();

//Função principal
int main(){
    setlocale(LC_ALL, "Portuguese");
    op = 1;
    while(op != 0){
        system("cls");
        mostrar_pilha();
        mostrar_menu();
        switch(op){
    case 1:
        push();
        break;
    case 2:
        pop();
        break;
    case 3:
        listar_livros();
        break;
        }
    }
}

//funções
void mostrar_pilha(){
    if(pilha.fim == 0){
        printf("[Vazio]");
    }else{
    printf("[ ");
    for(i = 0; i < pilha.fim; i++){
        printf("|%s|", pilha.livro[i].titulo);
    }
    printf(" ]");
    }
}

void mostrar_menu(){
    printf("\nEscolha uma das opções abaixo:\n\n");
    printf("1 - Adicionar livro à pilha.\n2 - Retirar um livro da pilha.\n3 - Listar os livros na pilha.\n0 - Sair do programa.\n\n");
    scanf("%d", &op);
}

void push(){
    system("cls");
    if(pilha.fim == tamanho){
        printf("A pilha já atingiu o tamanho máximo.\n");
        system("pause");
    }else{
        printf("Digite o título do livro: ");
        scanf("%s", &pilha.livro[pilha.fim].titulo);
        printf("\nDigite o nome do autor: ");
        scanf("%s", &pilha.livro[pilha.fim].autor);
        printf("\nDigite o código do livro: ");
        scanf("%d", &pilha.livro[pilha.fim].codigo);
        pilha.fim++;
    }
}

void pop(){
    system("cls");
    if(pilha.fim == 0){
        printf("\nA pilha está vazia!\n\n");
        system("pause");
    }else{
        pilha.fim--;
    }
}

void listar_livros(){
    system("cls");
    if(pilha.fim == 0){
        printf("\nA pilha está vazia!\n\n");
    }else{
    for(i = 0; i < pilha.fim; i++){
        printf("Livro - %d\n\n", pilha.livro[i].codigo);
        printf("Título: %s\n", pilha.livro[i].titulo);
        printf("Autor: %s\n\n", pilha.livro[i].autor);
        printf("--------------------------------------------------------------------------------\n\n");
        }
    }
    system("pause");
}
