---
page_title: "sonarqube_qualitygate_project_association Resource - terraform-provider-sonarqube"
subcategory: ""
description: |-
  Provides a Sonarqube Quality Gate Project association resource. This can be used to associate a Quality Gate to a Project
---

# sonarqube_qualitygate_project_association (Resource)

Provides a Sonarqube Quality Gate Project association resource. This can be used to associate a Quality Gate to a Project

## Example: create a quality gate project association

```terraform
resource "sonarqube_qualitygate" "main" {
    name = "my_qualitygate"

  condition {
    metric    = "new_coverage"
    op        = "LT"
    threshold = "30"
  }
}

resource "sonarqube_project" "main" {
    name       = "SonarQube"
    project    = "my_project"
    visibility = "public"
}

resource "sonarqube_qualitygate_project_association" "main" {
    gatename   = sonarqube_qualitygate.main.id
    projectkey = sonarqube_project.main.project
}
```

## Argument Reference

The following arguments are supported:

- gatename - (Required) The name of the Quality Gate
- projectkey - (Required) Key of the project. Maximum length 400. All letters, digits, dash, underscore, period or colon.

## Import

Quality Gates Project Associations can be imported using a combination of quality gate name and project key

```terraform
terraform import sonarqube_qualitygate_project_association.main my_qualitygate/my_project
```
