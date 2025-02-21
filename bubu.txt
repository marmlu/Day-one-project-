#include <iostream>

using namespace std;

char space [3][3]={{'1','2','3'},{'4','5','6'},{'7','8','9'}};
int row;
int column;
char token='x';
bool gametie=false;
string n1=" ";
string n2=" ";
void functionOne (){

    cout <<"   |   |   "<<endl;
    cout <<" "<<space[0][0]<<" | "<<space[0][1]<<" | "<<space[0][2]<<endl;
    cout <<"___|___|___"<<endl;
    cout <<"   |   |   "<<endl;
    cout << " "<<space[1][0]<<" | "<<space[1][1]<<" | "<<space[1][2]<<endl;
    cout <<"___|___|___"<<endl;
    cout <<"   |   |   "<<endl;
    cout << " "<<space[2][0]<<" | "<<space[2][1]<<" | "<<space[2][2]<<endl;
    cout <<"   |   |   "<<endl;
}

void functionTwo(){
    int digit;
    if (token=='x'){
        cout <<n1<<" Please enter "<<endl;
        cin>>digit;
    }
    else if(token=='o')
    {
        cout <<n2<<" Please enter "<<endl;
        cin>>digit;
    }
    if(digit==1)
    {
        row=0;
        column=0;
    }
    if(digit==2)
    {
        row=0;
        column=1;
    }
    if(digit==3)
    {
        row=0;
        column=2;
    }
    if(digit==4)
    {
        row=1;
        column=0;
    }
    if(digit==5)
    {
        row=1;
        column=1;
    }
    if(digit==6)
    {
        row=1;
        column=2;
    }
    if(digit==7)
    {
        row=2;
        column=0;
    }
    if(digit==8)
    {
        row=2;
        column=1;
    }
    if(digit==9)
    {
        row=2;
        column=2;
    }
    else if(digit<1 || digit>9)
{
    cout <<"Invalid" <<endl;
}
 if (token=='x'&& space[row][column]!='x'&& space[row][column]!='o'){
     space[row][column]='x';
     token='o';}
     else if(token=='o'&&space[row][column]!='x'&&space [row][column]!='o')

       {space [row][column]='o';
        token='x';
       }
       else
        {
            cout<<"There is no empty space"<<endl;
             functionTwo();
       }
       functionOne();


}

bool functionThree(){
    for (int i=0;i<3;i++){
        if( space [i][0]==space[i][1]&&space[1][i]&&space[0][i]==space[2][i])
            return true;
    }
    if( space [0][0]==space[1][1]&&space[1][1]==space[2][2] || space[0][2]==space[1][1]&&space[1][1]==space[2][0])
    {

        return true;
        }
        for (int i=0;i<3;i++){
                for (int j=0;j<3;j++){
                    if(space[i][j]!='x'&&space[i][j]!='o')
                    {
                        return false;
                    }
    }
}
}
int main()
{
    cout<<"Enter the name of the first player"<<endl;
    cin.ignore();
    getline(cin,n1);
    cout<<"Enter the name of the second player"<<endl;
    getline(cin,n2);


    while (!functionThree())
    {
        functionOne();
        functionTwo();
        functionThree();
    }
    if(token=='x'&&gametie==false)
    {
        cout <<n2<<"wins!"<<endl;
    }
    if(token=='o'&&gametie==false)
    {
        cout <<n1<<"wins!"<<endl;
    }
    else
    {
      cout <<"It's a draw!"<<endl;
    }

    return 0;
}

