using System;
class Program
{
    static void Main()
    {
        int jumlahTransaksi = 0;
        int beliLimaTiket = 0;
        bool lanjut = true;

        while (lanjut)
        {
            if (jumlahTransaksi >= 5)
            {
                Console.WriteLine("Aplikasi berhenti: maksimal 5 kali transaksi.");
                break;
            }

            Console.WriteLine("=== PEMBELIAN TIKET ONLINE ===");
            Console.Write("Masukkan jumlah tiket (1 - 5): ");
            int jumlahTiket = Convert.ToInt32(Console.ReadLine());

            if (jumlahTiket < 1 || jumlahTiket > 5)
            {
                Console.WriteLine("Jumlah tiket tidak valid!");
                continue;
            }

            int hargaPerTiket = 100000;
            int total = jumlahTiket * hargaPerTiket;
            double diskon = 0;

            if (jumlahTiket == 5)
            {
                beliLimaTiket++;

                if (beliLimaTiket > 3)
                {
                    diskon = 0.05;
                }
                else
                {
                    diskon = 0.10;
                }
            }

            double potongan = total * diskon;
            double totalBayar = total - potongan;

            Console.WriteLine("\n--- STRUK PEMBELIAN ---");
            Console.WriteLine("Jumlah Tiket : " + jumlahTiket);
            Console.WriteLine("Total Harga  : Rp " + total.ToString("N0"));
            Console.WriteLine("Diskon       : " + (diskon * 100) + "%");
            Console.WriteLine("Potongan     : Rp " + potongan.ToString("N0"));
            Console.WriteLine("Total Bayar  : Rp " + totalBayar.ToString("N0"));

            jumlahTransaksi++;

            Console.Write("\nIngin transaksi lagi? (y/n): ");
            string jawab = Console.ReadLine().ToLower();
            if (jawab != "y") lanjut = false;

            Console.WriteLine();
        }

        Console.WriteLine("Terima kasih telah menggunakan aplikasi!");
    }
}
