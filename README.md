# Sudoku
#include <stdio.h>

int main(void) {
  int SUDOKU[9][9] = {0};
    int N = 0,   K = 1;
    scanf("%d", &N);
    for(;N;N--){
    for(int i = 0;i < 9;i++){//LEITURA DA MATRIZ SUDOKU
        for(int j = 0;j < 9;j++){
            scanf("%d", &SUDOKU[i][j]);
        }
    }
    int FLAG_CONT = 0;
    for(int i = 0, FLAG_45 = 0 ; i<9 ;i++,FLAG_45 = 0){//CHECAGEM DE LINHA POR LINHA
        for(int j = 0;j<9;j++){
            FLAG_45 += SUDOKU[i][j];
            FLAG_CONT++;
        }
        if(FLAG_45 != 45){FLAG_CONT = 0; break;}
    }
    for(int j = 0, FLAG_45 = 0 ; j<9 ; j++, FLAG_45 = 0){//CHECAGEM DE COLUNA POR COLUNA
        for(int i = 0;i<9;i++){
            FLAG_45 += SUDOKU[i][j];
            FLAG_CONT++;
        }
        if(FLAG_45 != 45){FLAG_CONT = 0; break;}
    }
    for(int x = 0;x < 3;x++){//CHECAGEM DE BLOCO 3X3 POR BLOCO
        for(int y = 0, FLAG_45 = 0;y < 3;y++ , FLAG_45 = 0){
            for(int i = x*3;i < (x+1)*3;i++){
                for(int j = y*3;j < (y+1)*3;j++){
                    FLAG_45 += SUDOKU[i][j];
                    FLAG_CONT++;
                }
            }
        if(FLAG_45 != 45){FLAG_CONT = 0; break;}
        }
    }
    printf("Instancia %d\n", K);
    K++;
    if(FLAG_CONT == 3*81)printf("SIM\n");
    else printf("NAO\n");
    printf("\n");
    }

    return 0;
}
