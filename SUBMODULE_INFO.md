# Private Implementation Submodule

This repository references a private submodule containing the full implementation code.

## Submodule Information

- **Path**: `private-implementations/`
- **Repository**: `https://github.com/PrizmCaptCore/portfolio.git` (Private)
- **Branch**: `main`

## Access

The `private-implementations` submodule is a **private repository** containing:
- Full Terraform configurations (40+ files)
- Production MLOps pipeline code
- Healthcare integration implementations
- Kubernetes manifests
- Python package source code
- Complete Git history (219+ commits)

## For Reviewers with Access

If you have been granted access to the private repository:

```bash
# Clone this public repo with submodule
git clone --recurse-submodules https://github.com/PrizmCaptCore/portfolio_public.git

# Or if already cloned, initialize the submodule
git submodule init
git submodule update

# The private-implementations/ directory will be populated with full code
cd private-implementations/
ls -la  # See all implementation files
```

## Requesting Access

To request access to the private implementation repository:

1. Contact via email or LinkedIn (see main README)
2. Provide:
   - Brief introduction of your organization
   - GitHub username for access invitation
   - Intended use case (hiring evaluation, collaboration, etc.)

Access is typically granted within 24-48 hours for legitimate inquiries.

---

**Note**: Without access to the private repository, the `private-implementations/` directory will appear empty when cloning. This is expected behavior for private submodules.
