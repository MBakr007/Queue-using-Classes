#include <iostream>

using namespace std;
template<class t>
class Queue
{
private :
    int intial_Size;
    t *values;
    int Front = -1 , End = -1;

public :
    Queue()
    {
        intial_Size = 0;
        values = new t[intial_Size];
    }
    Queue(t value,int intial_Size)
    {
        this->intial_Size = intial_Size;
        values = new t[intial_Size];
        Front ++;
        for(int i=0 ; i<intial_Size ; i++)
        {
            values[i] = value;
            End++;
        }
    }
    ~Queue()
    {
        delete[]values;
    }
    t& froont ()
    {
        return values[Front];
    }
    void POP()
    {
        Front = (Front+1)%intial_Size;
    }
    void Push(t value)
    {
        if(Front==0 && End == intial_Size-1)
        {
            cout<<"The queue is Full :"<<endl;
        }
        else {
                End = (End+1)%intial_Size;
            values[End] = value;
        }
    }
    int Size()
    {
        int s;

        if(End > Front)
        {
            s = (End+1) - Front;
        }
        else
        {
            s = intial_Size - (End+1);
        }
        //int Size = Front > End ? (Front - End) : (Front+intial_Size -  End);
        return s;
    }
};
int main()
{
    Queue <int> S(5 , 5);
    S.POP();
    S.POP();
    S.Push(11);
    S.Size();

    return 0;
}
