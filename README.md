# 👻 Ghost Saugumo Modulis
**PowerShell Paremtas Windows ir Azure Saugumo Stiprinimo Įrankis**

> **Proaktyvus saugumo stiprinimas Windows galutiniams taškams ir Azure aplinkoms.** Ghost pateikia PowerShell paremtas stiprinimo funkcijas, kurios gali padėti sumažinti įprastus atakų vektorius išjungiant nereikalingas paslaugas ir protokolus.

## ⚠️ Svarbūs Perspėjimai

**REIKALINGAS TESTAVIMAS**: Visada pirmiau testuokite Ghost ne gamybos aplinkose. Paslaugų išjungimas gali paveikti teisėtas verslo funkcijas.

**NĖRA GARANTIJŲ**: Nors Ghost orientuotas į įprastus atakų vektorius, joks saugumo įrankis negali apsaugoti nuo visų atakų. Tai yra vienas komponento išsamioje saugumo strategijoje.

**VEIKLOS POVEIKIS**: Kai kurios funkcijos gali paveikti sistemos funkcionalumą. Kruopščiai peržiūrėkite kiekvieną nustatymą prieš diegimą.

**PROFESIONALUS VERTINIMAS**: Gamybos aplinkoms konsultuokitės su saugumo specialistais, kad užtikrintumėte, jog nustatymai atitinka jūsų organizacijos poreikius.

## 📊 Saugumo Kraštovaizdis

Ransomware žala pasiekė **57 milijardus dolerių 2025 m.**, tyrimai rodo, kad daugelis sėkmingų atakų išnaudoja pagrindinius Windows paslaugas ir netinkamas konfigūracijas. Įprasti atakų vektoriai apima:

- **90% ransomware incidentų** susijusių su RDP išnaudojimu
- **SMBv1 pažeidžiamumai** įgalino atakas kaip WannaCry ir NotPetya
- **Dokumentų makrokomandos** lieka pirminiu kenkėjiškatūros pristatymo metodu
- **USB paremti atakai** toliau taiko oro spragas tinklus
- **PowerShell piktnaudžiavimas** žymiai išaugo per pastaruosius metus

## 🛡️ Ghost Saugumo Funkcijos

Ghost pateikia **16 Windows stiprinimo funkcijų** plius **Azure saugumo integraciją**:

### Windows Galutinio Taško Stiprinimas

| Funkcija | Tikslas | Svarstymai |
|----------|---------|----------------|
| `Set-RDP` | Valdo Remote Desktop prieigą | Gali paveikti nuotolinį administravimą |
| `Set-SMBv1` | Kontroliuoja senąjį SMB protokolą | Reikalingas labai senoms sistemoms |
| `Set-AutoRun` | Kontroliuoja AutoPlay/AutoRun | Gali paveikti naudotojų patogumą |
| `Set-USBStorage` | Riboja USB saugojimo įrenginius | Gali paveikti teisėtą USB naudojimą |
| `Set-Macros` | Kontroliuoja Office makrokomandų vykdymą | Gali paveikti makrokomandų įgalintus dokumentus |
| `Set-PSRemoting` | Valdo PowerShell nuotolinę prieigą | Gali paveikti nuotolinę valdymą |
| `Set-WinRM` | Kontroliuoja Windows Remote Management | Gali paveikti nuotolinį administravimą |
| `Set-LLMNR` | Valdo vardų sprendimo protokolą | Paprastai saugu išjungti |
| `Set-NetBIOS` | Kontroliuoja NetBIOS per TCP/IP | Gali paveikti senąsias programas |
| `Set-AdminShares` | Valdo administracinius bendrinimus | Gali paveikti nuotolinę failų prieigą |
| `Set-Telemetry` | Kontroliuoja duomenų rinkimą | Gali paveikti diagnostikos galimybes |
| `Set-GuestAccount` | Valdo Svečio paskyrą | Paprastai saugu išjungti |
| `Set-ICMP` | Kontroliuoja ping atsakymus | Gali paveikti tinklo diagnostiką |
| `Set-RemoteAssistance` | Valdo Remote Assistance | Gali paveikti pagalbos centro operacijas |
| `Set-NetworkDiscovery` | Kontroliuoja tinklo atradimą | Gali paveikti tinklo naršymą |
| `Set-Firewall` | Valdo Windows ugniasienę | Kritinis tinklo saugumui |

### Azure Debesų Saugumas

