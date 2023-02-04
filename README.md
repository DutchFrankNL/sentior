# sentior
public repository for sentior developers

# Azure Pipelines for VS Code

[Get it on the VS Code Marketplace!](https://marketplace.visualstudio.com/items?itemName=ms-azure-devops.azure-pipelines)

This VS Code extension adds syntax highlighting and autocompletion for Azure Pipelines YAML to VS Code. It also helps you set up continuous build and deployment for Azure WebApps without leaving VS Code.

## Validation

Basic YAML validation is built in to VS Code, but now you can have syntax highlighting that's aware of the Pipelines YAML schema. This means that you get red squigglies if you say `tasks:` where you meant `task:`. IntelliSense is also schema-aware. Wherever you are in the file, press Ctrl-Space to see what options you have at that point.

By default, the extension will highlight known Azure Pipelines files in the root of your workspace. You can change the language mode at the lower right to work with one file at a time. Click the language picker, then choose "Azure Pipelines". If you have files which should always use this extension, set your user or workspace settings to match those file paths with this extension. For example:

```json
{
    "files.associations": {
        "**/.pipelines/*.yaml": "azure-pipelines"
    }
}
```

### Schema auto-detection

Out of the box, the extension has a generic schema file that includes only in-box tasks.
You probably have custom tasks installed in your organization.

To provide the most relevant IntelliSense, the extension will automatically detect and use your organization's schema! All you need to do is follow the instructions when prompted.

> If automatic fetching of the organization schema doesn't work, try signing out and signing back in using the `Azure: Sign Out` and `Azure: Sign In` commands from the VS Code command palette (Ctrl/Cmd + Shift + P).

### Specific schema

If you need to use a specific schema, that is also possible.

1. Visit `https://dev.azure.com/YOUR-ORG-HERE/_apis/distributedtask/yamlschema` and save the output as `my-schema.json`.
2. Edit your workspace's `settings.json` to include this:
```json
{
  "azure-pipelines.customSchemaFile": "./path/to/my-schema.json"
}
```
