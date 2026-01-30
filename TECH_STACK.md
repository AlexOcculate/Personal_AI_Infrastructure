# PAI Technology Stack

This document provides a comprehensive overview of the technologies, programming languages, frameworks, and tools used in the Personal AI Infrastructure (PAI) project.

---

## Core Runtime & Languages

### Primary Runtime
- **[Bun](https://bun.sh)** - Fast all-in-one JavaScript runtime and toolkit
  - Used as the primary runtime for TypeScript/JavaScript execution
  - Provides built-in SQLite support via `bun:sqlite`
  - Handles package management and script execution

### Programming Languages
- **TypeScript** - Primary language for application code
  - Version: ~5.8.3
  - Used for servers, hooks, tools, and utilities
  - Provides type safety across the codebase
  
- **JavaScript** - Configuration and build scripts
  - Used for configuration files (tailwind.config.js, postcss.config.js, etc.)
  
- **Bash/Shell** - System automation and installation
  - Installation scripts
  - Service management scripts
  - Platform-specific automation
  - Count: ~59 shell scripts in the project
  
- **Python** - Document processing and utilities
  - PDF manipulation and form filling
  - DOCX/XLSX/PPTX document processing
  - Office Open XML (OOXML) handling
  - Count: ~30 Python scripts in the project

---

## Frontend Technologies

### Frameworks & Libraries

#### Vue.js Stack (Observability Dashboard)
- **[Vue 3](https://vuejs.org/)** (v3.5.17) - Progressive JavaScript framework
  - Used for the Multi-Agent Observability Dashboard
  - Composition API with TypeScript support
  - Component-based architecture

#### React/Next.js Stack (Telos Dashboard)
- **[Next.js](https://nextjs.org/)** (v15.5.6) - React framework for production
  - Used for the Telos Dashboard Template
  - Server-side rendering and static generation
  
- **[React](https://react.dev/)** (v19.2.0) - UI library
  - Component library with modern React features
  - Used with Next.js for dashboard applications

### UI Component Libraries
- **[Lucide Icons](https://lucide.dev/)**
  - `lucide-vue-next` (v0.548.0) for Vue components
  - `lucide-react` (v0.546.0) for React components
  - Modern icon library with consistent design
  
- **UI Utilities**
  - `class-variance-authority` (v0.7.1) - Type-safe variant API
  - `clsx` (v2.1.1) - Utility for constructing className strings
  - `tailwind-merge` (v3.3.1) - Merge Tailwind CSS classes

### Styling
- **[Tailwind CSS](https://tailwindcss.com/)** (v3.4.16 / v4.1.15)
  - Utility-first CSS framework
  - Used across all frontend applications
  - Custom theme configurations

- **[PostCSS](https://postcss.org/)** (v8.5.3+)
  - CSS transformation and processing
  - Autoprefixer (v10.4.20+) for vendor prefixes

### Build Tools
- **[Vite](https://vitejs.dev/)** (v7.0.4)
  - Fast build tool and dev server for Vue applications
  - Hot module replacement (HMR)
  - Optimized production builds
  
- **[Vue TSC](https://github.com/vuejs/language-tools)** (v2.2.12)
  - TypeScript type checking for Vue components

---

## Backend Technologies

### Database
- **[Bun SQLite](https://bun.sh/docs/api/sqlite)** - Built-in SQLite support
  - Used via `bun:sqlite` module
  - Event storage for observability
  - Local data persistence
  - No external database dependencies

### Web Technologies
- **WebSocket** - Real-time communication
  - Used for live dashboard updates
  - Event streaming from agents to observability server
  - Type definitions: `@types/ws` (v8.5.13)

### API Integration
- **Anthropic Claude API** - Primary AI platform
  - Claude Code integration
  - AI-powered assistance and automation
  
- **Cloud Services** (Optional, pack-specific)
  - Google Cloud TTS (Text-to-Speech)
  - Various API integrations defined in packs

---

## Development Tools

### Type Definitions
- `@types/bun` - Type definitions for Bun runtime
- `@types/node` (v22.11.2 / v24.9.1) - Node.js type definitions
- `@types/react` (v19.2.2) - React type definitions
- `@types/react-dom` (v19.2.2) - React DOM type definitions
- `@types/ws` - WebSocket type definitions

### Configuration
- **TypeScript Compiler** (v5.8.3)
  - Strict type checking
  - Multiple tsconfig files for different contexts
  - ESNext target with modern features

---

## Platform Support

### Operating Systems
- **macOS** - ✅ Fully Supported (primary development platform)
  - LaunchAgent for auto-start
  - osascript for notifications
  - afplay for audio playback
  
- **Linux** - ✅ Fully Supported
  - systemd user services for auto-start
  - notify-send for notifications
  - mpg123/mpv for audio playback
  - Tested on Ubuntu/Debian
  
- **Windows** - ❌ Not Currently Supported
  - Community contributions welcome
  - Requires Task Scheduler, Windows notifications, and audio integration

### Platform Detection
- Shell: `uname -s` for OS detection
- TypeScript/JavaScript: `process.platform` checks
- Conditional execution based on platform

---

## Audio & Multimedia

### Audio Playback
- **macOS**: `afplay` (built-in)
- **Linux**: Auto-detection with fallback chain:
  - mpg123 (preferred)
  - mpv
  - snap/mpv
  
### Text-to-Speech
- Google Cloud TTS integration
- Voice configuration system with JSON-based voice profiles

---

## Architecture Patterns

### Design Philosophy
- **UNIX Philosophy** - Simple, modular, composable tools
- **Transparency** - No magic abstractions
- **Event-Driven** - Hook system for automation
- **Platform-Agnostic** - Cross-platform support where possible

### Code Organization
- **Packs** - Modular installable components
  - Self-contained functionality
  - Independent installation
  - 23+ official packs available
  
- **Bundles** - Pre-configured pack collections
  - Complete system setups
  - Wizard-based installation
  
- **Tools** - Reusable utilities and libraries
  - Shared functionality across packs
  - Validation and backup/restore utilities

---

## Package Management

### Primary Package Manager
- **Bun** - Default package manager
  - Fast dependency installation
  - Compatible with npm packages
  - Lock file: `bun.lock`

### Dependencies Philosophy
- Minimal external dependencies
- Prefer Bun built-ins (`bun:sqlite`, etc.)
- Avoid redundant packages (e.g., use `bun:sqlite` instead of `better-sqlite3`)

---

## Security & Configuration

### Environment Variables
- `.env` file for centralized configuration
- Single source of truth for API keys
- `.env.example` template provided
- Git-ignored by default

### Protected Configuration
- `.pai-protected.json` - Protected paths and resources
- Validation utilities for security checks

---

## Deployment & Process Management

### Service Management
- **macOS**: LaunchAgents (plist configuration)
- **Linux**: systemd user services
- Auto-start capabilities on both platforms

### Directory Structure
- Default installation: `~/.claude/` (Claude Code)
- Custom locations supported
- Platform-specific paths:
  - macOS: `~/Library/LaunchAgents`, `~/Library/Logs`
  - Linux: `~/.config/systemd/user`, `~/.config/pai`

---

## Version Control & CI/CD

### Git Configuration
- `.gitignore` - Excludes build artifacts, dependencies, secrets
- `.gitattributes` - Repository attributes
- GitHub Actions (via `.github/` directory)

---

## Documentation Format

- **Markdown** - All documentation
  - README files
  - Installation guides
  - Workflow documentation
  - API documentation

---

## Notable Dependencies Summary

### Server-Side
- TypeScript ~5.8.3
- Bun (runtime)
- Built-in SQLite (bun:sqlite)
- WebSocket support

### Vue Frontend (Observability)
- Vue 3.5.17
- Vite 7.0.4
- Tailwind CSS 3.4.16
- Lucide Vue Icons

### React Frontend (Telos)
- Next.js 15.5.6
- React 19.2.0
- Tailwind CSS 4.1.15
- Lucide React Icons

---

## External Services & APIs

### AI Platforms
- Anthropic Claude (primary)
- Compatible with:
  - Claude Code
  - Cursor
  - Windsurf
  - OpenCode
  - Custom AI systems

### Optional Integrations (Pack-Specific)
- Google Cloud TTS
- Browser automation (pai-browser-skill)
- OSINT tools (pai-osint-skill)
- Bright Data integration
- Various web services

---

## File Types Distribution

- **Shell Scripts**: ~59 files
- **TypeScript Files**: ~490 files
- **Python Scripts**: ~30 files
- **Vue Components**: ~20 components
- **JSON Configuration**: Multiple package.json and config files

---

## License

See [LICENSE](LICENSE) file for project licensing information.

---

## Contributing

When adding new technologies to PAI:
1. Update this document with the new technology
2. Specify version numbers
3. Explain the purpose and usage
4. Document any platform-specific considerations
5. Follow PAI's principles of simplicity and transparency

---

**Last Updated**: 2026-01-30

For more information about PAI, see [README.md](README.md)
