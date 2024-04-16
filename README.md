# AsciiArtify

### for training purposes


| NAME                    | PROMPT              | DESCRIPTION            | EXAMPLE                         |
|-------------------------|---------------------|------------------------|---------------------------------|
| app.yaml                | create an application for k8s, name is "scan", image from gcr.io/Azelyony/scan:v1.0.0 | YAML to define my application | [app.yaml](yaml/app.yaml)       |
| app-livenessProbe.yaml  | add liveness probe  | YAML with added livness probe | [app-livenessProbe.yaml](yaml/app-livenessProbe.yaml) |
| app-readinessProbe.yaml | add readiness probe | YAML with added readiness probe | [app-readinessProbe.yaml](yaml/app-readinessProbe.yaml) |
| app-volumeMounts.yaml   | configure volume mounts for this app | YAML with added volumeMounts | [app-volumeMounts.yaml](yaml/app-volumeMounts.yaml) |
| app-cronjob.yaml        | create cronjob      | YAML with example cronjob | [app-cronjob.yaml](yaml/app-cronjob.yaml) |
| app-job.yaml            | create a job example | YAML with example a job  | [app-job.yaml](yaml/app-job.yaml) |
| app-multicontainer.yaml | create a multicontainer app with examples of interaction between them | YAML with multi containers POD | [app-multicontainer.yaml](yaml/app-multicontainer.yaml) |
| app-resources.yaml      | configure resources uses for my app | YAML with resource configuration for app | [app-resources.yaml](yaml/app-resources.yaml) |
| app-secret-env.yaml     | configure for using secrets as env  | YAML with my app using secrets as Env variables | [app-secret-env.yaml](yaml/app-secret-env.yaml) |








