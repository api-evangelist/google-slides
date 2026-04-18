# Google Slides (google-slides)
An API for creating, reading, and editing Google Slides presentations.

**URL:** [Visit APIs.json URL](https://developers.google.com/slides)

**Run:** [Capabilities Using Naftiko](https://github.com/naftiko/fleet?utm_source=api-evangelist&utm_medium=readme&utm_campaign=company-api-evangelist&utm_content=repo)

## Tags:

 - Collaboration, Google Workspace, Presentations, Productivity, Slides

## Timestamps

- **Created:** 2024-01-01
- **Modified:** 2026-04-18

## APIs

### Google Slides API
Create and edit presentations programmatically.

**Human URL:** [https://developers.google.com/slides](https://developers.google.com/slides)

#### Tags:

 - Presentations, REST, Slides

#### Properties

- [Documentation](https://developers.google.com/slides/api/reference/rest)
- [OpenAPI](openapi/google-slides-api-openapi.yml)
- [JSONSchema](json-schema/google-slides-presentation-schema.json)
- [JSONLD](json-ld/google-slides-context.jsonld)
- [Authentication](https://developers.google.com/slides/api/guides/authorizing)
- [Python Quickstart](https://developers.google.com/slides/api/quickstart/python)
- [CodeExamples](https://developers.google.com/slides/api/samples)
- [Pricing](https://developers.google.com/slides/api/limits)
- [TermsOfService](https://developers.google.com/terms)
- [Support](https://developers.google.com/slides/api/support)
- [Client Libraries](https://developers.google.com/workspace/slides/api/guides/libraries)
- [ReleaseNotes](https://developers.google.com/workspace/slides/release-notes)
- [Troubleshooting](https://developers.google.com/workspace/slides/api/troubleshoot-authentication-authorization)
- [YouTube](https://developers.google.com/workspace/slides/api/videos)
- [GitHubRepository](https://github.com/googleworkspace/slides-api)

## Common Properties

- [Portal](https://console.cloud.google.com/)
- [Authentication](https://developers.google.com/identity/protocols/oauth2)
- [GettingStarted](https://developers.google.com/slides/api/quickstart/python)
- [StatusPage](https://status.cloud.google.com/)
- [PrivacyPolicy](https://policies.google.com/privacy)
- [TermsOfService](https://policies.google.com/terms)
- [Blog](https://cloud.google.com/blog/products/application-development/introducing-google-slides-api)

## Features

| Name | Description |
|------|-------------|
| Presentation Creation | Create blank or pre-configured presentations programmatically with custom titles and layouts. |
| Batch Updates | Apply multiple changes to a presentation in a single atomic request for efficient editing. |
| Slide Management | Add, reorder, duplicate, and delete slides within presentations. |
| Text and Shape Editing | Insert and format text, shapes, images, videos, tables, and charts on slides. |
| Page Thumbnails | Generate thumbnail images of individual slides for previews and exports. |
| Template Support | Use existing presentations as templates and populate them with dynamic content. |

## Use Cases

| Name | Description |
|------|-------------|
| Automated Report Generation | Generate presentation reports from data sources, populating charts, tables, and text automatically. |
| Dynamic Presentation Templates | Create branded presentations from templates, filling in customer-specific data. |
| Educational Content Creation | Build educational slide decks programmatically from lesson plans or course materials. |
| Meeting Preparation | Automatically compile meeting agendas, status updates, and metrics into presentation format. |

## Integrations

| Name | Description |
|------|-------------|
| Google Sheets | Embed live charts and data from Google Sheets into presentations. |
| Google Drive | Store, organize, and share presentations through Google Drive. |
| Google Workspace | Part of the Google Workspace suite with seamless cross-app integration. |
| Google Apps Script | Automate Slides workflows using Apps Script for custom macros and triggers. |
| Google Cloud | Deploy Slides API integrations on Google Cloud Platform infrastructure. |

## Artifacts

Machine-readable API specifications organized by format.

### OpenAPI

- [Google Slides API](openapi/google-slides-api-openapi.yml)

### JSON Schema

- [Presentation](json-schema/google-slides-presentation-schema.json)
- [Page](json-schema/google-slides-page-schema.json)
- [Page Element](json-schema/google-slides-page-element-schema.json)
- [Shape](json-schema/google-slides-shape-schema.json)
- [Image](json-schema/google-slides-image-schema.json)
- [Table](json-schema/google-slides-table-schema.json)
- [Text Content](json-schema/google-slides-text-content-schema.json)
- [Text Style](json-schema/google-slides-text-style-schema.json)

### JSON-LD

- [Google Slides Context](json-ld/google-slides-context.jsonld)

## Capabilities

Naftiko capabilities organized as shared per-API definitions composed into customer-facing workflows.

### Shared Per-API Definitions

- [Google Slides API](capabilities/shared/slides-api.yaml) -- 5 operations for presentation creation, editing, and page management

### Workflow Capabilities

| Workflow | APIs Combined | Tools | Persona |
|----------|--------------|-------|---------|
| [Presentation Management](capabilities/presentation-management.yaml) | Slides API | 5 | Content Creator |

## Rules

- [Google Slides Spectral Rules](rules/google-slides-spectral-rules.yml) -- 7 rules enforcing Google Slides API conventions

## Maintainers

**FN:** Kin Lane

**Email:** kin@apievangelist.com
