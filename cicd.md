* CI/CD
  * CICD tools
    * https://concourse-ci.org/
    * Jenkins
    * argo workflows + argo events + argocd
    * Entr https://eradman.com/entrproject/
    * Drone CI
  * Build AI-agents
    * https://github.com/dagger/dagger
  * Guides
    * https://hands-on-tech.github.io/2020/03/15/k8s-jenkins-example.html
  * Deployments: Canary, A/B
    * https://blog.argoproj.io/introducing-argo-rollouts-v1-0-803e87f76ef7
    * Istio+Flagger https://habr.com/ru/company/flant/blog/471620/
    * https://docs.flagger.app/tutorials/nginx-progressive-delivery
    * https://github.com/bookingcom/shipper
    * https://argoproj.github.io/argo-rollouts/features/traffic-management/nginx/
      * https://argoproj.github.io/argo-rollouts/features/canary/
  * ChatOps
    * https://pullreminders.com/ - збирати в одному місці всі свої PR/MR з GH/BB/GL
  * GitOps
    * Weave Flux
    * ArgoCD
      * Ready to go solution with ArgoCD, Vault, Atlantis, Keycloak (SSO), HELM https://github.com/kubefirst/nebulous
    * https://github.com/fluxcd/flux
    * https://github.com/argoproj/gitops-engine#slack-ask-us-anything
    * https://github.com/werf/werf
  * Builders
    * https://github.com/buildpacks-community/kpack
    * Docker
    * BuildKit https://github.com/moby/buildkit/blob/master/docs/rootless.md
    * img https://github.com/genuinetools/img
    * Buildah
    * kaniko https://github.com/GoogleContainerTools/kaniko
  * Pipelines
    * https://keptn.sh/
    * Jenkins
    * Jenkins X
    * Argo
      * деплойменти своїх values.yaml для публічних чартів https://github.com/argoproj/argocd-example-apps/tree/master/helm-dependency
    * Tekton
    * Spinnaker
    * Weave flux
    * blue/green deployment
      * Посоветуйте чем бы сделать B/G deployment в кубере, что бы еще и с istio умело.И сразу вопрос по argo-rollouts, это часть argoCD?
      * Сам по себе Argo Rollouts это контроллер с ui. Не часть ArgoCD но нативно  в него интегрируется. С истио отлично работает, мы им делаем canary деплойменты
      * https://spinnaker.io/
      * flagger
  * Developer experience
    * Skaffold
    * Tilt
    * Garden
  * Prow+Tekton+Harbor+ArgoCD
    * https://github.com/tektoncd/triggers
  * https://castlemilk.github.io/kubernetes-cicd/#/0
  * Kubernetes compatible: Jenkins, Gitlab, Argo CD, Concourse , Keel.sh+Go
    * Keel - allows to approve deployments https://keel.sh/docs/#approvals
  * Semantic release https://github.com/semantic-release/gitlab
  * Changelog - https://www.npmjs.com/package/generate-changelog
* Software dependency update and tracking 
  * github https://github.blog/2020-06-01-keep-all-your-packages-up-to-date-with-dependabot/ 
  * gitlab and github renovate bot
  * RSS slack
  * https://newreleases.io/
  * https://dependabot.com/
  * https://coderelease.io/
* Linter
  * https://github.blog/2020-06-18-introducing-github-super-linter-one-linter-to-rule-them-all/
  
