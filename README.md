# CPP-VirtualDestructor
Virtual Destructor 
#include <iostream>
using namespace std;

class base
{
    public:
    int *p;
    base();
  virtual ~base();
  virtual base*clone()
  {
      cout<<"virtual constr";
  }
};

base::base()
{
    p=new int;
    cout<<" base const"<<endl;
}
base::~base()
{
    cout<<"base dest"<<endl;
}

class derive: public base
{
    public:
    derive(){cout<<"der const"<<endl;}
    ~derive(){cout<<"der dest"<<endl;}
};

int main()
{
    base *c=new derive();
    derive *bd=dynamic_cast<derive*>(c);
    bd->clone();
    base *bs=new derive;
   bs->clone();
    delete bd;
}
