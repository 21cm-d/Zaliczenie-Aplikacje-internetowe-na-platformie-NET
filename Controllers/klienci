using BazaKlientow.Data;
using BazaKlientow.Models;
using Microsoft.AspNetCore.Mvc;
using Microsoft.EntityFrameworkCore;

namespace BazaKlientow.Controllers;

public class KlienciController : Controller
{
    private readonly BazaContext _baza;
    public KlienciController(BazaContext baza) => _baza = baza;

    public async Task<IActionResult> Index(string szukaj)
    {
        var klienci = _baza.Klienci.AsQueryable();
        if (!string.IsNullOrWhiteSpace(szukaj))
            klienci = klienci.Where(k => k.Imie.Contains(szukaj) || k.Nazwisko.Contains(szukaj) ||
                (k.Email != null && k.Email.Contains(szukaj)) || (k.Miasto != null && k.Miasto.Contains(szukaj)));
        ViewBag.Szukaj = szukaj;
        return View(await klienci.OrderBy(k => k.Nazwisko).ToListAsync());
    }

    public IActionResult Dodaj() => View(new Klient());

    [HttpPost]
    [ValidateAntiForgeryToken]
    public async Task<IActionResult> Dodaj(Klient klient)
    {
        if (!ModelState.IsValid) return View(klient);
        klient.DataDodania = DateTime.Now;
        _baza.Add(klient);
        await _baza.SaveChangesAsync();
        return RedirectToAction(nameof(Index));
    }

    public async Task<IActionResult> Edytuj(int id)
    {
        var klient = await _baza.Klienci.FindAsync(id);
        return klient == null ? NotFound() : View(klient);
    }

    [HttpPost]
    [ValidateAntiForgeryToken]
    public async Task<IActionResult> Edytuj(int id, Klient klient)
    {
        if (id != klient.Id) return NotFound();
        if (!ModelState.IsValid) return View(klient);
        _baza.Update(klient);
        await _baza.SaveChangesAsync();
        return RedirectToAction(nameof(Index));
    }

    public async Task<IActionResult> Szczegoly(int id)
    {
        var klient = await _baza.Klienci.FindAsync(id);
        return klient == null ? NotFound() : View(klient);
    }

    public async Task<IActionResult> Usun(int id)
    {
        var klient = await _baza.Klienci.FindAsync(id);
        return klient == null ? NotFound() : View(klient);
    }

    [HttpPost, ActionName("Usun")]
    [ValidateAntiForgeryToken]
    public async Task<IActionResult> PotwierdzUsuniecie(int id)
    {
        var klient = await _baza.Klienci.FindAsync(id);
        if (klient != null) { _baza.Klienci.Remove(klient); await _baza.SaveChangesAsync(); }
        return RedirectToAction(nameof(Index));
    }
}
