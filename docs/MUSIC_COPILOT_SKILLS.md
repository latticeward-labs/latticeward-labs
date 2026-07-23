# Music Copilot — Team Skills Map

> The capability map for taking Music Copilot from product definition to a stable Android MVP, a 50-driver closed beta, and future legal service integrations.

## Product boundary

### MVP we are building

- Native Android application
- Local, legally owned music files
- Library, artist, album, folder, and search experiences
- Reliable background playback and resume
- Lock-screen and notification controls
- Bluetooth-friendly playback behavior
- A low-distraction Driving Mode
- Push-to-Talk voice interaction
- Six short, direct playback and discovery commands
- Local settings, lightweight history, and privacy-first diagnostics

### Deliberately outside MVP

- Public streaming catalog
- Music downloading or redistribution
- iOS
- User accounts and cloud synchronization
- Conversational AI
- Wake-word listening
- Full Android Auto implementation
- Advanced EQ, DSP, and crossfade
- Artist-upload and distribution panel
- Large backend platform

These are product decisions, not missing ambition. They keep the first release measurable, legal, and achievable.

---

## 1. Product strategy and discovery

| Skill | What the team must know | Expected output |
| --- | --- | --- |
| Product vision | Define the problem, audience, promise, and product principles | One-page product vision |
| PRD writing | Turn user needs into functional and non-functional requirements | Versioned PRD |
| MVP scoping | Separate validation-critical work from future expansion | In/out-of-scope matrix |
| User research | Interview drivers and identify real playback pain points | Interview notes and insights |
| Jobs-to-be-Done | Describe why and when drivers use music controls | Prioritized user jobs |
| Roadmapping | Sequence discovery, build, beta, and learning milestones | Outcome-based roadmap |
| Backlog management | Convert requirements into epics, stories, and acceptance criteria | Prioritized GitHub backlog |
| Metrics design | Define success before implementation | Voice success, tap reduction, retention, crash-free rate |
| Experiment design | Test assumptions with the smallest credible release | Beta and usability test plans |
| Product analytics | Read behavior without collecting unnecessary personal data | Privacy-first event specification |

### MVP success targets

- Direct voice-command success: **85% or higher**
- Operations requiring taps after a voice command: **below 15%**
- Stable playback across background, lock screen, and Bluetooth transitions
- A closed beta with **50 drivers**
- Actionable qualitative feedback about safety, clarity, and usefulness

---

## 2. Android engineering

### Language and platform

- Kotlin
- Android SDK fundamentals
- Jetpack Compose
- Material 3
- Gradle and build variants
- Android permissions and scoped storage
- App lifecycle and process-death recovery
- Foreground services and notification policy
- Device, API-level, and manufacturer compatibility

### Architecture

- Clean or layered architecture
- MVVM or unidirectional data flow
- Multi-module project structure
- SOLID principles and pragmatic abstraction
- Dependency injection with Hilt
- Kotlin Coroutines and Flow
- Error modeling and resilient state management
- Offline-first thinking
- Configuration and feature flags

### Local data

- MediaStore integration
- Room database
- DataStore preferences
- Library indexing and incremental refresh
- Search and filtering
- Local listening history
- Playlist and queue persistence
- Database migrations and data recovery

---

## 3. Audio and media platform engineering

This is a core product discipline, not a secondary feature.

- AndroidX Media3
- ExoPlayer
- MediaSession and controller integration
- Playback queue management
- Background playback
- Notification and lock-screen controls
- Audio Focus and interruption handling
- Headset and Bluetooth media buttons
- Route changes and noisy-audio events
- Resume after process or connection changes
- Metadata, album art, and duration handling
- Corrupt or unsupported-file recovery
- Battery, memory, and startup optimization

### Scenarios the team must test

- Bluetooth connects or disconnects
- Phone call interrupts playback
- Another app requests Audio Focus
- Screen locks during playback
- App moves to background
- Process is killed and restored
- Headset is unplugged
- The local file disappears or becomes unreadable
- Queue changes while Driving Mode is active

---

## 4. Voice interaction engineering

### MVP capability

- Push-to-Talk interaction
- Android speech recognition or an evaluated on-device ASR option
- Six constrained intents
- Entity extraction for song, artist, album, and folder
- Confidence thresholds
- Clear success, ambiguity, and failure feedback
- Short Text-to-Speech confirmations
- Noise-aware error handling
- Fast cancellation and retry
- No always-listening behavior

### Required knowledge

- Automatic Speech Recognition fundamentals
- Intent classification and deterministic command parsing
- Entity normalization and fuzzy matching
- Persian and English language considerations
- Accent, road noise, and Bluetooth microphone behavior
- Latency measurement
- Audio ducking and playback coordination
- Privacy and microphone permission design
- Offline versus cloud recognition tradeoffs
- Voice test datasets and command success analysis

### Future capability

Only after the MVP proves value:

- Wake-word detection
- On-device language models
- Conversational context
- Recommendations
- Personalized voice behavior
- Multilingual NLU
- Safety guardrails for generative AI

---

## 5. Driver-centered UI/UX

- Figma
- Information architecture
- User flows and task modeling
- Wireframing and interactive prototyping
- Design systems and reusable components
- Material 3 patterns
- Dark theme and high-contrast states
- Accessibility and TalkBack
- Localization, RTL, and internationalization
- Motion with purpose
- Usability testing
- Design handoff and specification

### Driving Mode principles

- Large, reachable controls
- Minimal reading
- Strong hierarchy
- One primary action per state
- Glanceable feedback
- High contrast
- No decorative interaction that increases attention
- Safe failure states
- Voice-first, touch-available
- Manual activation in MVP
- Bluetooth-based suggestion only when validated

