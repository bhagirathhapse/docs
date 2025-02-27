---
title: "Zmiana oferty hostingowej"
excerpt: "Dowiedz się, jak zmienić formułę subskrypcji hostingu OVHcloud"
slug: how_to_change_hosting_offer
section: Optymalizacja strony WWW
order: 2
---

> [!primary]
> Tłumaczenie zostało wygenerowane automatycznie przez system naszego partnera SYSTRAN. W niektórych przypadkach mogą wystąpić nieprecyzyjne sformułowania, na przykład w tłumaczeniu nazw przycisków lub szczegółów technicznych. W przypadku jakichkolwiek wątpliwości zalecamy zapoznanie się z angielską/francuską wersją przewodnika. Jeśli chcesz przyczynić się do ulepszenia tłumaczenia, kliknij przycisk „Zaproponuj zmianę” na tej stronie.
>

**Ostatnia aktualizacja z dnia 19-05-2022**

## Wprowadzenie

W [Panelu klienta OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.pl/&ovhSubsidiary=pl) pozwala na zwiększenie pojemności [ofert hostingu www](https://www.ovhcloud.com/pl/web-hosting/), aby uzyskać wydajniejszy hosting, więcej przestrzeni dyskowej, baz danych, adresów e-mail lub dodatkowych funkcji, takich jak [listy mailingowe](https://docs.ovh.com/pl/emails/hosting_www_listy_mailingowe/) (począwszy od [oferta Pro](https://www.ovhcloud.com/pl/web-hosting/professional-offer/)) lub usługa [Prywatny SQL](https://www.ovhcloud.com/pl/web-hosting/options/private-sql/) (zawarty w ofertach [gama Performance](https://www.ovhcloud.com/pl/web-hosting/performance-offer/)).

**Dowiedz się, jak zmienić ofertę hostingu OVHcloud bez przerwy w działaniu.**

## Wymagania początkowe

- Posiadanie [hostingu](https://www.ovhcloud.com/pl/web-hosting/)
- Dostęp do [Panelu klienta OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.pl/&ovhSubsidiary=pl)

## W praktyce

> [!success]
> 
> **Potrzebujesz tymczasowo zwiększyć parametry hostingu?**
>
> Korzystając z [opcji Boost](https://www.ovhcloud.com/pl/web-hosting/options/boost/), dostępnej w ofercie OVHcloud *Performance*, możesz tymczasowo zwiększyć zasoby hostingu, aby obsłużyć tymczasowy wzrost ruchu. Jeśli wzrost ten trwa dłużej, możesz przejść na wyższy poziom, aby na stałe dysponować większą ilością zasobów.
>

### Ważne - Płatność w przypadku zmiany oferty

Kiedy zmieniasz ofertę w trakcie subskrypcji, na nowej ofercie obowiązuje *odroczenie*. To odroczenie odpowiada pozostałemu okresowi abonamentu na aktualną ofertę.

**Przykład:**<br>
Przechodzisz z oferty [Perso](https://www.ovhcloud.com/pl/web-hosting/personal-offer/) na ofertę [Pro](https://www.ovhcloud.com/pl/web-hosting/professional-offer/), podczas gdy abonament w trakcie nie został zakończony.<br>
W związku z tym pozostały okres abonamentu zostanie automatycznie dodany **dodany** pro rata temporis **Pro**.<br>
W związku z tym będzie on trwał **nieco dłużej niż rok**, aż do kolejnego odnowienia.

### Zmień ofertę hostingu <a name="modify"></a>

> [!primary]
>
> Zmiana subskrypcji dla oferty zapewniającej mniej zasobów jest możliwa tylko w przypadku oferty **natychmiast niższej**. 
> Na przykład nie można przejść z formuły *Performance 2* na formułę *Pro* w jednej operacji.
> Należy **najpierw** zmienić ofertę hostingu z poziomu oferty *Performance 2* na ofertę *Performance 1* **następnie** na ofertę *Pro*.
>
> Poniższe elementy dotyczą ofert płatnych. Aby zwiększyć [darmowy hosting Start10M](https://docs.ovh.com/pl/hosting/wlaczanie_start10m/), postępuj zgodnie z [instrukcjami](#start10m).
>

> [!warning]
>
> **Przed** każda zmiana abonamentu na niższą ofertę sprawdź, czy korzystanie z aktualnej oferty jest kompatybilne z charakterystyką kolejnej [oferty hostingowej](https://www.ovhcloud.com/pl/web-hosting/).
>
> W tym celu postępuj zgodnie z [instrukcjami](#checks) tymi, zmieniaj ofertę i powtarzać te operacje tyle razy, ile to konieczne.
>

Aby zmienić subskrypcję, przejdź do [Panelu klienta OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.pl/&ovhSubsidiary=pl) w części `Web Cloud`{.action}. Kliknij polecenie `Hosting`{.action} i wybierz odpowiedni hosting.

W polu `Abonament` kliknij przycisk `...`{.action} po prawej stronie `Usługa`, a następnie kliknij `Zmień ofertę`{.action}.

![change_plan](images/change_plan.png){.thumbnail}

Następnie wybierz Twój nowy abonament oraz czas jego trwania. Zatwierdź odpowiednie regulaminy i kliknij `Wyślij`{.action}.

### Zmień ofertę hostingu Start 10M na wyższą ofertę <a name="start10m"></a>

> [!primary]
>
> Poniższa procedura ma zastosowanie **tylko w przypadku aktywacji usługi poczty elektronicznej przypisanej do oferty Start 10M**.
>
> Jeśli nie włączyłeś usługi poczty elektronicznej, wystarczy instrukcja z [poprzedni punkt](#modify).
>

Nie będziesz mógł zmienić **bezpośrednio** z [bezpłatnego hostingu Start10M](https://docs.ovh.com/pl/hosting/wlaczanie_start10m/) na ofertę płatną. Wykonaj następujące operacje:

1. W razie potrzeby zapisz [pliki hostingu](https://docs.ovh.com/pl/hosting/eksportowanie-witryna-internetowa/#etap-1-pobranie-plikow-z-twojej-przestrzeni-dyskowej-ftp) i [wiadomości e-mail](https://docs.ovh.com/pl/emails/przenoszenie-kont-e-mail/)<br>
2. Uruchom usuwanie usługi Start10M. W tym celu w prawym górnym rogu kliknij Twoją nazwę, a następnie `Zarządzanie usługami`{.action}. Następnie kliknij przycisk `...`{.action} po prawej stronie danej usługi, po czym kliknij `Usuń natychmiast hosting`{.action}.<br>
3. Utwórz [zgłoszenie serwisowe](https://help.ovhcloud.com/pl/faq/support/cant-reach-support-phone/), aby zażądać przyspieszonego usunięcia Twojej oferty (adres e-mail Start10M jest domyślnie przechowywany przez 14 dni, w celu uniknięcia utraty danych z powodu błędu podczas operacji).<br>
4. [Zamów nową ofertę hostingu](https://www.ovhcloud.com/pl/web-hosting/).<br>
5. W razie potrzeby zaimportuj Twoją stronę do [nowej przestrzeni hostingowej](https://docs.ovh.com/pl/hosting/hosting_www_umieszczenie_strony_w_internecie/#etap-2-wgranie-plikow-strony-www-na-przestrzen-dyskowa).<br>
6. [Dodaj domenę do swojej strony w opcji MultiSite](https://docs.ovh.com/pl/hosting/konfiguracja-multisite-na-hostingu/#etap-2-dodanie-domeny-lub-subdomeny).<br>
7. [W razie potrzeby odtwórz adres e-mail](https://docs.ovh.com/pl/emails/przewodnik_na_temat_zakladania_adresu_e-mail/) i [zaimportuj wiadomości](https://docs.ovh.com/pl/emails/przenoszenie-kont-e-mail/).

### Sprawdź, czy Twój hosting jest kompatybilny z mniejszą ofertą <a name="checks"></a>

#### Liczba stron

Oferta [Kimsufi Web](https://www.ovhcloud.com/pl/web-hosting/old-web-hosting-offers/) nie pozwala na posiadanie więcej niż jednej domeny na [MultiSite](https://docs.ovh.com/pl/hosting/konfiguracja-multisite-na-hostingu/) na Twoim hostingu.

Przed przejściem z oferty [Perso](https://www.ovhcloud.com/pl/web-hosting/personal-offer/) na ofertę [Kimsufi Web](https://www.ovhcloud.com/pl/web-hosting/old-web-hosting-offers/) sprawdź, czy hosting zawiera tylko jedną stronę.

#### Bazy danych Start SQL

Przed przejściem na niższą ofertę upewnij się, że nowa oferta zawiera wystarczającą ilość [baz danych](https://www.ovhcloud.com/pl/web-hosting/options/start-sql/). Sprawdź również, czy są wystarczająco duże.

Jeśli tak się nie stanie, usuń nieużywane bazy danych i zmniejsz w razie potrzeby ilość danych, które zawierają. Ilość ta nie może przekroczyć maksymalnego rozmiaru baz danych w nowej ofercie (w przypadku prośby o pomoc w zakresie wykonywanych operacji, skontaktuj się z [partnerami OVHcloud](https://partner.ovhcloud.com/pl/)).

Po usunięciu danych z baz danych pamiętaj o przeliczeniu rozmiaru używanego w zakładce `Bazy danych`{.action} w części `Hosting`{.action} w Panelu klienta. Kliknij przycisk `...`{.action} po prawej stronie wybranej bazy, a następnie na `Przelicz rozmiar bazy`{.action}.

![quota](images/quota.png){.thumbnail}

#### CloudDB

Jeśli korzystasz z oferty [CloudDB](https://docs.ovh.com/pl/hosting/pierwsze-kroki-z-clouddb/#wlaczenie-prywatnego-clouddb-zawartego-w-ofercie-hostingu) zawartej w ofercie hostingu [Performance](https://www.ovhcloud.com/pl/web-hosting/performance-offer/) i chcesz przejść na ofertę hostingu [Pro](https://www.ovhcloud.com/pl/web-hosting/professional-offer/), przejdź do części 'Hosting{.action} w Twoim panelu klienta.<br>
Kliknij przycisk `...`{.action} w części `Prywatna baza danych`{.action} a następnie na `Odłącz`{.action}.

![clouddb](images/clouddb.png){.thumbnail}

Czynność ta pozwoli Ci na zamówienie usługi CloudDB niezależnej od Twojego abonamentu *Performance*. Dane przechowywane na serwerze zostaną zachowane.

Jeśli nie chcesz przechowywać tych danych, możesz również usunąć prywatny serwer SQL przed przejściem na ofertę *Pro*: 

1. Przechowuj swoje dane zgodnie z instrukcjami zawartymi w tym [przewodniku](https://docs.ovh.com/pl/hosting/kopia-zapasowa-eksportowa-bazy-danych/).<br>
2. Usuń serwer CloudDB z [Panelu klienta OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.pl/&ovhSubsidiary=pl). W tym celu w prawym górnym rogu kliknij Twoją nazwę, a następnie `Zarządzanie usługami`{.action}. Następnie kliknij przycisk `...`{.action} po prawej stronie odpowiedniej linii, po czym kliknij `Usuń serwer Private SQL`{.action}.

#### Przestrzeni FTP

Przed przejściem na niższą ofertę upewnij się, że nowa oferta jest wystarczająco dużo [przestrzeni dyskowej FTP](https://docs.ovh.com/pl/hosting/logowanie-przestrzen-dyskowa-ftp-hosting-web/), aby import plików z obecnego hostingu był możliwy.

Limit używany na Twoim hostingu FTP jest widoczny w części `Hosting`{.action} w Twoim Panelu klienta. Kliknij kartę `Informacje ogólne`{.action}, otrzymasz limit `Przestrzeń dyskowa`.

![ftp](images/ftp.png){.thumbnail}

#### Adresy e-mail

Sprawdź również, czy nowa oferta zawiera wystarczającą liczbę dostępnych adresów e-mail. W przeciwnym razie usuń zbędne adresy po ich wykonaniu [kopia zapasowa](https://docs.ovh.com/pl/emails/przenoszenie-kont-e-mail/).

Jeśli chcesz zachować tę samą liczbę kont e-mail, zanim przejdziesz na niższą ofertę hostingu, możesz również zamówić nową usługę poczty elektronicznej **MX Plan**. W części `E-maile`{.action} w Panelu klienta kliknij odpowiednią ofertę, a następnie przycisk `...`{.action} po prawej stronie `Usługa`. Na koniec kliknij polecenie `Zmień ofertę`{.action}.

![mxplan](images/mxplan.png){.thumbnail}

#### Listów mailingowych

Funkcja [Listy mailingowe](https://docs.ovh.com/pl/emails/hosting_www_listy_mailingowe/) jest opcjonalna dla hostingu [Perso](https://www.ovhcloud.com/pl/web-hosting/personal-offer/) i [Kimsufi Web](https://www.ovhcloud.com/pl/web-hosting/old-web-hosting-offers/).

Aby zmienić dotychczasowy hosting na ofertę [Perso](https://www.ovhcloud.com/pl/web-hosting/personal-offer/), należy najpierw usunąć listy mailingowe lub zamówić ofertę pocztową zawierającą tę funkcję (**MX Plan 100** lub **MX Plan Full**) w [Panelu klienta OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.pl/&ovhSubsidiary=pl).

W części `E-maile`{.action} w Panelu klienta wybierz odpowiednią ofertę, a następnie kliknij `...`{.action} po prawej stronie `Usługa`{.action}. Na koniec kliknij polecenie `Zmień ofertę`{.action}.

## Sprawdź również <a name="gofurther"></a>

[Sprawdź statystyki i logi strony zainstalowanej na hostingu](https://docs.ovh.com/pl/hosting/hosting_statystyki_i_logi_strony/)

[Optymalizacja wydajności strony](https://docs.ovh.com/pl/hosting/hosting_www_przewodnik_dotyczacy_optymalizacji_wydajnosci_strony/)

Skontaktuj się z [partnerami OVHcloud](https://partner.ovhcloud.com/pl/), jeśli szukasz zaawansowanych rozwiązań (indeksowanie, rozwój, etc).

Jeśli chcesz otrzymywać wsparcie w zakresie konfiguracji i użytkowania Twoich rozwiązań OVHcloud, sprawdź naszą [ofertę pomocy](https://www.ovhcloud.com/pl/support-levels/).

Dołącz do społeczności naszych użytkowników na stronie <https://community.ovh.com/en/>.
