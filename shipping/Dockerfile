#
# Build Stage
#
FROM debian:10-slim AS build

# Install only necessary packages and clean up
RUN apt-get update && \
    apt-get install -y --no-install-recommends maven && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

WORKDIR /opt/shipping

# Copy pom.xml first (better caching)
COPY pom.xml .
RUN mvn dependency:go-offline

# Copy source and build
COPY src ./src
RUN mvn clean package -DskipTests

#
# Runtime Stage
#
FROM openjdk:8-jre-slim  # Changed to JRE (smaller image)

EXPOSE 8080

WORKDIR /opt/shipping

# Set environment variables
ENV CART_ENDPOINT=cart:8080 \
    DB_HOST=mysql

# Copy jar from build stage
COPY --from=build /opt/shipping/target/shipping-1.0.jar shipping.jar

# Add non-root user for security
RUN groupadd -r shipping && \
    useradd -r -g shipping shipping && \
    chown -R shipping:shipping /opt/shipping

USER shipping

# Health check
HEALTHCHECK --interval=30s --timeout=3s --start-period=5s --retries=3 \
    CMD curl -f http://localhost:8080/health || exit 1

# Run the application
CMD ["java", "-Xmn256m", "-Xmx768m", "-jar", "shipping.jar"]