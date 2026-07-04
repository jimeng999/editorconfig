# Proposal: Index Exclude Patterns Property

## Issue
[editorconfig/editorconfig #228](https://github.com/editorconfig/editorconfig/issues/228) - Add property for files that should not be listed or not indexed for search [$100]

## Summary
Add a new EditorConfig property `index_exclude_patterns` that specifies file-glob patterns for files that should not be indexed or displayed in search results.

## Proposed Property

### `index_exclude_patterns`
A comma-separated list of file-glob patterns for files that should be excluded from:
1. File tree listings in IDEs/editors
2. Search index results within a repository
3. Auto-complete suggestions

### Example Usage
```ini
# .editorconfig
root = true

[*]
index_exclude_patterns = "**/*.pyc, **/__pycache__/**, **/.DS_Store, **/node_modules/**, **/*.o, **/*.class"

[*.md]
index_exclude_patterns = "**/CHANGELOG.md, **/HISTORY.md"
```

### Analogous Properties in Other Tools
- Sublime Text: `file_exclude_patterns`, `folder_exclude_patterns`, `index_exclude_patterns`
- VS Code: `files.exclude` (workspace settings)
- IntelliJ: `ignored files` patterns

## Implementation Notes
This property would be consumed by EditorConfig plugins for various editors/IDEs.
The core parser would need to recognize and pass through this property.

## Acceptance Criteria
- [ ] Property is recognized by the EditorConfig core parser
- [ ] Documentation added to the spec
- [ ] Example .editorconfig files provided
- [ ] Plugin implementations for major editors (VS Code, Sublime, Vim)
