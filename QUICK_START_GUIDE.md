# Quick Start Guide - SRE Demo Project

## Decision Matrix: Choose Your Stack

### Option 1: Python Stack (Recommended for Beginners)
- **Language**: Python 3.11+
- **Framework**: FastAPI
- **Database**: PostgreSQL
- **Why**: Easy to learn, great ecosystem, excellent for demos

### Option 2: Node.js Stack
- **Language**: Node.js 18+
- **Framework**: Express.js or Fastify
- **Database**: PostgreSQL or MongoDB
- **Why**: JavaScript everywhere, large community

### Option 3: Go Stack
- **Language**: Go 1.21+
- **Framework**: Gin or Echo
- **Database**: PostgreSQL
- **Why**: Fast, simple, great for microservices

**Recommendation**: Start with **Python + FastAPI** for fastest implementation.

---

## Step-by-Step: First 48 Hours

### Hour 1-2: Project Setup
```bash
# Create project structure
mkdir -p application/src application/tests
mkdir -p infrastructure/kubernetes
mkdir -p ci-cd/.github/workflows
mkdir -p monitoring/{prometheus,grafana,alertmanager}
mkdir -p docs/{runbooks,dr-plan}
mkdir -p scripts

# Initialize git
git init
git add .
git commit -m "Initial project structure"
```

### Hour 3-4: Create Sample Application
Create a simple REST API with:
- Health check endpoint (`/health`)
- One business endpoint (e.g., `/api/users`)
- Database connection
- Error handling

### Hour 5-6: Dockerize Application
- Create `Dockerfile`
- Create `.dockerignore`
- Test local build: `docker build -t sre-demo-app .`
- Test run: `docker run -p 8000:8000 sre-demo-app`

### Hour 7-8: Set Up Local Kubernetes
```bash
# Option 1: Minikube
minikube start

# Option 2: Kind (Kubernetes in Docker)
kind create cluster --name sre-demo

# Option 3: k3d
k3d cluster create sre-demo
```

### Hour 9-10: Create K8s Manifests
- Deployment manifest
- Service manifest
- ConfigMap for configuration
- Test deployment: `kubectl apply -f infrastructure/kubernetes/`

### Hour 11-12: Set Up Image Registry
- Create account on Docker Hub or GitHub Container Registry
- Configure authentication
- Test push: `docker push your-registry/sre-demo-app:latest`

### Hour 13-16: Basic CI/CD Pipeline
Create GitHub Actions workflow:
```yaml
# .github/workflows/ci.yml
name: CI Pipeline
on: [push, pull_request]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Build Docker image
        run: docker build -t app:latest .
      - name: Run tests
        run: docker run app:latest pytest
```

### Hour 17-20: Add Quality Checks
- Add linting (pylint/flake8 for Python, eslint for Node.js)
- Add unit tests
- Integrate into CI pipeline
- Set up branch protection rules

### Hour 21-24: Basic Monitoring
- Add structured logging
- Deploy Prometheus
- Create basic metrics endpoint
- Set up Grafana dashboard

---

## Technology Installation Checklist

### Required Tools
- [ ] Docker Desktop or Docker Engine
- [ ] kubectl
- [ ] Kubernetes cluster (minikube/kind/k3d)
- [ ] Git
- [ ] Code editor (VS Code recommended)

### Optional but Recommended
- [ ] Helm (K8s package manager)
- [ ] Terraform (IaC)
- [ ] k9s (K8s CLI tool)
- [ ] Postman/Insomnia (API testing)

### Cloud Services (if using cloud)
- [ ] AWS/GCP/Azure account
- [ ] Container registry access
- [ ] Cloud monitoring service access

---

## Sample Application Ideas

### Option 1: Todo API
- Simple CRUD operations
- User authentication
- Database persistence
- Good for demonstrating all SRE practices

### Option 2: E-commerce Microservice
- Product catalog
- Shopping cart
- Order processing
- More complex, better for advanced demos

### Option 3: URL Shortener
- Simple but realistic
- High traffic potential (for load testing)
- Easy to understand

**Recommendation**: Start with **Todo API**, expand later if needed.

---

## Common Pitfalls to Avoid

1. **Trying to do everything at once** - Follow the phased approach
2. **Over-engineering** - Keep it simple for the demo
3. **Skipping documentation** - Document as you build
4. **Ignoring testing** - Tests are crucial for CI/CD
5. **Complex infrastructure** - Start local, move to cloud later

---

## Getting Help

### Resources
- Kubernetes: https://kubernetes.io/docs/
- Prometheus: https://prometheus.io/docs/
- Docker: https://docs.docker.com/
- GitHub Actions: https://docs.github.com/en/actions

### When Stuck
1. Check the implementation plan
2. Review official documentation
3. Start with minimal viable implementation
4. Iterate and improve

---

## Next Steps After Setup

1. ✅ Complete Phase 1 (Foundation)
2. ✅ Test everything locally
3. ✅ Document your setup
4. ✅ Move to Phase 2 (Quality & Security)
5. ✅ Continue with remaining phases

Good luck! 🚀
