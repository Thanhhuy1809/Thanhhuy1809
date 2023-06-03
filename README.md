- 👋 Hi, I’m @Thanhhuy1809
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
Thanhhuy1809/Thanhhuy1809 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
#include<iostream>
#include<conio.h>
#include<fstream>
#include<stdio.h>
#include<stdlib.h>
#include<dos.h>
#include<bits/stdc++.h>
#include<iomanip>
#include<string.h>

 using namespace std;

//lop chinh restaurant nha hang

 class restaurant
 {
private:
 int ban;
 char name[30];
 char address[50];
 char phone[10];
 public:
// menu chinh
restaurant();
 void main_menu();
 //chuc nang 1 : chon 1 ban an  
 void chonban(); 
 //chuc nang 2: lua chon do an theo ban an
 void display();
 //chuc nang 3: xuat ra tinh trang hien tai cua ban an 
 void phongan(); 
 //chuc nang 4: sua chua cac ban an gom sua thong tin khach hang,xoa ban an ,xuat bill
 void edit(); 
 //kiem tra tinh trang cua cac ban an
 int check(int); 
 //sua thong tin ban an
 void suadoi(int); 
 //xoa ban an
 void xoaban(int);
 //ham huy
 ~restaurant();
     };
     
restaurant::restaurant()
{
	
}
     

//ham menumain
 void restaurant::main_menu()
 {
 int choice;
 while(choice!=5)
 {

  system("cls");
  system("color 3");
 cout<<"\n\t\t\t\t*************************";
 cout<<"\n\t\t\t\t*   QUAN LI NHA HANG    *";
 cout<<"\n\t\t\t\t     * MAIN MENU *";
 cout<<"\n\t\t\t\t*************************";
 cout<<"\n\n\n\t\t\t1.CHON BAN AN.";
 cout<<"\n\t\t\t2.CHON THUC AN CHO BAN.";
 cout<<"\n\t\t\t3.TINH TRANG BAN AN HIEN TAI";
 cout<<"\n\t\t\t4.EDIT BAN AN";
 cout<<"\n\t\t\t5.Exit";
 cout<<"\n\n\t\t\tNhap chuc nang so : ";
cin>>choice;
switch(choice)
{
 case 1: chonban();
break;
 case 2: display();
break;
 case 3: phongan();
break;
 case 4: edit();
break;
 case 5: break;
default:
{

 cout<<"\n\n\t\t\tVui long nhap lai.....!!!";
 cout<<"\n\t\t\tNhan de tiep tuc....!!";
 getch();

 }

 }
 }
}



 void restaurant::chonban()
 {

   system("cls");
 int r,flag;
 ofstream fout("dulieu.dat",ios::app);
system("color A");
 cout<<"\n NHAP THONG TIN";
 cout<<"\n ----------------------";
 cout<<"\n\n Ban an so: ";
 cout<<"\n Tong so ban an la 50";
 cout<<"\n Ban an  binh thuong (1 - 30)";
 cout<<"\n Ban an sang trong (31 - 45";
 cout<<"\n Ban an VIP  (46 - 50)";
 cout <<"\n Xin quy khach vui long nhap so ban an muon chon :- "<<endl;
 cin>>r;

 flag=check(r);

 if(flag)
{
 cout<<"\n Xin loi..!!!Ban da duoc dat tu truoc";
}
 else
 {

 ban=r;
 cout<<" Ten khach hang: ";
 fflush(stdin);
 cin.getline(name,30);
cout<<" Dia chi khach hang: ";
 cin.getline(address,50);
 cout<<" So dien thoai khach hang: ";
 cin>>phone;

 fout.write((char*)this,sizeof(restaurant));
 cout<<"\n THANH CONG...!!!";

 }

 cout<<"\n Press any key to continue.....!!";

 getch();
 fout.close();

 }




//display : chon thuc an thuc uong va xuat ra bill cua ban an do

