#include <stdlib.h>
#include <iostream>
#include <math.h>

#define DEL 0.0001
#define LEFT -5
#define RIGHT 5

using namespace std;

double func(double x)
{
  return x*x;
}

double FindMin(double l, double r)
{
 double left = l;
 double right = r;
 double eps = 0.000001;
 double a = 0;
 double b = 0;
  int count = 0;
  while ((right - left) >= DEL)
  {
    a = (right + left)*0.5 - eps;
    b = (right + left)*0.5 + eps;
    if (func(a) < func(b))
    {
      right = b;
    }
    else
    {
      left = a;
    }
    count++;
  }
  cout << "[" << left << " ; " << right << ']' << endl;
  cout << "Iter = " << count << endl;
  return (right + left)*0.5;
}

int main()
{
  double min = FindMin(LEFT, RIGHT);
  cout << "Min in " << min << endl;
  cout << "func(Min) = " << func(min) << endl;
  cout << endl;
}
