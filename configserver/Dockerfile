COPY gradle gradle
COPY build.gradle setting.gradle ./

RUN chmod +x gradlew
RUN ./gradlew dependencies

COPY src src
RUN ./gradlew bootJar

# runtime stage (jre) - jar
FROM eclipse-temurin:17-jdk-alpine
WORKDIR /app

COPY --from=builder /app/build/libs/*.jar app.jar

ENTRYPOINT ["java", "-jar", "app.jar"]