int tong;
void restaurant::display() {
   system("cls");
   ifstream fin("dulieu.dat",ios::in);
   int r,flag;
   system("color 7");
   cout<<"\n Nhap ban an so : "<<endl;
   cin>>r;
   
   while(fin.read((char*)this,sizeof(restaurant))) {
      if(ban==r) {
         system("cls");
         cout<<"\n Customer Details";
         cout<<"\n ----------------";
         cout<<"\n\n Ban an so: "<<ban;
         cout<<"\n Ten: "<<name;
         cout<<"\n Dia chi: "<<address;
         cout<<"\n SDT: "<<phone;
         cout<<endl;
     // In thông tin giá bàn
     if(r<=30&&r>=1){
        cout<<"\nBan an cua quy khach la: ban thuong (20000)"<<endl;
        tong += 20000;
     }
     else if(r>=31&&r<=45){
        cout<<"\nBan an cua quy khach la: ban sang trong(40000)"<<endl;
        tong += 40000;
     }
     else if(r<=50&&r>=46){
        cout<<"\nBan an cua quy khach la : ban VIP (10000)"<<endl;
        tong += 100000;
     }
     
     // Ham menu 
     class Menu {
        private:
        string tenMonAn;
        int soLuong;
        int giaTien;
        
        public:
        Menu(string tenMonAn, int giaTien) {
            this->tenMonAn = tenMonAn;
            this->soLuong = 0;
            this->giaTien = giaTien;
        }
        
        string getTenMonAn() {
            return tenMonAn;
        }
        
        int getSoLuong() {
            return soLuong;
        }
        
        void setSoLuong(int soLuong) {
            this->soLuong = soLuong;
        }
        
        int getGiaTien() {
            return giaTien;
        }
        
        void xuatThongTinMonAn() {
            cout <<setw(20)<< tenMonAn << " So luong " <<setw(5)<< soLuong << "   TONG : " <<setw(10)<< giaTien * soLuong << " VND" << endl;
        }
     };
     
     class MenuThucAn {
        private:
        Menu m[20] = {
            // Mon khai vi
            Menu("Ngo chien", 40000),
            Menu("Khoai chien", 40000),
            Menu("Banh mi chien", 20000),
            // Sup cac loai
            Menu("Sup ca hoi", 20000),
            Menu("Sup cua", 25000),
            Menu("Sup hai san", 25000),
            Menu("Sup luon", 15000),
            // Cac mon hai san
            Menu("Hao nuong pho mai", 10000),
            Menu("Hao nuong mo hanh", 5000),
            Menu("Tom sot chua cay", 40000),
            Menu("Tom nuong muoi ot", 40000),
            Menu("Bach tuoc sao cay", 50000),
            Menu("Sashimi bach tuoc", 50000),
            Menu("Oc huong bo toi", 5000),
            Menu("Oc buou den sao sa ot", 50000),
            // Cac mon an no
            Menu("Com chien tran chau", 25000),
            Menu("Com suon", 25000),
            Menu("Mi sao that cam", 25000),
            Menu("Mi cay", 25000),
            Menu("Banh canh cua", 30000)
        };
        
        public:
        void xuat() {
            cout << "------------------------------------------------------------" << endl;
            cout << "MENU" << endl;
            cout << "_________________________________________________________________________" << endl;
            cout << "| STT |             TEN MON AN                               |  GIA-VND |" << endl;
            cout << "-------------------------------------------------------------------------";
            for (int i = 0; i < 20; i++) {
                cout << "\n|" << setw(5) << i + 1 << "|";
                cout << setw(33) << m[i].getTenMonAn();
                cout << setw(21) << "           " << "|";
                cout << setw(8) << m[i].getGiaTien() << "  |";
                cout << "\n+-----+------------------------------------------------------+----------+";
            }
        }
        
        void chonMonAn(int stt, int soLuong) {
            m[stt - 1].setSoLuong(soLuong);
        }
        
        void nhap() {
            int stt, soLuong;
            do {
                cout << "\nNhap so thu tu mon an muon chon (nhap 0 de tro ve): ";
                cin >> stt;
                if (stt > 0 && stt <= 20) {
                    cout << "Nhap so luong: ";
                    cin >> soLuong;
                    chonMonAn(stt, soLuong);
                    cout << "Mon an da duoc chon!" << endl;
                }
                else if (stt != 0) {
                    cout << "So thu tu khong hop le. Vui long nhap lai!" << endl;
                }
            } while (stt != 0);
        }
        
        void xuatHoaDon() {
            int tongtien = 0;
            cout << "------------------------------------------------------------" << endl;
            cout<<endl;
            cout << "HOA DON" << endl;
            for (int i = 0; i < 20; i++) {
                if (m[i].getSoLuong() > 0) {
                    m[i].xuatThongTinMonAn();
                    tongtien += m[i].getGiaTien() * m[i].getSoLuong();
                }
            }
            cout << "------------------------------------------------------------" << endl;
            cout << "TONG CONG DO AN: " << tongtien << " VND" << endl;
            cout << "TIEN BAN AN: " << tong << " VND" << endl;
            cout << "TONG HOA DON: " << tongtien + tong << " VND" << endl;
        }
     };
     
     MenuThucAn ml;
     ml.xuat();
     ml.nhap();
     ml.xuatHoaDon();
     
     flag = 1;
     break;
  }
  else {
     flag = 0;
 }
 }

if (flag == 0) {
cout << "\nSo ban khong hop le hoac ban dang trong tinh trang khong co khach!";
}

cout << "\n\nNhan phim bat ky de tiep tuc...";
getch();
fin.close();
};
  



 

 void restaurant::phongan()
 {

   system("cls");

 ifstream fin("dulieu.dat",ios::in);
 cout<<"\n\t\t\t DANH SACH BAN AN HIEN TAI";
 cout<<"\n\t\t\t ----------------------";
 cout<<"\n\n BAN SO.\tTEN\t\tDIA CHI\t\t\t\tSO DIEN THOAI.\n";

 while(!fin.eof())
 {

 fin.read((char*)this,sizeof(restaurant));
 cout<<"\n\n "<<ban<<"\t\t"<<name;
 cout<<"\t\t"<<address<<"\t\t\t\t"<<phone;

 }

 cout<<"\n\n\n\t\t\tPress any key to continue.....!!";
 getch();
 fin.close();

 }



