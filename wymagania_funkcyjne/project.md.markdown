# System aukcyjny

## Wprowadzenie

Specyfikacja wymagań funkcjonalnych w ramach informatyzacji procesu sprzedaży produktów w oparciu o mechanizm aukcyjny. 

## Procesy biznesowe

---
<a id="bc1"></a>
### BC1: Sprzedaż aukcyjna 

**Aktorzy:** [Sprzedający](#ac1), [Kupujący](#ac2)

**Opis:** Proces biznesowy opisujący sprzedaż za pomocą mechanizmu aukcyjnego. |

**Scenariusz główny:**
1. [Sprzedający](#ac1) wystawia produkt na aukcję. ([UC1](#uc1)) ([BR3](#br3)) ([BR4](#br4))
2. [Kupujący](#ac2) oferuje kwotę za produkt wyższą od aktualnie najwyższej oferty. ([UC2](#uc2)) ([BR1](#br1))
3. [Kupujący](#ac2) wygrywa aukcję. ([UC3](#uc3)) ([BR2](#br2))
4. [Kupujący](#ac2) przekazuje należność Sprzedającemu. ([UC4](#uc4)) ([BR5](#br5))
5. [Sprzedający](#ac1) przekazuje produkt Kupującemu. ([UC5](#uc5)) ([BR5](#br5)) ([BR6](#br6))

**Scenariusze alternatywne:** 

2.A. Oferta Kupującego została przebita, a [Kupujący](#ac2) pragnie przebić aktualnie najwyższą ofertę.
* 2.A.1. Przejdź do kroku 2.

3.A. Czas aukcji upłynął i [Kupujący](#ac2) przegrał aukcję. ([BR2](#br2))
* 3.A.1. Koniec przypadku użycia.

---

## Aktorzy

<a id="ac1"></a>
### AC1: Sprzedający

Osoba oferująca towar na aukcji.

<a id="ac2"></a>
### AC2: Kupujący

Osoba chcąca zakupić produkt na aukcji.


## Przypadki użycia poziomu użytkownika

### Aktorzy i ich cele

[Sprzedający](#ac1):
* [UC1](#uc1): Wystawienie produktu na aukcję
* [UC5](#uc5): Przekazanie produktu Kupującemu 

[Kupujący](#ac2)
* [UC2](#uc2): Podanie kwoty za produkt na licytacji
* [UC3](#uc3): Wygranie aukcji
* [UC4](#uc4): Przekazanie należności Sprzedającemu 
---
<a id="uc1"></a>
### UC1: Wystawienie produktu na aukcję

**Aktorzy:** [Sprzedający](#ac1)

**Scenariusz główny:**
1. [Sprzedający](#ac1) zgłasza do systemu chęć wystawienia produktu na aukcję.
2. System prosi o podanie danych produktu i ceny wywoławczej.
3. [Sprzedający](#ac1) podaje dane produktu oraz cenę wywoławczą.
4. System weryfikuje poprawność danych.
5. System informuje o pomyślnym wystawieniu produktu na aukcję.

**Scenariusze alternatywne:** 

4.A. Podano niepoprawne lub niekompletne dane produktu.
* 4.A.1. System informuje o błędnie podanych danych.
* 4.A.2. Przejdź do kroku 2.

---

<a id="uc2"></a>
### UC2: Podanie kwoty za produkt na licytacji

**Aktorzy:** [Kupujący](#ac2)

**Scenariusz główny:**
1. [Kupujący](#ac2) wybiera aukcję, na której chce złożyć ofertę.
2. System wyświetla aktualną najwyższą ofertę oraz minimalną kwotę, jaką można zadeklarować.
3. [Kupujący](#ac2) podaje kwotę swojej oferty.
4. System weryfikuje poprawność podanej kwoty.
5. System informuje o pomyślnym przyjęciu oferty.

**Scenariusze alternatywne:** 

4.A. Podano kwotę niższą niż minimalna do zaakceptowania.
* 4.A.1. System informuje o nieprawidłowej kwocie oferty.([BR2](#br2))
* 4.A.2. Przejdź do kroku 2.

---

<a id="uc3"></a>
### UC3: Wygranie aukcji

**Aktorzy:** [Kupujący](#ac2), [Sprzedający](#ac1)

**Scenariusz główny:**
1. Aukcja kończy się po upływie określonego czasu lub po wybraniu opcji zakończenia przez [Sprzedającego](#ac1).
2. System weryfikuje najwyższą ofertę złożoną na aukcji.
3. System informuje [Kupującego](#ac2), który złożył najwyższą ofertę, że wygrał aukcję.
4. System informuje [Sprzedającego](#ac1) o zakończeniu aukcji i wygranej ofercie.

**Scenariusze alternatywne:**

2.A. Brak złożonych ofert na aukcji.
* 2.A.1. System informuje [Sprzedającego](#ac1) o zakończeniu aukcji bez wygranej oferty.

---

<a id="uc4"></a>
### UC4: Przekazanie należności Sprzedającemu 

**Aktorzy:** [Kupujący](#ac2), [Sprzedający](#ac1)

**Scenariusz główny:**
1. [Kupujący](#ac2), który wygrał aukcję, przechodzi do sekcji płatności.
2. System wyświetla należną kwotę za wygrany produkt oraz dostępne metody płatności.
3. [Kupujący](#ac2) dokonuje płatności.
4. System weryfikuje poprawność transakcji.
5. System informuje [Sprzedającego](#ac1) o pomyślnym przekazaniu należności.

**Scenariusze alternatywne:** 

4.A. Płatność nie powiodła się.
* 4.A.1. System informuje [Kupującego](#ac2) o nieudanej płatności i prosi o ponowne dokonanie transakcji.
* 4.A.2. Przejdź do kroku 2.

---

<a id="uc5"></a>
### UC5: Przekazanie produktu Kupującemu 

**Aktorzy:** [Sprzedający](#ac1), [Kupujący](#ac2)

**Scenariusz główny:**
1. System informuje [Sprzedającego](#ac1) o otrzymaniu płatności za produkt.
2. [Sprzedający](#ac1) przygotowuje produkt do wysyłki.
3. System udostępnia [Sprzedającemu](#ac1) dane kontaktowe [Kupującego](#ac2) oraz wybraną metodę dostawy.
4. [Sprzedający](#ac1) wysyła produkt do [Kupującego](#ac2) i zaznacza w systemie, że produkt został wysłany.
5. System informuje [Kupującego](#ac2) o wysłaniu produktu i udostępnia dane śledzenia przesyłki (jeśli są dostępne).
6. [Kupujący](#ac2) potwierdza odbiór produktu.

**Scenariusze alternatywne:**

4.A. Sprzedający nie wysłał produktu w terminie.
* 4.A.1. System przypomina [Sprzedającemu](#ac1) o konieczności wysyłki.
* 4.A.2. Jeśli nadal brak wysyłki, [Kupujący](#ac2) może skontaktować się z pomocą techniczną systemu.
---

## Obiewkty biznesowe (inaczje obiekty dziedzinowe lub informatycjne)

### BO1: Aukcja

Aukcja jest formą zawierania transakcji kupna-sprzedaży, w której Sprzedający określa cenę wywoławczą produktu, natomiast Kupujący mogą oferować własną ofertę zakupu każdorazowo proponując kwotę wyższą od aktualnie oferowanej kwoty. Aukcja kończy się po upływie określonego czasu. Jeśli złożona została co najmniej jedna oferta zakupy produkt nabywa ten Kupujący, który zaproponował najwyższą kwotę. 

### BO2: Produkt

Fizyczny lub cyfrowy obiekt, który ma zostać sprzedany w ramach aukcji.

### BO3: Oferta

Oferta jest propozycją zakupu produktu wystawionego na aukcji. Każda oferta jest składana przez Kupującego i musi być wyższa od aktualnej najwyższej oferty. Oferta jest wiążąca do momentu zakończenia aukcji.

### BO4: Płatność

Płatność jest procesem przekazania należności przez Kupującego na rzecz Sprzedającego po wygranej aukcji. Płatność musi zostać zatwierdzona przez system, aby mogło dojść do dalszych kroków, takich jak wysyłka produktu.

### BO5: Przesyłka

Przesyłka to fizyczne lub cyfrowe przekazanie produktu Kupującemu po dokonaniu płatności. Przesyłka jest inicjowana przez Sprzedającego i monitorowana przez system, który zapewnia Kupującemu możliwość śledzenia statusu przesyłki.

## Reguły biznesowe

<a id="br1"></a>
### BR1: Złożenie oferty

Złożenie oferty wymaga zaproponowania kwoty wyższej niż aktualnie oferowana o minimum 1,00 PLN.


<a id="br2"></a>
### BR2: Rozstrzygnięcie aukcji

Aukcję wygrywa ten z [Kupujących](#ac2), który w momencie jej zakończenia (upłynięcia czasu) złożył najwyższą ofertę.

<a id="br3"></a>
### BR3: Minimalna cena wywoławcza 

Aukcja nie może zostać rozpoczęta, jeżeli cena wywoławcza produktu jest mniejsza niż 1,00 PLN.

<a id="br4"></a>
### BR4: Czas trwania aukcji 
Aukcja musi trwać co najmniej 1 godzinę, a jej maksymalny czas trwania nie może przekroczyć 30 dni.

<a id="br5"></a>
### BR5: Potwierdzenie płatności
Płatność za wygrany produkt musi zostać potwierdzona przed rozpoczęciem procesu wysyłki.

<a id="br6"></a>
### BR6: Zgłoszenie problemu z produktem
Kupujący mają obowiązek zgłoszenia problemu z produktem w ciągu 7 dni roboczych od jego otrzymania.

## Macierz CRUDL


| Przypadek użycia                                  | Aukcja | Produkt | Oferta | Płatność | Przesyłka |
| ------------------------------------------------- | ------ | ------- | ------ | -------- | --------- |
| UC1: Wystawienie produktu na aukcję               |   C    |    C    |   -    |    -     |     -     |
| UC2: Podanie kwoty za produkt na licytacji        |   R    |    R    |   C    |    -     |     -     |
| UC3: Wygranie aukcji                              |   U    |    R    |   R    |    -     |     -     |
| UC4: Przekazanie należności Sprzedającemu         |   R    |    R    |   R    |    C     |     -     |
| UC5: Przekazanie produktu Kupującemu              |   R    |    R    |   R    |    R     |     C     |


