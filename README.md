# Ten Fingers

**The 10-finger typing trainer for macOS.**

Official public home for Ten Fingers, its German and English websites, and community feedback.

## Websites

- [Deutsch](https://www.tenfingers.app/)
- [English](https://en.tenfingers.app/)

## Website projects

The German and English sites are maintained as separate MDU roots in `de/` and `en/`. Each has its own navigation, site name, and assets so it can be rendered and deployed to its own domain. MDU 6.2.0 is pinned in `.config/dotnet-tools.json`; the build workflow pins the matching Docker image by digest. Update both together.

```sh
dotnet tool restore
dotnet mdu lint ./de
dotnet mdu lint ./en
dotnet mdu render ./de ./build/de
dotnet mdu render ./en ./build/en
```

Preview the rendered sites with `python3 -m http.server 8765 --directory build`, then open `http://localhost:8765/de/` or `http://localhost:8765/en/`.

Screenshots are captured from the current macOS app in German and English. Use the complete native macOS window at 1200 × 900 pixels for every scene, including its title bar and window controls. Capture PNGs with transparent corners and no drop shadow (`screencapture -x -o -a -l WINDOW_ID`); do not crop or resize individual scenes. Each scene has matching `-light.png` and `-dark.png` files. Keep paired Markdown images adjacent with identical alternative text and the MDU `#only-light` / `#only-dark` URL markers. Verify both explicit themes and automatic appearance, including the image lightbox, after replacing screenshots. Use real app captures; do not recolour dark screenshots to simulate light mode.

Pull requests render both sites for review. A push to `main` also deploys the build through the GitHub Actions `production` environment. The workflow uploads a release over SSH with a dedicated account that has no Docker or `sudo` access, then atomically switches the active release. The server configuration is in `deploy/`; Nginx serves the two roots read-only behind Traefik.

The website privacy pages describe MDU's browser-local display and navigation preferences. They do not set cookies, and the site does not embed third-party content or run analytics.

## About

Ten Fingers is a native macOS app for learning and practicing touch typing with guided lessons and progress statistics.

## Feedback and support

Use [GitHub Issues](https://github.com/capjan/ten-fingers/issues) for app bug reports, feature ideas, and website feedback. Issues are public, so please do not include personal information or App Store purchase details. For private support, email [support@tenfingers.app](mailto:support@tenfingers.app).

## Auf Deutsch

Dieses Repository ist der öffentliche Anlaufpunkt für Ten Fingers und die gemeinsame Pflege der deutschen und englischen Website. Fehlerberichte zur App, Verbesserungsideen und Hinweise zur Website kannst du über [GitHub Issues](https://github.com/capjan/ten-fingers/issues) einreichen.

Issues sind öffentlich. Bitte teile dort keine persönlichen Daten oder Informationen zu App-Store-Käufen. Für private Supportanfragen schreibe an [support@tenfingers.app](mailto:support@tenfingers.app).
