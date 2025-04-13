## Quick start

```shell
python3 -m venv venv
source ./venv/bin/activate
pip install flask
pip install opentelemetry-distro
pip install opentelemetry-exporter-otlp
opentelemetry-bootstrap -a install

export OTEL_PYTHON_LOGGING_AUTO_INSTRUMENTATION_ENABLED=true
opentelemetry-instrument \
    --traces_exporter otlp \
    --metrics_exporter otlp \
    --logs_exporter otlp \
    --service_name dice-server \
    flask run -p 8081
```

In the above example, you can also use `console` instead of `otlp` as exporter.

## OTEL in Python

Tutorial for getting started with [OTEL in Python](https://opentelemetry.io/docs/languages/python/):
```sh
pip install opentelemetry-api
pip install opentelemetry-sdk
pip install opentelemetry-exporter-{exporter}
pip install opentelemetry-instrumentation-{instrumentation}
```

where instrumentation exists for these [frameworks](https://github.com/open-telemetry/opentelemetry-python-contrib/tree/main/instrumentation) and these [exporters](https://github.com/open-telemetry/opentelemetry-python/tree/main/exporter) can be used to store logs, metrics and traces.

```shell
pip install opentelemetry-distro
opentelemetry-bootstrap -a install
```
install the instrumentation for the frameworks used in the project.

```shell
export OTEL_PYTHON_LOGGING_AUTO_INSTRUMENTATION_ENABLED=true
opentelemetry-instrument \
    --traces_exporter otlp \
    --metrics_exporter otlp \
    --logs_exporter otlp \
    --service_name dice-server \
    flask run -p 8081
```
starts a Python program (here flask server) with instrumentation turned on. Please note that Flask must be installed beforehand using this command:

```shell
pip install flask
```
