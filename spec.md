# Gewenste spec voor endpoints

## Deelnemers endpoint (GET)
```json
{
  "UPN": "(string)",
  "EwiseSync": "(bool)",
  "EwiseZID": "(string|int)",
  "EwiseProductID": "(string|int|null)",
  "OrganisatieID": "(string|int)",
  "ContactID": "(string|int)",
  "PersoonID": "(string|int)",
  "Voorletters": "(string)",
  "Roepnaam": "(string)",
  "Achternaam": "(string)",
  "Geslacht": "(string[man/vrouw])",
  "Opmerking": "(string)",
  "SessieCode": "(string[Sessie die gebruikt moet worden voor resultaten])",
}
```

#### Uitleg bij waardes:
 - `UPN` :           De unieke identifier die wordt gebruikt om twee kanten op te syncen,
                     Deze waarde is de hoofdemail vand de user in afas
- `EwiseSync`:       Deze waarde is of er aanpassingen zijn in afas sinds de laatste sync,
                     het is belangrijk dat je kan filteren hierop
- `EwiseZID`:        Dit is de id uit ons systeem, het zou ideaal zijn als we dit zouden kunnen
                     gebruiken als rest `resource identifier`
- `EwsieProductID`:  Dit is het product Dat deze gebruiker afneemt bij ewise, deze waarde moet null kunnen zijn
                     Om aan te kunnen geven dat er geen actieve producten zijn gekoppeld
- `OrganisatieID`:   De (afas) id van dorganisatie waar deze gebruiker onder valt
- `ContactID`:       A.U.B meer uitleg nodig
- `PersoonID`:       A.U.B meer uitleg nodig
- `Voorletters`:     De voorletters van de gebruiker
- `Achternaam`:      De achternaam van de gebruiker
- `Gelsacht`:        Het geslacht van de gebruiker. het liefsts met de exacte waardes `Man` en `Vrouw`. en null als niks gezet is
- `Opmerking`:       De opmerking toegevoegd aan deze gebruiker
- `SessieCode`:      De sessie code waar alle afgeronde cursussen aan gekoppeld moeten worden voor deze gebruiker


## Cursus toevoegen endpoint (POST) / Cursus aanpassen endpoint (PUT)
```json
{
  "*CursusID": "(string|int)",
  "CusrsusNaam": "(string)",
  "Opmerking": "(string)",
  "CursusType": "(string)",
}
```

#### Uitleg bij waardes:
- `CursusID` :        De unieke cursus id die door ewise wordt aangeleverd
- `CursusNaam` :      De naam van de cursus van ewise
- `Opmerking` :       Optionele opmerkingen voor de cursus
- `CursusType` :      Een optionele waarde voor het type cursus van ewise


## Resultaten doorgeven endpoint (POST)
```json
{
  "*PersoonID": "(string|int)",
  "*CusrusID": "(string|int)",
  "GestartOp": "(string)",
  "AfgerondOp": "(string)",
}
```

#### Uitleg bij waardes:
- `PersoonID` :       De (afas) id van de persoon Die de cursus heeft afgerond
- `CusrusID` :        De (ewise)cursus id van de cursus die is afgerond
- `GestartOp`:        Een datum in het formaat 'dd-mm-yyyy' Waarop de cursus gestart is
- `AfgerondOp`:       Een datum in het formaat 'dd-mm-yyyy' Waarop de cursus behaald is


## Andere endpoint TBD