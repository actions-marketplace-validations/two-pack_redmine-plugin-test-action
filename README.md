# Redmine plugin test action

This action is to test for [Redmine](https://www.redmine.org/) plugin.
It prepares a environment for tests and runs rake command with `redmine:plugins:test`.

## Attention

This plugin uses redmine-test-image docker image, and Autobuilds to support Redmine and ruby versions. However, the free Docker Hub Autobuilds will end on Monday, July 26, 2021.
Therefore, tests in the latest environment will not be provided in a timely.

## Inputs

### `plugin_name`

**Required** The name of the plugin to test.

### `redmine_version`

**Required** The version of Redmine to test, like **v4.1**. You can use matrix in your action.

### `ruby_version`

**Required** The version of Ruby to test, like **v2.6**. You can use matrix in your action.

### `database`

**Optional** The database of Redmine to test. You can choose from **sqlite3 (default), postgresql, mysql**, and can use matrix in your action.

## Outputs

Nothing.

## Example usage

```yaml
- name: Redmine plugin test
  uses: two-pack/redmine-plugin-test-action@v2
  with:
    plugin_name: redmine_auto_assign_group
    redmine_version: v4.1
    ruby_version: v2.6
    database: sqlite3
```

## Notice

* v1 used [Javascript action](https://help.github.com/en/actions/automating-your-workflow-with-github-actions/creating-a-javascript-action). But it's already **not updated**.  
* v2 uses [Docker container action](https://help.github.com/en/actions/automating-your-workflow-with-github-actions/creating-a-docker-container-action) for performance improvement. v2's parameters is **diffrent from v1**, so you **MUST** change action.yml of your workflow if you already used v1.

