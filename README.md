# Roveno — Management Dashboard

[![Live Demo](https://img.shields.io/badge/Live%20Demo-GitHub%20Pages-blue?style=for-the-badge&logo=github)](https://mrchandrayee.github.io/roveno-management-dashboard/)
[![HTML](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)](https://developer.mozilla.org) [![CSS](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)](https://developer.mozilla.org) [![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)](https://developer.mozilla.org)
[![License: MIT](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](./LICENSE)

A responsive vanilla HTML/CSS/JavaScript recreation based on the supplied 5.13-second screen recording (720 × 1280, 30 fps).

## Run
1. Extract `roveno-management-dashboard.zip`.
2. Open `index.html` in Chrome, Edge, Firefox or Safari.
3. No npm install, build tools or server are required.

Optional local server:
```bash
python3 -m http.server 8000
```
Open `http://localhost:8000`.

## What the recording shows

The title card says **Management Dashboard**. The application brand appears as **Roveno**, with workspace breadcrumb **Hondwell** and account **Ollie Mensah — Team & reviews lead**. The dashboard is a dark, compact review and reputation management workspace.

### Visible navigation
- Overview
- Insights
- Reviews
- Pros
- Clients
- Documents
- Inbox
- Settings
- Help

### Overview
- Welcome message: “Good morning, Odile.”
- Reputation score: 3.88 / 5
- 147 reviews this month
- 69% answered
- Median reply time: 2h 54m
- Star mix: 5★ 71%, 4★ 18%, 3★ 6%, 2★ 3%, 1★ 2%
- New reviews: 38
- Replies sent: 23
- Low ratings: 4
- Reviews with photos: 12
- New reviews and reviews needing a reply

### Reviews
- Tabs: To reply, Flagged, Answered
- Search and star-rating filters
- Review list with author, source, date and rating
- Review detail, public reply editor, suggest reply, flag, copy and publish actions

### Pros
- Directory and onboarding views
- Search and status filters (All, Live, Onboarding, Paused)
- Pro cards with trade, rating, review count, jobs and profile actions
- Invite pro form

### Other modules
- Insights: reputation score, review volume chart, sources, star distribution and sentiment
- Clients: client directory, category, review count, account value and status
- Documents: resource cards and upload interaction
- Inbox: conversation list and reply composer
- Settings: workspace and notification preferences
- Help: support topic cards

Also includes a collapsible sidebar, dark/light appearance toggle, notification shortcut, create menu, CSV export and keyboard search (Ctrl/⌘ + K).

## Code excerpt visible in the video

The lower code panel is labelled `src/motion.ts`. The visible function is `slidePill`, a helper that animates a rounded active-navigation highlight by moving its CSS `clip-path` edges.

Readable excerpt, transcribed from the visible panel:

```ts
export function slidePill(pill: HTMLElement, target: HTMLElement) {
  const box = pill.parentElement!, host = pill as HTML & { __st?: Edges };
  const to: Edges = {
    l: target.offsetLeft, t: target.offsetTop,
    r: box.offsetWidth - (target.offsetLeft + target.offsetWidth),
    b: box.offsetHeight - (target.offsetTop + target.offsetHeight)
  };
  const clip = (e: Edges) =>
    `inset(${e.t}px ${e.r}px ${e.b}px ${e.l}px round 11px)`;
  const prev = host.__st ?? { ...to };
  const fwd = to.l > prev.l;
  const [lead, trail] = fwd ? ['l', 'b'] : ['t', 'b'];
  const paint = () => gsap.set(pill, { clipPath: clip(to) });
  gsap.to(st, { [lead]: to[lead], duration: 0.36,
    ease: 'power3.out', onUpdate: paint });
  gsap.to(st, { [trail]: to[trail], duration: 0.55,
    ease: 'power3.inOut', onUpdate: paint });
}
```

Some tiny identifiers in the short code panel are difficult to distinguish; the snippet above preserves the visible structure and animation timings rather than claiming a byte-for-byte source recovery. The runnable dashboard uses CSS active-state transitions and does not depend on GSAP.

## Demo limitations
All review, client, pro, document and inbox records are local sample data reconstructed from visible UI. Forms, filters, review replies, invitation flows, CSV export and theme toggle run in the browser. There is no database, authentication, Google/Facebook review connection, email delivery, document storage, live messaging or production reputation-management backend.

## 👨‍💻 Author

**mrchandrayee** · [GitHub](https://github.com/mrchandrayee)

## 📄 License

[MIT License](./LICENSE)
