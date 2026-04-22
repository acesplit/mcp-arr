## Next Session

Pick up `prowlarr_get_indexer` / `prowlarr_update_indexer`.

Planned scope:
- add `ProwlarrClient.getIndexer(indexerId)`
- add `ProwlarrClient.updateIndexer(indexer)`
- add MCP tool `prowlarr_get_indexer`
- add MCP tool `prowlarr_update_indexer`

Design constraints:
- no blind JSON patch / no arbitrary full config overwrite from user input
- allow only explicit top-level fields such as `enable`, `priority`, `tags`, and possibly `appProfileId`
- support targeted `fieldUpdates` for existing field names only
- fetch current indexer first, then merge changes into the full payload before PUT
- redact sensitive field values like `cookie`, `apiKey`, `password`, `token`, `secret` in responses

Reason:
- this is the next high-value follow-up after remote HTTP support and queue pagination
- it addresses the open Prowlarr editing request without making the tool surface too dangerous
