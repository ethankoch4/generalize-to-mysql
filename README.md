# generalize-to-mysql

Generalize Crossplane PostgreSQL configuration to enable MySQL as well

## Getting Started

1. Follow Crossplane setup instructions: https://crossplane.io/docs/v0.14/getting-started/install-configure.html
2. Setup Docker registry: https://crossplane.io/docs/v0.14/getting-started/package-infrastructure.html#build-and-push-the-configuration
3. Build Configuration & Push:

```bash
cd generalized-config

kubectl crossplane build configuration
kubectl crossplane push configuration ${REG}/generalized-sql:master

cd ..
```

4. Install Configuration:

```bash
kubectl crossplane install configuration ${REG}/generalized-sql:master
```

5. Test Configuration with either SQL or PostgreSQL:

```bash

kubectl apply -f test/test-config-mysql.yaml

# or

kubectl apply -f test/test-config-postgresql.yaml
```

6. Watch it become ready:

```bash
kubectl get compositesqlinstance -w
```