| Funkcija | Tikslas | Reikalavimai |
|----------|---------|--------------|
| `Set-AzureSecurityDefaults` | Įjungia pagrindinį Azure AD saugumą | Microsoft Graph leidimai |
| `Set-AzureConditionalAccess` | Konfigūruoja prieigos politikas | Azure AD P1/P2 licencijavimas |
| `Set-AzurePrivilegedUsers` | Audituoja privilegijuotas paskyras | Global Admin leidimai |

### Įmonės Diegimo Parinktys

| Metodas | Naudojimo Atvejis | Reikalavimai |
|--------|----------|--------------|
| **Tiesioginis Vykdymas** | Testavimas, mažos aplinkos | Vietinės administratoriaus teisės |
| **Group Policy** | Domeno aplinkos | Domeno administratorius, GP valdymas |
| **Microsoft Intune** | Debesų valdomos įrangos | Intune licencijavimas, Graph API |

## 🚀 Greitas Pradžia

### Saugumo Vertinimas
```powershell
# Įkelti Ghost modulį
Invoke-WebRequest 'https://raw.githubusercontent.com/jimrtyler/Ghost/main/Ghost.ps1' -OutFile .\Ghost.ps1
Get-Content .\Ghost.ps1
. .\Ghost.ps1

# Patikrinti dabartinę saugumo būklę
Get-Ghost
```

### Pagrindinis Stiprinimas (Pirmiau Testuoti)
```powershell
# Esminis stiprinimas - pirmiau testuoti laboratorijos aplinkoje
Set-Ghost -SMBv1 -AutoRun -Macros

# Peržiūrėti pokyčius
Get-Ghost
```

### Įmonės Diegimas
```powershell
# Group Policy diegimas (domeno aplinkos)
Set-Ghost -SMBv1 -AutoRun -GroupPolicy

# Intune diegimas (debesų valdomos įrangos)
Set-Ghost -SMBv1 -RDP -USBStorage -Intune
```

## 📋 Diegimo Metodai

### 1 parinktis: Tiesioginis Atsisiuntimas (Testavimas)
```powershell
Invoke-WebRequest 'https://raw.githubusercontent.com/jimrtyler/Ghost/main/Ghost.ps1' -OutFile .\Ghost.ps1
Get-Content .\Ghost.ps1
. .\Ghost.ps1
```

### 2 parinktis: Modulio Diegimas
```powershell
# Diegti iš PowerShell Gallery (kai prieinama)
Install-Module Ghost -Scope CurrentUser
Import-Module Ghost
```

### 3 parinktis: Įmonės Diegimas
```powershell
# Kopijuoti į tinklo vietą Group Policy diegimui
# Konfigūruoti Intune PowerShell skriptus debesų diegimui
```

## 💼 Naudojimo Atvejų Pavyzdžiai

### Mažas Verslas
```powershell
# Pagrindinė apsauga su minimaliu poveikiu
Set-Ghost -SMBv1 -AutoRun -Macros -ICMP
```

### Sveikatos Priežiūros Aplinka
```powershell
# HIPAA orientuotas stiprinimas
Set-Ghost -SMBv1 -RDP -USBStorage -AdminShares -Telemetry
```

### Finansų Paslaugos
```powershell
# Aukšto saugumo konfigūracija
Set-Ghost -RDP -SMBv1 -AutoRun -USBStorage -Macros -PSRemoting -AdminShares
```

### Debesų Pirmoji Organizacija
```powershell
# Intune valdomas diegimas
Connect-IntuneGhost -Interactive
Set-Ghost -SMBv1 -RDP -AutoRun -Macros -Intune
```

## 🔍 Funkcijų Detalės

### Pagrindinės Stiprinimo Funkcijos

#### Tinklo Paslaugos
- **RDP**: Blokuoja nuotolinės darbalaukio prieigą arba atsitiktinai keičia prievadą
- **SMBv1**: Išjungia senąjį failų bendrinimo protokolą
- **ICMP**: Neleidžia ping atsakymų žvalgybai
- **LLMNR/NetBIOS**: Blokuoja senųjų vardų sprendimo protokolus

#### Programų Saugumas
- **Macros**: Išjungia makrokomandų vykdymą Office programose
- **AutoRun**: Neleidžia automatinio vykdymo iš keičiamų laikmenų

