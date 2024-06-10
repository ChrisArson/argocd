
# Wdrożenie i aktualizacja przykładowej aplikacji w K8s z wykorzystaniem GitHub Actions oraz ArgoCD – architektura i konfiguracja systemu oraz przykład użycia.
## Arkadiusz Szumny

Do wykonania zadania jako szkielet wykorzystałem prostą aplikację zbudowaną na K8S + HELM -> [źródło](https://github.com/devopsjourney1/argo-examples/tree/master)


Składa się ona z pliku zawierającego metadane dla chartu Helm ``Chart.yaml``, pliku ``values.yaml`` z domyślnymi ustawieniami konfiguracyjnymi oraz dwoma plikami konfiguracyjnymi z podziałem na środowisko dev i prod (``values-dev.yaml`` i ``values-prod.yaml``).

Ustawione Github Actions wywołują akcje stworzenia nowego obrazu na podstawie ``Dockerfile`` i wrzucenia do [Docker Hub](https://hub.docker.com/repository/docker/chrisarson/myapp_argo/general) przy każdej zmianie w repozytorium. ArgoCD ustawione na automatyczną synchronizację po wykryciu zmian w repozytorium korzystajac z nowego obrazu aktualizuje pody.

