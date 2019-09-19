# printer
printer with focus on toner level
public class Printer {

    private double tonerLevel;
    private int pagesPrinted;
    boolean isDuplex;

    public Printer(double tonerLevel, int pagesPrinted, boolean isDuplex) {
       if(tonerLevel<0&& tonerLevel<=100)
           tonerLevel=0;
        this.tonerLevel = tonerLevel;
        this.pagesPrinted = pagesPrinted;
        this.isDuplex = isDuplex;
    }

    public double getTonerLevel() {
        return tonerLevel;
    }

    public int getPagesPrinted() {
        return pagesPrinted;
    }

    public boolean isDuplex() {
        return isDuplex;
    }

    public void fillToner(double toner){
        if ((toner+tonerLevel)<=100.0){
            this.tonerLevel+=toner;
        }
        else
            System.out.println("Too many toner , please verify , toner level" + getTonerLevel());
    }

    public boolean print(){
        if((tonerLevel>0.1)&& (isDuplex)){
            System.out.println("Page was printed both size");
             pagesPrinted+=2;
             tonerLevel-=0.2;
             return true;
        }
        else  if((tonerLevel>0.1)&&(!isDuplex)){
            System.out.println("Page was printed one size");
            pagesPrinted+=1;
            tonerLevel-=0.1;
            return true;
        }
        return  false;
        }

public  int printPages(int pages){
        int pagesToPrint=pages;
        if(isDuplex){
            pagesToPrint=pages/2+pages%2;
        }
        this.pagesPrinted+=pagesToPrint;
        return pagesToPrint;
}


}
