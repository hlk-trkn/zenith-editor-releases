# Third-Party Notices

Zenith Editor uses third-party open-source software.

This document provides attribution and license references for key components used by the app.

> This document is provided for informational purposes and is not legal advice.

## Core Dependencies

| Component | Purpose in Zenith Editor | License | Upstream |
|---|---|---|---|
| FFmpeg / ffprobe | Media probing, decode/encode, export pipeline | FFmpeg project: LGPL-2.1-or-later (optional GPL components depending on build) | https://ffmpeg.org |
| whisper.cpp | Local speech-to-text runtime backend | MIT | https://github.com/ggerganov/whisper.cpp |
| OpenAI Whisper | Speech model family / model architecture reference | MIT | https://github.com/openai/whisper |
| whisper-rs | Rust bindings for whisper.cpp in Zenith backend | Unlicense | https://crates.io/crates/whisper-rs |

## FFmpeg Distribution Note

Zenith Editor currently expects FFmpeg to be installed on the user system and does not bundle FFmpeg binaries in the app package.

Because FFmpeg can be built with different codec options, effective license obligations can vary by build.

## Whisper Model Note

Zenith may download GGML Whisper model files from public model hosts.

Model availability, terms, and licensing can vary by source and model variant. Review the model source page terms before production or commercial use.

## License References

- FFmpeg legal: https://ffmpeg.org/legal.html
- whisper.cpp LICENSE (MIT): https://github.com/ggerganov/whisper.cpp/blob/master/LICENSE
- OpenAI Whisper LICENSE (MIT): https://github.com/openai/whisper/blob/main/LICENSE
- whisper-rs crate metadata: https://crates.io/crates/whisper-rs
