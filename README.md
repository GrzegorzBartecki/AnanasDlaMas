# AnanasDlaMas
projekty i skrypty, materiały
to jest test zmian w pliku tekstowym
przykładowy kod z egzaminu z III using System;

namespace laborka_6._1
{
    enum RodzajSilnika { pojemnosc0, pojemnosc1, pojemnosc2}
  
    class ObiektKolowy
    {
        int _szerokosc;      // atrybut private  właściwości
        public int _srednicaKola; // atrybut private public
        
        public int WlasciwosciSzerokosc                   //wlaściwosci get+set do atrybutu
        {
            get { return _szerokosc; }
            set { _szerokosc = value; }
        }               
       
        public ObiektKolowy() //konstruktor domyslny klasy podstawowej
        {
            _szerokosc = 2;
            _srednicaKola = 2;            
        }
        public ObiektKolowy(int iloscKol, int srednicaKola) //konstruktor ten drugi
        {
            _szerokosc = iloscKol;
            _srednicaKola = srednicaKola;            
        }         
    }
    class Motocykl : ObiektKolowy
    {
        public string _nazwa;        
        public bool _czyUruchomiony;        
        public Silnik _moc;
        public static int _nrSeryjny;

        public static int Licz()
        {
            return _nrSeryjny++;
        }
        public Motocykl()
        {
            _nazwa = "nazwa";
            _czyUruchomiony = false;
            _moc = new Silnik();
            _nrSeryjny = 0;
        }
        public Motocykl(int szerokosc, int srednicaKola, string nazwa, bool czyUruchmiony, Silnik moc, int nrSeryjny)
            : base(szerokosc, srednicaKola)
        {
            _nazwa = nazwa;
            _czyUruchomiony = czyUruchmiony;
            _moc = moc; //new Motocykl.Silnik(RodzajSilnika.pojemnosc1)
            _nrSeryjny = nrSeryjny;
        }
        public Motocykl(Motocykl PrzykladowyObiek)
        {                  
            _nazwa = PrzykladowyObiek._nazwa;
            _czyUruchomiony = PrzykladowyObiek._czyUruchomiony;
            _moc = PrzykladowyObiek._moc;
        }
        public bool WlasciwoscCzyUruchomiony
        {
            get { return _czyUruchomiony; }
            set { _czyUruchomiony = value; }
        }      
        private Silnik moc { get => _moc; set => _moc = value; }
        //wlasciwosc atrybutu o klasie zagnieżdzonej

        public void PokazStatus()
        {
            Console.WriteLine("pole1 dziedziczone:\t\t" + WlasciwosciSzerokosc);//z wlasciwosci
            Console.WriteLine("pole2 dziedziczone:\t\t" + _srednicaKola);
            
            Console.WriteLine("pole1 wlasne:\t\t" + _nazwa);
            Console.WriteLine("pole2 wlasne :\t\t" + _czyUruchomiony);
            
            if (_moc.pojemnosc == RodzajSilnika.pojemnosc1) Console.WriteLine("cos w typie 0");
            if (_moc.pojemnosc == RodzajSilnika.pojemnosc1) Console.WriteLine("cos w typie 1");
            if (_moc.pojemnosc == RodzajSilnika.pojemnosc2) Console.WriteLine("cos w typie 2");
            Console.WriteLine("ustawienie  :\t" + _moc.pojemnosc);           
        }
        public class Silnik
        {
            public RodzajSilnika pojemnosc;

            public Silnik()
            {
                pojemnosc = RodzajSilnika.pojemnosc1;
            }

            public Silnik(RodzajSilnika wybor)
            {
                this.pojemnosc = wybor;
            }
        }       
    }

    class Przyczepka : ObiektKolowy
    {
        public int _ladownosc;

        

        public Przyczepka()
        {            
            _ladownosc = 10;            
        }

