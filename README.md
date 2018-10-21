# Betweenthetwosets

#include <iostream>

using namespace std;

int GCD(int a,int b)
{
    if (a == 0)
        return b;
    return GCD(b % a, a);
}

long long findlcm(int arr[],int n)
{
    long long temp = arr[0];
    for (int i = 1; i < n; i++)
        temp = (((arr[i] * temp)) /(GCD(arr[i], temp)));

    return temp;
}
int betweentwosets(int a1[],int a2[],int m,int n)
{
    int gcd2;
    long long lcm;

    gcd2 = a2[0];
    for(int i=0;i<n;i++)
    {
         gcd2 = GCD(a2[i],gcd2);
    }

    lcm = findlcm(a1,m);
    int _count=0;
    while(lcm<=gcd2)
    {
        if(gcd2%lcm==0)
        {
            _count++;

        }
        lcm++;
    }

        return _count;
}


int main()
{
    int m,n;
    cout<<"Enter the number for array 1"<<endl;
    cin>>m;
    cout<<"Enter the number for array 2"<<endl;
    cin>>n;

    int a1[m],a2[n];

    for(int i=0;i<m;i++)
    {
        cin>>a1[i];
    }

    for(int i=0;i<n;i++)
    {
        cin>>a2[i];
    }

    int result = betweentwosets(a1,a2,m,n);
    cout<<result;
    return 0;
}
