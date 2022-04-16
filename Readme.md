## Дипломный проект профессии «Тестировщик ПО»

### Документация
1. [План автоматизации тестирования](https://github.com/TanyaLukina/Diploma/blob/main/documentation/Plan.md)
2. [Отчет по итогам тестирования](https://github.com/TanyaLukina/Diploma/blob/main/documentation/Report.md)
3. [Отчет по итогам автоматизации тестирования](https://github.com/TanyaLukina/Diploma/blob/main/documentation/Summary.md)

### Необходимое окружение:
* установленный Node.js
* установленный Docker
* установленная IntelliJ IDEA
* Java 11
* браузер

### Процедура установки, настройки и запуска ПО

#### Перед запуском авто-тестов, необходимо:
* Уcтановить программы "Intellij IDEA Ultimate", "Docker", "Docker-compose", для работы с контейнерами "MySQL",
  "PostgreSQL", "Node-app"

* Проверить наличие установленных версий библиотек в файле "build.gradle",
  необходимых для запуска авто-тестов

* Запустить контейнеры "MySQL", "PostgreSQL", "Node-app" в "Docker-compose"

* Запустить SUT для "MySQL" или "PostgreSQL"

1. Клонируйте репозиторий https://github.com/TanyaLukina/Diploma.git.
2. Открыть проект в IDE
* Открыть проект с помощью IntelliJ IDEA

Для запуска контейнеров "MySQL", "PostgreSQL", "Node-app",
внутри IntelliJ IDEA запустить терминал и выполнить команду docker-compose up -d --force-recreate

Проверить запуск приложения открыв в браузере страницу http://localhost:8080/

3. Запустить SUT командой
* Для MySQL: ```java -Dspring.datasource.url=jdbc:mysql://localhost:3306/app -jar artifacts/aqa-shop.jar```
* Для PostgreSQL: ```java -Dspring.datasource.url=jdbc:postgresql://localhost:5432/app -jar artifacts/aqa-shop.jar```
4. Запустить тесты командой:
* Для MySQL: ```./gradlew clean test -Ddb.url=jdbc:mysql://localhost:3306/app -Dlogin=app -Dpassword=pass -Dapp.url=http://localhost:8080```
* Для PostgreSQL: ```./gradlew clean test -Ddb.url=jdbc:postgresql://localhost:5432/postgres -Dlogin=app -Dpassword=pass -Dapp.url=http://localhost:8080```
5. Для запуска и просмотра отчета "Allure" по результатам тестирования выполнить команду:
   ```./gradlew allureReport```, затем ```./gradlew allureServe```
  