        public Przyczepka(int iloscKol, int srednicaKola, int ladownosc)
            :base (iloscKol,srednicaKola)
        {
            _ladownosc = ladownosc;
        }
    }

         
        class PrzyczepkaTowarowa :Przyczepka
        {
        public string _nazwa;
        public bool _czyZhakiem;
        
        public double _dlugosc;

        public static int _nrSeryjny;
        public static int Licz()
        {
            return _nrSeryjny++;
        }
        public PrzyczepkaTowarowa()
        {
            _nazwa = "PrzyczepkaZBajerami";
            _czyZhakiem = false;            
            _dlugosc = 1.5;
        }

        public PrzyczepkaTowarowa(int szerokosc, int srednicaKola, string nazwa, bool czyZhakiem, int ladownosc, int dlugosc)
            :base(szerokosc, srednicaKola, ladownosc)
        {
            _nazwa = nazwa;
            _czyZhakiem = czyZhakiem;            
            _dlugosc = dlugosc;
        }
         
        public PrzyczepkaTowarowa(PrzyczepkaTowarowa wzorcowaPrzyczepka)
        {
            _nazwa = wzorcowaPrzyczepka._nazwa;
            _czyZhakiem = wzorcowaPrzyczepka._czyZhakiem;            
            _dlugosc = wzorcowaPrzyczepka._dlugosc;
        }
        public bool WlasiwosciCzyzHakiem
        {
            get { return _czyZhakiem; }
            set { _czyZhakiem = value; }
        }
    }

    class PrzyczepkaMala : Przyczepka
    {
        public string _nazwa;
        public bool _czyZhakiem;
        
        public double _dlugosc;

        public static int _nrSeryjny;
        public static int Licz()
        {
            return _nrSeryjny++;
        }
        public PrzyczepkaMala()
        {
            _nazwa = "PrzyczepkaZBajerami";
            _czyZhakiem = false;
            
            _dlugosc = 1.5;
        }

        public PrzyczepkaMala(int szerokosc, int srednicaKola, string nazwa, bool czyZhakiem, int ladownosc, int dlugosc)
            : base(szerokosc, srednicaKola, ladownosc)
        {
            _nazwa = nazwa;
            _czyZhakiem = czyZhakiem;            
            _dlugosc = dlugosc;
        }

        public PrzyczepkaMala(PrzyczepkaTowarowa wzorcowaPrzyczepka)
        {
            _nazwa = wzorcowaPrzyczepka._nazwa;
            _czyZhakiem = wzorcowaPrzyczepka._czyZhakiem;
            _ladownosc = wzorcowaPrzyczepka._ladownosc;
            _dlugosc = wzorcowaPrzyczepka._dlugosc;
        }
        public bool WlasiwosciCzyzHakiem
        {
            get { return _czyZhakiem; }
            set { _czyZhakiem = value; }
        }
    }
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine(" program robiący coś tam coś tam ");
            Motocykl mojeMoto= new Motocykl();
            Motocykl mojeMoto1 = new Motocykl(4, 5, "nazwa",  false,  new Motocykl.Silnik(RodzajSilnika.pojemnosc1),1);
                                                                    //new Motocykl.Silnik(RodzajSilnika.pojemnosc1)  
            Console.WriteLine("  test   "+ Motocykl._nrSeryjny );
            Console.WriteLine("  static test   " + Motocykl.Licz());
            Console.WriteLine("  static test   " + Motocykl.Licz());

            Console.WriteLine("  nazwa moto   " + mojeMoto1._nazwa);
            mojeMoto1._nazwa="coś tam coś tam";
            mojeMoto1.PokazStatus();

            Console.WriteLine("Naciśnij dowolny klawisz, by zakończyć program.");

            Console.ReadKey();
        }         
        private static void FunkcjaZmienStatus(Motocykl mojobiekt)
        {
            mojobiekt._moc.pojemnosc = RodzajSilnika.pojemnosc1;
            mojobiekt._czyUruchomiony = false;            
            mojobiekt.PokazStatus();
        }   
    }
}