#### Nuotolinis Valdymas
- **PSRemoting**: Išjungia PowerShell nuotolinio sesijas
- **WinRM**: Sustabdo Windows Remote Management
- **Remote Assistance**: Blokuoja nuotolinės pagalbos ryšius

#### Prieigos Kontrolė
- **Admin Shares**: Išjungia C$, ADMIN$ bendrinimus
- **Guest Account**: Išjungia Svečio paskyros prieigą
- **USB Storage**: Riboja USB įrenginių naudojimą

### Azure Integracija
```powershell
# Prisijungti prie Azure nuomotojo
Connect-AzureGhost -Interactive

# Įjungti saugumo numatytuosius nustatymus
Set-AzureSecurityDefaults -Enable

# Konfigūruoti sąlyginę prieigą
Set-AzureConditionalAccess -BlockLegacyAuth -RequireMFA

# Audituoti privilegijuotus naudotojus
Set-AzurePrivilegedUsers -AuditOnly
```

### Intune Integracija (Nauja v2)
```powershell
# Prisijungti prie Intune
Connect-IntuneGhost -Interactive

# Diegti per Intune politikas
Set-IntuneGhost -Settings @{
    RDP = $true
    SMBv1 = $true
    USBStorage = $true
    Macros = $true
}
```

## ⚠️ Svarbūs Svarstymai

### Testavimo Reikalavimai
- **Laboratorijos Aplinka**: Pirmiau testuoti visus nustatymus izoliuotoje aplinkoje
- **Palaipsnis Diegimas**: Palaipsniui diegti problemų identifikavimui
- **Atšaukimo Planas**: Užtikrinti, kad galite atšaukti pokyčius jei reikia
- **Dokumentavimas**: Įrašyti kurie nustatymai veikia jūsų aplinkoje

### Galimas Poveikis
- **Naudotojų Produktyvumas**: Kai kurie nustatymai gali paveikti kasdienes darbo eigas
- **Senesnės Programos**: Senesnes sistemos gali reikalauti tam tikrų protokolų
- **Nuotolinė Prieiga**: Apsvarstykite poveikį teisėtam nuotoliniam administravimui
- **Verslo Procesai**: Patikrinkite, kad nustatymai nesugadina kritinių funkcijų

### Saugumo Apribojimai
- **Gylis Apsaugoje**: Ghost yra vienas saugumo sluoksnis, ne pilnas sprendimas
- **Nuolatinis Valdymas**: Saugumas reikalauja nuolatinio stebėjimo ir atnaujinimų
- **Naudotojų Mokymas**: Techninė kontrolė turi būti sujungta su saugumo sąmoningumo
- **Grėsmių Evoliucija**: Nauji atakų metodai gali apeiti dabartines apsaugas

## 🎯 Atakų Scenarijų Pavyzdžiai

Nors Ghost orientuotas į įprastus atakų vektorius, konkretus prevencija priklauso nuo tinkamo įgyvendinimo ir testavimo:

### WannaCry Stiliaus Atakai
- **Mažinimas**: `Set-Ghost -SMBv1` išjungia pažeidžiamą protokolą
- **Svarstymai**: Užtikrinti, kad jokai senesnes sistemos nereikalauja SMBv1

### RDP Paremta Ransomware
- **Mažinimas**: `Set-Ghost -RDP` blokuoja nuotolinės darbalaukio prieigą
- **Svarstymai**: Gali reikalauti alternatyvių nuotolinės prieigos metodų

### Dokumentų Paremta Kenkėjiška Programa
- **Mažinimas**: `Set-Ghost -Macros` išjungia makrokomandų vykdymą
- **Svarstymai**: Gali paveikti teisėtus makrokomandų įgalintus dokumentus

### USB Pristatomi Grėsmės
- **Mažinimas**: `Set-Ghost -USBStorage -AutoRun` riboja USB funkcionalumą
- **Svarstymai**: Gali paveikti teisėtą USB įrenginių naudojimą

## 🏢 Įmonės Funkcijos

### Group Policy Palaikymas
```powershell
# Taikyti nustatymus per Group Policy registry
Set-Ghost -SMBv1 -RDP -AutoRun -GroupPolicy

# Nustatymai taikomi visame domene po GP atnaujinimo
gpupdate /force
```

### Microsoft Intune Integracija
```powershell
# Sukurti Intune politikas Ghost nustatymams
Set-IntuneGhost -Settings $GhostSettings -Interactive

# Politikos automatiškai diegiamos valdomose įrengos
```

