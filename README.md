# Delivery Pipeline

*Born from frustration, refined through experience, shared for the benefit of the community.*

## Table of Contents

- [About This Repository](#about-this-repository)
- [Repository Structure](#repository-structure)
- [Implementation Approaches](#implementation-approaches)
  - [Two Long-Lived Branches (Main + Develop)](#two-long-lived-branches-main--develop)
  - [One Long-Lived Branch (Trunk-Based)](#one-long-lived-branch-trunk-based)
- [Which Approach Should You Choose?](#which-approach-should-you-choose)
- [Getting Started](#getting-started)
- [Key Benefits](#key-benefits)
- [Contributing](#contributing)
- [Philosophy](#philosophy)

## About This Repository

This repository is born from years of frustration with delivery pipelines that failed to meet real-world needs—either absent entirely, overly complex for developers, or misaligned with business objectives. As a software engineer who witnessed these challenges firsthand and subsequently acquired operations expertise, I developed a delivery pipeline approach that harmonizes two often-conflicting demands:

- **Technical Excellence (Quality)**: Fast feedback, automated testing, continuous integration, and developer-friendly workflows
- **Business Success (Cost & Time)**: Rapid delivery, cost efficiency, and measurable performance metrics

The result is a comprehensive framework that balances speed, quality, and cost—enabling organizations to achieve "Elite" performance according to DORA metrics while maintaining both developer satisfaction and business value.

## Repository Structure

This repository contains both theoretical foundations and practical implementations:

### 📚 [Theory](docs/theory.md)

The theory document provides comprehensive guidance on modern software delivery practices:

**Core Concepts:**
- **Goal**: Achieving elite pipeline performance (more features, cheaper delivery, faster time-to-market)
- **Definition of Terms**: CI/CD, deployments, releases, and release candidates
- **Objectives**: Automate repetitive tasks, measure with DORA metrics, assess performance, and continuously improve

**Key Topics:**
- **Principles**: 13 foundational principles including DRY, KISS, enforcement over convention, and always-green code
- **Branching Strategies**: Two proven approaches (Trunk-Based Development and Modified GitFlow)
- **Versioning**: Semantic versioning with automated release notes generation
- **Commit Messages**: Conventional commits with automated validation
- **Testing Pyramid**: Unit, smoke, integration, acceptance, exploratory, security, and performance testing
- **Security**: SAST, DAST, IAST, SCA, and fuzz testing with comprehensive security checklist
- **Environments**: Multi-environment strategy with clear promotion paths
- **Tools**: Recommendations for documentation, CI servers, SCM, testing, deployment, and monitoring
- **Audit & Reporting**: Release tracking, test tracking, deployment tracking, performance metrics, and security tracking

[Read the full theory →](docs/theory.md)

### 🔧 Implementation Approaches

Two battle-tested implementations are provided, each suited for different organizational needs:

#### 1. [Two Long-Lived Branches](docs/implementations/two-long-lived-branches.md)

**Best for:** Highly regulated environments with manual approval requirements

**Characteristics:**
- Uses `main` (production) and `develop` (integration) branches
- Additional safety layer with multi actor testing before production
- Explicit release candidates and staging phases
- Multiple approval gates (Developer, QA, BA/PM, PO)
- Automatic rollback on failures
- Suitable for teams building test coverage or transitioning to continuous delivery

**Key Features:**
- PR Pipeline → Main Branch Pipeline → QA Approval → PO Approval (QA) → Create Release → PO Approval (Stage) → Production
- Comprehensive validation at each stage
- Role-based deployment responsibilities
- Full DORA metrics collection

[View two-branch implementation →](docs/implementations/two-long-lived-branches.md)

#### 2. [One Long-Lived Branch](docs/implementations/one-long-lived-branch.md)

**Best for:** Organizations with mature CI/CD practices and comprehensive automated testing

**Characteristics:**
- Single long-lived `main` branch (trunk-based development)
- Simplified workflow with faster feedback loops
- Feature branches merge directly to `main`
- Quality gates through automated testing and approvals
- Multiple deployment stages with on-demand flexibility
- Includes dedicated bugfix workflow for production patches

**Key Features:**
- PR Pipeline → Main Pipeline → QA Pipeline → Stage Pipeline → Production Pipeline
- Ephemeral environments for testing
- Flexible deployment to multiple environments (On-Demand, Dev, QA, Stage, Production)
- Bugfix flow with version-specific branches
- Cherry-picking fixes back to main branch

[View single-branch implementation →](docs/implementations/one-long-lived-branch.md)

## Which Implementation to Choose?

**Choose Two Long-Lived Branches if:**
- You operate in a highly regulated industry
- Manual approvals are required by policy
- You need explicit integration testing phases
- You're transitioning from traditional release cycles
- You want an additional safety net before production

**Choose One Long-Lived Branch if:**
- You have comprehensive automated test coverage (>80%)
- Your test suite runs quickly (<10 minutes)
- You practice or want to achieve continuous deployment
- You want to maximize developer velocity
- Your team has mature CI/CD practices

## Getting Started

1. **Read the Theory**: Start with the [theory document](docs/theory.md) to understand the foundational principles and concepts
2. **Choose Your Implementation**: Review both implementation approaches and select the one that fits your organizational needs
3. **Adapt to Your Context**: Both implementations are templates—customize them for your specific tools, environments, and requirements
4. **Measure and Improve**: Implement DORA metrics tracking to continuously assess and improve your delivery process

## Key Benefits

- ✅ **Automated Validation**: Commit messages, builds, tests, and deployments
- ✅ **Fast Feedback**: Quick pipelines for developers (PR pipeline < 10 minutes)
- ✅ **Quality Gates**: Multiple approval points without blocking productivity
- ✅ **Automatic Rollback**: Reverts on failure to maintain stability
- ✅ **DORA Metrics**: Built-in tracking for deployment frequency, lead time, MTTR, and change failure rate
- ✅ **Security First**: Integrated security testing (SAST, DAST, SCA) throughout the pipeline
- ✅ **Flexible Environments**: On-demand, dev, QA, stage, and production environments
- ✅ **Clear Responsibilities**: Role-based deployments with explicit approval workflows

## Contributing

This repository represents real-world experience distilled into practical guidance. If you have improvements, suggestions, or alternative approaches that have worked in your environment, contributions are welcome.

## Philosophy

> "The easiest way to kill a software's future is to not test it."

This repository embodies the principle that great software delivery requires balancing competing demands: moving fast without breaking things, delivering quality without excessive cost, and empowering teams without sacrificing governance. The goal is to help organizations achieve Elite performance on DORA metrics while maintaining sustainable, enjoyable development practices.