using System;

namespace laborka_6._1
{
    enum RodzajSilnika { pojemnosc0, pojemnosc1, pojemnosc2}
  
    class ObiektKolowy
    {
        int _szerokosc;      // atrybut private  właściwości
        public int _srednicaKola; // atrybut private public
        
        public int WlasciwosciSzerokosc                   //wlaściwosci get+set do atrybutu
        {
            get { return _szerokosc; }
            set { _szerokosc = value; }
        }               
       
        public ObiektKolowy() //konstruktor domyslny klasy podstawowej
        {
            _szerokosc = 2;
            _srednicaKola = 2;            
        }
        public ObiektKolowy(int iloscKol, int srednicaKola) //konstruktor ten drugi
        {
            _szerokosc = iloscKol;
            _srednicaKola = srednicaKola;            
        }         
    }
    class Motocykl : ObiektKolowy
    {
        public string _nazwa;        
        public bool _czyUruchomiony;        
        public Silnik _moc;
        public static int _nrSeryjny;

        public static int Licz()
        {
            return _nrSeryjny++;
        }
        public Motocykl()
        {
            _nazwa = "nazwa";
            _czyUruchomiony = false;
            _moc = new Silnik();
            _nrSeryjny = 0;
        }
        public Motocykl(int szerokosc, int srednicaKola, string nazwa, bool czyUruchmiony, Silnik moc, int nrSeryjny)
            : base(szerokosc, srednicaKola)
        {
            _nazwa = nazwa;
            _czyUruchomiony = czyUruchmiony;
            _moc = moc; //new Motocykl.Silnik(RodzajSilnika.pojemnosc1)
            _nrSeryjny = nrSeryjny;
        }
        public Motocykl(Motocykl PrzykladowyObiek)
        {                  
            _nazwa = PrzykladowyObiek._nazwa;
            _czyUruchomiony = PrzykladowyObiek._czyUruchomiony;
            _moc = PrzykladowyObiek._moc;
        }
        public bool WlasciwoscCzyUruchomiony
        {
            get { return _czyUruchomiony; }
            set { _czyUruchomiony = value; }
        }      
        private Silnik moc { get => _moc; set => _moc = value; }
        //wlasciwosc atrybutu o klasie zagnieżdzonej

        public void PokazStatus()
        {
            Console.WriteLine("pole1 dziedziczone:\t\t" + WlasciwosciSzerokosc);//z wlasciwosci
            Console.WriteLine("pole2 dziedziczone:\t\t" + _srednicaKola);
            
            Console.WriteLine("pole1 wlasne:\t\t" + _nazwa);
            Console.WriteLine("pole2 wlasne :\t\t" + _czyUruchomiony);
            
            if (_moc.pojemnosc == RodzajSilnika.pojemnosc1) Console.WriteLine("cos w typie 0");
            if (_moc.pojemnosc == RodzajSilnika.pojemnosc1) Console.WriteLine("cos w typie 1");
            if (_moc.pojemnosc == RodzajSilnika.pojemnosc2) Console.WriteLine("cos w typie 2");
            Console.WriteLine("ustawienie  :\t" + _moc.pojemnosc);           
        }
        public class Silnik
        {
            public RodzajSilnika pojemnosc;

            public Silnik()
            {
                pojemnosc = RodzajSilnika.pojemnosc1;
            }

            public Silnik(RodzajSilnika wybor)
            {
                this.pojemnosc = wybor;
            }
        }       
    }

    class Przyczepka : ObiektKolowy
    {
        public int _ladownosc;

        

        public Przyczepka()
        {            
            _ladownosc = 10;            
        }

        public Przyczepka(int iloscKol, int srednicaKola, int ladownosc)
            :base (iloscKol,srednicaKola)
        {
            _ladownosc = ladownosc;
        }
    }

         
        class PrzyczepkaTowarowa :Przyczepka
        {
        public string _nazwa;
        public bool _czyZhakiem;
        
