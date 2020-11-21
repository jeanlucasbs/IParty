#include <stdio.h>
#include <locale.h>
#include <string.h>
#include <conio.h>
int main()
{
    setlocale(LC_ALL, "Portuguese");
    int opcao, opcao2;
    char nomeFesta[30];
    char dataFesta[20];
    char horaFesta[10];
    char localFesta[40];
    char exibirFestas[100];
    char todasFestas[1000];
    char dataEscolhida[20];
    char ingressoFesta[40];
    char descricaoFesta[500];

    do
    {
        textcolor(3);
        printf("\n\n");
        printf("\n##############################");
        printf("\n#                            #");
        printf("\n#           iPARTY           #");
        printf("\n#                            #");
        printf("\n#     DETECTOR DE FESTAS     #");
        printf("\n#                            #");
        printf("\n#                            #");
        printf("\n#                            #");
        printf("\n#                            #");
        printf("\n#                            #");
        printf("\n#                            #");
        printf("\n#       Versão alfa 1.0      #");
        printf("\n##############################");
        printf("\n\n\n\n\n");
        textcolor(5);
        printf("\nEscolha o que você quer fazer: ");
        printf("\n <1> Cadastrar festa");
        printf("\n <2> Procurar festa");
        printf("\n <3> Fechar programa \n");
        textcolor(15);scanf("%d", &opcao);
        while(opcao < 1 || opcao > 3)
        {
            printf("\n Opção inválida, digite novamente: ");
            scanf("%d", &opcao);
        }
        system("cls");
        switch (opcao)
        {
        case 1:
            system("cls");
            textcolor(3);
            printf("\n##############################");
            printf("\n#                            #");
            printf("\n#     CADASTRO DE FESTA      #");
            printf("\n#                            #");
            printf("\n##############################\n");
            setbuf(stdin,NULL);
            textcolor(5);
            printf("\n Nome da festa: \n");
            textcolor(15);gets(nomeFesta);
            textcolor(5);printf("\n Data da festa: \n");
            textcolor(15);gets(dataFesta);
            textcolor(5);printf("\n Horário da festa(hh:mm): \n");
            textcolor(15);gets(horaFesta);
            textcolor(5);printf("\n Local da festa: \n");
            textcolor(15);gets(localFesta);
            textcolor(5);printf("\n Ingresso: \n");
            textcolor(15);gets(ingressoFesta);
            textcolor(5);printf("\n Descrição da festa: \n");
            textcolor(15);gets(descricaoFesta);

            FILE *pFesta;
            pFesta = fopen(dataFesta, "a+");
            if(pFesta == NULL)
            {
                printf("Erro na abertura do arquivo!");
                return 1;
            }
            FILE *pTodas;
            pTodas = fopen("Todas as festas.txt", "a+");
            textcolor(3);
            fprintf(pFesta,"\n##############################");
            fprintf(pFesta,"\n#                            #");
            fprintf(pFesta,"\n#       %s   \t  #",nomeFesta);
            fprintf(pFesta,"\n#                            #");
            fprintf(pFesta,"\n##############################\n");
            textcolor(5);
            fprintf(pFesta,"\n\n Nome : %s", nomeFesta);
            fprintf(pTodas,"\n\n Data: %s", dataFesta);
            fprintf(pFesta,"\n\n Horário : %s", horaFesta);
            fprintf(pFesta,"\n\n Local : %s \n", localFesta);
            fprintf(pFesta,"\n\n Ingresso : %s \n", ingressoFesta);
            fprintf(pFesta,"\n\n Descrição : %s \n", descricaoFesta);
            fclose(pFesta);
            textcolor(3);
            fprintf(pTodas,"\n##############################");
            fprintf(pTodas,"\n#                            #");
            fprintf(pTodas,"\n#      %s   \t  #",nomeFesta);
            fprintf(pTodas,"\n#                            #");
            fprintf(pTodas,"\n##############################\n");
            textcolor(5);
            fprintf(pTodas,"\n\n Nome : %s", nomeFesta);
            fprintf(pTodas,"\n\n Horário : %s", dataFesta);
            fprintf(pTodas,"\n\n Horário : %s", horaFesta);
            fprintf(pTodas,"\n\n Local : %s \n", localFesta);
            fprintf(pTodas,"\n\n Ingresso : %s \n", ingressoFesta);
            fprintf(pTodas,"\n\n Descrição : %s \n", descricaoFesta);
            fclose(pTodas);
            system("\npause");
            system("cls");
            break;
        case 2:
            textcolor(5);
            printf("\nEscolha como deseja pesquisar: ");
            printf("\n <1> Mostras todas as festas");
            printf("\n <2> Buscar festas por data");
            printf("\n <3> Sair do programa\n");
            textcolor(15);scanf("%d", &opcao2);
            switch (opcao2)
            {
            case 1:
                system("cls");
                pTodas = fopen("Todas as festas.txt", "a+");
                if(pTodas == NULL)
                {
                    printf("Erro na abertura do arquivo!");
                    return 1;
                }
                while(fgets(todasFestas, 1000, pTodas) != NULL)
                {
                    printf("%s", todasFestas);
                }
                printf("\n\n");
                system("\npause\n");
                break;
            case 2:
                system("cls");
                setbuf(stdin, NULL);
                textcolor(5);printf("\n Digite uma data: ");
                textcolor(15);gets (dataEscolhida);
                pFesta = fopen(dataEscolhida, "a+");
                if(pFesta == NULL)
                {
                    printf("Erro na abertura do arquivo!");
                    return 1;
                }
                while(fgets(exibirFestas, 100, pFesta) != NULL)
                {
                    printf("%s", exibirFestas);
                }
                printf("\n\n");
                system("\npause\n");
                system("cls");
                break;
            }
        }
    }
    while(opcao!=3);
    system("cls");
    printf("\n\n ### FIM DE PROGRAMA ### \n\n ");
}
