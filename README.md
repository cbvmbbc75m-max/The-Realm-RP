<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ذا ريلم | The Realm RP</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;600;700;800;900&display=swap" rel="stylesheet">
    <style>
        /* Theme palette: dark obsidian canvas with crimson accents */
        :root {
            --bg-dark: #09090b;
            --card-bg: #121215;
            --card-hover: #18181c;
            --red-primary: #dc2626;
            --red-dark: #991b1b;
            --red-glow: rgba(220, 38, 38, 0.25);
            --border-color: rgba(220, 38, 38, 0.28);
            --text-main: #f4f4f5;
            --text-muted: #a1a1aa;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Cairo', sans-serif;
        }

        /* Prevent horizontal scroll and clipped text on mobile */
        html,
        body {
            width: 100%;
            max-width: 100%;
            overflow-x: hidden;
            background-color: var(--bg-dark);
            color: var(--text-main);
            background-image:
                radial-gradient(circle at 50% 0%, rgba(220, 38, 38, 0.14) 0%, transparent 55%),
                linear-gradient(rgba(220, 38, 38, 0.03) 1px, transparent 1px),
                linear-gradient(90deg, rgba(220, 38, 38, 0.03) 1px, transparent 1px);
            background-size: 100% 100%, 28px 28px, 28px 28px;
            min-height: 100vh;
            line-height: 1.65;
            font-size: 14px;
        }

        /* Top Header */
        .top-header {
            position: sticky;
            top: 0;
            z-index: 60;
            width: 100%;
            background: rgba(12, 12, 15, 0.96);
            backdrop-filter: blur(10px);
            border-bottom: 1px solid var(--border-color);
            padding: 10px 12px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            gap: 8px;
        }

        .header-left {
            display: flex;
            align-items: center;
            gap: 8px;
            min-width: 0;
            flex: 1;
        }

        /* 3-bar menu button (☰) */
        .menu-btn {
            width: 38px;
            height: 38px;
            flex-shrink: 0;
            border-radius: 10px;
            background: #141418;
            border: 1px solid var(--border-color);
            color: #fff;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            gap: 4px;
            cursor: pointer;
        }

        .menu-btn:hover {
            border-color: var(--red-primary);
            background: #1b1114;
        }

        .menu-btn span {
            width: 17px;
            height: 2px;
            background: #fff;
            border-radius: 2px;
            display: block;
        }

        .brand {
            display: flex;
            align-items: center;
            gap: 8px;
            cursor: pointer;
            min-width: 0;
        }

        .logo-box {
            width: 34px;
            height: 34px;
            flex-shrink: 0;
            background: linear-gradient(135deg, var(--red-primary), var(--red-dark));
            border-radius: 9px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 900;
            font-size: 0.88rem;
            color: #fff;
            box-shadow: 0 0 12px var(--red-glow);
        }

        .brand-title {
            min-width: 0;
        }

        .brand-title h1 {
            font-size: 0.92rem;
            font-weight: 900;
            line-height: 1.2;
            color: #fff;
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
        }

        .brand-title span {
            display: block;
            font-size: 0.68rem;
            color: var(--text-muted);
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
        }

        .discord-btn {
            background: var(--red-primary);
            color: #fff;
            text-decoration: none;
            padding: 8px 11px;
            border-radius: 9px;
            font-weight: 800;
            font-size: 0.78rem;
            box-shadow: 0 4px 14px var(--red-glow);
            white-space: nowrap;
            flex-shrink: 0;
        }

        .discord-btn:hover {
            background: #b91c1c;
        }

        /* Slide-out Drawer */
        .drawer-backdrop {
            position: fixed;
            inset: 0;
            background: rgba(0, 0, 0, 0.75);
            z-index: 90;
            display: none;
        }

        .drawer-backdrop.open {
            display: block;
        }

        .side-drawer {
            position: fixed;
            top: 0;
            left: -290px;
            width: 268px;
            max-width: 82vw;
            height: 100vh;
            background: #101014;
            border-right: 1px solid var(--border-color);
            z-index: 100;
            padding: 18px 14px;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            transition: left 0.22s ease;
            box-shadow: 10px 0 30px rgba(0, 0, 0, 0.75);
            overflow-y: auto;
        }

        .side-drawer.open {
            left: 0;
        }

        .drawer-top {
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding-bottom: 12px;
            border-bottom: 1px solid #27272a;
            margin-bottom: 14px;
        }

        .drawer-top strong {
            font-size: 0.96rem;
            color: #fff;
        }

        .close-drawer-btn {
            background: #18181c;
            border: 1px solid #27272a;
            color: #fff;
            width: 30px;
            height: 30px;
            border-radius: 8px;
            cursor: pointer;
            font-weight: 700;
        }

        .nav-list {
            display: flex;
            flex-direction: column;
            gap: 8px;
        }

        .nav-item-btn {
            width: 100%;
            background: #141418;
            border: 1px solid #27272a;
            color: #e4e4e7;
            padding: 11px 13px;
            border-radius: 10px;
            text-align: right;
            font-size: 0.88rem;
            font-weight: 800;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: space-between;
        }

        .nav-item-btn:hover,
        .nav-item-btn.active {
            background: rgba(220, 38, 38, 0.16);
            border-color: var(--red-primary);
            color: #fca5a5;
        }

        .drawer-footer-link {
            display: block;
            text-align: center;
            background: var(--red-primary);
            color: #fff;
            text-decoration: none;
            padding: 10px 12px;
            border-radius: 10px;
            font-weight: 800;
            font-size: 0.86rem;
            margin-top: 16px;
        }

        /* Main Container */
        .container {
            width: 100%;
            max-width: 900px;
            margin: 0 auto;
            padding: 18px 14px 48px;
        }

        .page-view {
            display: none;
            width: 100%;
        }

        .page-view.active {
            display: block;
        }

        /* Home View */
        .hero-card {
            background: linear-gradient(180deg, rgba(220, 38, 38, 0.13) 0%, rgba(18, 18, 21, 0.96) 55%);
            border: 1px solid var(--border-color);
            border-radius: 16px;
            padding: 24px 16px;
            text-align: center;
            box-shadow: 0 10px 28px rgba(0, 0, 0, 0.5);
        }

        .pill-badge {
            display: inline-block;
            background: rgba(220, 38, 38, 0.15);
            border: 1px solid var(--border-color);
            color: #fca5a5;
            padding: 4px 12px;
            border-radius: 999px;
            font-size: 0.76rem;
            font-weight: 700;
            margin-bottom: 10px;
        }

        .hero-card h2 {
            font-size: 1.45rem;
            font-weight: 900;
            margin-bottom: 8px;
            word-wrap: break-word;
            overflow-wrap: anywhere;
        }

        .hero-card h2 span {
            color: var(--red-primary);
        }

        .hero-card p {
            color: var(--text-muted);
            max-width: 620px;
            margin: 0 auto 18px;
            font-size: 0.88rem;
            word-wrap: break-word;
            overflow-wrap: anywhere;
        }

        .hero-actions {
            display: flex;
            gap: 10px;
            justify-content: center;
            flex-wrap: wrap;
        }

        .primary-enter-btn {
            background: var(--red-primary);
            color: #fff;
            text-decoration: none;
            padding: 10px 20px;
            border-radius: 10px;
            font-weight: 900;
            font-size: 0.88rem;
            box-shadow: 0 5px 18px var(--red-glow);
            border: none;
            cursor: pointer;
            display: inline-flex;
            align-items: center;
            justify-content: center;
        }

        .primary-enter-btn:hover {
            background: #b91c1c;
        }

        .secondary-nav-btn {
            background: #141418;
            color: #f4f4f5;
            border: 1px solid #27272a;
            padding: 10px 16px;
            border-radius: 10px;
            font-weight: 800;
            font-size: 0.84rem;
 