        public double _dlugosc;

        public static int _nrSeryjny;
        public static int Licz()
        {
            return _nrSeryjny++;
        }
        public PrzyczepkaTowarowa()
        {
            _nazwa = "PrzyczepkaZBajerami";
            _czyZhakiem = false;            
            _dlugosc = 1.5;
        }

        public PrzyczepkaTowarowa(int szerokosc, int srednicaKola, string nazwa, bool czyZhakiem, int ladownosc, int dlugosc)
            :base(szerokosc, srednicaKola, ladownosc)
        {
            _nazwa = nazwa;
            _czyZhakiem = czyZhakiem;            
            _dlugosc = dlugosc;
        }
         
        public PrzyczepkaTowarowa(PrzyczepkaTowarowa wzorcowaPrzyczepka)
        {
            _nazwa = wzorcowaPrzyczepka._nazwa;
            _czyZhakiem = wzorcowaPrzyczepka._czyZhakiem;            
            _dlugosc = wzorcowaPrzyczepka._dlugosc;
        }
        public bool WlasiwosciCzyzHakiem
        {
            get { return _czyZhakiem; }
            set { _czyZhakiem = value; }
        }
    }

    class PrzyczepkaMala : Przyczepka
    {
        public string _nazwa;
        public bool _czyZhakiem;
        
        public double _dlugosc;

        public static int _nrSeryjny;
        public static int Licz()
        {
            return _nrSeryjny++;
        }
        public PrzyczepkaMala()
        {
            _nazwa = "PrzyczepkaZBajerami";
            _czyZhakiem = false;
            
            _dlugosc = 1.5;
        }

        public PrzyczepkaMala(int szerokosc, int srednicaKola, string nazwa, bool czyZhakiem, int ladownosc, int dlugosc)
            : base(szerokosc, srednicaKola, ladownosc)
        {
            _nazwa = nazwa;
            _czyZhakiem = czyZhakiem;            
            _dlugosc = dlugosc;
        }

        public PrzyczepkaMala(PrzyczepkaTowarowa wzorcowaPrzyczepka)
        {
            _nazwa = wzorcowaPrzyczepka._nazwa;
            _czyZhakiem = wzorcowaPrzyczepka._czyZhakiem;
            _ladownosc = wzorcowaPrzyczepka._ladownosc;
            _dlugosc = wzorcowaPrzyczepka._dlugosc;
        }
        public bool WlasiwosciCzyzHakiem
        {
            get { return _czyZhakiem; }
            set { _czyZhakiem = value; }
        }
    }
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine(" program robiący coś tam coś tam ");
            Motocykl mojeMoto= new Motocykl();
            Motocykl mojeMoto1 = new Motocykl(4, 5, "nazwa",  false,  new Motocykl.Silnik(RodzajSilnika.pojemnosc1),1);
                                                                    //new Motocykl.Silnik(RodzajSilnika.pojemnosc1)  
            Console.WriteLine("  test   "+ Motocykl._nrSeryjny );
            Console.WriteLine("  static test   " + Motocykl.Licz());
            Console.WriteLine("  static test   " + Motocykl.Licz());

            Console.WriteLine("  nazwa moto   " + mojeMoto1._nazwa);
            mojeMoto1._nazwa="coś tam coś tam";
            mojeMoto1.PokazStatus();

            Console.WriteLine("Naciśnij dowolny klawisz, by zakończyć program.");

            Console.ReadKey();
        }         
        private static void FunkcjaZmienStatus(Motocykl mojobiekt)
        {
            mojobiekt._moc.pojemnosc = RodzajSilnika.pojemnosc1;
            mojobiekt._czyUruchomiony = false;            
            mojobiekt.PokazStatus();
        }   
    }
}
