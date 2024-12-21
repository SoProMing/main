# Variablen
PROJECT_NAME = hello-world-bootstrap
DOCKER_IMAGE = $(PROJECT_NAME):latest
CONTAINER_NAME = $(PROJECT_NAME)-container
PORT = 8080

# Standardziel
.PHONY: all
all: build run

# Docker-Image bauen
.PHONY: build
build:
	docker build -t $(DOCKER_IMAGE) .

# Container starten
.PHONY: run
run:
	docker run -d --name $(CONTAINER_NAME) -p $(PORT):80 $(DOCKER_IMAGE)

# Logs des Containers anzeigen
.PHONY: logs
logs:
	docker logs -f $(CONTAINER_NAME)

# Container stoppen
.PHONY: stop
stop:
	docker stop $(CONTAINER_NAME) || true
	docker rm $(CONTAINER_NAME) || true

# Docker-Image und ungenutzte Ressourcen entfernen
.PHONY: clean
clean: stop
	docker rmi $(DOCKER_IMAGE) || true

# System bereinigen (alle gestoppten Container und ungenutzten Images entfernen)
.PHONY: prune
prune:
	docker system prune -f

# Hilfe anzeigen
.PHONY: help
help:
	@echo "Verfügbare Befehle:"
	@echo "  make build     - Docker-Image bauen"
	@echo "  make run       - Container starten"
	@echo "  make logs      - Logs des Containers anzeigen"
	@echo "  make stop      - Container stoppen und entfernen"
	@echo "  make clean     - Docker-Image entfernen"
	@echo "  make prune     - System bereinigen (gestoppte Container, ungenutzte Images)"
	@echo "  make help      - Diese Hilfe anzeigen"
