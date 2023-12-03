using System;
using System.Globalization;

class HoroscopeProgram
{
    static void Main()
    {
        Console.WriteLine("Doğum tarihinizi girin (YYYY-AA-GG): ");
        DateTime birthdate;
        while (!DateTime.TryParseExact(Console.ReadLine(), "yyyy-MM-dd", CultureInfo.InvariantCulture, DateTimeStyles.None, out birthdate))
        {
            Console.WriteLine("Geçersiz format. Lütfen doğum tarihinizi girin (YYYY-AA-GG): ");
        }

        Console.WriteLine("Cinsiyetinizi girin (E/K): ");
        string sex;
        do
        {
            sex = Console.ReadLine().ToUpper();
            if (sex != "E" && sex != "K")
            {
                Console.WriteLine("Geçersiz giriş. Lütfen 'E' erkek veya 'K' kadın olarak girin: ");
            }
        } while (sex != "E" && sex != "K");

        string zodiacSign = GetZodiacSign(birthdate);
        string horoscope = GetHoroscope(zodiacSign);
        string info = GetInfo(zodiacSign, sex);

        Console.WriteLine($"Burcunuz: {zodiacSign}");
        Console.WriteLine($"Burç Yorumunuz: {horoscope}");
        Console.WriteLine($"Bilgi: {info}");
    }

    static string GetZodiacSign(DateTime birthdate)
    {
        int month = birthdate.Month;
        int day = birthdate.Day;

        if ((month == 3 && day >= 21) || (month == 4 && day <= 19)) return "Koç";
        if ((month == 4 && day >= 20) || (month == 5 && day <= 20)) return "Boğa";
        if ((month == 5 && day >= 21) || (month == 6 && day <= 20)) return "İkizler";
        if ((month == 6 && day >= 21) || (month == 7 && day <= 22)) return "Yengeç";
        if ((month == 7 && day >= 23) || (month == 8 && day <= 22)) return "Aslan";
        if ((month == 8 && day >= 23) || (month == 9 && day <= 22)) return "Başak";
        if ((month == 9 && day >= 23) || (month == 10 && day <= 22)) return "Terazi";
        if ((month == 10 && day >= 23) || (month == 11 && day <= 21)) return "Akrep";
        if ((month == 11 && day >= 22) || (month == 12 && day <= 21)) return "Yay";
        if ((month == 12 && day >= 22) || (month == 1 && day <= 19)) return "Oğlak";
        if ((month == 1 && day >= 20) || (month == 2 && day <= 18)) return "Kova";
        if ((month == 2 && day >= 19) || (month == 3 && day <= 20)) return "Balık";

        return "Bilinmeyen"; // Varsayılan durum
    }

    static string GetHoroscope(string sign)
    {
        switch (sign)
        {
            case "Koç": return "Bugün yeni başlangıçlar için iyi bir gün.";
            case "Boğa": return "Sabır başarının anahtarı olacak.";
            case "İkizler": return "Uyum yeteneğiniz yeni kapılar açacak.";
            case "Yengeç": return "Duygusal sağlığınıza odaklanın.";
            case "Aslan": return "Karizmanız heyecan verici fırsatlar sunuyor.";
            case "Başak": return "Detaylara dikkat etmek ödüllendirilecek.";
            case "Terazi": return "İlişkilerde denge bugün çok önemli.";
            case "Akrep": return "Yolunuza çıkan değişikliklere sarılın.";
            case "Yay": return "Macera bekliyor, keşfetmeye hazır olun.";
            case "Oğlak": return "Kararlılığınız başarıya yol açacak.";
            case "Kova": return "Yenilik, ilerlemenizin anahtarıdır.";
            case "Balık": return "İçgüdüleriniz doğru yolu gösteriyor.";
            default: return "Burç yorumu bulunamadı.";
        }
    }

    static string GetInfo(string sign, string sex)
    {
        // Her burç ve cinsiyet için örnek bilgiler
        string baseInfo = sign switch
        {
            "Koç" => "Cesur ve enerjiksiniz.",
            "Boğa" => "Güvenilir ve pratiksiniz.",
            "İkizler" => "Meraklı ve uyumlu bir yapınız var.",
            "Yengeç" => "Empatik ve sadıksınız.",
            "Aslan" => "Kendinden emin ve karizmatiksiniz.",
            "Başak" => "Analitik ve çalışkansınız.",
            "Terazi" => "Diplomatik ve adil bir bakış açınız var.",
            "Akrep" => "Tutkulu ve kaynaklarını iyi kullanan bir yapınız var.",
            "Yay" => "İyimser ve özgürlüğüne düşkünsünüz.",
            "Oğlak" => "Disiplinli ve sorumluluk sahibisiniz.",
            "Kova" => "Yenilikçi ve bağımsızsınız.",
            "Balık" => "Sezgileri kuvvetli ve merhametlisiniz.",
            _ => "Kişiliğiniz eşsiz ve çok yönlü."
        };

        string genderInfo = sex == "E" ? "Adalet duygusu güçlü." : "Bakım ve şefkat dolu bir doğanız var.";

        return $"{baseInfo} {genderInfo}";
    }
}
