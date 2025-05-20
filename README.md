#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define MAX_REGISTRADORES 8
#define TAM_LINHA 100

int registradores[MAX_REGISTRADORES];

void mostrar_registradores() {
    printf("Estado dos Registradores:\n");
    for (int i = 0; i < MAX_REGISTRADORES; i++) {
        printf("R%d = %d\n", i, registradores[i]);
    }
}

void executar_instrucao(char *instrucao) {
    char operacao[10];
    int r1, r2, valor;

    if (sscanf(instrucao, "%s R%d R%d", operacao, &r1, &r2) == 3) {
        if (strcmp(operacao, "ADD") == 0)
            registradores[r1] += registradores[r2];
        else if (strcmp(operacao, "SUB") == 0)
            registradores[r1] -= registradores[r2];
        else
            printf("Operação inválida: %s\n", operacao);
    } else if (sscanf(instrucao, "%s R%d %d", operacao, &r1, &valor) == 3) {
        if (strcmp(operacao, "LOAD") == 0)
            registradores[r1] = valor;
        else
            printf("Operação inválida: %s\n", operacao);
    } else {
        printf("Instrução mal formatada: %s\n", instrucao);
    }
}

void carregar_e_executar(const char *nome_arquivo) {
    FILE *arquivo = fopen(nome_arquivo, "r");
    if (!arquivo) {
        printf("Erro ao abrir o arquivo.\n");
        return;
    }

    char linha[TAM_LINHA];
    while (fgets(linha, sizeof(linha), arquivo)) {
        executar_instrucao(linha);
    }

    fclose(arquivo);
}

int main() {
    int opcao;
    char nome_arquivo[100];

    do {
        printf("\nMENU:\n");
        printf("1 - Mostrar registradores\n");
        printf("2 - Carregar e executar arquivo\n");
        printf("0 - Sair\n");
        printf("Escolha uma opção: ");
        scanf("%d", &opcao);

        switch (opcao) {
            case 1:
                mostrar_registradores();
                break;
            case 2:
                printf("Nome do arquivo: ");
                scanf("%s", nome_arquivo);
                carregar_e_executar(nome_arquivo);
                break;
            case 0:
                printf("Saindo...\n");
                break;
            default:
                printf("Opção inválida!\n");
        }
    } while (opcao != 0);

    return 0;
}
