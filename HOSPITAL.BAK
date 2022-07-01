#include<iostream.h>
#include<graphics.h>
#include<fstream.h>
#include<iomanip.h>
#include<conio.h>
#include<stdio.h>
#include<stdlib.h>
#include<string.h>
#include<dos.h>
class patient
{
int pid;
char pname[30];
char description[50];
char phone[20];
float medicine;
char room;
int rcharge;
int nods;
double tamt;
		int AssignRoomCharge()
		{
			if(room=='y')
			{
				rcharge=1000;
			}
			else
			{
				rcharge=0;
			}
			return rcharge;
		}
	public:

		void getdata();
		void show();
		void showdata(int n);
		float getTotalAmount();
		void generateBill();
		int getPid()
		{
			return pid;
		}
		char *getName()
		{
			return pname;
		}

};
float patient::getTotalAmount()
{

	tamt=medicine+(rcharge*nods);
	return tamt;
}

void patient::getdata()
{
cout<<"Please enter the following patient details:"<<endl;
cout<<"Patient Id 	:";
cin>>pid;
cout<<"Patient Name	:";
gets(pname);
cout<<"Disease		:";
gets(description);
cout<<"Enter contact no :";
gets(phone);
cout<<"Cost of Medicine :";
cin>>medicine;
cout<<"Room(Y/N)	:";
cin>>room;
cout<<"Time stayed(Days):";
cin>>nods;
AssignRoomCharge();
getTotalAmount();
}
void patient::show()
{
cout<<"Patient Id	:"<<pid<<endl;
cout<<"Patient Name	:"<<pname<<endl;
cout<<"Disease		:"<<description<<endl;
cout<<"Phone Number	:"<<phone<<endl;
cout<<"Medicine Cost	:"<<medicine<<endl;
cout<<"Day Stayed	:"<<nods<<endl;
cout<<"Total Amount	:"<<tamt<<endl;
}
void patient::showdata(int n)
{
gotoxy(3,4+n);
cout<<pid;
gotoxy(15,4+n);
cout<<pname;
gotoxy(30,4+n);
cout<<description;
gotoxy(50,4+n);
cout<<phone;
gotoxy(45,4+n);


}
void patient::generateBill()
{
int i;
gotoxy(25,4);
cout<<"Recepit of Mr./Ms. :";
for(i=1;i<=80;i++)
{
	gotoxy(i,5);
	cout<<"_";
}
gotoxy(45,4);
cout<<pname;
gotoxy(3,6);
cout<<"PID";
gotoxy(15,6);
cout<<"Medicines ";
gotoxy(30,6);
cout<<"Room Charge";
gotoxy(45,6);
cout<<"No of Days";
gotoxy(60,6);
cout<<"Total Amount ";
gotoxy(3,8);
cout<<pid;
gotoxy(15,8);
cout<<medicine;
gotoxy(30,8);
cout<<rcharge;
gotoxy(45,8);
cout<<nods;
gotoxy(60,8);
cout<<tamt;
for(i=1;i<=80;i++)
{
	gotoxy(i,7);
	cout<<"_";
}

	for(i=1;i<=80;i++)      //top border
	{
		gotoxy(i,1);
		cout<<"°";
		//delay(10);
	}
	for(i=2;i<=23;i++)   //left
	{
		gotoxy(1,i);
		cout<<"°";
		//delay(10);
	}
	for(i=2;i<=80;i++)  // bottom
	{
		gotoxy(i,23);
		cout<<"°";
		//delay(10);
	}
	for(i=2;i<=23;i++)
	{
		gotoxy(80,i);
		cout<<"°";
		//delay(10);
	}

		for(i=1;i<=5;i++)

		{     textcolor(RED);
		      gotoxy(38,12+i);
			cprintf("±±");
			textcolor(WHITE);
		}
		for(i=1;i<=9;i++)
		{
			textcolor(RED);
			gotoxy(33+i,15);
			cprintf("±±");
			textcolor(WHITE);
		}

gotoxy(25,20);
cout<<"Thank You";
gotoxy(29,21);
cout<<"And";
gotoxy(25,22);
cout<<"Get Well Soon!!";
}
void searchRec()
{
	patient p;
	int pid;
	ifstream fin;
	fin.open("hospital.dat",ios::in);
	if(!fin)
	{
		cout<<"File not found";
		getch();
		exit(0);
	}
       gotoxy(3,2);
       cout<<"Please enter patient Id :";
       gotoxy(30,2);
       cin>>pid;
       while(!fin.eof())
       {
		fin.read((char*)&p,sizeof(p));
		if(p.getPid()==pid)
		{
			p.generateBill();
		}
       }
       fin.close();

}
void write2file()
{
patient p;
	ofstream fout;
	fout.open("hospital.dat",ios::app|ios::binary);
	if(!fout)
	{
		cout<<"Can't create a file ";
		getch();
		exit(0);
	}
	p.getdata();
	fout.write((char*)&p,sizeof(p));
	fout.close();
}

