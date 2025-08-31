# Repository Guidelines

## Project Structure & Module Organization
- Source: `src/main/java/lynk/oneblock/**` (base package `lynk.oneblock`).
- Resources: `src/main/resources/` with `fabric.mod.json`, mixins, assets under `assets/`, data packs under `data/`.
- Build output: `build/libs/` (remapped JAR). Gradle cache in `build/`.
- Run configs and logs: `run/` (client/server dev runs).
- Tests (when added): `src/test/java/**` mirroring package structure.

## Build, Test, and Development Commands
- `./gradlew build`: Compile, remap, and package JAR to `build/libs/`.
- `./gradlew runClient`: Launch Fabric dev client with the mod.
- `./gradlew runServer`: Start dedicated dev server.
- `./gradlew runDatagen`: Generate assets/data via Fabric Data Gen.
- `./gradlew clean`: Remove build artifacts.
- `./gradlew test`: Run tests (none yet; see Testing Guidelines).

## Coding Style & Naming Conventions
- Language: Java 17; indent with 4 spaces.
- Packages: `lynk.oneblock.*`.
- Classes: PascalCase; methods/fields: camelCase; constants: UPPER_SNAKE_CASE.
- Mod IDs, registry names, and resource paths: lowercase_with_underscores (e.g., `assets/oneblock/textures/...`).
- Server-only logic in `lynk.oneblock.server`; commands in `lynk.oneblock.command`.

## Testing Guidelines
- Frameworks: Prefer Fabric GameTest for gameplay; JUnit 5 for unit logic.
- Layout: `src/test/java/**` mirroring main packages; name tests `*Test.java` (e.g., `BlockProgressionTest.java`).
- Running: `./gradlew test`. Aim for meaningful coverage on core progression and registry code.

## Commit & Pull Request Guidelines
- Commits: Use Conventional Commits (`feat:`, `fix:`, `chore:`, `docs:`, `refactor:`). Keep subjects ≤72 chars; include concise body and reference issues (e.g., `#123`).
- PRs: Describe changes, link issues, note gameplay/behavior impacts, and attach screenshots/logs when relevant. Verify locally with `runClient`/`runServer`.

## Security & Configuration Tips
- Config path: `minecraft/config/oneblock/OneBlock.json`. Validate user input and provide safe defaults.
- Avoid filesystem access outside Minecraft paths; no blocking I/O on the main thread.
