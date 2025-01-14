---
# generated by https://github.com/hashicorp/terraform-plugin-docs
page_title: "sentry_team_member Resource - terraform-provider-sentry"
subcategory: ""
description: |-
  Sentry Team Member resource.
---

# sentry_team_member (Resource)

Sentry Team Member resource.

## Example Usage

```terraform
# Add a member to a team
resource "sentry_organization_member" "default" {
  organization = "my-organization"
  email        = "test@example.com"
  role         = "member"
}

resource "sentry_team" "default" {
  organization = "my-organization"
  name         = "my-team"
  slug         = "my-team"
}

resource "sentry_team_member" "default" {
  organization = "my-organization"
  team         = sentry_team.default.id
  member_id    = sentry_organization_member.default.internal_id
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Required

- `member_id` (String) The ID of the member to add to the team.
- `organization` (String) The slug of the organization the team should be created for.
- `team` (String) The slug of the team to add the member to.

### Optional

- `role` (String) The role of the member in the team. When not set, resolve to the minimum team role given by this member's organization role.

### Read-Only

- `id` (String) The ID of this resource.

## Import

Import is supported using the following syntax:

```shell
# import using the member ID and team slug from the URL:
# https://[org-slug].sentry.io/settings/teams/[team-slug]/members/
# https://[org-slug].sentry.io/settings/members/[member-id]/
terraform import sentry_team_member.default org-slug/team-slug/member-id
```
