# Spis Treści

## 1. Wstęp

## 2. Cele i założenia

## 3. Przebieg pracy

## 4. Część Informatyczna

Jedną z najważniejszych zalet **Net-Worku** jest jego infrastruktura informatyczna. W celu zbudowania funkcjonującego systemu wykorzystane zostały najnowsze frameworki oraz języki programowania. Samo oprogramowanie zostało napisane w kilku językach, strona serwerowa została napisana w języku ***Go***, natomiast strona użytkownika została napisana w języku ***JavaScript*** wraz z frameworkiem ***Vue.js*** i komponentami w najnowszym standardzie material ***Vuetify***, do automatyzacji kompilacji i uruchamiania oprogramowania został wykorzystany ***Make*** oraz ***Bash***.

Komunikacja w oprogramowaniu opiera się na protokołach ***Message Queuing Telemetry Transport*** **(MQTT) w wersji 3.11** oraz ***Represantional State Transfer*** **(REST)**, oba są przydatne w różnych kontekstach komunikacyjnych. Protokół MQTT został wykorzystany ze względu na jego lekkość i efektywność, co czyni go idealnym rozwiązaniem dla aplikacji związanych z **Internetem Rzeczy (IoT)** oraz systemów o niskich wymaganiach zasobowych. Dzięki modelowi publikacji i subskrypcji **(PUBSUB)**, MQTT umożliwia efektywną wymianę danych między urządzeniami w czasie rzeczywistym. Z kolei architektura REST stanowi uniwersalny interfejs komunikacyjny, który pozwala na zarządzanie zasobami w sposób zrozumiały dla ludzi oraz maszyn. Wykorzystanie tych protokołów pozwala na elastyczne i skalowalne budowanie aplikacji, które są w stanie efektywnie komunikować się z różnymi systemami i urządzeniami.

### 4.1 Backend - strona serwerowa

W celu zbudowania bezpiecznego oraz wydajnego serwera REST i brokera MQTT, wykorzystane zostały następujące pakiety języka Go:

- [GIN](https://github.com/gin-gonic/gin/releases/tag/v1.9.1) wersja 1.9.1
- [COMQTT](https://github.com/wind-c/comqtt/releases/tag/v2.5.4) wersja 2.5.4

Technologie te pozwalają na bezpośrednią integracje obu protokołów komunikacyjnych w jednej bazie kodu. W przypadku pakietu GIN dodatkowe możliwości wprowadzania **middleware'ów** (programów pośrednich między żądaniem a właściwą częścią aplikacji) pozwoliły na proste wbudowanie dodatkowych zabezpieczeń dostępu do serwera REST, takie jak:

- **ograniczenie szybkości zapytań** (Rate-Limiting) które jak sama nazwa wskazuje zmniejsza częstotliwość odpowiedzi na  zapytania pochodzących od jednego klienta w określonym przedziale czasowym, co może pomóc w zapobieganiu nadmiernemu obciążeniu serwera.


Ponadto, GIN oferuje obsługę middleware'ów, co umożliwia łatwe dodawanie dodatkowej logiki do przetwarzania żądań HTTP, takiej jak logowanie, autoryzacja czy walidacja danych wejściowych.

Natomiast pakiet COMQTT zapewnia nie tylko implementację protokołu MQTT, ale również możliwość konfiguracji oraz monitorowania brokera MQTT. Dzięki temu można skonfigurować różne parametry działania brokera, takie jak np. maksymalny rozmiar wiadomości czy maksymalna liczba klientów, a także monitorować jego wydajność i obciążenie.

Dzięki wykorzystaniu tych pakietów możliwe było zbudowanie nie tylko bezpiecznego, ale także wydajnego serwera REST oraz brokera MQTT, który spełnia wymagania zarówno pod kątem funkcjonalności, jak i wydajnościowej.

oraz **Json Web Token** (JWT)