### Atitikties Ataskaitų Teikimas
```powershell
# Generuoti saugumo vertinimo ataskaitą
Get-Ghost | Export-Csv -Path "SecurityAudit-$(Get-Date -Format 'yyyy-MM-dd').csv"

# Azure saugumo pozicijos ataskaita
Get-AzureGhost | Out-File "AzureSecurityReport.txt"
```

## 📚 Geriausia Praktika

### Prieš Diegimą
1. **Dokumentuoti Dabartinę Būklę**: Paleisti `Get-Ghost` prieš pokyčius
2. **Kruopščiai Testuoti**: Patvirtinti ne gamybos aplinkoje
3. **Planuoti Atšaukimą**: Žinoti kaip atšaukti kiekvieną nustatymą
4. **Suinteresuotųjų Šalių Peržiūra**: Užtikrinti, kad verslo padaliniai patvirtina pokyčius

### Diegimo Metu
1. **Palaipsnio Priėjimas**: Pirmiau diegti bandomoms grupėms
2. **Stebėti Poveikį**: Sekti naudotojų skundus ar sistemos problemas
3. **Dokumentuoti Problemas**: Įrašyti bet kokias problemas tolesniam pasinaudojimui
4. **Komunikuoti Pokyčius**: Informuoti naudotojus apie saugumo pagerinimus

### Po Diegimo
1. **Reguliarus Vertinimas**: Periodiškai paleisti `Get-Ghost` nustatymų patikrinimui
2. **Atnaujinti Dokumentaciją**: Išlaikyti aktualias saugumo konfigūracijas
3. **Peržiūrėti Efektyvumą**: Stebėti saugumo incidentus
4. **Nuolatinis Gerinimas**: Koreguoti nustatymus pagal grėsmių kraštovaizdį

## 🔧 Problemų Šalinimas

### Dažnos Problemos
- **Leidimų Klaidos**: Užtikrinti aukštesnį PowerShell sesiją
- **Paslaugų Priklausomybės**: Kai kurios paslaugos gali turėti priklausomybių
- **Programų Suderinamumas**: Testuoti su verslo programomis
- **Tinklo Jungiamumas**: Patikrinti, kad nuotolinė prieiga vis dar veikia

### Atkūrimo Parinktys
```powershell
# Pakartotinai įjungti konkrečias paslaugas jei reikia
Set-RDP -Enable
Set-SMBv1 -Enable
Set-AutoRun -Enable
Set-Macros -Enable
```

## 👨‍💻 Apie Autorių

**Jim Tyler** - Microsoft MVP PowerShell
- **YouTube**: [@PowerShellEngineer](https://youtube.com/@PowerShellEngineer) (10,000+ sekėjų)
- **Naujienlaiškis**: [PowerShell.News](https://powershell.news) - Savaitės saugumo žvalgyba
- **Autorius**: "PowerShell for Systems Engineers"
- **Patirtis**: Dešimtmečių PowerShell automatizavimo ir Windows saugumo

## 📄 Licencija ir Atsakomybės Apribojimas

### MIT Licencija
Ghost pateikiamas pagal MIT licenciją nemokamam naudojimui, modifikavimui ir platinimui.

### Saugumo Atsakomybės Apribojimas
- **Nėra Garantijų**: Ghost pateikiamas "kaip yra" be jokių garantijų
- **Reikalingas Testavimas**: Visada testuoti ne gamybos aplinkose pirmiau
- **Profesionalūs Nurodymai**: Konsultuotis su saugumo specialistais gamybos diegimams
- **Veiklos Poveikis**: Autoriai nėra atsakingi už jokius veiklos sutrikimus
- **Išsamus Saugumas**: Ghost yra vienas komponentas pilnoje saugumo strategijoje

### Palaikymas
- **GitHub Issues**: [Pranešti apie klaidas ar prašyti funkcijų](https://github.com/jimrtyler/Ghost/issues)
- **Dokumentacija**: Naudokite `Get-Help <function> -Full` detaliai pagalbai
- **Bendruomenė**: PowerShell ir saugumo bendruomenės forumai

---

**🔒 Stiprinkite savo saugumo poziciją su Ghost - bet visada pirmiau testuokite.**

```powershell
# Pradėkite su vertinimu, ne prielaidomis
Get-Ghost
```

**⭐ Pažymėkite žvaigždute šį saugyklą jei Ghost padeda pagerinti jūsų saugumo poziciją!**