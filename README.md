# trabalho_prog
#include <stdio.h>
#include <stdlib.h>
#include <time.h>
#include <conio.h>
#include <locale.h>


int numero[10];
int quantidade;
char esc=0;
int numero_sorteado[10];
int cont=0;

char resposta;
void funcao_conversa() {
    printf("Primeira vez jogando a MEGA-TRÔ? Responda com 's' para sim ou 'n' para não: ");
    scanf(" %c", &resposta);
    if (resposta == 's' || resposta == 'S') {
        printf("A MEGA-TRÔ é um jogo de apostas altamente renomado!!\n");
        printf("Regras do jogo:\n\n 1. A quantidade de números a ser apostado é: mínimo 6 e máximo 10\n");
        printf(" 2. As dezenas têm que ser entre os numerais 1 e 60.\n");
        printf(" 3. As dezenas devem ser diferentes!\n");
        printf("Seguindo essas três regrinhas você vai ter uma ótima experiência neste jogo.\n");
        printf("Divirta-se e não gaste todo seu dinheiro!!\n");
    }
    else if(resposta=='n' || resposta=='N'){
        printf("\nDivirta-se e não gaste todo o seu dinheiro!!\n");
    }
    else{
        printf("Você é um pouquinho mal educado...");
    }
}

int funcao_Numeros(){

while(esc!=27){
printf("digite a quantidade de numeros a ser apostado(numero minimo 6 e maximo 10):\n");
scanf("%d", &quantidade);

while(quantidade<6 || quantidade>10){
printf("\nVocê errou!! Digite novamente a quantidade de numeros a ser apostado(número minimo 6 e maximo 10):\n");
scanf("%d", &quantidade);
}
    printf("digite as dezenas a serem apostadas:\n");
    for(int i=0;i<quantidade;i++){
    scanf("%i", &numero[i]);

    while(numero[i]<1 || numero[i]>60){
    printf("voce errou, as dezenas devem ser entre 1 e 60:\nDigite novamente!!\n(apenas as que não seguiram as regras)\n");
    scanf("%i", &numero[i]);
    }


    for(int j=0; j<i;j++){
    if(numero[i]==numero[j]){
    printf("voce errou, as dezenas devem ser diferentes:\nDigite novamente!\n(apenas as dezenas que foram repetidas)\n");
    scanf("%i", &numero[i]);
    }
    }
    }
  printf("\n\nOs numeros apostados foram:\n");
  int aux;
  for(int i=0;i<quantidade;i++){
  for(int j=i+1;j<quantidade;j++){
    if(numero[i]>numero[j]){
    aux = numero[i];
    numero[i] = numero[j];
    numero[j] = aux;
    }
    }
    }
    for(int i=0; i<quantidade;i++){
    printf("%i\n", numero[i]);
    }

  break;
  }
  return 0;}

int funcao_Sorteia(){

      srand(time(NULL));

      while(esc!=27){
      printf("\n\nA seguir os numeros sorteados aleatoriamente:\n");

      for(int i=0; i<6; i++){
      numero_sorteado[i] = 1 +(rand() % 60);

      for(int j=0; j<6; j++){
      if(numero_sorteado[i]==numero_sorteado[j]){
      numero_sorteado[i] = 1 +(rand() % 60);
      }
      }
      }

      for(int i=0; i<6; i++){
      printf("%i\n", numero_sorteado[i]);
      }


      for(int j=0; j<6; j++){
      for(int i=0; i<quantidade; i++){
      if(numero_sorteado[j]==numero[i]){
      cont++;
        }
        }
        }



            if(cont==1){
            printf("\nPARABÉNS, você fez  UM acerto!!\n Você acertou o numero %i", cont);
            }
            else if(cont==2){
            printf("\nPARABÉNS, você fez DOIS acertos!!\n");
            }
            else if(cont==3){
            printf("\nPARABÉNS, você fez uma TRÊS acertos!!\n");
              }
              else if(cont==4){
                printf("\nPARABÉNS, você fez uma QUADRA _TRÔ!!\n");
              }
              else if(cont==5){
                  printf("\nPARABÉNS, você fez uma QUINA_TRÔ!!\n");
                }
              else if(cont==6){
                  printf("\nPARABÉNS, você fez uma SENA_TRÔ!!\n A sorte está com você!\n");
                }
              else{
                printf("\n Uma pena, você nao acertou NENHUM numero, tente novamente\n" );
              }


         break;


}

return 0;}

int main(void) {
setlocale(LC_ALL, "portuguese");
  printf("Bem vindo ao MEGA-Trô!\n\n");

  char nome[100];
  printf("Digite seu nome:\n");
  gets(nome);
  printf("Boa sorte na aposta %s\n", nome);
  do {
  funcao_conversa();
  funcao_Numeros();
  funcao_Sorteia();



          printf("Deseja fazer uma nova aposta?\n (ESC para encerrar, qualquer outra tecla para continuar): ");
          fflush(stdin);
          esc = getch();

          if (esc == 27) {
              printf("\nEncerrando o programa...\n");
              break;
          } else {
              printf("\nReiniciando o programa...\n");

          }
      } while (1);


      return 0;
  }
