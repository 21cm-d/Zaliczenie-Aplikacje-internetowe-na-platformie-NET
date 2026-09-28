using System.ComponentModel.DataAnnotations;

namespace BazaKlientow.Models;

public class Klient
{
    public int Id { get; set; }

    [Required(ErrorMessage = "Podaj imię")]
    [Display(Name = "Imię")]
    public string Imie { get; set; } = "";

    [Required(ErrorMessage = "Podaj nazwisko")]
    public string Nazwisko { get; set; } = "";

    [Phone(ErrorMessage = "Nieprawidłowy numer telefonu")]
    public string? Telefon { get; set; }

    [EmailAddress(ErrorMessage = "Nieprawidłowy adres e-mail")]
    [Display(Name = "E-mail")]
    public string? Email { get; set; }

    public string? Miasto { get; set; }

    [Display(Name = "Data dodania")]
    public DateTime DataDodania { get; set; } = DateTime.Now;
}
