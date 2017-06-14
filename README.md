#include<stdio.h>
#include<stdlib.h>
#include<string.h>

typedef struct{

 char heroi[25];
 int poder;
} heroes;

//void simularBatalha(heroes * herois[], heroes *thanos){

//}
heroes** selecaoParaAtaque(heroes herois[]){
    heroes **locao = (heroes*) malloc( sizeof(heroes*)*11);

    int i,c=0,escolha=0;
    for(i=0;i<11;i++){
            locao[i]=NULL;
        printf("Escolha se o %s vai entrar:\n",herois[i].heroi);
        printf("1-SIM || 2-NAO\n");
        scanf("%d",&escolha);
        if(escolha==1){
            locao[c]=&herois[i];
            c++;
        }




    }
    return locao;
}

void imprime(heroes*thanos, heroes  herois[]){
    int i;
    printf("%s\n",thanos->heroi);
    printf("%d\n",thanos->poder);
    for(i=0; i<11;i++){
        printf("%s\n",herois[i].heroi);
        printf("%d\n",herois[i].poder);
}
}
//heroes** selecaoParaAtaque(heroes vetor[])
//}
void leHeroi(heroes *thanos,heroes h[])  {
    int i=0, temp1=0, temp2=0;
    FILE * entrada;
    entrada = fopen ("herois.txt", "r");
    if (entrada != NULL){

        do{
            fscanf (entrada,"%s",thanos->heroi);
            fscanf (entrada,"%d",&temp1);
            thanos->poder = temp1;
            for (i=0 ; i<11 ; i++){
            fscanf(entrada,"%s",h[i].heroi);
            fscanf(entrada,"%d",&h[i].poder);
            }
        }while(!feof(entrada));
        fclose(entrada);


    } else { printf("Deu ruim."); }// treta no file







}


int main(void){
int i,j,k,somapoder=0;
heroes thanos, herois[11] ;
leHeroi(&thanos, herois);
imprime(&thanos, herois);
heroes **locao=selecaoParaAtaque(herois);

for(i=0;i<11;i++){
    if (locao[i] != NULL){
        printf("%d\n",locao[i]->poder);
       somapoder=somapoder+locao[i]->poder;
    }
}
        if(somapoder>(thanos.poder*1.25)){
            printf("deu ruim pra caralho\n");}
        else if (somapoder < thanos.poder){
                thanos.poder *1.5;
                for(j=0;j<11;j++){
                    locao[j]->poder = locao[j]->poder*0.5;
                }
        }
        else if(somapoder >= thanos.poder && somapoder <= thanos.poder*1.25){
            thanos.poder*0.5;
            for(k=0;k<11;k++){
                    locao[k]->poder = locao[k]->poder*0.5;
            }
        }



imprime(&thanos, herois);





return 0;
}
// o que ta dando de errado: na hora de executar, ta fazendo a divisao tudo certo menos a do thanos,esse eh o detalhe q a gnt tem descobrir
// 2- eu troquei a parte do somatudo,porque eu n qro diminuir 50% do poder de todos os herois,mas sim dos que eu escolhi,nesse caso eu chamei o locao pra fazer sua parte, obs,nao esquecer de botar "->" EX: locao[i]->poder :)
