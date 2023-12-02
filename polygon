#include <iostream>
#include <fstream>
#include <string>
#include <algorithm>
#include <cctype>
#include <sstream>
#include <cmath>

using namespace std;

class wyjatek{
private:
    string _wyjatek;
public:
    wyjatek();
    wyjatek(const string & awyjatek);
    string & wyjatki();

};

wyjatek::wyjatek()
{
}

wyjatek::wyjatek(const string & awyjatek) {
    _wyjatek = awyjatek;
}

string & wyjatek::wyjatki(){
    return _wyjatek;
}

void SprawdzZnacznik(const string &line, const string &tag){
    if (line[0] != '[')
        throw wyjatek("Niepoprawny format pliku!");
    if (line.back() != ']')
        throw wyjatek("Niepoprawny format pliku");
    string tagPierwszy = line.substr(1,line.length()-2);
    if (tagPierwszy.length() != tag.length())
        throw wyjatek("Niepoprawny format pliku!");
    for (int i = 0; i < tagPierwszy.length(); i++){
        if (toupper(tagPierwszy[i]) != tag[i])
            throw wyjatek("Niepoprawny format pliku!- 1");
    }

}

class punkt{
private:
    double _x; // atrybut
    double _y;
public:
    punkt(); //konstruktor
    punkt(double ax, double ay);  //konstruktor
    double & x(); //metody
    double & y();
    const double & x() const; // deklaracja metody
    const double & y() const;
};

punkt::punkt() { //definicja metody
    _x = 0.0;
    _y = 0.0;
}

punkt::punkt(double ax, double ay) {
    _x = ax;
    _y = ay;
}

double & punkt::x() {
    return _x;
}

double & punkt::y(){
    return _y;
}

const double & punkt::x() const  {
    return _x;
}
const double & punkt::y() const {
    return _y;
}

class polygon {
private:
    punkt *punkty;
    int _nnumber;
public:
    polygon();
    polygon(const string & nazwapliku);
    ~polygon();
    double pole ();
    double obwod ();
};
polygon::polygon(){

}

polygon::~polygon() {
    delete[] punkty;
}

polygon::polygon(const string & nazwapliku) {
    try {
        string tag;
        int nn;
        ifstream data (nazwapliku);
        if (!data.is_open()) {
            throw wyjatek("Nie mozna otworzyc pliku");
        }

        string line;
        getline(data, line);
        SprawdzZnacznik(line, "NUMBER OF NODES");
        getline(data,line);
        stringstream ssl(line);
        ssl >> nn;
        _nnumber = nn;
        //cout << nn <<endl;
        getline(data, line);
        cout << "Liczba wezlow = " << nn <<endl;
        cout << "Wspolrzedne " << endl;
        SprawdzZnacznik(line, "NODES");
        punkty = new punkt[nn];
        punkt* tmp = new punkt[nn];
        for (int i=0; i < nn; i++){
            getline(data, line);
            stringstream ssn(line);
            int index;
            double x;
            double y;
            ssn >> index >> x >> y;
            cout << index << " "<< x << " " << y << " " << endl;
           // punkty [index - 1] = punkt(x, y);
            tmp [index - 1] = punkt(x, y);

        }
        cout<< "Kolejnosc wezlow"<< endl;

        getline(data, line);
        SprawdzZnacznik(line, "POLYGON");
        getline(data, line);
        stringstream ssp(line);
        for (int i=0; i < nn; i++){
            int a1;
            ssp >> a1;
            cout << a1 << " ";
            punkty[i] = punkt(tmp[a1 - 1].x(),(tmp[a1 - 1].y()));

        }
        cout<< ""<< endl;
        data.close();
        delete[] tmp;
    }
    catch(wyjatek &eer){
        cout << eer.wyjatki() <<endl;
    }
}



double polygon::pole(){
    double pol = 0.0;
    int j = _nnumber - 1;
    for (int i=0; i < _nnumber; i++)
    {
        pol += (punkty[j].x() + punkty[i].x()) * (punkty[j].y() - punkty[i].y());
        j = i;
    }
    return fabs(pol / 2.0);
}

double polygon::obwod() {
    double obw = 0.0;
    int j = _nnumber - 1;
    for (int i=0; i < _nnumber; i++)
    {
        obw += sqrt(((punkty[j].x() - punkty[i].x()) * (punkty[j].x() - punkty[i].x()) ) +  ((punkty[j].y() - punkty[i].y()) *( punkty[j].y() - punkty[i].y())));
        j = i;
    }
    return obw;
}



int main(){
    polygon testp("C:\\Users\\olass\\Documents\\untitled\\dane.txt");
    cout << "Obwod wynosi: " << testp.obwod()<<endl;
    cout << "Pole wynosi: " << testp.pole()<< endl;
    cout << "Czyszcze pamiec" << endl;
    return 0;
    }
    
