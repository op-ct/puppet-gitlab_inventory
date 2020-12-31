# Reference

<!-- DO NOT EDIT: This document was generated by Puppet Strings -->

## Table of Contents

### Tasks

* [`resolve_reference`](#resolve_reference): Return a GitLab organization's projects as local inventory targets

### Plans

* [`gitlab_inventory::count`](#gitlab_inventorycount): Example plan, prints number of Targets from inventory
* [`gitlab_inventory::latest_semver_tags`](#gitlab_inventorylatest_semver_tags): Report the highest SemVer tag for each repo (that has SemVer tags)
* [`gitlab_inventory::required_checks`](#gitlab_inventoryrequired_checks): List and/or set which PR checks are required on each repo
* [`gitlab_inventory::workflows`](#gitlab_inventoryworkflows): Return repos with GitLab Actions workflows

## Tasks

### `resolve_reference`

Return a GitLab organization's projects as local inventory targets

**Supports noop?** false

#### Parameters

##### `group`

Data type: `String[1]`

GitLab group name (or user login) with repos

##### `gitlab_api_endpoint`

Data type: `String[1]`

URL of GitLab instance's base API endpoint

##### `gitlab_api_token`

Data type: `Optional[String[1]]`

Optional GitLab personal OAuth token, which may be useful to avoid the GitLab API's unauthenticated rate limits

##### `archived_repos`

Data type: `Boolean`

When true, includes archived projects in results.

##### `visibility`

Data type: `Optional[Array[Enum['public','internal','private']]]`

When set, filters projects by visibility

##### `allow_list`

Data type: `Optional[Array[String[1]]]`

repo names/patterns to include in inventory, drops all other repos

##### `block_list`

Data type: `Optional[Array[String[1]]]`

repo names/patterns to reject from inventory (can reject targets in allow_list)

##### `transport_type`

Data type: `String[1]`

Bolt Transport type of repository Targets

##### `extra_gem_path`

Data type: `Optional[String[1]]`

Additional GEM_PATH path for ruby gems (to find `octokit`)

## Plans

### `gitlab_inventory::count`

Example plan, prints number of Targets from inventory

#### Parameters

The following parameters are available in the `gitlab_inventory::count` plan.

##### `targets`

Data type: `TargetSpec`

By default: `repo_targets` group from inventory

Default value: `'repo_targets'`

##### `gitlab_api_token`

Data type: `String[1]`

GitLab API token.  By default, this will use the `GITHUB_API_TOKEN` environment variable.

Default value: `system::env('GITHUB_API_TOKEN')`

### `gitlab_inventory::latest_semver_tags`

Report the highest SemVer tag for each repo (that has SemVer tags)

* **Note** ONLY reports repos with SemVer tags (ignores `/^v/` and `/-d$/`)

#### Parameters

The following parameters are available in the `gitlab_inventory::latest_semver_tags` plan.

##### `targets`

Data type: `TargetSpec`

By default: `repo_targets` group from inventory

Default value: `'repo_targets'`

##### `gitlab_api_token`

Data type: `Sensitive[String[1]]`

GitLab API token.  By default, this will use the `GITHUB_API_TOKEN` environment variable.

Default value: `(system::env('GITHUB_API_TOKEN'))`

### `gitlab_inventory::required_checks`

List and/or set which PR checks are required on each repo

#### Parameters

The following parameters are available in the `gitlab_inventory::required_checks` plan.

##### `targets`

Data type: `TargetSpec`

By default: `repo_targets` group from inventory

Default value: `'repo_targets'`

##### `gitlab_api_token`

Data type: `Sensitive[String[1]]`

GitLab API token.  By default, this will use the `GITHUB_API_TOKEN` environment variable.

Default value: `(system::env('GITHUB_API_TOKEN'))`

##### `checks`

Data type: `Optional[String[1]]`

Optional comma-delimited list of required PR Checks to set on all repos
If defined, this will overwrite ALL repos' required PR checks

Default value: ``undef``

### `gitlab_inventory::workflows`

Return repos with GitLab Actions workflows

#### Parameters

The following parameters are available in the `gitlab_inventory::workflows` plan.

##### `targets`

Data type: `TargetSpec`

By default: `repo_targets` group from inventory

Default value: `get_targets('repo_targets')`

##### `gitlab_api_token`

Data type: `Sensitive[String[1]]`

GitLab API token.  By default, this will use the `GITHUB_API_TOKEN` environment variable.

Default value: `(system::env('GITHUB_API_TOKEN'))`
