# CI/CD

CI/CD tools, best practices, and deployment strategies

## CI/CD Platforms

### Self-Hosted Solutions
- [Jenkins](https://jenkins.io/) - Open-source automation server
- [Concourse CI](https://concourse-ci.org/) - Pipeline-based continuous integration
- [Drone CI](https://drone.io/) - Container-native CI platform
- [GitLab CI/CD](https://docs.gitlab.com/ee/ci/) - Integrated CI/CD with GitLab
- [TeamCity](https://www.jetbrains.com/teamcity/) - Enterprise CI/CD server
- [Entr](https://eradman.com/entrproject/) - Run arbitrary commands when files change

### Cloud/SaaS Options
- [GitHub Actions](https://github.com/features/actions) - Integrated with GitHub repositories
- [CircleCI](https://circleci.com/) - Cloud-native CI/CD
- [Travis CI](https://travis-ci.org/) - Distributed CI service
- [AWS CodePipeline](https://aws.amazon.com/codepipeline/) - Continuous delivery service
- [Azure DevOps](https://azure.microsoft.com/services/devops/) - Development collaboration tools

### Kubernetes-Native
- [Argo Workflows](https://argoproj.github.io/workflows/) - Container-native workflow engine
- [Tekton](https://tekton.dev/) - Cloud-native CI/CD
- [Jenkins X](https://jenkins-x.io/) - CI/CD for Kubernetes
- [Argo Events](https://github.com/argoproj/argo-events) - Event-driven workflow automation

## Deployment Strategies

### Progressive Delivery
- [Argo Rollouts](https://argoproj.github.io/argo-rollouts/) - Kubernetes progressive delivery
- [Flagger](https://docs.flagger.app/) - Progressive delivery operator
  - [Nginx Tutorial](https://docs.flagger.app/tutorials/nginx-progressive-delivery)
  - [Istio Integration](https://habr.com/ru/company/flant/blog/471620/)
- [Shipper](https://github.com/bookingcom/shipper) - Kubernetes-native multi-cluster canary
- [Spinnaker](https://spinnaker.io/) - Multi-cloud continuous delivery
- [Keptn](https://keptn.sh/) - Event-based control plane for delivery

### Deployment Types
- **Blue/Green Deployment**
  - Runs two identical environments with only one live
  - Allows instant rollback by switching traffic
  - Examples: AWS CodeDeploy, Argo Rollouts, Spinnaker

- **Canary Deployment**
  - Gradually routes traffic to new version
  - Monitors for errors before full deployment
  - Examples: [Istio+Flagger](https://docs.flagger.app/tutorials/istio-progressive-delivery), Argo Rollouts, LaunchDarkly
  - [Argo Rollouts Nginx Traffic Management](https://argoproj.github.io/argo-rollouts/features/traffic-management/nginx/)

- **A/B Testing**
  - Routes traffic based on specific criteria
  - Tests features with subset of users
  - Examples: Istio, Nginx service mesh

## GitOps Tools

- [ArgoCD](https://argo-cd.readthedocs.io/) - Declarative GitOps for Kubernetes
  - [Example Apps](https://github.com/argoproj/argocd-example-apps/tree/master/helm-dependency) - Helm chart values deployment examples
  - [Ready to go solution](https://github.com/kubefirst/nebulous) - Includes ArgoCD, Vault, Atlantis, Keycloak (SSO), HELM
- [Flux CD](https://github.com/fluxcd/flux) - GitOps Kubernetes operator
- [Weave Flux](https://github.com/weaveworks/flux) - GitOps for cluster management
- [Werf](https://github.com/werf/werf) - GitOps delivery tool
- [GitOps Engine](https://github.com/argoproj/gitops-engine#slack-ask-us-anything) - Core GitOps implementation

## Container Building

### Container Builders
- [Docker](https://www.docker.com/) - Standard container platform
- [BuildKit](https://github.com/moby/buildkit) - Enhanced Docker builder
  - [Rootless Mode](https://github.com/moby/buildkit/blob/master/docs/rootless.md) - Run BuildKit without root privileges 
- [Kaniko](https://github.com/GoogleContainerTools/kaniko) - Build images in Kubernetes
- [Buildah](https://buildah.io/) - OCI container builder
- [Img](https://github.com/genuinetools/img) - Standalone, daemon-less builder
- [Buildpacks/kpack](https://github.com/buildpacks-community/kpack) - Kubernetes-native builder

## Developer Experience

- [Skaffold](https://skaffold.dev/) - Local Kubernetes development
  - [CI/CD Integration Tutorial](https://skaffold.dev/docs/tutorials/ci_cd/)
- [Tilt](https://tilt.dev/) - Microservice development environment
- [Garden](https://garden.io/) - Development orchestration platform
- [Telepresence](https://www.telepresence.io/) - Local development with remote clusters

## Pipeline Implementations

- [Jenkins](https://www.jenkins.io/) - Traditional automation server
- [Jenkins X](https://jenkins-x.io/) - Cloud-native Jenkins for Kubernetes
- [Argo Workflows](https://argoproj.github.io/argo-workflows/) - Kubernetes-native workflow engine
- [Tekton](https://tekton.dev/) - Kubernetes-native CI/CD pipelines
  - [Triggers](https://github.com/tektoncd/triggers) - Event-based triggering
- [Spinnaker](https://spinnaker.io/) - Multi-cloud CD platform
- [Keptn](https://keptn.sh/) - Cloud-native application lifecycle orchestration
- [Prow](https://docs.prow.k8s.io/docs/) - Kubernetes-based CI/CD system

## ChatOps & Collaboration

- [Pull Reminders](https://pullreminders.com/) - Consolidate PRs/MRs from GitHub/BitBucket/GitLab
- [Slack Integrations](https://slack.com/apps) - CI/CD notifications in Slack
- [Keel](https://keel.sh/docs/#approvals) - Kubernetes operator for automating updates with approval workflows

## Environment Management

### Environment Levels
- **Development**:
  - Individual environments for each developer
  - Frequent changes and experimentation
  - Often uses mocks for external dependencies

- **Testing/QA**:
  - Shared environment for integration testing
  - Automated testing with real dependencies
  - Team synchronization point

- **Staging**:
  - Production-identical configuration
  - Performance and load testing
  - Pre-production validation

- **Production**:
  - Customer-facing environment
  - Strict deployment controls
  - Monitoring and alerting

## Dependency Management

- [Dependabot](https://dependabot.com/) - Automated dependency updates
  - [GitHub Integration](https://github.blog/2020-06-01-keep-all-your-packages-up-to-date-with-dependabot/)
- [Renovate](https://github.com/renovatebot/renovate) - Automated dependency updates for GitLab and GitHub
- [New Releases](https://newreleases.io/) - Release notifications
- [CodeRelease](https://coderelease.io/) - Dependency tracking

## Code Quality & Release Management

### Linting and Static Analysis
- [GitHub Super Linter](https://github.com/github/super-linter) - Unified linting platform
  - [Introduction Blog](https://github.blog/2020-06-18-introducing-github-super-linter-one-linter-to-rule-them-all/)
- [SonarQube](https://www.sonarqube.org/) - Code quality and security
- [ESLint](https://eslint.org/) - JavaScript linting
- [Rubocop](https://rubocop.org/) - Ruby static code analyzer

### Release & Versioning
- [Semantic Release](https://github.com/semantic-release/gitlab) - Automates the versioning process
- [Changelog Generator](https://www.npmjs.com/package/generate-changelog) - Automated changelog generation

## Real-world Advice

- Keep CI/CD pipelines fast (under 10 minutes if possible)
- Implement proper caching strategies
- Consider self-hosted runners for sensitive code
- Separate build and deployment stages
- Use environment-specific configuration
- Implement proper secrets management
- Monitor pipeline health and runtime

## Learning Resources

- [Kubernetes CICD Guide](https://castlemilk.github.io/kubernetes-cicd/#/0) - Step-by-step guide
- [Enterprise CI/CD Best Practices](https://github.com/y0zg/docs/blob/master/cicd-EnterpriseCICDBestPractices-2ndEdition.pdf)
- [Jenkins Kubernetes Example](https://hands-on-tech.github.io/2020/03/15/k8s-jenkins-example.html) - Setup guide
- [Awesome GitHub Actions](https://project-awesome.org/sdras/awesome-actions) - Curated list
- [AWS Actions](https://github.com/aws-actions) - AWS-specific GitHub Actions
- [Actions Runner Controller](https://github.com/actions-runner-controller/actions-runner-controller) - Self-hosted runners on Kubernetes
