# net-core-pluralsight

## Elavult infók

- Az Entity Framework (EF) tooling már nincs a `dotnet` alá default telepítve. Külön kell installálni azt a `dotnet tool install --global dotnet-ef` paranccsal. Utána így hívható az EF tool: `dotnet ef`.
- Az adatbázisról információkat a `dotnet ef dbcontext info` paranccsal lehet lekérni a DbContext-et tartalmazó projektben. Viszont ez a projekt nem tartalmazza az adatbázis beállításait (connection string, DbContextPool service), ezeket a web projekt állítja be (appsettings.json, Startup.cs). A parancsnak meg lehet adni a startup projektet, ami a web projekt lesz: `dotnet ef dbcontext info -s <a web projekt az aktuális projekthez viszonyított relatív elérési útvonala>`. Viszont ahhoz, hogy ez a parancs működjön, a startup projektnek referálnia kell a **Microsoft.EntityFrameworkCore.Design** NuGet csomagot.