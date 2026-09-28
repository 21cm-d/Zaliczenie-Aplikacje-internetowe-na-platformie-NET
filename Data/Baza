using BazaKlientow.Models;
using Microsoft.EntityFrameworkCore;

namespace BazaKlientow.Data;

public class BazaContext : DbContext
{
    public BazaContext(DbContextOptions<BazaContext> options) : base(options) { }
    public DbSet<Klient> Klienci => Set<Klient>();
}
