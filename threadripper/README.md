# Some steps to remember

1. Define environment variable `OSPROFILER_HMAC_KEY` with the value of
`osprofiler_secret` in `current/password.yml`. This has to be done before
defining the test environment in Rally (Rally venv).

2. Define the test environment in Rally:

```
rally deployment create --fromenv --name=enosexperiment
```

3. To run Rally test (Rally venv):

```
rally task start samples/tasks/scenarios/neutron/create-and-bind-ports.yaml
```

4. To get Rally report (Rally venv):

```
rally task report dd363d4f-acf2-4bac-8641-59eec7c9ff07 --out ~/rally-reports/iterations-80-concurrency-20.html
```

5. To get osprofiler report (Enos experiment venv), provide connection string
   pointing to port 9200 in controller node in following command:

```
osprofiler trace show --connection-string elasticsearch://192.168.42.245:9200 28838f46-894f-4fbd-a8e4-e1c71225cf7b --html --out ~/rally-reports/iterations-80-concurrency-20-osprofiler-iteration-37.html
```

6. To monitor deployment with Grafana, point browser to poprt 3000 of
   controller node:

```
http://192.168.42.245:3000
```
