#include <iostream>
#include <stdlib.h>
#include <cstdlib>
#include <time.h>

using namespace std;
int Valor_cartas(int x, int y,int bar[4][10]);
void Preencher_mao(int bar[4][10],int mao1[] , int mao2[]);
bool Start(int bar[4][10]);
bool Computador(void);

int main ()
{

    int baralho[4][10];
    int jog1[3],jog2[3];
    bool jogo = true;

    while(Start(baralho))
    {
        Preencher_mao(baralho,jog1,jog2);
        for(int i = 0; i < 3 ; i++)
        {

            cout<<"mao1["<<i<<"]"<<jog1[i]<<endl;
            cout<<"mao2["<<i<<"]"<<jog2[i]<<endl;

        }
        int a = 0;
        cin>>a;
        cout<<"oie";
    }



    return 0 ;
}
int Valor_cartas(int x, int y,int bar[4][10])
{

    if(x == 9 && y == 3 || x == 6 && y == 2 || x == 2 && y == 1 || x == 6 && y == 0 )
    {

        if(x == 9 && y == 3)
        {
            return 1;
        }
        else if(x == 6 && y == 2)
        {
            return 2;
        }
        else if(x == 2 && y == 1)
        {
            return 3;
        }
        else if(x == 6 && y == 0)
        {
            return 4;
        }
    }
    else
    {
        return bar[x][y];
    }

}



void Preencher_mao(int bar[4][10],int mao1[] , int mao2[])
{
    srand(time(NULL));
    int key = 3, x , y , cont_pos = 0,fernando = 1;

    while(key != 0) ///Mão do jogador1
    {
        x = 0;
        y = 0;
        x = rand() % 4;
        y = rand() % 10;
        if(fernando == 1)
        {
            x = 9;
            y = 3;
            fernando--;
        }

        if(bar[x][y] != 0)
        {

            mao1[cont_pos] = Valor_cartas(x,y,bar);
            cont_pos++;
            key--;
            bar[x][y] = 0;
        }

    }
    cont_pos = 0;

    while(key < 3) ///Mão do jogador2
    {
        x = 0;
        y = 0;
        x = rand() % 4;
        y = rand() % 10;

        if(bar[x][y] != 0)
        {

            mao2[cont_pos] = Valor_cartas(x,y,bar);
            cont_pos++;
            key++;
            bar[x][y] = 0;
        }
    }
}
bool Computador(void)
{
    char comp;
    cout<<"Jogar contra o computador ?('S'/'N') ";
    cin>>comp;
    if(comp == 'n' || comp == 'N')
    {
        return false;
    }
    else
    {
        return true;
    }
}
bool Start(int bar[4][10])
{
   // system("cls");
    char comp ;
    cout<<"Deseja jogar Truco ?('S'/'N') ";
    cin>>comp;
    for(int i = 0; i < 4 ; i++)
    {
        for(int b = 0; b < 10 ; b++)
        {
            bar[i][b] = b + 5;
        }
    }
    if(comp == 'n' || comp == 'N')
    {
        return false;
    }
    else
    {
        return true;
    }
}


