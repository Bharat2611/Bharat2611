<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Developer Portfolio | Your Name</title>
  <meta name="description" content="Professional GitHub portfolio of a software engineer showcasing skills, projects, and experience." />

  <!-- Typography -->
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet" />

  <style>
    :root {
      --bg: #0b1020;
      --bg-elevated: #151a2c;
      --bg-soft: #101525;
      --text: #f5f7ff;
      --muted: #a6aec9;
      --accent: #4f8cff;
      --accent-soft: rgba(79, 140, 255, 0.16);
      --border-subtle: rgba(255, 255, 255, 0.06);
      --danger: #ff6363;

      --font-sans: "Inter", system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI",
        sans-serif;

      --radius-lg: 16px;
      --radius-md: 12px;
      --radius-pill: 999px;

      --shadow-soft: 0 18px 45px rgba(0, 0, 0, 0.6);
      --transition-fast: 180ms ease-out;
      --transition-med: 220ms ease;

      --nav-height: 68px;
    }

    /* Light mode */
    :root[data-theme="light"] {
      --bg: #f4f5fb;
      --bg-elevated: #ffffff;
      --bg-soft: #e5e8f2;
      --text: #141627;
      --muted: #5d6680;
      --accent: #2563eb;
      --accent-soft: rgba(37, 99, 235, 0.12);
      --border-subtle: rgba(15, 23, 42, 0.08);
      --shadow-soft: 0 18px 45px rgba(15, 23, 42, 0.12);
    }

    *,
    *::before,
    *::after {
      box-sizing: border-box;
    }

    html {
      scroll-behavior: smooth;
    }

    body {
      margin: 0;
      min-height: 100vh;
      font-family: var(--font-sans);
      background: radial-gradient(circle at top, #151a30 0, var(--bg) 50%);
      color: var(--text);
      -webkit-font-smoothing: antialiased;
      text-rendering: optimizeLegibility;
    }

    img {
      max-width: 100%;
      display: block;
    }

    a {
      color: inherit;
      text-decoration: none;
    }

    button {
      font-family: inherit;
      border: none;
      background: none;
      cursor: pointer;
    }

    /* Layout */

    .page {
      max-width: 1120px;
      margin: 0 auto;
      padding: 0 1.5rem 4rem;
    }

    .skip-link {
      position: absolute;
      left: -999px;
      top: 8px;
      padding: 0.5rem 1rem;
      background: var(--accent);
      color: #ffffff;
      border-radius: var(--radius-pill);
      z-index: 1000;
      font-size: 0.9rem;
    }

    .skip-link:focus-visible {
      left: 12px;
      outline: 2px solid #ffffff;
      outline-offset: 2px;
    }

    header.site-header {
      position: sticky;
      top: 0;
      z-index: 999;
      backdrop-filter: blur(14px);
      background: linear-gradient(
        to bottom,
        rgba(6, 10, 25, 0.9),
        rgba(6, 10, 25, 0.7),
        transparent
      );
    }

    .nav {
      max-width: 1120px;
      margin: 0 auto;
      padding: 0.75rem 1.5rem;
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 1.5rem;
    }

    .nav-left {
      display: inline-flex;
      align-items: center;
      gap: 0.5rem;
    }

    .nav-logo {
      width: 32px;
      height: 32px;
      border-radius: 40% 60% 60% 40%;
      background: radial-gradient(circle at 30% 30%, #e5f0ff, #4f8cff 40%, #151a2c 72%);
      box-shadow: 0 0 0 2px rgba(79, 140, 255, 0.5);
    }

    .nav-title {
      font-weight: 600;
      letter-spacing: 0.02em;
      font-size: 0.95rem;
    }

    .nav-links {
      display: flex;
      align-items: center;
      gap: 0.75rem;
    }

    .nav-links a {
      font-size: 0.9rem;
      padding: 0.35rem 0.8rem;
      border-radius: 999px;
      color: var(--muted);
      transition: color var(--transition-fast), background var(--transition-fast),
        transform var(--transition-fast);
    }

    .nav-links a:hover,
    .nav-links a:focus-visible {
      color: var(--text);
      background: rgba(255, 255, 255, 0.04);
      transform: translateY(-1px);
    }

    .nav-links a.active {
      color: var(--text);
      background: var(--accent-soft);
    }

    .nav-actions {
      display: flex;
      align-items: center;
      gap: 0.5rem;
    }

    .theme-toggle {
      width: 40px;
      height: 22px;
      border-radius: 999px;
      background: var(--bg-soft);
      border: 1px solid var(--border-subtle);
      display: inline-flex;
      align-items: center;
      padding: 2px;
      position: relative;
    }

    .theme-toggle-thumb {
      width: 16px;
      height: 16px;
      border-radius: 50%;
      background: #ffffff;
      transform: translateX(0);
      transition: transform var(--transition-med), background var(--transition-fast);
      box-shadow: 0 2px 6px rgba(15, 23, 42, 0.5);
    }

    :root[data-theme="light"] .theme-toggle-thumb {
      transform: translateX(18px);
    }

    .theme-toggle-icon {
      position: absolute;
      font-size: 0.7rem;
      opacity: 0.65;
      transition: opacity var(--transition-fast), transform var(--transition-fast);
    }

    .theme-toggle-icon.sun {
      left: 6px;
    }

    .theme-toggle-icon.moon {
      right: 6px;
    }

    :root[data-theme="light"] .theme-toggle-icon.sun {
      opacity: 1;
      transform: translateY(-1px);
    }

    :root[data-theme="light"] .theme-toggle-icon.moon {
      opacity: 0;
    }

    :root:not([data-theme="light"]) .theme-toggle-icon.sun {
      opacity: 0;
    }

    :root:not([data-theme="light"]) .theme-toggle-icon.moon {
      opacity: 1;
      transform: translateY(-1px);
    }

    .nav-cta {
      padding: 0.4rem 0.9rem;
      border-radius: 999px;
      border: 1px solid var(--border-subtle);
      background: rgba(15, 23, 42, 0.8);
      color: var(--muted);
      font-size: 0.8rem;
      display: inline-flex;
      align-items: center;
      gap: 0.35rem;
      transition: background var(--transition-fast), color var(--transition-fast),
        transform var(--transition-fast), box-shadow var(--transition-fast);
    }

    .nav-cta:hover,
    .nav-cta:focus-visible {
      background: var(--accent-soft);
      color: var(--text);
      box-shadow: 0 0 0 1px rgba(79, 140, 255, 0.2);
      transform: translateY(-1px);
    }

    .nav-burger {
      display: none;
      flex-direction: column;
      gap: 4px;
    }

    .nav-burger span {
      width: 18px;
      height: 2px;
      background: var(--text);
      border-radius: 999px;
      transition: transform var(--transition-fast), opacity var(--transition-fast);
    }

    .nav-burger.open span:nth-child(1) {
      transform: translateY(3px) rotate(45deg);
    }

    .nav-burger.open span:nth-child(2) {
      opacity: 0;
    }

    .nav-burger.open span:nth-child(3) {
      transform: translateY(-3px) rotate(-45deg);
    }

    .nav-links-mobile {
      display: none;
    }

    main {
      padding-top: 1.5rem;
    }

    section {
      padding: 3rem 0 0;
    }

    section:first-of-type {
      padding-top: 2rem;
    }

    .section-heading {
      display: inline-flex;
      align-items: center;
      gap: 0.5rem;
      font-size: 0.85rem;
      letter-spacing: 0.16em;
      text-transform: uppercase;
      color: var(--muted);
      margin-bottom: 0.9rem;
    }

    .section-heading-dot {
      width: 7px;
      height: 7px;
      border-radius: 999px;
      background: var(--accent);
      box-shadow: 0 0 0 4px rgba(79, 140, 255, 0.22);
    }

    .section-title {
      font-size: clamp(1.6rem, 2vw + 1rem, 2rem);
      margin: 0 0 0.75rem;
    }

    .section-subtitle {
      margin: 0;
      color: var(--muted);
      font-size: 0.95rem;
      max-width: 520px;
    }

    /* Hero */

    .hero {
      display: grid;
      grid-template-columns: minmax(0, 2.1fr) minmax(0, 1.6fr);
      gap: 2.5rem;
      align-items: center;
    }

    .badge {
      display: inline-flex;
      align-items: center;
      gap: 0.4rem;
      padding: 0.25rem 0.7rem;
      border-radius: 999px;
      border: 1px solid var(--border-subtle);
      background: linear-gradient(
        135deg,
        rgba(79, 140, 255, 0.22),
        rgba(10, 16, 36, 0.96)
      );
      color: #e5edff;
      font-size: 0.75rem;
      margin-bottom: 0.7rem;
    }

    .badge-dot {
      width: 7px;
      height: 7px;
      border-radius: 999px;
      background: #4ade80;
      box-shadow: 0 0 0 4px rgba(22, 163, 74, 0.4);
    }

    .hero-title {
      font-size: clamp(2.4rem, 3.4vw + 1rem, 3.4rem);
      line-height: 1.05;
      letter-spacing: -0.04em;
      margin: 0 0 0.75rem;
    }

    .hero-title span {
      display: inline-block;
      background: linear-gradient(120deg, #60a5ff, #a855f7 55%, #fb7185);
      -webkit-background-clip: text;
      color: transparent;
    }

    .hero-role {
      display: inline-flex;
      flex-wrap: wrap;
      gap: 0.5rem;
      align-items: center;
      font-size: 0.9rem;
      color: var(--muted);
      margin-bottom: 0.9rem;
    }

    .hero-role-pill {
      padding: 0.2rem 0.75rem;
      border-radius: 999px;
      background: rgba(17, 24, 39, 0.8);
      border: 1px solid rgba(148, 163, 184, 0.45);
      font-size: 0.75rem;
      letter-spacing: 0.09em;
      text-transform: uppercase;
    }

    :root[data-theme="light"] .hero-role-pill {
      background: #eef1ff;
      border-color: rgba(37, 99, 235, 0.32);
    }

    .hero-tagline {
      margin: 0 0 1.3rem;
      color: var(--muted);
      max-width: 520px;
      font-size: 0.95rem;
    }

    .hero-actions {
      display: flex;
      flex-wrap: wrap;
      gap: 0.75rem;
      align-items: center;
      margin-bottom: 1rem;
    }

    .btn {
      padding: 0.65rem 1.2rem;
      border-radius: var(--radius-pill);
      font-size: 0.9rem;
      display: inline-flex;
      align-items: center;
      gap: 0.4rem;
      border: 1px solid transparent;
      transition: background var(--transition-med), transform var(--transition-fast),
        box-shadow var(--transition-fast), border-color var(--transition-fast);
      white-space: nowrap;
    }

    .btn-primary {
      background: linear-gradient(135deg, #4f8cff, #6366f1);
      color: #ffffff;
      box-shadow: 0 16px 35px rgba(37, 99, 235, 0.45);
    }

    .btn-primary:hover,
    .btn-primary:focus-visible {
      transform: translateY(-1px);
      box-shadow: 0 22px 55px rgba(37, 99, 235, 0.6);
    }

    .btn-ghost {
      background: rgba(15, 23, 42, 0.75);
      border-color: var(--border-subtle);
      color: var(--muted);
    }

    :root[data-theme="light"] .btn-ghost {
      background: #e5e7f5;
      color: #374151;
    }

    .btn-ghost:hover,
    .btn-ghost:focus-visible {
      background: var(--accent-soft);
      color: var(--text);
      transform: translateY(-1px);
      border-color: rgba(79, 140, 255, 0.4);
    }

    .hero-meta {
      display: flex;
      flex-wrap: wrap;
      gap: 1rem;
      font-size: 0.8rem;
      color: var(--muted);
    }

    .hero-meta-item span {
      display: block;
    }

    .hero-meta-label {
      text-transform: uppercase;
      letter-spacing: 0.16em;
      font-size: 0.75rem;
      margin-bottom: 0.2rem;
    }

    .hero-meta-value {
      font-weight: 500;
      color: var(--text);
    }

    .hero-visual {
      position: relative;
    }

    .hero-card {
      position: relative;
      padding: 1.2rem 1.3rem;
      border-radius: 24px;
      background: radial-gradient(circle at 0% 0%, #334155 0, #020617 60%);
      border: 1px solid rgba(148, 163, 184, 0.55);
      box-shadow: var(--shadow-soft);
      overflow: hidden;
      isolation: isolate;
    }

    :root[data-theme="light"] .hero-card {
      background: radial-gradient(circle at 0% 0%, #e0ecff 0, #ffffff 65%);
      border-color: rgba(148, 163, 184, 0.3);
    }

    .hero-card-header {
      display: flex;
      align-items: center;
      gap: 0.75rem;
      margin-bottom: 1rem;
    }

    .hero-avatar {
      width: 48px;
      height: 48px;
      border-radius: 18px;
      background: conic-gradient(from 180deg, #4f8cff, #a855f7, #22c55e, #4f8cff);
      padding: 2px;
    }

    .hero-avatar-inner {
      width: 100%;
      height: 100%;
      border-radius: inherit;
      background: radial-gradient(circle at 30% 20%, #f9fafb, #020617);
      display: grid;
      place-items: center;
      color: #e5edff;
      font-weight: 600;
      font-size: 1.2rem;
    }

    :root[data-theme="light"] .hero-avatar-inner {
      background: radial-gradient(circle at 30% 20%, #ffffff, #1f2937);
      color: #0b1020;
    }

    .hero-card-title {
      font-size: 0.95rem;
      font-weight: 500;
    }

    .hero-card-sub {
      font-size: 0.75rem;
      color: var(--muted);
    }

    .hero-card-body {
      display: grid;
      gap: 0.75rem;
      font-size: 0.8rem;
      color: var(--muted);
    }

    .hero-card-tags {
      display: flex;
      flex-wrap: wrap;
      gap: 0.35rem;
    }

    .chip {
      padding: 0.2rem 0.55rem;
      border-radius: 999px;
      border: 1px solid rgba(148, 163, 184, 0.6);
      background: rgba(15, 23, 42, 0.85);
      font-size: 0.7rem;
    }

    :root[data-theme="light"] .chip {
      background: #eef2ff;
      border-color: rgba(148, 163, 184, 0.4);
      color: #1f2933;
    }

    .hero-card-footer {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-top: 0.75rem;
      font-size: 0.75rem;
      color: var(--muted);
    }

    .hero-card-status {
      display: inline-flex;
      align-items: center;
      gap: 0.3rem;
    }

    .status-dot {
      width: 7px;
      height: 7px;
      border-radius: 999px;
      background: #22c55e;
      box-shadow: 0 0 0 4px rgba(34, 197, 94, 0.35);
    }

    .hero-card-overlay {
      position: absolute;
      inset: -40%;
      background:
        radial-gradient(circle at 0% 0%, rgba(59, 130, 246, 0.7), transparent 60%),
        radial-gradient(circle at 100% 0%, rgba(147, 51, 234, 0.7), transparent 60%);
      mix-blend-mode: screen;
      opacity: 0.4;
      pointer-events: none;
    }

    :root[data-theme="light"] .hero-card-overlay {
      mix-blend-mode: normal;
      opacity: 0.3;
    }

    .hero-card-grid {
      display: grid;
      grid-template-columns: repeat(3, minmax(0, 1fr));
      gap: 0.75rem;
      margin-top: 0.75rem;
    }

    .hero-card-pill {
      padding: 0.5rem 0.6rem;
      border-radius: 14px;
      background: rgba(15, 23, 42, 0.9);
      border: 1px solid rgba(148, 163, 184, 0.45);
      display: grid;
      gap: 0.15rem;
      font-size: 0.7rem;
    }

    :root[data-theme="light"] .hero-card-pill {
      background: rgba(248, 250, 252, 0.98);
      border-color: rgba(148, 163, 184, 0.4);
    }

    .hero-pill-label {
      color: var(--muted);
    }

    .hero-pill-value {
      color: var(--text);
      font-weight: 500;
    }

    /* About */

    .about {
      display: grid;
      grid-template-columns: minmax(0, 1.7fr) minmax(0, 1.3fr);
      gap: 2rem;
      margin-top: 1rem;
    }

    .about-text {
      font-size: 0.95rem;
      color: var(--muted);
      line-height: 1.7;
    }

    .about-highlight {
      color: var(--text);
    }

    .about-grid {
      display: grid;
      grid-template-columns: repeat(2, minmax(0, 1fr));
      gap: 0.85rem;
    }

    .about-stat {
      padding: 0.7rem 0.9rem;
      border-radius: var(--radius-md);
      border: 1px dashed rgba(148, 163, 184, 0.55);
      background: rgba(15, 23, 42, 0.85);
      font-size: 0.8rem;
      color: var(--muted);
    }

    :root[data-theme="light"] .about-stat {
      background: #f3f4ff;
      border-style: solid;
    }

    .about-stat-value {
      display: block;
      font-size: 1.1rem;
      color: var(--text);
      font-weight: 600;
      margin-bottom: 0.15rem;
    }

    /* Skills */

    .skills-grid {
      display: grid;
      grid-template-columns: minmax(0, 1.4fr) minmax(0, 1.6fr);
      gap: 2rem;
      margin-top: 1rem;
    }

    .skill-group-title {
      font-size: 0.85rem;
      letter-spacing: 0.14em;
      text-transform: uppercase;
      color: var(--muted);
      margin-bottom: 0.5rem;
    }

    .skill-tags {
      display: flex;
      flex-wrap: wrap;
      gap: 0.4rem;
    }

    .skill-tag {
      padding: 0.25rem 0.6rem;
      border-radius: 999px;
      border: 1px solid rgba(148, 163, 184, 0.6);
      font-size: 0.75rem;
      color: var(--muted);
      background: rgba(15, 23, 42, 0.9);
      display: inline-flex;
      align-items: center;
      gap: 0.4rem;
    }

    :root[data-theme="light"] .skill-tag {
      background: #eef2ff;
    }

    .skill-dot {
      width: 7px;
      height: 7px;
      border-radius: 999px;
      background: var(--accent);
    }

    .skill-meters {
      display: grid;
      gap: 0.8rem;
    }

    .skill-meter {
      display: grid;
      gap: 0.35rem;
    }

    .skill-meter-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      font-size: 0.8rem;
      color: var(--muted);
    }

    .skill-meter-name {
      color: var(--text);
      font-weight: 500;
    }

    .meter-track {
      position: relative;
      height: 7px;
      border-radius: 999px;
      background: rgba(30, 64, 175, 0.35);
      overflow: hidden;
    }

    :root[data-theme="light"] .meter-track {
      background: rgba(148, 163, 184, 0.25);
    }

    .meter-fill {
      position: absolute;
      inset: 0;
      transform-origin: left;
      transform: scaleX(0);
      border-radius: inherit;
      background: linear-gradient(90deg, #4f8cff, #a855f7);
    }

    .meter-fill.visible {
      transform: scaleX(var(--value, 0.75));
      transition: transform 900ms cubic-bezier(0.26, 0.76, 0.27, 0.99);
    }

    /* Projects */

    .projects-grid {
      display: grid;
      grid-template-columns: repeat(3, minmax(0, 1fr));
      gap: 1.2rem;
      margin-top: 1.2rem;
    }

    .project-card {
      position: relative;
      padding: 1rem 0.95rem;
      border-radius: var(--radius-lg);
      background: radial-gradient(circle at 0% 0%, #1f2937 0, #020617 65%);
      border: 1px solid rgba(148, 163, 184, 0.7);
      box-shadow: 0 18px 35px rgba(15, 23, 42, 0.75);
      display: grid;
      gap: 0.5rem;
      font-size: 0.83rem;
      color: var(--muted);
      transform-origin: center;
      transition: transform var(--transition-med), box-shadow var(--transition-med),
        border-color var(--transition-med), background var(--transition-med);
    }

    :root[data-theme="light"] .project-card {
      background: radial-gradient(circle at 0% 0%, #e5edff 0, #ffffff 65%);
      border-color: rgba(148, 163, 184, 0.4);
      box-shadow: var(--shadow-soft);
    }

    .project-card:hover {
      transform: translateY(-4px) scale(1.01);
      border-color: rgba(79, 140, 255, 0.85);
      box-shadow: 0 22px 55px rgba(15, 23, 42, 0.92);
      background: radial-gradient(circle at 0% 0%, #1d283a 0, #020617 80%);
    }

    :root[data-theme="light"] .project-card:hover {
      background: radial-gradient(circle at 0% 0%, #dbeafe 0, #eff6ff 45%, #ffffff 70%);
      box-shadow: 0 24px 60px rgba(15, 23, 42, 0.18);
    }

    .project-title {
      font-size: 0.95rem;
      font-weight: 500;
      color: var(--text);
      display: flex;
      justify-content: space-between;
      align-items: center;
      gap: 0.5rem;
    }

    .project-badge {
      font-size: 0.7rem;
      padding: 0.15rem 0.45rem;
      border-radius: 999px;
      background: rgba(15, 23, 42, 0.85);
      border: 1px solid rgba(148, 163, 184, 0.6);
      color: var(--muted);
    }

    :root[data-theme="light"] .project-badge {
      background: #eef2ff;
    }

    .project-desc {
      margin: 0;
      line-height: 1.5;
    }

    .project-meta {
      display: flex;
      justify-content: space-between;
      align-items: flex-end;
      margin-top: 0.4rem;
      gap: 0.5rem;
    }

    .project-stack {
      display: flex;
      flex-wrap: wrap;
      gap: 0.25rem;
      font-size: 0.72rem;
    }

    .project-stack span {
      padding: 0.15rem 0.45rem;
      border-radius: 999px;
      background: rgba(15, 23, 42, 0.9);
      border: 1px solid rgba(148, 163, 184, 0.6);
    }

    :root[data-theme="light"] .project-stack span {
      background: #eef2ff;
    }

    .project-links {
      display: inline-flex;
      gap: 0.4rem;
      font-size: 0.75rem;
    }

    .project-link {
      display: inline-flex;
      align-items: center;
      gap: 0.2rem;
      padding: 0.2rem 0.45rem;
      border-radius: 999px;
      color: var(--muted);
      background: rgba(15, 23, 42, 0.85);
      border: 1px solid rgba(148, 163, 184, 0.6);
      transition: background var(--transition-fast), color var(--transition-fast),
        transform var(--transition-fast), border-color var(--transition-fast);
    }

    :root[data-theme="light"] .project-link {
      background: #eef2ff;
    }

    .project-link:hover,
    .project-link:focus-visible {
      background: var(--accent-soft);
      color: var(--text);
      border-color: rgba(79, 140, 255, 0.75);
      transform: translateY(-1px);
    }

    /* Experience */

    .timeline {
      position: relative;
      margin-top: 1.4rem;
      padding-left: 1.1rem;
    }

    .timeline::before {
      content: "";
      position: absolute;
      left: 4px;
      top: 0;
      bottom: 0;
      width: 1px;
      background: linear-gradient(
        to bottom,
        rgba(148, 163, 184, 0.5),
        rgba(79, 140, 255, 0.8)
      );
    }

    .timeline-item {
      position: relative;
      padding-left: 1.1rem;
      padding-bottom: 1.4rem;
    }

    .timeline-item:last-child {
      padding-bottom: 0;
    }

    .timeline-marker {
      position: absolute;
      left: -3px;
      top: 0.35rem;
      width: 9px;
      height: 9px;
      border-radius: 999px;
      background: var(--accent);
      box-shadow: 0 0 0 5px rgba(79, 140, 255, 0.26);
    }

    .timeline-heading {
      display: flex;
      justify-content: space-between;
      align-items: baseline;
      gap: 0.5rem;
    }

    .timeline-role {
      font-size: 0.9rem;
      font-weight: 500;
      color: var(--text);
    }

    .timeline-meta {
      font-size: 0.78rem;
      color: var(--muted);
    }

    .timeline-org {
      font-size: 0.8rem;
      color: var(--muted);
      margin-top: 0.15rem;
    }

    .timeline-body {
      margin-top: 0.35rem;
      font-size: 0.8rem;
      color: var(--muted);
      line-height: 1.6;
    }

    /* Contact */

    .contact-grid {
      display: grid;
      grid-template-columns: minmax(0, 1.4fr) minmax(0, 1.6fr);
      gap: 2rem;
      margin-top: 1.1rem;
    }

    .contact-card {
      padding: 1rem 1.1rem;
      border-radius: var(--radius-lg);
      background: radial-gradient(circle at 0% 0%, #1f2937 0, #020617 65%);
      border: 1px solid rgba(148, 163, 184, 0.6);
      box-shadow: var(--shadow-soft);
      font-size: 0.85rem;
      color: var(--muted);
    }

    :root[data-theme="light"] .contact-card {
      background: radial-gradient(circle at 0% 0%, #e5edff 0, #ffffff 75%);
      border-color: rgba(148, 163, 184, 0.4);
    }

    .contact-row {
      display: flex;
      flex-wrap: wrap;
      align-items: center;
      gap: 0.75rem;
      margin-top: 0.6rem;
    }

    .contact-link {
      display: inline-flex;
      align-items: center;
      gap: 0.4rem;
      padding: 0.35rem 0.75rem;
      border-radius: 999px;
      background: rgba(15, 23, 42, 0.9);
      border: 1px solid rgba(148, 163, 184, 0.6);
      font-size: 0.8rem;
      color: var(--muted);
      transition: background var(--transition-fast), color var(--transition-fast),
        transform var(--transition-fast), border-color var(--transition-fast);
    }

    :root[data-theme="light"] .contact-link {
      background: #eef2ff;
    }

    .contact-link:hover,
    .contact-link:focus-visible {
      background: var(--accent-soft);
      color: var(--text);
      transform: translateY(-1px);
      border-color: rgba(79, 140, 255, 0.75);
    }

    .contact-icon {
      width: 18px;
      height: 18px;
      border-radius: 999px;
      display: inline-flex;
      align-items: center;
      justify-content: center;
      font-size: 0.75rem;
      background: rgba(15, 23, 42, 0.95);
    }

    :root[data-theme="light"] .contact-icon {
      background: rgba(15, 23, 42, 0.03);
    }

    .contact-note {
      margin-top: 0.75rem;
      font-size: 0.78rem;
      color: var(--muted);
    }

    .contact-note strong {
      color: var(--text);
    }

    .contact-meta {
      font-size: 0.8rem;
      color: var(--muted);
      line-height: 1.7;
    }

    .contact-meta-list {
      margin-top: 0.65rem;
      display: grid;
      gap: 0.35rem;
      font-size: 0.8rem;
    }

    .contact-meta-item {
      display: inline-flex;
      align-items: center;
      gap: 0.4rem;
    }

    .contact-meta-bullet {
      width: 5px;
      height: 5px;
      border-radius: 999px;
      background: var(--accent);
    }

    footer {
      max-width: 1120px;
      margin: 2.5rem auto 0;
      padding: 0 1.5rem 0;
      border-top: 1px solid rgba(148, 163, 184, 0.32);
      font-size: 0.78rem;
      color: var(--muted);
      display: flex;
      justify-content: space-between;
      gap: 0.5rem;
    }

    footer span {
      display: inline-flex;
      align-items: center;
      gap: 0.25rem;
    }

    footer span:last-child {
      opacity: 0.9;
    }

    /* Utilities */

    .visually-hidden {
      border: 0;
      clip: rect(0 0 0 0);
      height: 1px;
      margin: -1px;
      overflow: hidden;
      padding: 0;
      position: absolute;
      width: 1px;
    }

    /* Responsive */

    @media (max-width: 900px) {
      .hero {
        grid-template-columns: minmax(0, 1.6fr) minmax(0, 1.6fr);
        gap: 2rem;
      }

      .projects-grid {
        grid-template-columns: repeat(2, minmax(0, 1fr));
      }

      .skills-grid,
      .about,
      .contact-grid {
        grid-template-columns: minmax(0, 1fr);
      }
    }

    @media (max-width: 720px) {
      .nav-links {
        display: none;
      }

      .nav-burger {
        display: inline-flex;
      }

      .nav-links-mobile {
        display: grid;
        gap: 0.1rem;
        padding: 0 1.5rem 0.7rem;
        background: rgba(6, 10, 25, 0.98);
        border-bottom: 1px solid rgba(148, 163, 184, 0.45);
      }

      :root[data-theme="light"] .nav-links-mobile {
        background: rgba(239, 241, 251, 0.98);
        border-color: rgba(148, 163, 184, 0.35);
      }

      .nav-links-mobile a {
        padding: 0.45rem 0.3rem;
        border-radius: 12px;
        font-size: 0.9rem;
        color: var(--muted);
      }

      .nav-links-mobile a:hover,
      .nav-links-mobile a:focus-visible {
        background: rgba(15, 23, 42, 0.04);
        color: var(--text);
      }

      .hero {
        grid-template-columns: minmax(0, 1fr);
      }

      .hero-visual {
        order: -1;
      }

      .projects-grid {
        grid-template-columns: minmax(0, 1fr);
      }

      .page {
        padding-inline: 1.1rem;
      }

      .nav {
        padding-inline: 1.1rem;
      }

      footer {
        flex-direction: column;
        align-items: flex-start;
        padding-inline: 1.1rem;
      }
    }

    @media (prefers-reduced-motion: reduce) {
      html {
        scroll-behavior: auto;
      }

      * {
        animation-duration: 0.001ms !important;
        animation-iteration-count: 1 !important;
        transition-duration: 0.001ms !important;
        scroll-behavior: auto !important;
      }
    }
  </style>
</head>
<body>
  <a href="#main" class="skip-link">Skip to main content</a>

  <header class="site-header">
    <nav class="nav" aria-label="Primary">
      <div class="nav-left">
        <div class="nav-logo" aria-hidden="true"></div>
        <div class="nav-title" aria-label="Site name">
          Your Name
        </div>
      </div>

      <div class="nav-links" role="list">
        <a href="#about" class="nav-link active">About</a>
        <a href="#skills" class="nav-link">Skills</a>
        <a href="#projects" class="nav-link">Projects</a>
        <a href="#experience" class="nav-link">Experience</a>
        <a href="#contact" class="nav-link">Contact</a>
      </div>

      <div class="nav-actions">
        <button
          class="theme-toggle"
          id="themeToggle"
          type="button"
          aria-label="Toggle dark and light theme"
        >
          <span class="theme-toggle-thumb"></span>
          <span class="theme-toggle-icon sun" aria-hidden="true">☀︎</span>
          <span class="theme-toggle-icon moon" aria-hidden="true">☾</span>
        </button>

        <a
          href="https://github.com/your-username"
          target="_blank"
          rel="noreferrer"
          class="nav-cta"
        >
          <span>GitHub</span>
          <span aria-hidden="true">↗</span>
        </a>

        <button
          class="nav-burger"
          id="navBurger"
          type="button"
          aria-label="Toggle navigation"
          aria-expanded="false"
        >
          <span></span>
          <span></span>
          <span></span>
        </button>
      </div>
    </nav>

    <div class="nav-links-mobile" id="navMobile" aria-label="Mobile navigation">
      <a href="#about" class="nav-link">About</a>
      <a href="#skills" class="nav-link">Skills</a>
      <a href="#projects" class="nav-link">Projects</a>
      <a href="#experience" class="nav-link">Experience</a>
      <a href="#contact" class="nav-link">Contact</a>
    </div>
  </header>

  <div class="page">
    <main id="main">
      <!-- Hero -->
      <section aria-labelledby="hero-heading">
        <div class="hero">
          <div>
            <div class="badge">
              <span class="badge-dot" aria-hidden="true"></span>
              <span>Open to backend-heavy roles</span>
            </div>

            <h1 id="hero-heading" class="hero-title">
              Building reliable<br />
              <span>developer‑first experiences.</span>
            </h1>

            <div class="hero-role">
              <span class="hero-role-pill">Full Stack Developer</span>
              <span>Java · JavaScript · Laravel</span>
            </div>

            <p class="hero-tagline">
              Software engineer focusing on maintainable architectures, clean APIs,
              and thoughtful UI engineering for web products that scale gracefully.
            </p>

            <div class="hero-actions">
              <a href="#projects" class="btn btn-primary">
                View projects
                <span aria-hidden="true">→</span>
              </a>
              <a href="#contact" class="btn btn-ghost">
                Download résumé
                <span aria-hidden="true">⤓</span>
              </a>
            </div>

            <div class="hero-meta" aria-label="Key metrics">
              <div class="hero-meta-item">
                <span class="hero-meta-label">Experience</span>
                <span class="hero-meta-value">3+ years</span>
              </div>
              <div class="hero-meta-item">
                <span class="hero-meta-label">Focus</span>
                <span class="hero-meta-value">Web & APIs</span>
              </div>
              <div class="hero-meta-item">
                <span class="hero-meta-label">Location</span>
                <span class="hero-meta-value">Haryana, India</span>
              </div>
            </div>
          </div>

          <div class="hero-visual" aria-hidden="true">
            <div class="hero-card">
              <div class="hero-card-overlay"></div>

              <div class="hero-card-header">
                <div class="hero-avatar">
                  <div class="hero-avatar-inner">YN</div>
                </div>
                <div>
                  <div class="hero-card-title">Your Name</div>
                  <div class="hero-card-sub">
                    Full Stack · Java Developer
                  </div>
                </div>
              </div>

              <div class="hero-card-body">
                <div>
                  <span>Currently shipping reliable web tooling and internal dashboards with tight feedback loops and strong typing.</span>
                </div>

                <div class="hero-card-tags">
                  <span class="chip">Clean architecture</span>
                  <span class="chip">Testable code</span>
                  <span class="chip">DX‑driven</span>
                </div>

                <div class="hero-card-grid" aria-hidden="true">
                  <div class="hero-card-pill">
                    <span class="hero-pill-label">Primary stack</span>
                    <span class="hero-pill-value">Java · Laravel · React</span>
                  </div>
                  <div class="hero-card-pill">
                    <span class="hero-pill-label">Specialty</span>
                    <span class="hero-pill-value">Task & workflow systems</span>
                  </div>
                  <div class="hero-card-pill">
                    <span class="hero-pill-label">Preferred db</span>
                    <span class="hero-pill-value">MySQL · Postgres</span>
                  </div>
                </div>

                <div class="hero-card-footer">
                  <span class="hero-card-status">
                    <span class="status-dot"></span>
                    <span>Available for full‑time & remote</span>
                  </span>
                  <span>GMT+5:30</span>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>

      <!-- About -->
      <section id="about" aria-labelledby="about-heading">
        <div class="section-heading">
          <span class="section-heading-dot" aria-hidden="true"></span>
          <span>About</span>
        </div>
        <h2 id="about-heading" class="section-title">Engineer with product mindset</h2>
        <p class="section-subtitle">
          Blending backend robustness with a strong sense for UX to ship reliable, developer-friendly web products.
        </p>

        <div class="about">
          <p class="about-text">
            As a <span class="about-highlight">full stack software engineer</span>, the work concentrates on
            building pragmatic, maintainable systems that solve concrete business problems without unnecessary complexity.[web:19]  
            Typical projects range from task management tools and internal dashboards to
            data‑driven platforms backed by Laravel and modern JavaScript frontends.[web:7]
          </p>

          <div class="about-grid" aria-label="Selected highlights">
            <div class="about-stat">
              <span class="about-stat-value">15+ projects</span>
              <span>Real‑world applications shipped across personal and client work.</span>
            </div>
            <div class="about-stat">
              <span class="about-stat-value">Backend‑leaning</span>
              <span>API design, database modeling, and performance‑aware endpoints.</span>
            </div>
            <div class="about-stat">
              <span class="about-stat-value">Frontend craft</span>
              <span>Accessible, responsive UI with thoughtful interaction details.</span>
            </div>
            <div class="about-stat">
              <span class="about-stat-value">Continuous learning</span>
              <span>Actively refining architecture decisions, testing strategy, and DX.</span>
            </div>
          </div>
        </div>
      </section>

      <!-- Skills -->
      <section id="skills" aria-labelledby="skills-heading">
        <div class="section-heading">
          <span class="section-heading-dot" aria-hidden="true"></span>
          <span>Skills</span>
        </div>
        <h2 id="skills-heading" class="section-title">Building from database to UI</h2>
        <p class="section-subtitle">
          Focused on a modern web stack: Java, Laravel, JavaScript, and clean, accessible frontends.
        </p>

        <div class="skills-grid">
          <div>
            <h3 class="skill-group-title">Core technologies</h3>
            <div class="skill-tags" aria-label="Primary skills">
              <span class="skill-tag">
                <span class="skill-dot"></span>
                Java
              </span>
              <span class="skill-tag">
                <span class="skill-dot"></span>
                JavaScript (ES6+)
              </span>
              <span class="skill-tag">
                <span class="skill-dot"></span>
                Laravel · PHP
              </span>
              <span class="skill-tag">
                <span class="skill-dot"></span>
                HTML5 · CSS3
              </span>
              <span class="skill-tag">
                <span class="skill-dot"></span>
                MySQL · SQL
              </span>
              <span class="skill-tag">
                <span class="skill-dot"></span>
                Git · GitHub
              </span>
            </div>

            <h3 class="skill-group-title" style="margin-top: 1.2rem;">
              Tooling & practices
            </h3>
            <div class="skill-tags">
              <span class="skill-tag">
                <span class="skill-dot"></span>
                REST APIs
              </span>
              <span class="skill-tag">
                <span class="skill-dot"></span>
                Object‑oriented design
              </span>
              <span class="skill-tag">
                <span class="skill-dot"></span>
                Testing & debugging
              </span>
              <span class="skill-tag">
                <span class="skill-dot"></span>
                Responsive UI
              </span>
              <span class="skill-tag">
                <span class="skill-dot"></span>
                Performance budgets
              </span>
            </div>
          </div>

          <div class="skill-meters" aria-label="Skill proficiency">
            <div class="skill-meter" data-skill-level="0.85">
              <div class="skill-meter-header">
                <span class="skill-meter-name">Backend & APIs</span>
                <span>Advanced</span>
              </div>
              <div class="meter-track">
                <div class="meter-fill"></div>
              </div>
            </div>

            <div class="skill-meter" data-skill-level="0.8">
              <div class="skill-meter-header">
                <span class="skill-meter-name">Frontend engineering</span>
                <span>Advanced</span>
              </div>
              <div class="meter-track">
                <div class="meter-fill"></div>
              </div>
            </div>

            <div class="skill-meter" data-skill-level="0.75">
              <div class="skill-meter-header">
                <span class="skill-meter-name">Databases & modeling</span>
                <span>Strong</span>
              </div>
              <div class="meter-track">
                <div class="meter-fill"></div>
              </div>
            </div>

            <div class="skill-meter" data-skill-level="0.7">
              <div class="skill-meter-header">
                <span class="skill-meter-name">Architecture & testing</span>
                <span>Growing</span>
              </div>
              <div class="meter-track">
                <div class="meter-fill"></div>
              </div>
            </div>
          </div>
        </div>
      </section>

      <!-- Projects -->
      <section id="projects" aria-labelledby="projects-heading">
        <div class="section-heading">
          <span class="section-heading-dot" aria-hidden="true"></span>
          <span>Projects</span>
        </div>
        <h2 id="projects-heading" class="section-title">Selected work on GitHub</h2>
        <p class="section-subtitle">
          A snapshot of systems, dashboards, and tools that focus on reliability and developer experience.
        </p>

        <div class="projects-grid">
          <article class="project-card">
            <header class="project-title">
              <span>TaskFlow Manager</span>
              <span class="project-badge">Web app</span>
            </header>
            <p class="project-desc">
              Full‑stack task management system with recurring schedules, status workflows, and team dashboards tailored for engineering teams.
            </p>
            <div class="project-meta">
              <div class="project-stack" aria-label="Tech stack">
                <span>Laravel</span>
                <span>MySQL</span>
                <span>Blade</span>
                <span>Alpine.js</span>
              </div>
              <div class="project-links">
                <a
                  href="https://github.com/your-username/taskflow-manager"
                  class="project-link"
                  target="_blank"
                  rel="noreferrer"
                >
                  <span aria-hidden="true"></span>
                  <span>Code</span>
                </a>
              </div>
            </div>
          </article>

          <article class="project-card">
            <header class="project-title">
              <span>Mess Coupon System</span>
              <span class="project-badge">Platform</span>
            </header>
            <p class="project-desc">
              QR‑based mess management portal with registration workflows, admin approval, and scan‑to‑consume meal coupons.[memory:1]
            </p>
            <div class="project-meta">
              <div class="project-stack">
                <span>Laravel</span>
                <span>MySQL</span>
                <span>Bootstrap</span>
                <span>QR APIs</span>
              </div>
              <div class="project-links">
                <a
                  href="https://github.com/your-username/mess-coupon-system"
                  class="project-link"
                  target="_blank"
                  rel="noreferrer"
                >
                  <span aria-hidden="true"></span>
                  <span>Code</span>
                </a>
              </div>
            </div>
          </article>

          <article class="project-card">
            <header class="project-title">
              <span>Dev Metrics Dashboard</span>
              <span class="project-badge">Internal</span>
            </header>
            <p class="project-desc">
              Lightweight analytics dashboard surfaces repository activity, deployment status, and key alerts for engineering leads.
            </p>
            <div class="project-meta">
              <div class="project-stack">
                <span>React</span>
                <span>Node.js</span>
                <span>REST</span>
                <span>PostgreSQL</span>
              </div>
              <div class="project-links">
                <a
                  href="https://github.com/your-username/dev-metrics-dashboard"
                  class="project-link"
                  target="_blank"
                  rel="noreferrer"
                >
                  <span aria-hidden="true"></span>
                  <span>Code</span>
                </a>
              </div>
            </div>
          </article>
        </div>
      </section>

      <!-- Experience -->
      <section id="experience" aria-labelledby="experience-heading">
        <div class="section-heading">
          <span class="section-heading-dot" aria-hidden="true"></span>
          <span>Experience</span>
        </div>
        <h2 id="experience-heading" class="section-title">Experience & education</h2>
        <p class="section-subtitle">
          Industry experience and self‑driven learning combined into a hands‑on engineering practice.[web:19]
        </p>

        <div class="timeline" aria-label="Experience and education timeline">
          <article class="timeline-item">
            <div class="timeline-marker"></div>
            <header class="timeline-heading">
              <h3 class="timeline-role">Full Stack Developer</h3>
              <span class="timeline-meta">2023 — Present · Remote / Hybrid</span>
            </header>
            <div class="timeline-org">Product teams & freelance clients</div>
            <p class="timeline-body">
              Designing and implementing end‑to‑end web solutions from data modeling and APIs
              to polished frontends, with a focus on DX and maintainable abstractions.
            </p>
          </article>

          <article class="timeline-item">
            <div class="timeline-marker"></div>
            <header class="timeline-heading">
              <h3 class="timeline-role">Backend‑leaning engineer</h3>
              <span class="timeline-meta">2021 — 2023</span>
            </header>
            <div class="timeline-org">Independent projects & collaborations</div>
            <p class="timeline-body">
              Built internal tools, admin dashboards, and scheduling systems using Java and Laravel,
              integrating with external APIs and third‑party services.[web:7]
            </p>
          </article>

          <article class="timeline-item">
            <div class="timeline-marker"></div>
            <header class="timeline-heading">
              <h3 class="timeline-role">Self‑taught foundations</h3>
              <span class="timeline-meta">Ongoing</span>
            </header>
            <div class="timeline-org">Computer science, algorithms, and web fundamentals</div>
            <p class="timeline-body">
              Continuously improving understanding of data structures, design patterns, and modern web practices
              to inform technical decisions and long‑term code health.[web:20]
            </p>
          </article>
        </div>
      </section>

      <!-- Contact -->
      <section id="contact" aria-labelledby="contact-heading">
        <div class="section-heading">
          <span class="section-heading-dot" aria-hidden="true"></span>
          <span>Contact</span>
        </div>
        <h2 id="contact-heading" class="section-title">Let’s work on something reliable</h2>
        <p class="section-subtitle">
          Available for full‑time roles, long‑term collaboration, or focused project work.
        </p>

        <div class="contact-grid">
          <div class="contact-card">
            <h3 class="visually-hidden">Primary contact channels</h3>
            <p>
              The fastest way to reach out is via email, but GitHub and LinkedIn are also monitored frequently.
            </p>
            <div class="contact-row">
              <a
                href="mailto:you@example.com"
                class="contact-link"
                aria-label="Email"
              >
                <span class="contact-icon">✉</span>
                <span>you@example.com</span>
              </a>
              <a
                href="https://github.com/your-username"
                class="contact-link"
                target="_blank"
                rel="noreferrer"
                aria-label="GitHub profile"
              >
                <span class="contact-icon"></span>
                <span>@your-username</span>
              </a>
              <a
                href="https://www.linkedin.com/in/your-handle"
                class="contact-link"
                target="_blank"
                rel="noreferrer"
                aria-label="LinkedIn profile"
              >
                <span class="contact-icon">in</span>
                <span>/in/your-handle</span>
              </a>
            </div>
            <p class="contact-note">
              For quick context, feel free to include a short description of the problem space and desired timeline.
            </p>
          </div>

          <div class="contact-meta">
            <p>
              This portfolio is intentionally lightweight: a single static page, semantic HTML, and minimal JavaScript to keep performance high and maintenance low.[web:7][web:19]
            </p>
            <div class="contact-meta-list">
              <div class="contact-meta-item">
                <span class="contact-meta-bullet"></span>
                <span>Fully responsive and keyboard‑accessible sections.</span>
              </div>
              <div class="contact-meta-item">
                <span class="contact-meta-bullet"></span>
                <span>Color contrast and reduced‑motion support for accessibility.[web:8]</span>
              </div>
              <div class="contact-meta-item">
                <span class="contact-meta-bullet"></span>
                <span>Optimized for GitHub Pages hosting with no external build steps.[web:7]</span>
              </div>
            </div>
          </div>
        </div>
      </section>
    </main>

    <footer>
      <span>© <span id="year"></span> Your Name</span>
      <span>Built with semantic HTML, modern CSS, and vanilla JavaScript.</span>
    </footer>
  </div>

  <script>
    (function () {
      const root = document.documentElement;
      const storedTheme = localStorage.getItem("theme");

      if (storedTheme === "light" || storedTheme === "dark") {
        root.setAttribute("data-theme", storedTheme);
      } else if (window.matchMedia &&
        window.matchMedia("(prefers-color-scheme: light)").matches
      ) {
        root.setAttribute("data-theme", "light");
      } else {
        root.setAttribute("data-theme", "dark");
      }
    })();

    window.addEventListener("DOMContentLoaded", function () {
      const root = document.documentElement;
      const themeToggle = document.getElementById("themeToggle");
      const navBurger = document.getElementById("navBurger");
      const navMobile = document.getElementById("navMobile");
      const navLinks = document.querySelectorAll(".nav-link");
      const meterElements = document.querySelectorAll(".skill-meter");
      const yearSpan = document.getElementById("year");

      if (yearSpan) {
        yearSpan.textContent = new Date().getFullYear();
      }

      function setTheme(theme) {
        root.setAttribute("data-theme", theme);
        localStorage.setItem("theme", theme);
      }

      themeToggle?.addEventListener("click", function () {
        const current = root.getAttribute("data-theme") || "dark";
        setTheme(current === "light" ? "dark" : "light");
      });

      navBurger?.addEventListener("click", function () {
        const expanded =
          navBurger.getAttribute("aria-expanded") === "true";
        navBurger.setAttribute("aria-expanded", String(!expanded));
        navBurger.classList.toggle("open");
        if (navMobile) {
          navMobile.style.display = expanded ? "none" : "grid";
        }
      });

      navMobile?.addEventListener("click", function (event) {
        if (event.target instanceof HTMLAnchorElement) {
          navBurger.setAttribute("aria-expanded", "false");
          navBurger.classList.remove("open");
          navMobile.style.display = "none";
        }
      });

      const sections = document.querySelectorAll("section[id]");
      function updateActiveLink() {
        let currentId = null;
        const scrollPos =
          window.scrollY + (window.innerHeight * 0.18);

        sections.forEach((section) => {
          const rect = section.getBoundingClientRect();
          const top = window.scrollY + rect.top;
          const bottom = top + rect.height;

          if (scrollPos >= top && scrollPos < bottom) {
            currentId = section.id;
          }
        });

        navLinks.forEach((link) => {
          if (!currentId) {
            link.classList.remove("active");
            return;
          }
          const href = link.getAttribute("href") || "";
          const id = href.startsWith("#") ? href.slice(1) : null;
          link.classList.toggle("active", id === currentId);
        });
      }

      updateActiveLink();
      window.addEventListener("scroll", updateActiveLink);

      const observer = new IntersectionObserver(
        (entries) => {
          entries.forEach((entry) => {
            if (entry.isIntersecting) {
              const meter = entry.target;
              const level =
                parseFloat(meter.getAttribute("data-skill-level")) || 0.7;
              const fill = meter.querySelector(".meter-fill");
              if (fill) {
                fill.style.setProperty("--value", level.toString());
                fill.classList.add("visible");
              }
              observer.unobserve(meter);
            }
          });
        },
        {
          threshold: 0.4,
        }
      );

      meterElements.forEach((meter) => observer.observe(meter));
    });
  </script>
</body>
</html>
