#include <iostream>
using namespace std;

struct nodo
{
int dato;
struct nodo *sig;
};

typedef struct nodo *lista;

void menu();
void insertarcabeza(lista &cabeza, int n);
void mostrarnodos(lista cabeza);
void eliminarcabeza(lista &cabeza);
void insertarcola(lista &cabeza, int n);
void eliminarcola(lista &cabeza);
int contarnodos(lista cabeza);
int contadorpares(lista cabeza);
int main()
{
int opcion, numero;
lista cabeza=NULL;
do
{
menu();
cin>>opcion;
switch(opcion)
{
    case 1:
        mostrarnodos(cabeza);
        cout<<"codigo de la opcion 1";
        system("pause");
        break;
    case 2:
        cout<<"ingrese un numero:";
        cin>>numero;
        insertarcabeza(cabeza, numero);
        system("pause");
        break;
    case 3:
        eliminarcabeza(cabeza);
        system("pause");
        break;
    case 4:
        cout<<"ingrese un numero:";
        cin>>numero;
        insertarcola(cabeza, numero);
        system("pause");
        break;
    case 5:
    	eliminarcola(cabeza);
    	system("pause");
    	break;
    case 6:
    	int con;
    	con=contarnodos(cabeza);
    	cout<<"la lista tiene "<<con<<" nodos "<<endl;
    	system("pause");
    	break;
    case 7:
    	int contpar;
    	contpar=contadorpares(cabeza);
    	cout<<" la lista tiene "<<contpar<<" nodos pares"<<endl;
    	system("pause");
    	break;
    }
system("cls");
}
while(opcion!=10);
}

void insertarcola(lista &cabeza, int n)
{
	lista aux=new(struct nodo);
	aux->dato=n;
	aux->sig=NULL;
	
	if(cabeza==NULL)
	{
		cabeza=aux;
		aux=NULL;
	}else{
		lista temp;
		temp=cabeza;
		while(temp->sig!=NULL){
			temp=temp->sig;
		}
		temp->sig=aux;
		aux=NULL;
		temp=NULL;
	}
	
}

void eliminarcola(lista &cabeza)
{
	if(cabeza==NULL)
	{
		cout<<"no hay nodos "<<endl;
	}else
	{
		if(cabeza->sig==NULL){
			cabeza=NULL;
		}else
		{
			lista aux;
			aux=cabeza;
			while(aux->sig->sig!=NULL){
				aux=aux->sig;
			}
			aux->sig=NULL;
		}
	}
}

void eliminarcabeza(lista &cabeza)
{
	lista aux;
	aux=cabeza;
	
	if(cabeza==NULL)
	{
		cout<<"no hay nodos ";
		
	}else
	{
		cabeza=cabeza->sig;
	    aux->sig=NULL;
	    aux=NULL;
	}

}

void mostrarnodos(lista cabeza)
{
	cout<<"lista de nodos "<<endl<<"----------"<<endl;
	while(cabeza!=NULL)
	{
		cout<<cabeza->dato<<endl;
		cabeza=cabeza->sig;
	}
}
void insertarcabeza(lista &cabeza, int n)
{
lista aux;
aux=new(struct nodo);
aux->dato=n;
aux->sig=cabeza;
cabeza=aux;
aux=NULL;
}
int contarnodos(lista cabeza)
{
	int contador=0;
	while(cabeza!=NULL){
		contador++;
		cabeza=cabeza->sig;
	}
	return contador;
}
int contadorpares(lista cabeza)
{
	int conpar=0;
	while(cabeza!=NULL)
	{
		if(cabeza->dato%2==0){
			conpar++;
		}
		cabeza=cabeza->sig;
	}
	return conpar;
}

void menu()
{
cout<<"Menu principal"<<endl;
cout<<"--------------"<<endl;
cout<<"1.  Mostrar datos"<<endl;
cout<<"2.  Insertar por la cabeza"<<endl;
cout<<"3. eliminar por la cabeza "<<endl;
cout<<"4.  insertar por la cola "<<endl;
cout<<"5. eliminar por la cola "<<endl;
cout<<"6. contador "<<endl;
cout<<"7. contador pares "<<endl;
cout<<"10. Salir"<<endl;
cout<<endl;
cout<<"Ingrese su opcion:"<<endl;
}
