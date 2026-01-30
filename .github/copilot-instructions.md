# Copilot Instructions for OnBoardingEsign

## Project Overview
This is a Salesforce DX (SFDX) project for an e-signature onboarding solution. The codebase is organized for Salesforce metadata deployment and development, with Apex classes, Lightning Web Components (LWC), custom objects, and supporting configuration.

## Architecture & Key Components
- **Apex Classes** (`force-app/main/default/classes/`): Core business logic, security, document analysis, and integration services. Example: `AdvancedAIService.cls`, `SecurityDashboardController.cls`.
- **Lightning Web Components** (`force-app/main/default/lwc/`): UI components for document generation, viewing, face verification, signature pad, dashboards, and health monitoring.
- **Custom Objects & Fields** (`force-app/main/default/objects/`): Data model for audit trails, document lifecycle, identity verification, and signature requests. Custom fields are explicitly listed in `package.xml` for granular deployment.
- **Named Credentials & Static Resources**: Integrations with external APIs (e.g., FacePlusPlus) and static assets (e.g., ChartJS).

## Developer Workflows
- **Source Deployment/Retrieval**: Use SFDX CLI for all source operations. Example:
  - Retrieve: `sfdx force:source:retrieve -m ApexClass:SecurityDashboardController`
  - Deploy: `sfdx force:source:deploy -m CustomField:AuditTrail__c.Session_Id__c`
- **Field Type Changes**: If a custom field (e.g., `Session_Id__c`) needs to change type, delete or rename it in Salesforce before deploying the new definition (see README for details).
- **Metadata Granularity**: `package.xml` is curated for selective deployment. Always update it when adding/removing classes, components, or fields.

## Project Conventions
- **Apex Naming**: Service and controller classes use clear, descriptive names (e.g., `*Service`, `*Controller`, `*Engine`).
- **LWC Naming**: Folders and files use camelCase (e.g., `documentGenerator`).
- **Field References**: Custom fields are referenced as `Object__c.Field__c` in both code and `package.xml`.
- **Component Bundling**: Each LWC is in its own folder with `.js`, `.html`, `.css`, and `.js-meta.xml` files.

## Integration & Cross-Component Patterns
- **Apex-LWC Communication**: LWCs call Apex methods via `@AuraEnabled` endpoints for business logic and data access.
- **External APIs**: Integrations use Named Credentials and custom metadata for secure configuration.

## Key Files & Directories
- `package.xml`: Controls metadata deployment scope.
- `force-app/main/default/classes/`: Apex logic.
- `force-app/main/default/lwc/`: Lightning Web Components.
- `force-app/main/default/objects/`: Custom objects and fields.
- `README.md`: Contains special deployment instructions for tricky field changes.

## Example: Deploying a New Apex Class
```sh
sfdx force:source:deploy -m ApexClass:NewClassName
```

## Example: Adding a New LWC
1. Create a new folder in `force-app/main/default/lwc/`.
2. Add `.js`, `.html`, `.css`, and `.js-meta.xml` files.
3. Update `package.xml` under `<name>LightningComponentBundle</name>`.

---
For more details, see the README or ask for specific workflow guidance.
