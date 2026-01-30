# Spring Boot Hello World -sovellus

Tämä projekti sisältää Spring Boot -pohjaisen Hello World -sovelluksen, joka on suunniteltu konttikehitykseen ja Docker-imagen rakentamiseen.

## Työvaiheet

Seuraavat vaiheet vaaditaan Spring Boot Hello World -sovelluksen luomiseksi konttikehityksellä ja Docker-tuella:

1. **Spring Boot -projektin luonti**
   - Käytä Spring Initializr -työkalua (https://start.spring.io) tai luo projekti manuaalisesti
   - Valitse Java-kieli, Maven tai Gradle build-työkalu
   - Lisää Spring Web -riippuvuus

2. **Hello World -kontrollerin luonti**
   - Luo `HelloController` -luokka `src/main/java/com/example/demo` -kansioon
   - Lisää `@RestController` -annotaatio
   - Luo metodi, joka palauttaa "Hello World" -viestin GET-pyynnölle

3. **Sovelluksen testaus paikallisesti**
   - Aja sovellus `mvn spring-boot:run` tai `gradle bootRun` -komennolla
   - Tarkista että sovellus toimii osoitteessa http://localhost:8080/hello

4. **Konttikehityksen määrittäminen**
   - Luo `.devcontainer/devcontainer.json` -tiedosto projektin juureen
   - Määritä Java-kehitysympäristö kontissa (käytä Microsoftin devcontainers/java -imagea)
   - Lisää tarvittavat extensions (esim. Java Extension Pack)

5. **Dockerfile:n luonti**
   - Luo `Dockerfile` projektin juureen
   - Käytä multi-stage build:a: yksi stage builaamiseen, toinen runtime-imagen luomiseen
   - Käytä OpenJDK:n slim-imagea runtime:ssa

6. **Docker Compose -konfiguraatio kehitystä varten**
   - Luo `docker-compose.yml` -tiedosto
   - Määritä palvelu sovellukselle
   - Lisää volume-mäppäys lähdekoodille hot-reloadia varten (jos käytetään)

7. **Docker-imagen rakentaminen**
   - Rakenna image komennolla `docker build -t spring-hello .`
   - Aja kontti komennolla `docker run -p 8080:8080 spring-hello`
   - Testaa että sovellus toimii kontissa

8. **CI/CD -putken määrittäminen (valinnainen)**
   - Luo GitHub Actions -workflow Docker-imagen automaattiseen rakentamiseen
   - Pushaa image Docker Hubiin tai Azure Container Registryyn

## Käynnistäminen

- Paikallinen ajo: `./mvnw spring-boot:run`
- Kontissa kehitys: Avaa projekti VS Code:ssa dev container -tilassa
- Docker: `docker-compose up` (kehitys) tai `docker run spring-hello` (tuotanto)