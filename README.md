# Clusterwide External Secrets Store Configuration


This repository contains a [Crossplane configuration](https://docs.crossplane.io/latest/concepts/packages/#configuration-packages), tailored for users establishing their initial control plane. This configuration deploys fully managed ESO resources. Currently only supports GCP Secret Manager and AWS Secrets Manager/ with workload identity.

## Overview

The core components of a custom API in [Crossplane](https://docs.crossplane.io/latest/getting-started/introduction/) include:

- **CompositeResourceDefinition (XRD):** Defines the API's structure.
- **Composition(s):** Implements the API by orchestrating a set of Crossplane managed resources.

In this specific configuration, the ArgoCD API contains:

- **an [CESS](/apis/definition.yaml) custom resource type.**
- **Composition of the CESS resources:** Configured in [/apis/composition.yaml](/apis/composition.yaml), it provisions CESS resources in the `upbound-system` namespace.

This repository contains an Composite Resource (XR) file.

## Deployment

```shell
apiVersion: pkg.crossplane.io/v1
kind: Configuration
metadata:
  name: configuration-cluster-ess
spec:
  package: xpkg.upbound.io/judasz/configuration-cluster-ess:v0.1.0
```

## Next steps

This repository serves as a foundational step. To enhance your control plane, consider:

1. creating new API definitions in this same repo
2. editing the existing API definition to your needs
