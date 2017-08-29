
# Running the integrations tests 

To run the integration tests use the following steps:

## Deploy the database

```
oc new-app -e POSTGRESQL_USER=luke -ePOSTGRESQL_PASSWORD=secret -ePOSTGRESQL_DATABASE=my_data openshift/postgresql-92-centos7 --name=my-database
```

## Deploy the booster

```
mvn -Popenshift fabric8:deploy
```

### Run the integration tests

```
mvn -Popenshift-it verify
```

### Undeploy the booster

```
mvn -Popenshift fabric8:undeploy
```

### Remove the database

```
oc delete dc my-database
oc delete svc my-database
```
