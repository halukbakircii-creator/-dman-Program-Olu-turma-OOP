# ıdman olusturma-OOP
public class Egzersiz {
    private String isim;
    private int setSayisi;
    private int tekrarSayisi;

    // Constructor (Yapıcı Metot)
    public Egzersiz(String isim, int setSayisi, int tekrarSayisi) {
        this.isim = isim;
        this.setSayisi = setSayisi;
        this.tekrarSayisi = tekrarSayisi;
    }

    // Getters and Setters
    public String getIsim() { return isim; }
    public void setIsim(String isim) { this.isim = isim; }

    public int getSetSayisi() { return setSayisi; }
    public void setSetSayisi(int setSayisi) { this.setSayisi = setSayisi; }

    public int getTekrarSayisi() { return tekrarSayisi; }
    public void setTekrarSayisi(int tekrarSayisi) { this.tekrarSayisi = tekrarSayisi; }
}    


public class Idman {
    private int burpeeSayisi;
    private int pushupSayisi;
    private int situpSayisi;
    private int squatSayisi;

    public Idman(int burpeeSayisi, int pushupSayisi, int situpSayisi, int squatSayisi) {
        this.burpeeSayisi = burpeeSayisi;
        this.pushupSayisi = pushupSayisi;
        this.situpSayisi = situpSayisi;
        this.squatSayisi = squatSayisi;
    }

    public void hareketYap(String hareketIsmi, int sayi) {
        if (hareketIsmi.equalsIgnoreCase("Burpee")) {
            burpeeYap(sayi);
        } else if (hareketIsmi.equalsIgnoreCase("Pushup")) {
            pushupYap(sayi);
        } else if (hareketIsmi.equalsIgnoreCase("Situp")) {
            situpYap(sayi);
        } else if (hareketIsmi.equalsIgnoreCase("Squat")) {
            squatYap(sayi);
        } else {
            System.out.println("Geçersiz hareket...");
        }
    }

    public void burpeeYap(int sayi) {
        if (burpeeSayisi == 0) System.out.println("Burpee bitti!");
        else if (burpeeSayisi - sayi < 0) {
            System.out.println("Hedefi geçtin! Kalan: 0");
            burpeeSayisi = 0;
        } else {
            burpeeSayisi -= sayi;
            System.out.println("Kalan Burpee: " + burpeeSayisi);
        }
    }

    // Diğer metotlar (pushupYap, situpYap vb.) buraya benzer şekilde eklenebilir.
    
    public boolean idmanBittiMi() {
        return (burpeeSayisi == 0) && (pushupSayisi == 0) && (situpSayisi == 0) && (squatSayisi == 0);
    }
}



import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.println("İdman Programına Hoşgeldiniz...");
        String idmanlar = "Geçerli Hareketler: Burpee, Pushup, Situp, Squat";
        System.out.println(idmanlar);

        System.out.print("Burpee Sayısı: ");
        int burpee = scanner.nextInt();
        System.out.print("Pushup Sayısı: ");
        int pushup = scanner.nextInt();
        System.out.print("Situp Sayısı: ");
        int situp = scanner.nextInt();
        System.out.print("Squat Sayısı: ");
        int squat = scanner.nextInt();
        scanner.nextLine(); // Dummy

        Idman idman = new Idman(burpee, pushup, situp, squat);

        while (!idman.idmanBittiMi()) {
            System.out.print("Hareket Türü (Burpee, Pushup vb.): ");
            String tur = scanner.nextLine();
            System.out.print("Kaç adet yapacaksınız? : ");
            int sayi = scanner.nextInt();
            scanner.nextLine();
            
            idman.hareketYap(tur, sayi);
        }
        System.out.println("Tebrikler, idmanını başarıyla tamamladın!");
    }
}
