---
title: "Creating private projects with custom roles"
excerpt: ""
---
[block:callout]
{
  "type": "info",
  "title": "This feature requires an enterprise plan",
  "body": "Custom roles are only available to customers on our enterprise plans. \n\nTo learn more about enterprise plans, contact [sales@launchdarkly.com](mailto:sales@launchdarkly.com?Subject=Custom%20roles)."
}
[/block]

[block:api-header]
{
  "title": "Overview"
}
[/block]
This topic explains how to use custom roles to create private projects or restrict access to projects. It gives examples of both how to restrict access to one project, effectively creating a private project for members you choose, and to grant access only to one or some projects.

This topic uses the `viewProject` action to restrict and grant access to projects. To learn more about it, read [Actions in custom roles](doc:actions-in-custom-roles).
[block:callout]
{
  "type": "info",
  "body": "Viewing access is required to modify a resource, so if a member cannot view a resource, they also cannot modify it in any way. \n\nYou can use the policies below to control who can access and modify the feature flags or other child resources in a project.",
  "title": "Team members can't modify what they can't see"
}
[/block]

[block:api-header]
{
  "title": "Restricting access to a project"
}
[/block]
This example policy forbids viewing access to a project called `project-1`. 

This policy is useful for restricting access to a project to only those team members who are working on it.

The following code sample restricts view and edit access to a project:
[block:code]
{
  "codes": [
    {
      "code": "[\n  {\n    \"resources\": [\"proj/project-1\"],\n    \"actions\": [\"viewProject\"],\n    \"effect\": \"deny\"\n  }\n]",
      "language": "json"
    }
  ]
}
[/block]

[block:api-header]
{
  "title": "Granting access to selected projects"
}
[/block]
You can restrict individual members' or teams' access to certain projects by explicitly denying view access to projects you do not want them to see. Excluding most projects effectively creates a dashboard and project picker that only displays the projects you want a given user or group to see. 

You can even restrict teams or members to their own project-based workspace by allowing them to see only one project. 

The example below allows access to every project in an environment except the four listed in the `"resources"` parameter. 
[block:code]
{
  "codes": [
    {
      "code": "[\n  {\n    \"resources\": [\"proj/project-1,project-2,project-3,project-4\"],\n    \"actions\": [\"viewProject\"],\n    \"effect\": \"deny\"\n  }\n]",
      "language": "text"
    }
  ]
}
[/block]