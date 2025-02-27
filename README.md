## Þorsteinn Heiðar Hreimsson


## 1. Uppsetning á Windows og grunn stillingar
* #### first thing i did after installing windows was selecting Setup for organization and Domain join instead
* #### after that i renamed the computer to
```
KEST2VW-TorsteinnHeidarHreimsson
```
* #### after that i installed and setup [Python](https://www.python.org/downloads/) and [VS Code](https://code.visualstudio.com/)

* #### after that i installed and setup [Git](https://www.python.org/downloads/)
* <img width="302" alt="kest2-mynd1" src="https://github.com/user-attachments/assets/1b06a5a9-1bd8-4392-a87d-689073ba12bf" />


  
## 2. Notendur
* ### ég bjó til hópana: Innkaup, Sala, Yfirstjórn og Allir
* <img width="71" alt="kest2-mynd2" src="https://github.com/user-attachments/assets/24246454-c59b-4901-a822-2de828dea08f" />
*
* ### ég bjó til vinnumen.csv
```
nafn,fornafn,eftirnafn,notendanafn,hopur
Guðríður Eiríksdóttir,Guðríður,Eiríksdóttir,GudEir,Yfirstjórn
Eva Markúsdóttir,Eva,Markúsdóttir,EvaMar,Yfirstjórn
Ásdís Magnúsdóttir,Ásdís,Magnúsdóttir,AsdMag,Innkaup
Vilborg Traustadóttir,Vilborg,Traustadóttir,VilTra,Innkaup
Kristján Björn Snorrason,Kristján,Snorrason,KriSno,Sala
Baldvin Kr Baldvinsson,Baldvin,Baldvinsson,BalBal,Sala
Ólafur Þór Leifsson,Ólafur,Leifsson,OlaLei,Sala
Guðmundur Óskar Bjarnason,Guðmundur,Bjarnason,GudBja,Sala
Per Stephansen,Per,Stephansen,PerSte,Sala
```
* ### ég bjó til þetta powershell script til að importa users 

```powershell
$gogn = Import-Csv C:\Users\steini\Desktop\vscode\vinnumen.csv
foreach($faersla in $gogn) {
    $nafn = $faersla.nafn
    $fnanf = $faersla.fornafn
    $enafn = $faersla.eftirnafn
    $notendanafn = $faersla.notendanafn
    $hopur = $faersla.hopur
    $password = Read-Host "sláðu inn lykilorð" -AsSecureString
    New-LocalUser -Name $notendanafn -Password $password 
    Add-LocalGroupMember -Group $hopur -Member $notendanafn
    Add-LocalGroupMember -Group "Allir" -Member $notendanafn
}
```