---

## 6. Quality engineering

### Automated testing

- Kotlin unit tests
- ViewModel and Flow testing
- Repository and database tests
- Media-session tests
- Voice parser and entity matching tests
- Compose UI tests
- Instrumented Android tests
- Snapshot or screenshot regression where useful
- Static analysis with Detekt and Ktlint

### Real-device testing

- Different Android API levels
- Samsung, Xiaomi, Google Pixel, and other relevant device families
- Multiple Bluetooth head units
- Wired and wireless headphones
- Low-memory and battery-saver modes
- Offline behavior
- Road-noise simulations
- Accessibility checks
- Long playback sessions
- Permission denial and recovery

### Release quality

- Definition of Done
- Risk-based test plans
- Regression suites
- Crash-free session monitoring
- Performance budgets
- Battery and memory profiling
- Beta feedback triage
- Release checklists

---

## 7. DevOps and team workflow

- Git and GitHub
- GitHub Issues and Projects
- Small, reviewable pull requests
- Branch protection
- Required code review
- Conventional Commits
- Semantic Versioning
- GitHub Actions
- Automated build, lint, and test pipelines
- Signed Android builds
- Secret management
- Internal and beta release channels
- Google Play Internal Testing
- Release notes and changelogs
- Architecture Decision Records
- Documentation ownership

### Recommended workflow

1. Product requirement becomes an issue.
2. Acceptance criteria and design are attached.
3. Work happens on a short-lived branch.
4. Pull request runs automated checks.
5. Another team member reviews code and UX impact.
6. Approved work is merged into the protected main branch.
7. A tested build moves to Internal Testing.
8. Feedback returns to the backlog as evidence, not opinion.

---

## 8. Observability and learning

- Firebase Crashlytics
- Privacy-limited analytics
- Structured app logging
- ANR monitoring
- Playback failure tracking
- Voice-intent success and fallback tracking
- Performance monitoring
- Beta feedback forms
- Support issue classification
- Experiment and cohort analysis

Collect only what helps improve reliability and product decisions. Avoid recording raw voice, precise routes, contact data, or unnecessary identifiers.

---

## 9. Security, privacy, and legal literacy

### Application security

- Principle of least privilege
- Secure local storage
- Dependency and supply-chain review
- Secret isolation
- Input and file validation
- Safe intent and deep-link handling
- Threat modeling
- Secure network foundations for future APIs

### Privacy

- Data minimization
- Permission transparency
- Microphone-use disclosure
- Local-first processing where possible
- Data retention rules
- Deletion and export planning
- GDPR-aware product design
- Privacy policy and consent language

### Music rights and platform compliance

- Copyright fundamentals
- Sound recording and composition rights
- Local-file playback boundaries
- API and SDK terms
- OAuth scopes and user authorization
- Label, publisher, and distributor roles
- Regional licensing differences
- Google Play policies
- No extraction, redistribution, or replay outside service permissions

Legal review is required before any public catalog, download, artist upload, or standalone streaming model.

---

## 10. Future backend and service integration

These capabilities are intentionally deferred but should influence clean interfaces today.

- REST or GraphQL API design
- OAuth 2.0 and OpenID Connect
- User identity and account security
- PostgreSQL and data modeling
- Cloud storage and CDN fundamentals
- Caching, queues, and background jobs
- Rate limiting and abuse prevention
- Observability and incident response
- Feature flags and staged rollout
- Payment and subscription systems
- Music-service SDK and API integration
- Catalog metadata normalization
- Rights and territory enforcement
- Artist and content administration
- Recommendation systems
- Streaming architecture and DRM fundamentals

A service integration means controlling playback through an authorized API or SDK. It does not mean copying or re-streaming that service's media files.

---

## 11. Team roles

A small team can combine roles, but ownership must remain explicit.

| Role | Primary ownership |
| --- | --- |
| Product Lead | Vision, PRD, priorities, metrics, research |
| Android Engineer | App architecture, Compose, platform behavior |
| Audio Engineer | Media3, playback lifecycle, Bluetooth, reliability |
| Voice/AI Engineer | Recognition, intent parsing, evaluation, privacy |
| Product Designer | UX, Driving Mode, design system, accessibility |
| QA Engineer | Test strategy, device matrix, regression, release quality |
| DevOps/Release Owner | CI/CD, signing, Internal Testing, releases |
| Legal/Content Advisor | Rights, licenses, policies, service contracts |
| Data/Insights Owner | Analytics design, experiments, beta learning |

---

## 12. Delivery path

### Phase 0 — Foundation

- Confirm PRD and MVP
- Define success metrics
- Establish architecture and design system
- Prepare GitHub workflow and quality gates

### Phase 1 — Reliable player

- Local library
- Search
- Queue
- Background playback
- Lock-screen controls
- Bluetooth behavior

### Phase 2 — Driving and voice

- Driving Mode
- Push-to-Talk
- Six commands
- TTS feedback
- Noise and failure handling

### Phase 3 — Closed beta

- Internal testing
- 50-driver beta
- Crash and command analysis
- UX interviews
- Scope decisions based on evidence

### Phase 4 — Version 1.1

- Reliability improvements
- Better song and artist matching
- Local playlists
- Accessibility and localization refinements

### Phase 5 — Legal integrations

- Select approved service partners
- Implement OAuth and supported SDK/API controls
- Complete rights and policy review
- Avoid unauthorized catalog ownership or media redistribution

---

## Working principle

> Learn the whole system, build the smallest trustworthy version, measure real behavior, and expand only with evidence.
