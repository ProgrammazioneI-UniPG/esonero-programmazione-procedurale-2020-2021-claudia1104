NOME: Claudia Zarahi
COGNOME: Serquen Montero
NUMERO MATRICOLA: 330198


#include <stdlib.h>
#include <stdio.h>
#include <time.h>
#include <string.h>

void get_user_input(char * input);

int main()
{

char m[128];
char k[128];
char c[128];

char testo_originale[128];

int scelta;
int lunghezza_m;
int lunghezza_k;


  printf("Attenzione:La stringa M deve avere una lunghezza massima di 128 caratteri.\nInserisca la stringa M da cifrare:");

  get_user_input(m);


lunghezza_m = strlen(m);
printf("La lunghezza della stringa è:%d\n",lunghezza_m-1);

{
  printf("Adesso como vuole procedere? Ha due possibilità:\nPremendo (1) dovrà inserire una chiave k di lunghezza >= a M. Premendo (2) verrà generata una chiave k casuale\nAttenzione:La chiave deve avere una lunghezza massima di 128 caratteri\n");
  scanf("%d", &scelta);

}

  switch(scelta)
  {
    case (1):

    printf("Ha scelto la prima opzione\nInserisca la chiave k:");

    get_user_input(k);

 lunghezza_k = strlen(k);
 printf("La lunghezza della chiave k è:%d\n", lunghezza_k);



    while(lunghezza_k<lunghezza_m){
    printf("Attenzione: La chiave k deve essere >= a M\n");
    printf("Inserisca nuovamente la chiave k:\n");

    get_user_input(k);
  lunghezza_k= strlen(k);

}


    printf("Possiamo procedere alla codifica\n");

    for(int i=0;i<lunghezza_m;i++){

      c[i]=m[i]^k[i];

}

printf("\n");

printf("Il testo C cifrato è:");

for(int i=0; i<lunghezza_m; i++){
  printf("%X",c[i]);}

printf("\n");

    for(int i=0;i<lunghezza_m; i++){

      testo_originale[i]=c[i]^k[i];}

printf("Il testo M invece era:%s\n",testo_originale);

break;


case (2):
printf("Ha scelto la seconda opzione\nGenerando chiave k...\n");


printf("La chiave generata è: ");

  for(int i=0; i<lunghezza_m-1; i++){
    srand((unsigned)time(NULL));

    k[i]=32+rand()%96;

printf("%c",k[i]);}

lunghezza_k =strlen(k);



    for(int i=0;i<lunghezza_m;i++){

      c[i]=m[i]^k[i];

}

printf("\n");

printf("Il testo C cifrato è:");

for(int i=0; i<lunghezza_m; i++){
  printf("%X",c[i]);}

printf("\n");

    for(int i=0;i<lunghezza_m; i++){

      testo_originale[i]=c[i]^k[i];}

printf("Il testo M invece era:%s\n",testo_originale);

break;

default:printf("Fine programma\n");
break;

}

return 0;
}

void get_user_input(char * input){
  int lunghezza;
  *input = '\0';
  do {
    if (fgets(input,128,stdin)==NULL){
      break;
    }
    lunghezza = strlen(input)-1;
    input [lunghezza] = '\0';
  }
  while(lunghezza ==0);
}
