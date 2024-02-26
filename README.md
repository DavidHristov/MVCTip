namespace ddz.Model
{
    public class Plochki
    {
        private double n;
        private double w;
        private double l;
        private double m;
        private double o;
        public Plochki(double n, double w,double l , double m, double o) 
        {
            this.N = n;
            this.W = w;
            this.L = l;
            this.M = m;
            this.O = o;
        }

        public double N { get; set; }
        public double W { get; set; }
        public double L { get; set; }
        public double M { get; set;}
        public double O {get; set;}

        public double[] Calculate()
        {
            var plosht = N * N;
            var pokrivane = plosht - O;
            var plochki = W * L;
            var nujniPlochki = pokrivane / N;
            var vreme = nujniPlochki * 0.2;
            double[] niga = {nujniPlochki, vreme};
            return niga;
            

        }
        
    }
}




namespace ddz.View
{
    public class Display
    {
        public Display()
        {
            this.N = 0;
            this.W = 0;
            this.L = 0;
            this.M = 0;
            this.O = 0;
            this.Plocki = 0;
            this.Vreme = 0;
            this.GetValue();
        }
        public double N
        {
            get;set;
        }
        public double W
        {
            get; set;
        }
        public double L
        {
            get; set;
        }
        public double M
        {
            get; set;
        }
        public double O
        {
            get; set;
        }
        public double Plocki
        { get; set; }

        public double Vreme
        { get; set; }

        public void GetValue()
        {
            N = double.Parse(Console.ReadLine());
            W = double.Parse(Console.ReadLine());
            L = double.Parse(Console.ReadLine());
            M = double.Parse(Console.ReadLine());
            O = double.Parse(Console.ReadLine());
        }
        public void Show()
        {
            Console.WriteLine($"{this.Plocki:F2}");
            Console.WriteLine($"{this.Vreme:F2}");
        }
    }
}






namespace ddz.Controller
{
    public class PlochkiController
    {
        private Display display;
        private Plochki plochki;

        public PlochkiController()
        {
            display = new Display();
            plochki = new Plochki(display.N,display.W,display.L,display.M,display.O);
            display.Plocki = plochki.Calculate()[0];
            display.Vreme = plochki.Calculate()[1];
            display.Show();
        }
    }
}