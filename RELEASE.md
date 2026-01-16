# Release Guide

## Creating a New Release

To create a new release with automatic binary builds:

```bash
./scripts/release.sh 1.0.0
```

This will:
1. Update version in `wails.json`
2. Commit the version bump
3. Create and push a git tag (e.g., `v1.0.0`)
4. Trigger GitHub Actions to build binaries for all platforms
5. Create a GitHub release with all binaries attached

## What Gets Built

The GitHub Actions workflow automatically builds:
- **macOS Intel** (darwin-amd64) - Universal binary
- **macOS Apple Silicon** (darwin-arm64) - Native ARM64 binary
- **Windows** (windows-amd64) - .exe installer
- **Linux** (linux-amd64) - AppImage/executable

## Manual Release

If you prefer to create releases manually:

```bash
# Update version
vim wails.json  # Change version field

# Commit changes
git add wails.json
git commit -m "chore: bump version to 1.0.0"
git push

# Create and push tag
git tag -a v1.0.0 -m "Release 1.0.0"
git push origin v1.0.0
```

## Monitoring Build Progress

After pushing a tag, check:
- **Actions**: https://github.com/yyyumeniku/HyPrism/actions
- **Releases**: https://github.com/yyyumeniku/HyPrism/releases

Builds typically take 10-15 minutes to complete.

## Version Numbering

Follow semantic versioning (MAJOR.MINOR.PATCH):
- **MAJOR**: Breaking changes
- **MINOR**: New features (backward compatible)
- **PATCH**: Bug fixes

Examples:
- `1.0.0` - Initial release
- `1.1.0` - Add new feature
- `1.1.1` - Fix bug
- `2.0.0` - Breaking change
