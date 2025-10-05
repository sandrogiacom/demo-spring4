# Demo Spring Boot 4, Java 25, Kotlin com Gradle

Um projeto de exemplo usando Spring Boot 4 (milestone) com Kotlin e Gradle. Ideal para quem está começando e quer ver como iniciar, compilar, executar e testar um serviço simples.

O aplicativo sobe uma aplicação web básica (sem endpoints de domínio), mas já vem com o Spring Boot Actuator habilitado para verificação de saúde (healthcheck).


## O que este projeto faz
- Cria uma aplicação Spring Boot 4 (4.0.0-M3) em Kotlin.
- Disponibiliza o endpoint de saúde do Actuator em `GET /actuator/health`.
- Estrutura mínima para você adicionar seus próprios controladores, serviços e repositórios (JPA já adicionado nas dependências).


## Pré-requisitos
Você pode construir e executar tudo apenas com o Gradle Wrapper do projeto (sem instalar o Gradle). Sobre o JDK:

- Java Development Kit (JDK): o projeto está configurado para usar
  - Toolchain Java 25 (build.gradle.kts: `JavaLanguageVersion.of(25)`)
  - Kotlin direcionado para JVM 24
- Gradle Toolchains normalmente baixa e usa automaticamente o JDK apropriado. Se sua máquina não permitir o download automático, instale um JDK recente que ofereça suporte à JVM 24/25 (por exemplo, JDK 25 EA) e configure o JAVA_HOME.

Outros opcionais:
- Git (para clonar o repositório)
- IDE recomendada: IntelliJ IDEA (Community ou Ultimate) com suporte a Kotlin e Spring
- Docker (opcional – não é necessário para rodar este projeto; o compose.yaml ainda não define serviços)


## Como clonar
```
# via SSH
git clone git@github.com:sandrogiacom/demo-spring4.git
cd demo-spring4

# ou via HTTPS
# git clone https://github.com/sandrogiacom/demo-spring4.git
# cd demo-spring4
```


## Como compilar (build)
Use o Gradle Wrapper incluso no projeto:

- Linux/macOS
```
./gradlew clean build
```

- Windows (PowerShell ou CMD)
```
gradlew clean build
```

Os artefatos serão gerados em `build/libs/`. O JAR final deve ter o nome semelhante a `demo-spring4-0.0.1-SNAPSHOT.jar`.


## Como executar a aplicação
- Executar direto pelo Gradle (recomendado para desenvolvimento):
  - Linux/macOS: `./gradlew bootRun`
  - Windows: `gradlew bootRun`

- Executar o JAR empacotado (após o build):
```
java -jar build/libs/demo-spring4-0.0.1-SNAPSHOT.jar
```

A aplicação inicia por padrão em `http://localhost:8080`.


## Endpoints úteis
- Healthcheck: `GET http://localhost:8080/actuator/health`
  - Resposta esperada (exemplo): `{"status":"UP"}`


## Como rodar os testes
```
# Linux/macOS
./gradlew test

# Windows
gradlew test
```


## Estrutura do projeto (resumo)
- `src/main/kotlin/.../DemoSpring4Application.kt` — classe principal do Spring Boot
- `src/test/kotlin/.../DemoSpring4ApplicationTests.kt` — testes de exemplo
- `build.gradle.kts` — build script Kotlin/Gradle com dependências (Web MVC, JPA, Actuator)
- `application.properties` — configurações da aplicação


## Problemas comuns (Troubleshooting)
- Erro relacionado a versão de Java/JVM:
  - Certifique-se de que o Gradle Toolchains está habilitado (padrão) ou instale um JDK compatível (JDK 25). Verifique `java -version` e `./gradlew -v`.
- Porta 8080 em uso:
  - Pare o processo que está usando a porta ou rode com outra porta: `./gradlew bootRun --args='--server.port=8081'`.


## Licença
Este é um projeto de demonstração. Ajuste a licença conforme necessário para seu uso.