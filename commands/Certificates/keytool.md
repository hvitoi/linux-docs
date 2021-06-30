# keytool

```shell
# Add cert to default keystore
keytool \
  -importcert \
  -noprompt \
  -trustcacerts \
  -keystore "$JAVA_HOME/jre/lib/security/cacerts" \
  -storepass "changeit" \
  -file "~/cacorp.crt" \
  -alias "cacorp"
```

```Dockerfile
USER root
WORKDIR $JAVA_HOME/jre/lib/security
COPY cacorp.crt ./
RUN keytool -importcert -noprompt -trustcacerts -keystore cacerts -storepass changeit -file cacorp.crt -alias cacorp
```
