# Copilot Instructions for AI Agents

## Project Overview
This is a dbt (Data Build Tool) project for analytics engineering. The project is organized around dbt's conventions: models, macros, seeds, snapshots, and tests. It supports modular SQL development and leverages dbt's dependency and build system.

## Key Directories & Files
- `models/`: Core SQL models. Subfolders (e.g., `example/`) group related models. Example: `models/first.sql`.
- `macros/`: Custom Jinja macros for reusable SQL logic.
- `seeds/`: CSV files for static data loading.
- `snapshots/`: Track slowly changing dimensions.
- `dbt_project.yml`: Main dbt config (project name, paths, etc.).
- `README.md`: Quickstart, common commands, and dbt resources.
- `dbt_internal_packages/`: Vendor macros and adapters (e.g., `dbt-snowflake`).
- `target/`: Build artifacts, compiled SQL, logs, and run results.

## Developer Workflows
- **Run models:** `dbt run` or `dbt run -s <model_name>`
- **Test models:** `dbt test` or `dbt test -s <model_name>`
- **Debug:** Use `dbt debug` for environment checks.
- **Build artifacts:** Found in `target/` after running dbt commands.

## Project-Specific Patterns
- Models use explicit column naming and can leverage Jinja templating for dynamic SQL.
- Macros are organized by adapter, function, and utility type in `dbt_internal_packages/`.
- Tests are defined in `tests/` and as YAML in model folders (e.g., `models/example/schema.yml`).
- Adapters (e.g., Snowflake) extend dbt via custom macros in `dbt_internal_packages/dbt-snowflake/`.

## Integration Points
- External dependencies managed via dbt packages in `dbt_internal_packages/`.
- Cross-model references use `ref()` and `source()` Jinja functions.
- Custom macros can be imported and used in models for DRY SQL.

## Conventions
- Use singular model names for tables/views.
- Organize models by domain or feature in subfolders.
- Place reusable SQL logic in macros, not models.
- Document models and tests in YAML files alongside SQL.

## Example: Adding a Column
To add a column to a model, edit the relevant SQL file in `models/`:
```sql
select 1 as id, 'prakash' as name
```

## References
- See `README.md` for quickstart and links to dbt docs/community.
- See `dbt_project.yml` for project config and paths.
- See `dbt_internal_packages/` for advanced macro usage and adapter logic.

---
For questions about project structure or workflows, consult the dbt documentation or the README.
