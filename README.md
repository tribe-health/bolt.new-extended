# Bolt Application

## Deployment Methods

This project supports two deployment methods: Direct GitHub Actions deployment and GitOps with ArgoCD. Below is a comparison of both approaches:

### Direct Deployment (GitHub Actions)

Pros:
- Immediate deployment feedback
- Simpler setup for small projects
- Direct control over deployment process
- Easier debugging of deployment issues
- Better suited for development and testing environments

Cons:
- Less scalable for multiple environments
- Manual intervention needed for rollbacks
- State management can be challenging
- Security policies harder to enforce consistently
- No automatic drift detection

Best for:
- Development environments
- Small teams
- Quick iterations
- Testing new features
- Projects with simple deployment needs

### GitOps Deployment (ArgoCD)

Pros:
- Declarative configuration
- Automatic drift detection and reconciliation
- Better security through pull-based model
- Easy rollbacks and version control
- Better audit trail
- Cluster state always matches git repository
- Scalable across multiple clusters and environments

Cons:
- More complex initial setup
- Requires additional cluster resources
- Learning curve for team members
- May require changes to existing workflows
- Slower feedback loop for deployments

Best for:
- Production environments
- Multiple clusters/environments
- Large teams
- Compliance requirements
- Complex deployment scenarios

## Deployment Setup

### Prerequisites

- Azure Kubernetes Service (AKS) cluster
- Azure Container Registry (ACR)
- GitHub repository
- TLS certificates for domain
- NGINX Ingress Controller installed on the cluster
- ArgoCD installed on the cluster

### GitHub Actions Deployment

#### Repository Secrets

The following secrets need to be configured in your GitHub repository:

```bash
DOCKERHUB_USERNAME
ARM_CLIENT_ID
ARM_CLIENT_SECRET
ARM_SUBSCRIPTION_ID
ARM_TENANT_ID
TLS_CRT
TLS_KEY
```

#### Repository Variables

The following variables need to be configured:

```bash
LOCATION
RESOURCE_GROUP_NAME
CLUSTER_NAME
KUBERNETES_NAMESPACE
TLS_SECRET_NAME
DOCKER_IMAGE_NAME
```

### ArgoCD Setup

1. Apply the ArgoCD configuration:
```bash
kubectl apply -f argocd/application.yaml
```

2. Verify the application is synced:
```bash
argocd app get bolt
argocd app sync bolt
```

3. Monitor sync status:
```bash
argocd app list
argocd app logs bolt
```

### Choosing Between Deployment Methods

1. Use GitHub Actions Direct Deployment when:
   - Developing new features (features/azure branch)
   - Need immediate feedback on deployments
   - Testing configuration changes
   - Working in development environments

2. Use ArgoCD when:
   - Deploying to production
   - Managing multiple environments
   - Need automated drift detection
   - Require strict governance
   - Want automated reconciliation

### Hybrid Approach

You can use both methods together:
1. GitHub Actions for:
   - Building and pushing Docker images
   - Running tests
   - Creating necessary secrets
   - Development deployments

2. ArgoCD for:
   - Production deployments
   - Configuration management
   - Drift detection
   - Environment consistency

## Ingress Configuration

The application uses a secure ingress that:
- Forces SSL/TLS encryption
- Only accepts traffic for configured domain
- Uses TLSv1.2 and TLSv1.3
- Includes optimized proxy settings

Key ingress features:
```yaml
annotations:
  kubernetes.io/ingress.class: "nginx"
  nginx.ingress.kubernetes.io/ssl-redirect: "true"
  nginx.ingress.kubernetes.io/force-ssl-redirect: "true"
  nginx.ingress.kubernetes.io/ssl-protocols: "TLSv1.2 TLSv1.3"
```

## Monitoring and Troubleshooting

### GitHub Actions Deployment

```bash
# Check deployment status
kubectl get deployment -n ${KUBERNETES_NAMESPACE}
kubectl describe deployment bolt-app -n ${KUBERNETES_NAMESPACE}

# Check pods
kubectl get pods -n ${KUBERNETES_NAMESPACE}
kubectl logs -l app=bolt -n ${KUBERNETES_NAMESPACE}
```

### ArgoCD Deployment

```bash
# Check ArgoCD application status
argocd app get bolt
argocd app logs bolt

# Check sync status
argocd app list
argocd app sync bolt --dry-run

# Debug sync issues
argocd app diff bolt
argocd app terminate-op bolt
```

### General Troubleshooting

1. Check pod status:
```bash
kubectl get pods -n ${KUBERNETES_NAMESPACE}
kubectl describe pod <pod-name> -n ${KUBERNETES_NAMESPACE}
```

2. Check ingress status:
```bash
kubectl get ingress -n ${KUBERNETES_NAMESPACE}
kubectl describe ingress bolt-ingress -n ${KUBERNETES_NAMESPACE}
```

3. Check TLS secret:
```bash
kubectl get secret ${TLS_SECRET_NAME} -n ${KUBERNETES_NAMESPACE}
kubectl describe secret ${TLS_SECRET_NAME} -n ${KUBERNETES_NAMESPACE}
```

4. Verify NGINX Ingress Controller:
```bash
kubectl get pods -n ingress-nginx
kubectl logs -n ingress-nginx -l app.kubernetes.io/name=ingress-nginx
```

## Security Notes

- All HTTP traffic is automatically redirected to HTTPS
- Only TLSv1.2 and TLSv1.3 are allowed
- Only requests to configured domain are accepted
- Invalid hostnames return 404
- SSL certificates are managed through Kubernetes secrets
- ArgoCD provides additional security through pull-based model