//sua thong tin cua nha hang
 void restaurant::edit()
 {

   system("cls");

 int choice,r;
 cout<<"\n EDIT MENU";
 cout<<"\n ---------";
 cout<<"\n\n 1.Sua thong tin ban an";
 cout<<"\n 2.Xoa ban an";
 cout<<"\n Enter your choice: ";

 cin>>choice;
   system("cls");

 cout<<"\n Nhap ban so: " ;
 cin>>r;
 switch(choice)
 {

 case 1: suadoi(r);
 break;

 case 2: xoaban(r);
 break;

 default: cout<<"\n Nhap sai.....!!";

 }
 cout<<"\n Press any key to continue....!!!";

 getch();
 }


 int restaurant::check(int r)
 {

 int flag=0;

 ifstream fin("dulieu.dat",ios::in);

 while(!fin.eof())
 {

 fin.read((char*)this,sizeof(restaurant));
 if(ban==r)
 {

 flag=1;
 break;

 }

 }

 fin.close();
 return(flag);

 }




//sua thongtin
 void restaurant::suadoi(int r)
 {

 long pos,flag=0;

 fstream file("dulieu.dat",ios::in|ios::out|ios::binary);

 while(!file.eof())
 {

 pos=file.tellg();
 file.read((char*)this,sizeof(restaurant));

 if(ban==r)
 {

 cout<<"\nNhap thong tin moi cua khach hang ";
 cout<<"\n -----------------";
 cout<<"\n Ten moi: ";
 fflush(stdin);
 cin.getline(name,30);
 cout<<" Dia chi moi: ";
 cin.getline(address,50);
 cout<<" So dien thoai moi ";
 cin>>phone;
 file.seekg(pos);
 file.write((char*)this,sizeof(restaurant));
 cout<<"\n Thay doi thanh cong...";
 flag=1;
 break;

 }

 }

 if(flag==0)
 cout<<"\n Xin loi. Hien tai ban khong co nguoi....!!";
 file.close();

 }



//xoa ban an
 void restaurant::xoaban(int r)
 {

 int flag=0;
 char ch;
 ifstream fin("dulieu.dat",ios::in);
 ofstream fout("temp.dat",ios::out);

 while(!fin.eof())
 {

 fin.read((char*)this,sizeof(restaurant));
 if(ban==r)

 {

 cout<<"\n Ten khach: "<<name;
 cout<<"\n Dia chi: "<<address;
 cout<<"\n So dien thoai: "<<phone;
 cout<<"\n\n Ban co muon xoa ban an cua khach nay khong(y/n): ";
 cin>>ch;
 if(ch=='n')
 fout.write((char*)this,sizeof(restaurant));
 flag=1;

 }

 else
 fout.write((char*)this,sizeof(restaurant));

 }

 fin.close();
 fout.close();

 if(flag==0)
 cout<<"\nXin loi.Hien tai ban dang chua co nguoi....!!";

 else
 {

 remove("dulieu.dat");
 rename("temp.dat","dulieu.dat");

 }

 }
 
 
 //hamhuy
 restaurant::~restaurant()
 {
 	delete[]name;
 	delete[]address;
 	delete[]phone;
 }


 //ham main
 int main()
 {

 restaurant r;

   system("cls");

 cout<<"\n\t\t________________________________";
 cout<<"\n\t\t| RESTAURANT MANAGEMENT PROJECT|";
 cout<<"\n\t\t********************************";
 cout<<"\n\n\t\tTHANH VIEN:";
 cout<<"THANH HUY AND QUOC KHANH";
 cout<<"\n\n\n\n\n\n\n\t\t\t\t\tPress any key to continue....!!";

 getch();

 r.main_menu();
return 0;
 }
