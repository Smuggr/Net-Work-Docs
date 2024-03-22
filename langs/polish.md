<!-- markdownlint-disable MD033 -->

# Spis Treści <!-- omit in toc -->

- [1. Wstęp](#1-wstęp)
- [2. Cele i założenia](#2-cele-i-założenia)
- [3. Przebieg pracy](#3-przebieg-pracy)
- [4. Część informatyczna](#4-część-informatyczna)
- [4.1. Backend - strona serwerowa](#41-backend---strona-serwerowa)
- [4.2. Frontend - strona użytkownika](#42-frontend---strona-użytkownika)
- [4.3. Wygląd aplikacji](#43-wygląd-aplikacji)
- [4.4. Prototypowy wygląd urządzenia](#44-prototypowy-wygląd-urządzenia)
- [4.5. Finalny wygląd urządzenia](#45-finalny-wygląd-urządzenia)

## 1. Wstęp

## 2. Cele i założenia

## 3. Przebieg pracy

## 4. Część informatyczna

Jedną z najważniejszych zalet **Net-Worku** jest jego infrastruktura informatyczna. W celu zbudowania funkcjonującego systemu wykorzystane zostały najnowsze frameworki oraz języki programowania. Samo oprogramowanie zostało napisane w kilku językach, strona serwerowa została napisana w języku ***Go***, natomiast strona użytkownika została napisana w języku ***JavaScript*** wraz z frameworkiem ***Vue.js*** i komponentami w najnowszym standardzie material, ***Vuetify***, do automatyzacji kompilacji i uruchamiania oprogramowania został wykorzystany ***Make*** oraz ***Bash***.

Komunikacja w oprogramowaniu opiera się na protokołach ***Message Queuing Telemetry Transport*** **(MQTT) w wersji 3.11** oraz ***Represantional State Transfer*** **(REST)**, oba są przydatne w różnych kontekstach komunikacyjnych. Protokół **MQTT** został wykorzystany ze względu na jego lekkość i efektywność, co czyni go idealnym rozwiązaniem dla aplikacji związanych z **Internetem Rzeczy (IoT)** oraz systemów o niskich wymaganiach zasobowych. Dzięki modelowi publikacji i subskrypcji **(PUBSUB)**, **MQTT** umożliwia efektywną wymianę danych między urządzeniami w czasie rzeczywistym. Z kolei architektura **REST** stanowi uniwersalny interfejs komunikacyjny, który pozwala na zarządzanie zasobami w sposób zrozumiały dla ludzi oraz maszyn. Wykorzystanie tych protokołów pozwala na elastyczne i skalowalne budowanie aplikacji, które są w stanie efektywnie komunikować się z różnymi systemami i urządzeniami.

<div class="page"/>

## 4.1. Backend - strona serwerowa

W celu zbudowania bezpiecznego oraz wydajnego serwera **REST** i brokera **MQTT**, wykorzystane zostały następujące pakiety języka **Go**:

- ***GIN* 1.9.1**
- ***COMQTT* 2.5.4**

Technologie te pozwalają na bezpośrednią integracje obu protokołów komunikacyjnych w jednej bazie kodu. W przypadku pakietu **GIN** dodatkowe możliwości wprowadzania **middleware'ów** (programów pośrednich między żądaniem a właściwą częścią aplikacji) pozwoliły na proste wbudowanie dodatkowych zabezpieczeń dostępu do serwera **REST**, takie jak:

- **Ograniczenie szybkości zapytań (Rate Limiting)** które jak sama nazwa wskazuje zmniejsza częstotliwość odpowiedzi na  zapytania pochodzących od jednego klienta w określonym przedziale czasowym, co może pomóc w zapobieganiu nadmiernemu obciążeniu serwera.

- **Tokeny JWT (Json Web Token)** które stanowią sposób na uwierzytelnianie i autoryzację użytkowników w serwerze **REST**. **JWT** są tokenami zawierającymi informacje o użytkowniku oraz jego uprawnieniach, podpisane przez serwer, co pozwala na bezpieczne przesyłanie tych danych między klientem a serwerem. Dzięki nim można łatwo kontrolować dostęp do zasobów oraz identyfikować użytkowników w systemie.

Natomiast pakiet **COMQTT** zapewnia nie tylko implementację protokołu **MQTT**, ale również możliwość bezpośredniego konfigurowania, monitorowania oraz ingerencji w broker **MQTT**. Dzięki temu można skonfigurować różne parametry działania brokera w sposób programowy, takie jak na przykład maksymalny rozmiar wiadomości czy maksymalna liczba połączonych klientów, a także monitorować jego wydajność i obciążenie. Ważną kwestią jest też możliwość uwierzetelniania klientów którzy próbują połączyć się z brokerem, realizowane jest to poprzez pozyskiwanie danych na temat klientów z bazy danych oraz porównywanie danych z którymi dany klient próbuje się połączyć. W wyniku tego można zapewnić bezpieczne i kontrolowane połączenia między klientami a brokerem **MQTT**.

Dzięki wykorzystaniu tych pakietów możliwe było zrealizowanie nie tylko bezpiecznego, ale także wydajnego serwera **REST** oraz brokera **MQTT**, który spełnia wymagania zarówno pod kątem funkcjonalności, jak i wydajności.

<div class="page"/>

Dodatkowe narzędzia i paczki użyte przy tworzeniu strony serwerowej:

- Curl
- Postman
- MQTT Explorer
- PostgreSQL Explorer
- [github.com/charmbracelet/lipgloss](https://github.com/charmbracelet/lipgloss)
- [github.com/didip/tollbooth](https://github.com/didip/tollbooth)
- [github.com/gin-contrib/cors](https://github.com/gin-contrib/cors)
- [github.com/gin-gonic/gin](https://github.com/gin-gonic/gin)
- [github.com/golang-jwt/jwt/v5](https://github.com/golang-jwt/jwt)
- [github.com/hashicorp/mdns](https://github.com/hashicorp/mdns)
- [github.com/joho/godotenv](https://github.com/joho/godotenv)
- [github.com/spf13/viper](https://github.com/spf13/viper)
- [golang.org/x/crypto](https://pkg.go.dev/golang.org/x/crypto)
- [gorm.io/gorm](https://gorm.io/gorm)

<!-- Dodać tutaj dokumentacje API ze Swaggera -->

<div class="page"/>

## 4.2. Frontend - strona użytkownika

Aplikacja internetowa w całości oparta została na frameworku ***Vue.js* 3**. Dzięki zastosowaniu tej technologii aplikacja pod względem wydajnościowym wyraźnie wyprzedza inne projekty, które z domysłu oparte są o statyczne strony internetowe.

Aplikacja internetowa oparta jest na nowoczesnych technologiach takich jak framework ***Vue.js* 3**, ***Vite* 5.2.2** jako narzędzie do budowania projektu w jedna spójną całość gotową do uruchomienia, oraz ***Vuetify***, biblioteki komponentów **Material Design**. W połączeniu z biblioteką ***Pinia* 2.1.7** do zarządzania stanem aplikacji oraz ***Axios* 1.6.7** do komunikacji z serwerem, te technologie pozwoliły nam na stworzenie wyjątkowo wydajnej aplikacji jednostronowej **SPA (Single Page Application)**. **Vue.js** umożliwia dynamiczne routowanie po stronie użytkownika, eliminując jednocześnie konieczność przeładowywania całej strony podczas przejść miedzy różnymi widokami, co poprawia doświadczenie i komfort użytkownika. **Pinia** wraz z **Axios** zapewniają bezpieczną i wydajną komunikację z serwerem, a wykorzystanie komponentów z **Vuetify** ułatwiło stworzenie interfejsu użytkownika zgodnego ze standardem **Material Design**. Dzięki temu, architektura kodu aplikacji staje się bardziej przejrzysta i skalowalna, co znacznie ułatwia rozwój aplikacji o nowe funkcjonalności.

<div class="container">
  <div class="content-compact">
    <h3>Przykładowy komponent</h3>
    <img src="../static/frontend_sample_component.png" alt="Komponent">
  </div>
</div>

<div class="page"></div>

<div class="container">
  <div class="content">
    <h3>Struktura plików frontendu</h3>
    <img src="../static/frontend_structure.png" alt="Struktura">
  </div>
</div>

<div class="page"/>

## 4.3. Wygląd aplikacji

<div class="container">
  <div class="content">
    <h3>Strona główna przed zalogowaniem</h3>
    <img src="../static/frontend_not_logged_in.png" alt="Nie zalogowany">
  </div>
</div>

<div class="container">
  <div class="content">
    <h3>Okno logowania</h3>
    <img src="../static/frontend_login_screen.png" alt="Okno logowania">
  </div>
</div>

<div class="page"/>

<div class="container">
  <div class="content">
    <h3>Demonstracja weryfikacji danych</h3>
    <img src="../static/frontend_login_screen_validation.png" alt="Weryfikacja danych">
  </div>
</div>

<div class="container">
  <div class="content">
    <h3>Demonstracja weryfikacji danych</h3>
    <img src="../static/frontend_login_screen_validation.png" alt="Demonstracja weryfikacji danych">
  </div>
</div>

<div class="container">
  <div class="content">
    <h3>Strona główna po zalogowaniu</h3>
    <img src="../static/frontend_home_page.png" alt="Strona główna">
  </div>
</div>

<div class="page"/>

<div class="container">
  <div class="content">
    <h3>Profil zalogowanego użytkownika</h3>
    <img src="../static/frontend_login_screen.png" alt="Profil użytkownika">
  </div>
</div>

<div class="container">
  <div class="content">
    <h3>Strona "O stronie"</h3>
    <img src="../static/frontend_about_page.png" alt="O stronie">
  </div>
</div>

<div class="page"/>

<div class="container">
  <div class="content">
    <h3>Panel z urządzeniami</h3>
    <img src="../static/frontend_dashboard_page_devices.png" alt="Urządzenia">
  </div>
</div>

<div class="page"/>

## 4.4. Prototypowy wygląd urządzenia

<div class="container">
  <div class="content">
    <h3>Prototyp PCB</h3>
    <img src="../static/prototype_top.jpg" alt="Prototyp PCB">
  </div>
</div>

<div class="container-left">
  <div class="content">
    <h3>1. Przekaźnik mechaniczy wraz z układem</h3>
    <h3>2. Konwerter poziomów logicznych</h3>
    <h3>3. Zasilanie 5V oraz 3.3V</h3>
    <h3>4. Linie I2C 5V oraz 3.3V</h3>
    <h3>5. Złącza śrubowe</h3>
  </div>
</div>

<div class="page"/>

<div class="container">
  <div class="content">
    <img src="../static/prototype_bottom.jpg" alt="Prototyp PCB">
  </div>
</div>

<div class="page"/>

<div class="container">
  <div class="content">
    <h3>Prototypowe złożenie niektórych elementów</h3>
    <img src="../static/schedule_keepr_prototype_assembly.jpg" alt="Prototypowe złożenie">
  </div>
</div>

<div class="container-left">
  <div class="content">
    <h3>1. Prototyp PCB</h3>
    <h3>2. Raspberry Pi Zero W 2</h3>
    <h3>3. Wyświetlacz LCD</h3>
  </div>
</div>

<div class="page"/>

## 4.5. Finalny wygląd urządzenia

<div class="container">
  <div class="content-compact">
    <h3>Wyprodukowane PCB</h3>
    <img src="../static/pcb_top.jpg" alt="Góra PCB">
  </div>
</div>

W gotowym projekcie zamiast płytki stykowej lub perforowanej - przydatnych w pierwszych fazach budowy i testowania - została stworzona dedykowana płytka PCB, którą stosuje się praktycznie we wszystkich profesjonalnych urządzeniach elektronicznych. Wynika to między innymi z tego że płytki PCB świetnie nadają się do tworzenia dowolnych układów elektronicznych o dowolnej złożoności.

<div class="page"/>

<div class="container">
  <div class="content-compact">
    <h3>Układ PCB</h3>
    <img src="../static/pcb_layout.png" alt="Układ PCB">
  </div>
</div>

<div class="container">
  <div class="content-expanded">
    <h3>Schemat PCB</h3>
    <img src="../static/pcb_schematic.png" alt="Schemat PCB">
  </div>
</div>
