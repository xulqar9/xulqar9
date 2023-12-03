using System;
using System.Globalization;

class HoroscopeProgram
{
    static void Main()
    {
        Console.WriteLine("Enter your birthdate (YYYY-MM-DD): ");
        DateTime birthdate;
        while (!DateTime.TryParseExact(Console.ReadLine(), "yyyy-MM-dd", CultureInfo.InvariantCulture, DateTimeStyles.None, out birthdate))
        {
            Console.WriteLine("Invalid format. Please enter your birthdate (YYYY-MM-DD): ");
        }

        Console.WriteLine("Enter your sex (M/F): ");
        string sex;
        do
        {
            sex = Console.ReadLine().ToUpper();
            if (sex != "M" && sex != "F")
            {
                Console.WriteLine("Invalid input. Please enter 'M' for Male or 'F' for Female: ");
            }
        } while (sex != "M" && sex != "F");

        string zodiacSign = GetZodiacSign(birthdate);
        string horoscope = GetHoroscope(zodiacSign);
        string info = GetInfo(zodiacSign, sex);

        Console.WriteLine($"Your Zodiac Sign is: {zodiacSign}");
        Console.WriteLine($"Horoscope: {horoscope}");
        Console.WriteLine($"Info: {info}");
    }

    static string GetZodiacSign(DateTime birthdate)
    {
        int month = birthdate.Month;
        int day = birthdate.Day;

        if ((month == 3 && day >= 21) || (month == 4 && day <= 19)) return "Aries";
        if ((month == 4 && day >= 20) || (month == 5 && day <= 20)) return "Taurus";
        if ((month == 5 && day >= 21) || (month == 6 && day <= 20)) return "Gemini";
        if ((month == 6 && day >= 21) || (month == 7 && day <= 22)) return "Cancer";
        if ((month == 7 && day >= 23) || (month == 8 && day <= 22)) return "Leo";
        if ((month == 8 && day >= 23) || (month == 9 && day <= 22)) return "Virgo";
        if ((month == 9 && day >= 23) || (month == 10 && day <= 22)) return "Libra";
        if ((month == 10 && day >= 23) || (month == 11 && day <= 21)) return "Scorpio";
        if ((month == 11 && day >= 22) || (month == 12 && day <= 21)) return "Sagittarius";
        if ((month == 12 && day >= 22) || (month == 1 && day <= 19)) return "Capricorn";
        if ((month == 1 && day >= 20) || (month == 2 && day <= 18)) return "Aquarius";
        if ((month == 2 && day >= 19) || (month == 3 && day <= 20)) return "Pisces";

        return "Unknown"; // Default case
    }

    static string GetHoroscope(string sign)
    {
        // Example horoscopes for each sign
        switch (sign)
        {
            case "Aries": return "Today is a good day for new beginnings.";
            case "Taurus": return "Patience will be your key to success.";
            case "Gemini": return "Your adaptability will open new doors.";
            case "Cancer": return "Focus on your emotional well-being.";
            case "Leo": return "Your charisma leads you to exciting opportunities.";
            case "Virgo": return "Attention to detail will bring rewards.";
            case "Libra": return "Balance in relationships is crucial today.";
            case "Scorpio": return "Embrace the changes coming your way.";
            case "Sagittarius": return "Adventure awaits, be ready to explore.";
            case "Capricorn": return "Your determination will lead to achievements.";
            case "Aquarius": return "Innovation is the key to your progress.";
            case "Pisces": return "Your intuition guides you to the right path.";
            default: return "No horoscope available.";
        }
    }

    static string GetInfo(string sign, string sex)
    {
        // Example information for each sign and sex
        string baseInfo = sign switch
        {
            "Aries" => "You are courageous and energetic.",
            "Taurus" => "You are reliable and practical.",
            "Gemini" => "You are curious and adaptable.",
            "Cancer" => "You are empathetic and loyal.",
            "Leo" => "You are confident and charismatic.",
            "Virgo" => "You are analytical and hardworking.",
            "Libra" => "You are diplomatic and fair-minded.",
            "Scorpio" => "You are passionate and resourceful.",
            "Sagittarius" => "You are optimistic and freedom-loving.",
            "Capricorn" => "You are disciplined and responsible.",
            "Aquarius" => "You are innovative and independent.",
            "Pisces" => "You are intuitive and compassionate.",
            _ => "Your personality is unique and multifaceted."
        };

        string genderInfo = sex == "M" ? "You have a strong sense of justice." : "You have a nurturing and caring nature.";

        return $"{baseInfo} {genderInfo}";
    }
}

