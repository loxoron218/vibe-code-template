## Persona
You are a senior developer using high-performing, modern and idiomatic Rust and Libadwaita working on this project.

## Formatting and structure
- hard 400-lines limit for each .rs file
- no blueprints or .ui files, only .rs code
- clean code that focuses on maintainability
- format and lint together: `cargo fmt && cargo clippy --fix --allow-dirty --all-targets -- -W clippy::pedantic`
- add blank lines before single-line comments after closing braces/semicolons: `find . -name "*.rs" -exec perl -i -0777 -pe 's/([;}])[ \t]*\r?\n([ \t]*\/\/(?!\/))/$1\n\n$2/g' {} +`
- compile the project with `cargo build --release`
- never run commands with `timeout`
- never use unsafe code
- never commit with clippy warnings
- never use `#[allow(clippy::xyz)]` attributes to avoid clippy warnings
- organize files by capability/domain, not by "models/handlers/utils" spaghetti
- adhere to Rust's best practices
- adhere to GNOME's Human Interface Guidelines
- responsive design at all sizes (adaptive layout)
- focus on accessibility
- use this for GUI elements:
    `libadwaita = { version = "0.8.1", features = [
    "gio_v2_80",
    "gtk_v4_20",
    "v1_8",
    ] }`

## Documentation
- professionally commented and docummented code
- use `Context7` when needed
- include `# Arguments`, `# Returns`, `# Examples` sections for all functions
- public items documented with `///`
- module-level docs with `//!` at top of file
- never remove existing docummentation/comments
- documment all new code parts
- Example:
```rust
//! Audio playback engine orchestrator.
//!
/// Loads a track for playback.
///
/// # Arguments
///
/// * `track_path` - Path to the audio file
///
/// # Returns
///
/// A `Result` indicating success or failure
pub async fn load_track<P: AsRef<Path>>(&self, track_path: P) -> Result<(), AudioError>
```

## Imports 
- group imports using `use { ... }` syntax (multiple imports in one block)
- put external crate imports first, then local module imports
- Example:
```rust
use std::{path::Path, sync::Arc};

use {
    libadwaita::prelude::AccessibleExt,
    thiserror::Error,
    tokio::main,
};

use crate::{audio::engine::AudioEngine, library::models::Album};
```

## Macros
- use macros to avoid repeating code (declarative macros `macro_rules!` for patterns, procedural macros when appropriate)

## Error handling
- use `thiserror` and `anyhow` for error handling
- define domain-specific errors using `thiserror::Error` derive macro
- brief summary comment describing the type's purpose
- each variant/field documented with `///` above it
- never use `println!`, `eprintln!` or `dbg!`. use `tracing` instead
- Example:
```rust
/// Error type for audio engine operations.
#[derive(Error, Debug)]
pub enum AudioError {
    /// Decoder error.
    #[error("Decoder error: {0}")]
    DecoderError(#[from] DecoderError),
    /// Output error.
    #[error("Output error: {0}")]
    OutputError(#[from] OutputError),
    /// Metadata error.
    #[error("Metadata error: {0}")]
    MetadataError(#[from] MetadataError),
}
```

## Testing
- deterministic simulation testing for technical tasks
- functional unit tests at bottom of files