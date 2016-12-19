# Laborator-11
#include<iostream>
using namespace std;
class Matrix{

private:
   int **v;
   int size;

public:
    Matrix()
    {
        v=new int*[size];
        for(int i=0;i<size;i++)
            v[i]=new int[size];
    }

    Matrix(int n)
    {
        v=new int*[n];
        for(int i=0;i<n;i++)
            v[i]=new int[n];
        size=n;
    }

    void citire()
    {
        for(int i=0;i<size;i++)
            for(int j=0;j<size;j++)
                cin>>v[i][j];
    }


    Matrix operator+ (Matrix m2)
    {
        Matrix T(size);
        for(int i = 0; i < size; i++)
        {
            for(int j = 0; j < size; j++)
            {
                T.v[i][j] = v[i][j] + m2.v[i][j];
            }
        }
        return T;
   }
   
   Matrix operator- (Matrix m2)
    {
        Matrix T(size);
        for(int i = 0; i < size; i++)
        {
            for(int j = 0; j < size; j++)
            {
                T.v[i][j] = v[i][j] - m2.v[i][j];
            }
        }
        return T;
   }

    Matrix& operator* (const Matrix& T)
    {
        for(int i = 0; i < T.size; ++i)
            for(int k = 0; k < size; ++k)
                v[i][k] *= T.v[k][i];
        return *this;
    }

    Matrix putere(Matrix a,int p)
    {
        Matrix c(size);
        c=a;
        if(p==1)
            return a;
        if(p>=2)
            for(int i=2;i<=p;i++)
                c=c*a;
        return c;
    }

    void afisare()
    {
        for(int i=0;i<size;i++)
            {
                for(int j=0;j<size;j++)
                    cout<<this->v[i][j]<<" ";
                cout<<endl;
            }
    }

};
    int main()
    {
        int x,p;
        cout<<"Numarul de linii si de coloane al matricei : ";
        cin>>x;
        Matrix a(x);
        a.citire();
        Matrix b(x);
        b.citire();
        Matrix d(x);
        cout<<"Diferenta matricelor: "<<endl;
        d=a-b;
        d.afisare();
        Matrix c(x);
        cout<<"Suma matricelor: "<<endl;
        c=a+b;
        c.afisare();
        cout<<"Inmultirea matricelor: "<<endl;
        c=a*b;
        c.afisare();
        cout<<"Puterea : "; cin>>p;
        cout<<"Ridicarea la puterea "<<p<<endl;
        c.putere(a,p).afisare();
        return 0;
}
