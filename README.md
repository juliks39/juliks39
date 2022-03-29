#include <iostream>

#include <cmath>

using namespace std;

template <class T>
class arrays {
	T* t;
	T* newt;
	int size;
public:
	arrays();
	arrays(int n);
	~arrays();
	void set();
	void base_print();
	void rebuild();
	void new_print();
};

template<class T> arrays<T>::arrays() {}
template<class T>
arrays<T>::arrays(int n)
{
	size = n;
	t = new T[size];
	newt = new T[size];
}

template<class T>
arrays<T>::~arrays()
{
	delete[]t;
	delete[]newt;
}

template<class T>
void arrays<T>::set()
{
	for (int i = 0; i < size; i++)
	{
		cout << "Enter " << i + 1 << " element ";
		cin >> t[i];
	}
}

template<class T>
void arrays<T>::base_print()
{
	cout << "\nBase array:" << endl;
	for (int i = 0; i < size; i++)
	{
		cout << i + 1 << " element = " << t[i] << endl;
	}
}

template<class T>
void arrays<T>::rebuild()
{
	for (int i = 0; i < size; i++)
	{
		newt[i] = t[i] + t[i + 1] + t[i + 2];
		if (size - i == 2) {
			newt[i] = t[i] + t[i + 1];
		}
		if (size - i == 1) {
			newt[i] = t[i];
		}
	}
}

template<class T>
void arrays<T>::new_print()
{
	cout << "\nNew array:" << endl;
	for (int i = 0; i < size; i++)
	{
		cout << i + 1 << "st element = " << newt[i] << endl;
	}
}

int main() {
	int k, na;
	cout << "Data types for temlpate:\n1.int\n2.double\n0.exit\n";
	while (true) {
		cout << "\nChoose the type for template ";
		cin >> k;
		switch (k)
		{
		case 1: {
			cout << "\nYour type is INT" << endl;
			cout << "Enter the number of elements ";
			cin >> na;
			arrays<int>I(na);
			I.set();
			I.base_print();
			I.rebuild();
			I.new_print();
			break;
		}
		case 2: {
			cout << "\nYour type is DOUBLE" << endl;
			cout << "Enter the number of elements ";
			cin >> na;
			arrays<double>D(na);
			D.set();
			D.base_print();
			D.rebuild();
			D.new_print();
			break;
		}
		case 0: {
			exit(1);
			break;
		}
		default:
			break;
		}
	}
}