void dispRec()
{
patient p;
	int k=0;
	ifstream fin;
	fin.open("hospital.dat",ios::in);
	if(!fin)
	{
		cout<<"File not found ";
		getch();
		exit(0);
	}
	while(!fin.eof())
	{
		k++;
		fin.read((char*)&p,sizeof(p));
		if(fin.eof())break;
		p.showdata(k);

	}
	fin.close();
}
void box()
{
int i;
gotoxy(30,2);
textcolor(CYAN+BLINK);
textbackground(MAGENTA);
cprintf("PATIENTS DETAILS ");
textcolor(WHITE);
textbackground(0);
gotoxy(3,3);
cout<<"PatientID";
gotoxy(15,3);
cout<<"Name ";
gotoxy(30,3);
cout<<"Disease";
gotoxy(50,3);
cout<<"Phone No.";
for(i=1;i<=80;i++)
{       gotoxy(i,4);
	cout<<"=";
}

	for(i=1;i<=80;i++)      //top border
	{
		gotoxy(i,1);
		cout<<"°";
		delay(10);
	}
	for(i=2;i<=23;i++)   //left
	{
		gotoxy(1,i);
		cout<<"°";
		delay(10);
	}
	for(i=2;i<=80;i++)  // bottom
	{
		gotoxy(i,23);
		cout<<"°";
		delay(10);
	}
	for(i=2;i<=23;i++)
	{
		gotoxy(80,i);
		cout<<"°";
		delay(10);
	}


}
void delRecord()
{
	patient p;
	ifstream fin("hospital.dat",ios::in);
	ofstream fout("temp.dat",ios::out);
	int pid;
	char found='f',confirm='n';
	cout<<"Enter patient Id of patient whose record is to be deleted\n";
	cin>>pid;
	while(!fin.eof())
	{
		fin.read((char*)&p,sizeof(p));
		if(p.getPid()==pid)
		{
			p.show();
			found='t';
			cout<<"Are you sure,You want to delete this record?(Y/N)..";
			cin>>confirm;
			if(confirm=='n')
				fout.write((char*)&p,sizeof(p));
		}
		else
		fout.write((char*)&p,sizeof(p));
	}

	if(found=='f')
	cout<<"\nRecord not found ";
	fin.close();
	fout.close();
	remove("hospital.dat");
	rename("temp.dat","hospital.dat");
}
void exitPro()
{
	int i;
	for(i=1;i<=30;i++)
	{
	gotoxy(i,3);
	cout<<" Developed By ";
	delay(1);
	}
	for(i=80;i>=30;i--)
	{
		gotoxy(i,4);
		cout<<" ->Rishabh Jain ";
		delay(1);
	}
	for(i=1;i<=30;i++)
	{
	gotoxy(i,5);
	cout<<" Class: XII-B ";
	delay(10);
	}
	getch();
}

void main()
{
int i,k,midx,midy,left,top,right,bottom;
int gdriver=DETECT,gmode,ec;

patient p;
char ch,pass[30];
i=k=0;

initgraph(&gdriver,&gmode,"c:\\tc\\bgi");
ec=graphresult();
	if(ec!=grOk)
	{
		cout<<"Error in Graphic Driver"<<grapherrormsg(ec);
		getch();
		exit(0);
	}
left=getmaxx()/2-200;
top=getmaxy()/2-50;
right=getmaxx()/2+100;
bottom=getmaxy()/2-20;
midx=getmaxx()/2;
midy=getmaxy()/2;

rectangle(left,top,right,bottom);
setcolor(GREEN);
settextstyle(8,0,1);
outtextxy(left+1,top,"Enter password");
while((ch=getch())!=13)
{
	k=k+10;
	outtextxy(left+160+k,top,"*");
	pass[i]=ch;
	i++;
}
pass[i]='\0';
settextstyle(4,0,5);
if(strcmp(pass,"welcome")==0)
{
	outtextxy(midx-100,midy,"Password Accepted!!!!!");
	outtextxy(midx-100,midy+40,"Please Wait.......");
	delay(3000);
}
else
{
	setcolor(RED);
	outtextxy(midx-100,midy,"Invalid Password");
	outtextxy(midx-100,midy+40,"Try Again......");
	delay(300);
}
cleardevice();
closegraph();


clrscr();
	do
	{
		clrscr();
		cout<<"1. Add Patient"<<endl;
		cout<<"2. Display Reports "<<endl;
		cout<<"3. Generate Bill "<<endl;
		cout<<"4. Delete Record "<<endl;
		cout<<"5. Exit Program "<<endl;
		ch=getch();
		switch(ch)
		{
			case '1':

				write2file();
				break;
			case '2':
				clrscr();
				box();
				dispRec();
				getch();
				break;
			case '3':
				clrscr();
				searchRec();
				getch();
				break;
			case '4':
				delRecord();
				getch();
				break;
			case '5':
				clrscr();
				exitPro();
				exit(0);
		}
	}while(ch!='5');


getch();
}








