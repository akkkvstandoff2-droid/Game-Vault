<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>GameVault — аккаунты с рейтингом</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css" />
    <style>
        /* ---------- RESET & BASE ---------- */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: #0b0e14;
            color: #e4e7ed;
            min-height: 100vh;
            padding: 20px;
        }
        ::-webkit-scrollbar {
            width: 8px;
        }
        ::-webkit-scrollbar-track {
            background: #1a1f2b;
        }
        ::-webkit-scrollbar-thumb {
            background: #3b4a5e;
            border-radius: 6px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #5a6f8a;
        }
        .container {
            max-width: 1300px;
            margin: 0 auto;
        }

        /* ---------- HEADER ---------- */
        header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 16px;
            padding: 20px 28px;
            background: #141a24;
            border-radius: 20px;
            margin-bottom: 16px;
            box-shadow: 0 8px 30px rgba(0, 0, 0, 0.6);
            border: 1px solid #2a3342;
        }
        .logo {
            display: flex;
            align-items: center;
            gap: 12px;
            font-size: 26px;
            font-weight: 800;
            color: #f0c94b;
        }
        .logo i {
            font-size: 32px;
            color: #f0c94b;
            filter: drop-shadow(0 0 10px rgba(240, 201, 75, 0.3));
        }
        .logo span {
            color: #e4e7ed;
        }
        .header-actions {
            display: flex;
            align-items: center;
            gap: 12px;
            flex-wrap: wrap;
        }
        .header-stats {
            display: flex;
            align-items: center;
            gap: 18px;
            font-size: 14px;
            background: #1f2634;
            padding: 6px 16px;
            border-radius: 40px;
            border: 1px solid #2f3a4c;
        }
        .header-stats i {
            color: #f0c94b;
            margin-right: 4px;
        }
        .header-stats .stat-item {
            display: flex;
            align-items: center;
            gap: 4px;
        }
        .stat-item .num {
            font-weight: 700;
            color: #fff;
            min-width: 18px;
        }
        .user-info {
            display: flex;
            align-items: center;
            gap: 10px;
            background: #1f2634;
            padding: 4px 14px 4px 18px;
            border-radius: 40px;
            border: 1px solid #2f3a4c;
        }
        .user-info .email {
            font-size: 14px;
            color: #b0bccf;
        }
        .user-info .vip-badge {
            background: #f0c94b;
            color: #0b0e14;
            padding: 2px 10px;
            border-radius: 30px;
            font-size: 11px;
            font-weight: 700;
        }
        .user-info .logout-btn {
            background: none;
            border: none;
            color: #f87171;
            cursor: pointer;
            font-size: 14px;
            padding: 6px 0;
        }
        .user-info .logout-btn:hover {
            color: #ff9a9a;
        }
        .auth-btn {
            background: #2a3342;
            border: none;
            color: #e4e7ed;
            padding: 6px 16px;
            border-radius: 40px;
            font-size: 14px;
            font-weight: 600;
            cursor: pointer;
            transition: 0.2s;
            border: 1px solid #3f4d64;
            display: flex;
            align-items: center;
            gap: 6px;
        }
        .auth-btn:hover {
            background: #3b4a5e;
            border-color: #f0c94b;
        }
        .admin-toggle-btn {
            background: #2a3342;
            border: none;
            color: #e4e7ed;
            padding: 6px 16px;
            border-radius: 40px;
            font-size: 14px;
            font-weight: 600;
            cursor: pointer;
            transition: 0.2s;
            border: 1px solid #3f4d64;
            display: flex;
            align-items: center;
            gap: 6px;
        }
        .admin-toggle-btn:hover {
            background: #3b4a5e;
            border-color: #f0c94b;
        }
        .admin-toggle-btn.active {
            background: #f0c94b;
            border-color: #f0c94b;
            color: #0b0e14;
        }
        .account-btn {
            background: #2a3342;
            border: none;
            color: #e4e7ed;
            padding: 6px 16px;
            border-radius: 40px;
            font-size: 14px;
            font-weight: 600;
            cursor: pointer;
            transition: 0.2s;
            border: 1px solid #3f4d64;
            display: flex;
            align-items: center;
            gap: 6px;
        }
        .account-btn:hover {
            background: #3b4a5e;
            border-color: #f0c94b;
        }

        /* ---------- VIP BANNER ---------- */
        .vip-banner {
            background: linear-gradient(135deg, #1f2634, #2a1f2a);
            border: 1px solid #f0c94b;
            border-radius: 16px;
            padding: 16px 24px;
            margin-bottom: 24px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            flex-wrap: wrap;
            gap: 16px;
        }
        .vip-banner .text {
            display: flex;
            align-items: center;
            gap: 12px;
        }
        .vip-banner .text i {
            font-size: 28px;
            color: #f0c94b;
        }
        .vip-banner .text span {
            font-size: 16px;
            font-weight: 600;
            color: #e4e7ed;
        }
        .vip-banner .text span strong {
            color: #f0c94b;
        }
        .vip-banner .btn-vip {
            background: #f0c94b;
            border: none;
            color: #0b0e14;
            padding: 8px 28px;
            border-radius: 40px;
            font-weight: 700;
            font-size: 16px;
            cursor: pointer;
            transition: 0.2s;
            display: inline-flex;
            align-items: center;
            gap: 8px;
            text-decoration: none;
        }
        .vip-banner .btn-vip:hover {
            background: #ffd95e;
            transform: scale(1.03);
            box-shadow: 0 4px 20px rgba(240, 201, 75, 0.3);
        }
        .vip-banner .btn-vip i {
            font-size: 18px;
        }

        /* ---------- NAV ---------- */
        .nav-section {
            display: flex;
            align-items: center;
            gap: 12px;
            margin-bottom: 24px;
            flex-wrap: wrap;
        }
        .nav-section .back-btn {
            background: #1f2634;
            border: 1px solid #2a3342;
            color: #b0bccf;
            padding: 10px 18px;
            border-radius: 40px;
            font-size: 14px;
            font-weight: 600;
            cursor: pointer;
            transition: 0.2s;
            display: none;
            align-items: center;
            gap: 8px;
        }
        .nav-section .back-btn:hover {
            background: #2a3342;
            color: #fff;
        }
        .nav-section .back-btn.visible {
            display: inline-flex;
        }
        .nav-section .category-title {
            font-size: 24px;
            font-weight: 700;
            color: #f0c94b;
            display: none;
        }
        .nav-section .category-title.visible {
            display: block;
        }

        /* ---------- GRID ---------- */
        .grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
            gap: 24px;
        }

        /* ---------- CATEGORY CARD ---------- */
        .category-card {
            background: #141a24;
            border-radius: 18px;
            border: 1px solid #212a38;
            padding: 28px 20px 24px;
            transition: 0.25s ease;
            cursor: pointer;
            text-align: center;
            position: relative;
            overflow: hidden;
        }
        .category-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 3px;
            background: linear-gradient(90deg, #f0c94b, #d4a82a);
            opacity: 0;
            transition: 0.3s;
        }
        .category-card:hover {
            border-color: #3f4d64;
            transform: translateY(-4px);
            box-shadow: 0 12px 40px rgba(0, 0, 0, 0.5);
        }
        .category-card:hover::before {
            opacity: 1;
        }
        .category-card .icon {
            font-size: 48px;
            color: #f0c94b;
            margin-bottom: 12px;
            width: 64px;
            height: 64px;
            margin-left: auto;
            margin-right: auto;
            display: flex;
            align-items: center;
            justify-content: center;
            border-radius: 16px;
            background: #1f2634;
            overflow: hidden;
        }
        .category-card .icon img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
        .category-card .icon i {
            font-size: 36px;
        }
        .category-card .name {
            font-size: 20px;
            font-weight: 700;
            color: #fff;
            margin-bottom: 6px;
            margin-top: 8px;
        }
        .category-card .count {
            font-size: 14px;
            color: #8a9bb0;
        }
        .category-card .vip-badge {
            position: absolute;
            top: 12px;
            left: 12px;
            background: #f0c94b;
            color: #0b0e14;
            padding: 2px 12px;
            border-radius: 30px;
            font-size: 11px;
            font-weight: 700;
        }
        .category-card .vip-lock {
            position: absolute;
            top: 12px;
            right: 12px;
            color: #f0c94b;
            font-size: 18px;
        }
        .admin-delete-category {
            position: absolute;
            top: 12px;
            right: 12px;
            background: rgba(248, 113, 113, 0.15);
            border: 1px solid #f87171;
            color: #f87171;
            width: 32px;
            height: 32px;
            border-radius: 50%;
            display: none;
            align-items: center;
            justify-content: center;
            font-size: 16px;
            cursor: pointer;
            transition: 0.2s;
        }
        .admin-delete-category:hover {
            background: #f87171;
            color: #0b0e14;
        }
        .category-card.admin-mode .admin-delete-category {
            display: flex;
        }

        /* ---------- ACCOUNT CARD ---------- */
        .account-card {
            background: #141a24;
            border-radius: 18px;
            border: 1px solid #212a38;
            padding: 22px 20px 20px;
            transition: 0.25s ease;
            display: flex;
            flex-direction: column;
            position: relative;
            overflow: hidden;
        }
        .account-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 3px;
            background: linear-gradient(90deg, #f0c94b, #d4a82a);
            opacity: 0;
            transition: 0.3s;
        }
        .account-card:hover {
            border-color: #3f4d64;
            transform: translateY(-4px);
            box-shadow: 0 12px 40px rgba(0, 0, 0, 0.5);
        }
        .account-card:hover::before {
            opacity: 1;
        }
        .credential-row {
            display: flex;
            align-items: center;
            justify-content: space-between;
            background: #0f141e;
            padding: 8px 14px;
            border-radius: 10px;
            border: 1px solid #1f2634;
            margin-bottom: 8px;
            font-size: 14px;
        }
        .credential-row .label {
            color: #8a9bb0;
            font-weight: 500;
            font-size: 12px;
            text-transform: uppercase;
            letter-spacing: 0.4px;
        }
        .credential-row .value {
            color: #e4e7ed;
            font-weight: 600;
            font-family: 'Consolas', monospace;
            word-break: break-all;
            max-width: 140px;
            text-align: right;
        }
        .credential-row .value.password-hidden {
            filter: blur(6px);
            user-select: none;
            cursor: pointer;
            transition: 0.2s;
        }
        .credential-row .value.password-hidden:hover {
            filter: blur(2px);
        }
        .credential-row .value.password-hidden.show {
            filter: blur(0);
        }
        .credential-row .value.placeholder {
            color: #6f7d95;
            font-style: italic;
            font-weight: 400;
            filter: none;
            cursor: default;
        }

        .rating-section {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 24px;
            margin-top: 12px;
            padding-top: 12px;
            border-top: 1px solid #1f2634;
        }
        .rating-btn {
            display: flex;
            align-items: center;
            gap: 6px;
            background: transparent;
            border: none;
            color: #8a9bb0;
            font-size: 18px;
            cursor: pointer;
            transition: 0.2s;
            padding: 4px 12px;
            border-radius: 30px;
        }
        .rating-btn:hover {
            background: #1f2634;
        }
        .rating-btn.like:hover {
            color: #4ade80;
        }
        .rating-btn.dislike:hover {
            color: #f87171;
        }
        .rating-btn .count {
            font-size: 16px;
            font-weight: 600;
            color: #e4e7ed;
        }
        .rating-btn .count.likes-count {
            color: #4ade80;
        }
        .rating-btn .count.dislikes-count {
            color: #f87171;
        }
        .rating-btn.active-like {
            color: #4ade80;
        }
        .rating-btn.active-dislike {
            color: #f87171;
        }
        .rating-btn.active-like .count.likes-count {
            color: #4ade80;
        }
        .rating-btn.active-dislike .count.dislikes-count {
            color: #f87171;
        }
        .rating-btn.disabled {
            cursor: default;
            opacity: 0.5;
            pointer-events: none;
        }

        .admin-actions {
            display: flex;
            gap: 8px;
            margin-top: 12px;
            justify-content: flex-end;
        }
        .admin-btn {
            background: #2a3342;
            border: 1px solid #3f4d64;
            color: #e4e7ed;
            padding: 4px 12px;
            border-radius: 30px;
            font-size: 12px;
            cursor: pointer;
            transition: 0.2s;
            display: flex;
            align-items: center;
            gap: 4px;
        }
        .admin-btn:hover {
            background: #3b4a5e;
        }
        .admin-btn.danger {
            border-color: #f87171;
            color: #f87171;
        }
        .admin-btn.danger:hover {
            background: #f87171;
            color: #0b0e14;
        }

        .vip-lock-msg {
            text-align: center;
            padding: 16px;
            color: #f0c94b;
            background: #1f2634;
            border-radius: 12px;
            border: 1px dashed #f0c94b;
            margin-top: 8px;
        }

        /* ---------- EMPTY ---------- */
        .empty-state {
            grid-column: 1 / -1;
            text-align: center;
            padding: 80px 20px;
            background: #141a24;
            border-radius: 24px;
            border: 1px dashed #2a3342;
        }
        .empty-state i {
            font-size: 56px;
            color: #2a3342;
            margin-bottom: 16px;
        }
        .empty-state h3 {
            font-size: 22px;
            color: #b0bccf;
            margin-bottom: 6px;
        }
        .empty-state p {
            color: #6f7d95;
        }
        .empty-state .admin-hint {
            margin-top: 16px;
            display: inline-block;
            background: #f0c94b;
            color: #0b0e14;
            padding: 8px 24px;
            border-radius: 40px;
            font-weight: 600;
            cursor: pointer;
            border: none;
            font-size: 14px;
        }

        /* ---------- MODAL ---------- */
        .modal-overlay {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.7);
            backdrop-filter: blur(6px);
            z-index: 1000;
            align-items: center;
            justify-content: center;
            padding: 20px;
        }
        .modal-overlay.open {
            display: flex;
        }
        .modal {
            background: #141a24;
            border: 1px solid #2a3342;
            border-radius: 24px;
            max-width: 550px;
            width: 100%;
            padding: 32px 30px 28px;
            max-height: 90vh;
            overflow-y: auto;
            box-shadow: 0 20px 60px rgba(0, 0, 0, 0.8);
            animation: modalFade 0.25s ease;
        }
        .admin-modal .modal {
            max-width: 700px;
        }
        @keyframes modalFade {
            from {
                transform: scale(0.95) translateY(20px);
                opacity: 0;
            }
            to {
                transform: scale(1) translateY(0);
                opacity: 1;
            }
        }
        .modal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 24px;
        }
        .modal-header h2 {
            font-size: 24px;
            display: flex;
            align-items: center;
            gap: 12px;
            color: #f0c94b;
        }
        .modal-header h2 i {
            font-size: 26px;
        }
        .modal-close {
            background: none;
            border: none;
            color: #6f7d95;
            font-size: 28px;
            cursor: pointer;
            transition: 0.2s;
            padding: 0 8px;
        }
        .modal-close:hover {
            color: #e4e7ed;
            transform: rotate(90deg);
        }
        .form-group {
            display: flex;
            flex-direction: column;
            gap: 4px;
            margin-bottom: 14px;
        }
        .form-group label {
            font-size: 13px;
            font-weight: 600;
            color: #b0bccf;
            display: flex;
            align-items: center;
            gap: 6px;
        }
        .form-group input,
        .form-group select {
            background: #0f141e;
            border: 1px solid #2a3342;
            border-radius: 12px;
            padding: 12px 16px;
            color: #e4e7ed;
            font-size: 15px;
            transition: 0.2s;
            outline: none;
            width: 100%;
        }
        .form-group input:focus,
        .form-group select:focus {
            border-color: #f0c94b;
            box-shadow: 0 0 0 3px rgba(240, 201, 75, 0.15);
        }
        .form-group .checkbox-group {
            display: flex;
            align-items: center;
            gap: 10px;
            margin-top: 4px;
        }
        .form-group .checkbox-group input[type="checkbox"] {
            width: 20px;
            height: 20px;
            accent-color: #f0c94b;
            cursor: pointer;
        }
        .form-group .checkbox-group label {
            font-weight: 400;
            color: #e4e7ed;
            cursor: pointer;
        }
        .form-row {
            display: flex;
            gap: 14px;
            flex-wrap: wrap;
        }
        .form-row .form-group {
            flex: 1;
            min-width: 120px;
        }
        .btn-primary {
            background: #f0c94b;
            border: none;
            color: #0b0e14;
            padding: 12px 28px;
            border-radius: 40px;
            font-weight: 700;
            font-size: 16px;
            cursor: pointer;
            transition: 0.2s;
            display: inline-flex;
            align-items: center;
            gap: 10px;
            justify-content: center;
        }
        .btn-primary:hover {
            background: #ffd95e;
            transform: scale(1.02);
            box-shadow: 0 4px 20px rgba(240, 201, 75, 0.3);
        }
        .btn-secondary {
            background: #2a3342;
            border: 1px solid #3f4d64;
            color: #e4e7ed;
            padding: 12px 28px;
            border-radius: 40px;
            font-weight: 600;
            font-size: 16px;
            cursor: pointer;
            transition: 0.2s;
            display: inline-flex;
            align-items: center;
            gap: 10px;
            justify-content: center;
        }
        .btn-secondary:hover {
            background: #3b4a5e;
        }
        .btn-small {
            padding: 6px 16px;
            font-size: 13px;
        }
        .auth-switch {
            text-align: center;
            margin-top: 12px;
            color: #8a9bb0;
            font-size: 14px;
        }
        .auth-switch a {
            color: #f0c94b;
            cursor: pointer;
            text-decoration: none;
        }
        .auth-switch a:hover {
            text-decoration: underline;
        }

        /* Стили для загрузки изображения (для админки) */
        .file-upload-wrapper {
            position: relative;
            width: 100%;
            margin-bottom: 4px;
        }
        .file-upload-wrapper input[type="file"] {
            position: absolute;
            left: 0;
            top: 0;
            opacity: 0;
            width: 100%;
            height: 100%;
            cursor: pointer;
        }
        .file-upload-label {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 12px;
            background: #0f141e;
            border: 2px dashed #2a3342;
            border-radius: 12px;
            padding: 16px;
            color: #8a9bb0;
            font-weight: 500;
            transition: 0.2s;
            cursor: pointer;
            text-align: center;
        }
        .file-upload-label:hover {
            border-color: #f0c94b;
            color: #e4e7ed;
        }
        .file-upload-label i {
            font-size: 28px;
            color: #f0c94b;
        }
        .file-upload-label .file-name {
            color: #e4e7ed;
            font-weight: 600;
            margin-left: 6px;
        }
        .file-preview {
            display: none;
            margin-top: 10px;
            border-radius: 12px;
            overflow: hidden;
            max-height: 120px;
            width: 100%;
            object-fit: cover;
            border: 1px solid #2a3342;
        }
        .file-preview.show {
            display: block;
        }

        /* ---------- ADMIN MODAL ---------- */
        .modal-section {
            border-top: 1px solid #2a3342;
            padding-top: 20px;
            margin-top: 20px;
        }
        .modal-section:first-of-type {
            border-top: none;
            padding-top: 0;
            margin-top: 0;
        }
        .modal-section h3 {
            font-size: 18px;
            color: #b0bccf;
            margin-bottom: 16px;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        .modal-section h3 i {
            color: #f0c94b;
        }
        .category-list-admin {
            display: flex;
            flex-direction: column;
            gap: 8px;
            margin-bottom: 16px;
        }
        .category-item-admin {
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: #0f141e;
            padding: 10px 16px;
            border-radius: 12px;
            border: 1px solid #1f2634;
            flex-wrap: wrap;
            gap: 8px;
        }
        .category-item-admin .cat-name {
            font-weight: 600;
            color: #e4e7ed;
        }
        .category-item-admin .cat-actions {
            display: flex;
            gap: 8px;
            align-items: center;
        }
        .category-item-admin .vip-tag {
            font-size: 11px;
            background: #f0c94b;
            color: #0b0e14;
            padding: 2px 10px;
            border-radius: 30px;
        }
        .admin-small-btn {
            background: transparent;
            border: none;
            color: #6f7d95;
            cursor: pointer;
            font-size: 16px;
            transition: 0.2s;
            padding: 0 4px;
        }
        .admin-small-btn:hover {
            color: #f87171;
        }
        .admin-small-btn.add-acc-btn {
            color: #4ade80;
        }
        .admin-small-btn.add-acc-btn:hover {
            color: #4ade80;
            transform: scale(1.1);
        }
        .admin-select-category {
            margin-bottom: 16px;
        }
        .account-item-admin {
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: #0f141e;
            padding: 8px 16px;
            border-radius: 10px;
            border: 1px solid #1f2634;
            margin-bottom: 6px;
            font-size: 14px;
            flex-wrap: wrap;
            gap: 8px;
        }
        .account-item-admin .acc-info {
            display: flex;
            gap: 16px;
            flex-wrap: wrap;
            align-items: center;
        }
        .account-item-admin .acc-info span {
            color: #b0bccf;
        }
        .account-item-admin .acc-info .login {
            color: #e4e7ed;
            font-weight: 600;
        }
        .account-item-admin .acc-info .pass {
            color: #8a9bb0;
        }
        .account-item-admin .acc-info .rating {
            font-size: 13px;
            color: #f0c94b;
        }

        /* ---------- USERS LIST ---------- */
        .users-list-admin {
            display: flex;
            flex-direction: column;
            gap: 8px;
            margin-bottom: 16px;
        }
        .user-item-admin {
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: #0f141e;
            padding: 10px 16px;
            border-radius: 12px;
            border: 1px solid #1f2634;
            flex-wrap: wrap;
            gap: 8px;
        }
        .user-item-admin .user-email {
            font-weight: 600;
            color: #e4e7ed;
        }
        .user-item-admin .user-vip {
            font-size: 13px;
            color: #8a9bb0;
        }
        .user-item-admin .user-actions {
            display: flex;
            gap: 8px;
        }

        /* ---------- STATS MODAL ---------- */
        .stats-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 16px;
            margin: 16px 0;
        }
        .stats-item {
            background: #0f141e;
            padding: 16px;
            border-radius: 12px;
            border: 1px solid #1f2634;
            text-align: center;
        }
        .stats-item .number {
            font-size: 28px;
            font-weight: 700;
            color: #f0c94b;
        }
        .stats-item .label {
            font-size: 13px;
            color: #8a9bb0;
            margin-top: 4px;
        }
        .stats-user-info {
            background: #0f141e;
            padding: 16px;
            border-radius: 12px;
            border: 1px solid #1f2634;
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 12px;
            margin-bottom: 12px;
        }
        .stats-user-info .id {
            font-weight: 600;
            color: #e4e7ed;
        }
        .stats-user-info .vip-status {
            font-weight: 600;
            color: #f0c94b;
        }

        /* ---------- TOAST ---------- */
        .toast-container {
            position: fixed;
            bottom: 30px;
            right: 30px;
            z-index: 9999;
            display: flex;
            flex-direction: column;
            gap: 10px;
            max-width: 380px;
            width: 100%;
        }
        .toast {
            background: #141a24;
            border: 1px solid #2a3342;
            border-radius: 16px;
            padding: 16px 20px;
            box-shadow: 0 12px 40px rgba(0, 0, 0, 0.7);
            display: flex;
            align-items: center;
            gap: 14px;
            animation: slideIn 0.3s ease;
            backdrop-filter: blur(10px);
            background: rgba(20, 26, 36, 0.95);
        }
        .toast.success i {
            color: #4ade80;
        }
        .toast.error i {
            color: #f87171;
        }
        .toast.warning i {
            color: #fbbf24;
        }
        .toast .toast-icon {
            font-size: 22px;
            flex-shrink: 0;
        }
        .toast .toast-msg {
            font-size: 14px;
            font-weight: 500;
            color: #e4e7ed;
            flex: 1;
        }
        .toast .toast-close {
            background: none;
            border: none;
            color: #6f7d95;
            cursor: pointer;
            font-size: 18px;
            padding: 0 4px;
        }
        .toast .toast-close:hover {
            color: #e4e7ed;
        }
        @keyframes slideIn {
            from {
                transform: translateX(60px);
                opacity: 0;
            }
            to {
                transform: translateX(0);
                opacity: 1;
            }
        }

        /* ---------- RESPONSIVE ---------- */
        @media (max-width: 640px) {
            header {
                flex-direction: column;
                align-items: stretch;
                padding: 16px 18px;
            }
            .header-stats {
                justify-content: space-around;
                padding: 6px 10px;
                font-size: 12px;
                flex-wrap: wrap;
            }
            .logo {
                font-size: 22px;
                justify-content: center;
            }
            .header-actions {
                justify-content: center;
                flex-wrap: wrap;
            }
            .grid {
                grid-template-columns: 1fr;
            }
            .modal {
                padding: 24px 18px;
            }
            .form-row {
                flex-direction: column;
            }
            .toast-container {
                right: 12px;
                left: 12px;
                max-width: none;
                bottom: 16px;
            }
            .account-item-admin .acc-info {
                flex-direction: column;
                gap: 4px;
                align-items: flex-start;
            }
            .rating-section {
                gap: 12px;
                flex-wrap: wrap;
            }
            .stats-grid {
                grid-template-columns: 1fr;
            }
            .vip-banner {
                flex-direction: column;
                text-align: center;
            }
            .file-upload-label {
                flex-direction: column;
                gap: 8px;
            }
        }
        @media (min-width: 641px) and (max-width: 900px) {
            .grid {
                grid-template-columns: repeat(2, 1fr);
            }
        }
    </style>
</head>

<body>

    <div class="container">

        <!-- HEADER -->
        <header>
            <div class="logo">
                <i class="fas fa-gamepad"></i>
                Game<span>Vault</span>
            </div>
            <div class="header-actions">
                <div class="header-stats">
                    <span class="stat-item">
                        <i class="fas fa-folder"></i>
                        <span class="num" id="totalCategories">0</span>
                    </span>
                    <span class="stat-item">
                        <i class="fas fa-user"></i>
                        <span class="num" id="totalAccounts">0</span>
                    </span>
                </div>
                <div id="userInfoContainer" style="display:flex; align-items:center; gap:8px;"></div>
                <button class="admin-toggle-btn" id="adminToggleBtn">
                    <i class="fas fa-cog"></i> Админ
                </button>
            </div>
        </header>

        <!-- VIP BANNER -->
        <div class="vip-banner" id="vipBanner">
            <div class="text">
                <i class="fas fa-crown"></i>
                <span><strong>VIP-доступ</strong> — эксклюзивные игры и аккаунты. Купите премиум и получите все преимущества!</span>
            </div>
            <a href="https://gamevault.trademc.org/" target="_blank" class="btn-vip" id="vipBannerBtn">
                <i class="fas fa-shopping-cart"></i> Купить премиум
            </a>
        </div>

        <!-- NAV -->
        <div class="nav-section">
            <button class="back-btn" id="backBtn"><i class="fas fa-arrow-left"></i> Назад к играм</button>
            <span class="category-title" id="categoryTitle"></span>
        </div>

        <!-- GRID -->
        <div class="grid" id="mainGrid"></div>

    </div>

    <!-- МОДАЛКА АВТОРИЗАЦИИ -->
    <div class="modal-overlay" id="authModal">
        <div class="modal">
            <div class="modal-header">
                <h2 id="authModalTitle"><i class="fas fa-sign-in-alt"></i> Вход</h2>
                <button class="modal-close" id="authModalClose">&times;</button>
            </div>
            <form id="authForm">
                <div id="authFormBody"></div>
            </form>
        </div>
    </div>

    <!-- МОДАЛКА АДМИН-ПАРОЛЯ -->
    <div class="modal-overlay" id="adminPasswordModal">
        <div class="modal" style="max-width:420px;">
            <div class="modal-header">
                <h2><i class="fas fa-lock"></i> Вход в админку</h2>
                <button class="modal-close" id="adminPasswordClose">&times;</button>
            </div>
            <div class="form-group">
                <label>Введите пароль администратора</label>
                <input type="password" id="adminPasswordInput" placeholder="Пароль" />
            </div>
            <button class="btn-primary" id="adminPasswordSubmit" style="width:100%;"><i class="fas fa-key"></i> Войти</button>
        </div>
    </div>

    <!-- МОДАЛКА АДМИНКИ -->
    <div class="modal-overlay admin-modal" id="adminModal">
        <div class="modal">
            <div class="modal-header">
                <h2><i class="fas fa-user-cog"></i> Админ-панель</h2>
                <button class="modal-close" id="modalCloseBtn">&times;</button>
            </div>

            <!-- Управление играми -->
            <div class="modal-section">
                <h3><i class="fas fa-folder-plus"></i> Управление играми</h3>
                <div class="form-row">
                    <div class="form-group" style="flex:2;">
                        <label>Название игры</label>
                        <input type="text" id="newCategoryInput" placeholder="Например: Cyberpunk 2077" />
                    </div>
                </div>
                <div class="form-group">
                    <label>Иконка игры (загрузите изображение)</label>
                    <div class="file-upload-wrapper">
                        <input type="file" id="categoryIconInput" accept="image/*" />
                        <div class="file-upload-label" id="categoryFileLabel">
                            <i class="fas fa-cloud-upload-alt"></i>
                            <span>Выберите файл или перетащите сюда</span>
                        </div>
                        <img id="categoryFilePreview" class="file-preview" alt="Предпросмотр иконки" />
                    </div>
                    <div id="categoryFileStatus" style="font-size:13px; color:#8a9bb0; margin-top:4px;"></div>
                </div>
                <div class="form-group">
                    <div class="checkbox-group">
                        <input type="checkbox" id="newCategoryVip" />
                        <label for="newCategoryVip">VIP-игра (доступна только VIP)</label>
                    </div>
                </div>
                <button class="btn-primary" id="addCategoryBtn" style="width:100%;"><i class="fas fa-plus"></i> Добавить игру</button>
                <div class="category-list-admin" id="categoryListAdmin" style="margin-top:16px;"></div>
            </div>

            <!-- Управление аккаунтами -->
            <div class="modal-section">
                <h3><i class="fas fa-user-plus"></i> Аккаунты в игре</h3>
                <div class="admin-select-category">
                    <select id="adminCategorySelect" style="width:100%; background:#0f141e; border:1px solid #2a3342; border-radius:12px; padding:12px; color:#e4e7ed; font-size:15px;">
                        <option value="">-- Выберите игру --</option>
                    </select>
                </div>
                <div id="adminAccountsList"><p style="color:#6f7d95; font-size:14px;">Выберите игру.</p></div>
                <div style="margin-top:12px; display:flex; gap:10px; flex-wrap:wrap;">
                    <input type="text" id="adminLoginInput" placeholder="Логин" style="flex:1; background:#0f141e; border:1px solid #2a3342; border-radius:12px; padding:10px 14px; color:#e4e7ed;" />
                    <input type="text" id="adminPassInput" placeholder="Пароль" style="flex:1; background:#0f141e; border:1px solid #2a3342; border-radius:12px; padding:10px 14px; color:#e4e7ed;" />
                    <button class="admin-btn success" id="addAccountBtn"><i class="fas fa-plus"></i> Добавить</button>
                </div>
            </div>

            <!-- Управление пользователями -->
            <div class="modal-section">
                <h3><i class="fas fa-users"></i> Пользователи</h3>
                <div class="users-list-admin" id="usersListAdmin">
                    <p style="color:#6f7d95; font-size:14px;">Загружаем...</p>
                </div>
            </div>

            <div style="margin-top:20px; text-align:right;">
                <button class="btn-secondary" id="modalCloseBtn2">Закрыть</button>
            </div>
        </div>
    </div>

    <!-- МОДАЛКА АККАУНТА (статистика) -->
    <div class="modal-overlay" id="accountModal">
        <div class="modal">
            <div class="modal-header">
                <h2><i class="fas fa-user-circle"></i> Аккаунт</h2>
                <button class="modal-close" id="accountModalClose">&times;</button>
            </div>
            <div id="accountStatsContent">
                <!-- динамически -->
            </div>
        </div>
    </div>

    <!-- TOAST -->
    <div class="toast-container" id="toastContainer"></div>

    <script>
        // --------------------------------------------------------------
        //  ДАННЫЕ
        // --------------------------------------------------------------
        let data = {};
        let votes = {};
        let users = {};
        let currentUser = null;
        let currentCategory = null;
        let isAdmin = false;
        let adminAuthenticated = false;

        const ADMIN_PASSWORD = '43WEFm123m';

        // Для загрузки иконки игры
        let categoryIconFile = null;
        let categoryIconPreview = null;

        // --------------------------------------------------------------
        //  ЗАГРУЗКА / СОХРАНЕНИЕ
        // --------------------------------------------------------------
        function loadData() {
            const storedData = localStorage.getItem('gamevault_categories');
            if (storedData) {
                try {
                    data = JSON.parse(storedData);
                    for (const cat in data) {
                        if (typeof data[cat] === 'object' && !Array.isArray(data[cat])) {
                            if (!data[cat].accounts) data[cat].accounts = [];
                            data[cat].accounts = data[cat].accounts.map(acc => ({
                                ...acc,
                                likes: acc.likes || 0,
                                dislikes: acc.dislikes || 0
                            }));
                            // Если нет iconImage, но есть icon — оставляем, иначе ставим стандартную
                            if (!data[cat].iconImage && !data[cat].icon) {
                                data[cat].icon = 'fa-solid fa-gamepad';
                            }
                        } else {
                            const oldAccs = data[cat];
                            data[cat] = {
                                icon: 'fa-solid fa-gamepad',
                                vip: false,
                                iconImage: null,
                                accounts: oldAccs.map(acc => ({
                                    ...acc,
                                    likes: acc.likes || 0,
                                    dislikes: acc.dislikes || 0
                                }))
                            };
                        }
                    }
                } catch (_) { data = {}; }
            } else {
                data = {};
            }

            const storedVotes = localStorage.getItem('gamevault_votes');
            if (storedVotes) {
                try { votes = JSON.parse(storedVotes); } catch (_) { votes = {}; }
            } else {
                votes = {};
            }

            const storedUsers = localStorage.getItem('gamevault_users');
            if (storedUsers) {
                try {
                    users = JSON.parse(storedUsers);
                    for (const email in users) {
                        if (typeof users[email] === 'string') {
                            users[email] = { password: users[email], vip: false };
                        } else {
                            users[email].vip = users[email].vip || false;
                        }
                    }
                } catch (_) { users = {}; }
            } else {
                users = {};
            }

            const storedUser = localStorage.getItem('gamevault_current_user');
            if (storedUser) {
                currentUser = storedUser;
            } else {
                currentUser = null;
            }
            saveData();
        }

        function saveData() {
            localStorage.setItem('gamevault_categories', JSON.stringify(data));
            localStorage.setItem('gamevault_votes', JSON.stringify(votes));
            localStorage.setItem('gamevault_users', JSON.stringify(users));
            if (currentUser) {
                localStorage.setItem('gamevault_current_user', currentUser);
            } else {
                localStorage.removeItem('gamevault_current_user');
            }
        }

        // --------------------------------------------------------------
        //  DOM-ссылки
        // --------------------------------------------------------------
        const mainGrid = document.getElementById('mainGrid');
        const backBtn = document.getElementById('backBtn');
        const categoryTitle = document.getElementById('categoryTitle');
        const totalCategoriesEl = document.getElementById('totalCategories');
        const totalAccountsEl = document.getElementById('totalAccounts');
        const userInfoContainer = document.getElementById('userInfoContainer');

        const adminModal = document.getElementById('adminModal');
        const adminToggleBtn = document.getElementById('adminToggleBtn');
        const modalCloseBtn = document.getElementById('modalCloseBtn');
        const modalCloseBtn2 = document.getElementById('modalCloseBtn2');
        const newCategoryInput = document.getElementById('newCategoryInput');
        const newCategoryVip = document.getElementById('newCategoryVip');
        const addCategoryBtn = document.getElementById('addCategoryBtn');
        const categoryListAdmin = document.getElementById('categoryListAdmin');
        const adminCategorySelect = document.getElementById('adminCategorySelect');
        const adminAccountsList = document.getElementById('adminAccountsList');
        const adminLoginInput = document.getElementById('adminLoginInput');
        const adminPassInput = document.getElementById('adminPassInput');
        const addAccountBtn = document.getElementById('addAccountBtn');
        const usersListAdmin = document.getElementById('usersListAdmin');

        // Элементы загрузки иконки
        const categoryIconInput = document.getElementById('categoryIconInput');
        const categoryFileLabel = document.getElementById('categoryFileLabel');
        const categoryFilePreview = document.getElementById('categoryFilePreview');
        const categoryFileStatus = document.getElementById('categoryFileStatus');

        const authModal = document.getElementById('authModal');
        const authModalClose = document.getElementById('authModalClose');
        const authModalTitle = document.getElementById('authModalTitle');
        const authFormBody = document.getElementById('authFormBody');
        const authForm = document.getElementById('authForm');

        const adminPasswordModal = document.getElementById('adminPasswordModal');
        const adminPasswordClose = document.getElementById('adminPasswordClose');
        const adminPasswordInput = document.getElementById('adminPasswordInput');
        const adminPasswordSubmit = document.getElementById('adminPasswordSubmit');

        const accountModal = document.getElementById('accountModal');
        const accountModalClose = document.getElementById('accountModalClose');
        const accountStatsContent = document.getElementById('accountStatsContent');

        const toastContainer = document.getElementById('toastContainer');

        // --------------------------------------------------------------
        //  UI АВТОРИЗАЦИИ
        // --------------------------------------------------------------
        function renderAuthUI() {
            if (currentUser) {
                const isVip = users[currentUser]?.vip || false;
                userInfoContainer.innerHTML = `
                    <div class="user-info">
                        <span class="email"><i class="fas fa-user"></i> ${escHtml(currentUser)}</span>
                        ${isVip ? '<span class="vip-badge">VIP</span>' : ''}
                        <button class="logout-btn" id="logoutBtn"><i class="fas fa-sign-out-alt"></i></button>
                    </div>
                    <button class="account-btn" id="accountBtn"><i class="fas fa-chart-pie"></i> Аккаунт</button>
                `;
                document.getElementById('logoutBtn')?.addEventListener('click', logout);
                document.getElementById('accountBtn')?.addEventListener('click', openAccountModal);
            } else {
                userInfoContainer.innerHTML = `
                    <button class="auth-btn" id="loginBtn"><i class="fas fa-sign-in-alt"></i> Войти</button>
                `;
                document.getElementById('loginBtn')?.addEventListener('click', () => openAuthModal('login'));
            }
        }

        // --------------------------------------------------------------
        //  АВТОРИЗАЦИЯ
        // --------------------------------------------------------------
        function openAuthModal(mode = 'login') {
            authModal.classList.add('open');
            renderAuthForm(mode);
        }

        function closeAuthModal() {
            authModal.classList.remove('open');
        }

        function renderAuthForm(mode) {
            if (mode === 'login') {
                authModalTitle.innerHTML = '<i class="fas fa-sign-in-alt"></i> Вход';
                authFormBody.innerHTML = `
                    <div class="form-group">
                        <label>Email</label>
                        <input type="email" id="loginEmail" placeholder="example@mail.com" required />
                    </div>
                    <div class="form-group">
                        <label>Пароль</label>
                        <input type="password" id="loginPassword" placeholder="Пароль" required />
                    </div>
                    <button type="submit" class="btn-primary" style="width:100%;"><i class="fas fa-sign-in-alt"></i> Войти</button>
                    <div class="auth-switch">Нет аккаунта? <a id="switchToRegister">Зарегистрироваться</a></div>
                `;
                authForm.onsubmit = function(e) {
                    e.preventDefault();
                    const email = document.getElementById('loginEmail').value.trim();
                    const password = document.getElementById('loginPassword').value.trim();
                    loginUser(email, password);
                };
                document.getElementById('switchToRegister')?.addEventListener('click', () => renderAuthForm('register'));
            } else {
                authModalTitle.innerHTML = '<i class="fas fa-user-plus"></i> Регистрация';
                authFormBody.innerHTML = `
                    <div class="form-group">
                        <label>Email</label>
                        <input type="email" id="regEmail" placeholder="example@mail.com" required />
                    </div>
                    <div class="form-group">
                        <label>Пароль</label>
                        <input type="password" id="regPassword" placeholder="Пароль" required />
                    </div>
                    <div class="form-group">
                        <label>Подтверждение пароля</label>
                        <input type="password" id="regPassword2" placeholder="Повторите пароль" required />
                    </div>
                    <button type="submit" class="btn-primary" style="width:100%;"><i class="fas fa-user-plus"></i> Зарегистрироваться</button>
                    <div class="auth-switch">Уже есть аккаунт? <a id="switchToLogin">Войти</a></div>
                `;
                authForm.onsubmit = function(e) {
                    e.preventDefault();
                    const email = document.getElementById('regEmail').value.trim();
                    const password = document.getElementById('regPassword').value.trim();
                    const password2 = document.getElementById('regPassword2').value.trim();
                    registerUser(email, password, password2);
                };
                document.getElementById('switchToLogin')?.addEventListener('click', () => renderAuthForm('login'));
            }
        }

        function registerUser(email, password, password2) {
            if (!email || !password || !password2) {
                showToast('Заполните все поля', 'warning');
                return;
            }
            if (password !== password2) {
                showToast('Пароли не совпадают', 'warning');
                return;
            }
            if (users[email]) {
                showToast('Пользователь с таким email уже существует', 'warning');
                return;
            }
            users[email] = { password, vip: false };
            currentUser = email;
            if (!votes[email]) votes[email] = {};
            saveData();
            closeAuthModal();
            renderAuthUI();
            render();
            showToast(`✅ Добро пожаловать, ${email}!`, 'success');
        }

        function loginUser(email, password) {
            if (!email || !password) {
                showToast('Заполните все поля', 'warning');
                return;
            }
            if (!users[email]) {
                showToast('Пользователь не найден', 'error');
                return;
            }
            if (users[email].password !== password) {
                showToast('Неверный пароль', 'error');
                return;
            }
            currentUser = email;
            if (!votes[email]) votes[email] = {};
            saveData();
            closeAuthModal();
            renderAuthUI();
            render();
            showToast(`👋 С возвращением, ${email}!`, 'success');
        }

        function logout() {
            currentUser = null;
            saveData();
            renderAuthUI();
            render();
            showToast('Вы вышли', 'info');
        }

        // --------------------------------------------------------------
        //  VIP-проверка
        // --------------------------------------------------------------
        function isVipUser() {
            return currentUser && users[currentUser] && users[currentUser].vip === true;
        }

        function isLoggedIn() {
            return currentUser !== null;
        }

        // --------------------------------------------------------------
        //  ГОЛОСОВАНИЕ
        // --------------------------------------------------------------
        function handleRating(category, index, type) {
            if (!currentUser) {
                showToast('Пожалуйста, войдите, чтобы голосовать', 'warning');
                return;
            }
            const cat = data[category];
            if (!cat) return;
            const acc = cat.accounts[index];
            if (!acc) return;

            if (!votes[currentUser]) votes[currentUser] = {};
            if (!votes[currentUser][category]) votes[currentUser][category] = {};
            const userVote = votes[currentUser][category][index];

            if (userVote === type) {
                delete votes[currentUser][category][index];
                if (type === 'like') acc.likes = Math.max(0, (acc.likes || 0) - 1);
                else acc.dislikes = Math.max(0, (acc.dislikes || 0) - 1);
                saveData();
                render();
                showToast('Голос снят', 'info');
                return;
            }

            if (userVote && userVote !== type) {
                if (userVote === 'like') acc.likes = Math.max(0, (acc.likes || 0) - 1);
                else acc.dislikes = Math.max(0, (acc.dislikes || 0) - 1);
                votes[currentUser][category][index] = type;
                if (type === 'like') acc.likes = (acc.likes || 0) + 1;
                else acc.dislikes = (acc.dislikes || 0) + 1;
                saveData();
                render();
                showToast(`Голос изменён на ${type === 'like' ? '👍' : '👎'}`, 'info');
                return;
            }

            votes[currentUser][category][index] = type;
            if (type === 'like') acc.likes = (acc.likes || 0) + 1;
            else acc.dislikes = (acc.dislikes || 0) + 1;
            saveData();
            render();
            showToast(`Голос ${type === 'like' ? '👍' : '👎'} поставлен`, 'success');
        }

        // --------------------------------------------------------------
        //  ОТОБРАЖЕНИЕ
        // --------------------------------------------------------------
        function render() {
            const categories = Object.keys(data);
            totalCategoriesEl.textContent = categories.length;
            let totalAccs = 0;
            for (const cat of categories) totalAccs += data[cat].accounts.length;
            totalAccountsEl.textContent = totalAccs;

            if (currentCategory && data[currentCategory]) {
                showAccounts(currentCategory);
            } else {
                showCategories();
            }
            renderAuthUI();
        }

        // ----- КАТЕГОРИИ (видны всем) -----
        function showCategories() {
            backBtn.classList.remove('visible');
            categoryTitle.classList.remove('visible');

            const categories = Object.keys(data);
            if (categories.length === 0) {
                mainGrid.innerHTML = `
                    <div class="empty-state">
                        <i class="fas fa-folder-open"></i>
                        <h3>Пока нет игр</h3>
                        <p>Добавьте первую игру через админ-панель.</p>
                        <button class="admin-hint" id="emptyAdminHint">Перейти в админку</button>
                    </div>
                `;
                document.getElementById('emptyAdminHint')?.addEventListener('click', () => openAdminModal());
                return;
            }

            let html = '';
            for (const cat of categories) {
                const catData = data[cat];
                const count = catData.accounts.length;
                const adminClass = isAdmin ? 'admin-mode' : '';
                const vipBadge = catData.vip ? '<span class="vip-badge">VIP</span>' : '';
                const lockIcon = catData.vip ? '<i class="fas fa-lock vip-lock"></i>' : '';

                // Иконка: если есть iconImage — показываем img, иначе иконка Font Awesome
                let iconHtml;
                if (catData.iconImage) {
                    iconHtml = `<img src="${catData.iconImage}" alt="${escHtml(cat)}" />`;
                } else {
                    const iconClass = catData.icon || 'fa-solid fa-gamepad';
                    iconHtml = `<i class="${iconClass}"></i>`;
                }

                html += `
                    <div class="category-card ${adminClass}" data-category="${escHtml(cat)}">
                        ${vipBadge}
                        ${lockIcon}
                        ${isAdmin ? `<button class="admin-delete-category" data-category="${escHtml(cat)}" title="Удалить игру"><i class="fas fa-trash"></i></button>` : ''}
                        <div class="icon">${iconHtml}</div>
                        <div class="name">${escHtml(cat)}</div>
                        <div class="count">${count} аккаунт${count % 10 === 1 && count !== 11 ? '' : (count % 10 >= 2 && count % 10 <= 4 && (count < 10 || count > 20) ? 'а' : 'ов')}</div>
                    </div>
                `;
            }
            mainGrid.innerHTML = html;

            document.querySelectorAll('.category-card').forEach(card => {
                card.addEventListener('click', function(e) {
                    if (e.target.closest('.admin-delete-category')) return;
                    const cat = this.dataset.category;
                    if (cat) {
                        if (data[cat] && data[cat].vip && !isVipUser()) {
                            showToast('Эта игра доступна только VIP-пользователям!', 'warning');
                            return;
                        }
                        currentCategory = cat;
                        render();
                    }
                });
            });

            if (isAdmin) {
                document.querySelectorAll('.admin-delete-category').forEach(btn => {
                    btn.addEventListener('click', function(e) {
                        e.stopPropagation();
                        const cat = this.dataset.category;
                        if (confirm(`Удалить игру "${cat}" и все её аккаунты?`)) deleteCategory(cat);
                    });
                });
            }
        }

        // ----- АККАУНТЫ -----
        function showAccounts(category) {
            backBtn.classList.add('visible');
            categoryTitle.classList.add('visible');
            categoryTitle.textContent = `🎮 ${category}`;

            const catData = data[category];
            if (!catData) {
                mainGrid.innerHTML = `<div class="empty-state"><i class="fas fa-exclamation-triangle"></i><h3>Игра не найдена</h3></div>`;
                return;
            }
            const accounts = catData.accounts;
            if (accounts.length === 0) {
                mainGrid.innerHTML = `
                    <div class="empty-state">
                        <i class="fas fa-user-slash"></i>
                        <h3>В этой игре пока нет аккаунтов</h3>
                        <p>Добавьте аккаунты через админ-панель.</p>
                    </div>
                `;
                return;
            }

            const userVotes = (currentUser && votes[currentUser] && votes[currentUser][category]) ? votes[currentUser][
                category
            ] : {};
            const loggedIn = isLoggedIn();

            let html = '';
            accounts.forEach((acc, index) => {
                const likes = acc.likes || 0;
                const dislikes = acc.dislikes || 0;
                const userVote = userVotes[index];
                const likeActive = userVote === 'like' ? 'active-like' : '';
                const dislikeActive = userVote === 'dislike' ? 'active-dislike' : '';

                let loginDisplay, passDisplay;
                if (loggedIn) {
                    loginDisplay = `<span class="value">${escHtml(acc.login)}</span>`;
                    passDisplay =
                        `<span class="value password-hidden" data-index="${index}">${escHtml(acc.password)}</span>`;
                } else {
                    loginDisplay = `<span class="value placeholder">Только для зарегистрированных</span>`;
                    passDisplay = `<span class="value placeholder">Только для зарегистрированных</span>`;
                }

                html += `
                    <div class="account-card" data-category="${escHtml(category)}" data-index="${index}">
                        <div class="credential-row">
                            <span class="label"><i class="fas fa-user"></i> Логин</span>
                            ${loginDisplay}
                        </div>
                        <div class="credential-row">
                            <span class="label"><i class="fas fa-key"></i> Пароль</span>
                            ${passDisplay}
                        </div>

                        <div class="rating-section">
                            <button class="rating-btn like ${likeActive} ${!loggedIn ? 'disabled' : ''}" data-category="${escHtml(category)}" data-index="${index}" data-type="like" ${!loggedIn ? 'disabled' : ''}>
                                <i class="fas fa-thumbs-up"></i>
                                <span class="count likes-count">${likes}</span>
                            </button>
                            <button class="rating-btn dislike ${dislikeActive} ${!loggedIn ? 'disabled' : ''}" data-category="${escHtml(category)}" data-index="${index}" data-type="dislike" ${!loggedIn ? 'disabled' : ''}>
                                <i class="fas fa-thumbs-down"></i>
                                <span class="count dislikes-count">${dislikes}</span>
                            </button>
                        </div>

                        ${isAdmin ? `
                        <div class="admin-actions">
                            <button class="admin-btn danger" data-category="${escHtml(category)}" data-index="${index}"><i class="fas fa-trash"></i> Удалить</button>
                        </div>
                        ` : ''}
                    </div>
                `;
            });
            mainGrid.innerHTML = html;

            if (loggedIn) {
                document.querySelectorAll('.password-hidden').forEach(el => {
                    el.addEventListener('click', function(e) {
                        e.stopPropagation();
                        this.classList.toggle('show');
                        if (this.classList.contains('show')) {
                            clearTimeout(this._hideTimer);
                            this._hideTimer = setTimeout(() => this.classList.remove('show'), 4000);
                        }
                    });
                });
            }

            document.querySelectorAll('.rating-btn:not(.disabled)').forEach(btn => {
                btn.addEventListener('click', function(e) {
                    e.stopPropagation();
                    const cat = this.dataset.category;
                    const idx = parseInt(this.dataset.index);
                    const type = this.dataset.type;
                    handleRating(cat, idx, type);
                });
            });

            if (isAdmin) {
                document.querySelectorAll('.admin-btn.danger').forEach(btn => {
                    btn.addEventListener('click', function(e) {
                        const cat = this.dataset.category;
                        const idx = parseInt(this.dataset.index);
                        if (confirm('Удалить этот аккаунт?')) deleteAccount(cat, idx);
                    });
                });
            }

            backBtn.onclick = function() { currentCategory = null;
                render(); };
        }

        // --------------------------------------------------------------
        //  УДАЛЕНИЕ
        // --------------------------------------------------------------
        function deleteCategory(category) {
            if (!data[category]) return;
            delete data[category];
            for (const email in votes) {
                if (votes[email][category]) delete votes[email][category];
            }
            if (currentCategory === category) currentCategory = null;
            saveData();
            render();
            showToast(`🗑️ Игра "${category}" удалена`, 'info');
        }

        function deleteAccount(category, index) {
            if (!data[category]) return;
            data[category].accounts.splice(index, 1);
            for (const email in votes) {
                if (votes[email][category] && votes[email][category][index] !== undefined) {
                    delete votes[email][category][index];
                }
            }
            saveData();
            render();
            showToast('🗑️ Аккаунт удалён', 'info');
        }

        // --------------------------------------------------------------
        //  АДМИН-ПАНЕЛЬ
        // --------------------------------------------------------------
        function openAdminPasswordModal() {
            adminPasswordModal.classList.add('open');
            adminPasswordInput.value = '';
            adminPasswordInput.focus();
        }

        function closeAdminPasswordModal() {
            adminPasswordModal.classList.remove('open');
        }

        function checkAdminPassword() {
            const pass = adminPasswordInput.value.trim();
            if (pass === ADMIN_PASSWORD) {
                adminAuthenticated = true;
                closeAdminPasswordModal();
                openAdminModal();
            } else {
                showToast('Неверный пароль', 'error');
                adminPasswordInput.value = '';
                adminPasswordInput.focus();
            }
        }

        function openAdminModal() {
            if (!adminAuthenticated) {
                openAdminPasswordModal();
                return;
            }
            adminModal.classList.add('open');
            isAdmin = true;
            adminToggleBtn.classList.add('active');
            refreshAdminUI();
            render();
        }

        function closeAdminModal() {
            adminModal.classList.remove('open');
            isAdmin = false;
            adminToggleBtn.classList.remove('active');
            // Сбрасываем загрузку иконки
            resetCategoryIconUpload();
            render();
        }

        function resetCategoryIconUpload() {
            categoryIconFile = null;
            categoryIconPreview = null;
            categoryIconInput.value = '';
            categoryFilePreview.classList.remove('show');
            categoryFilePreview.src = '';
            const span = categoryFileLabel.querySelector('span');
            if (span) span.textContent = 'Выберите файл или перетащите сюда';
            categoryFileStatus.textContent = '';
        }

        function refreshAdminUI() {
            const categories = Object.keys(data);
            let html = '';
            if (categories.length === 0) {
                html = '<p style="color:#6f7d95; font-size:14px;">Игр пока нет.</p>';
            } else {
                for (const cat of categories) {
                    const catData = data[cat];
                    const vipTag = catData.vip ? '<span class="vip-tag">VIP</span>' : '';
                    html += `
                        <div class="category-item-admin">
                            <span class="cat-name">${escHtml(cat)} ${vipTag}</span>
                            <div class="cat-actions">
                                <button class="admin-small-btn add-acc-btn" data-category="${escHtml(cat)}" title="Выбрать для добавления аккаунтов"><i class="fas fa-user-plus"></i></button>
                                <button class="admin-small-btn" data-category="${escHtml(cat)}" title="Удалить игру"><i class="fas fa-trash"></i></button>
                            </div>
                        </div>
                    `;
                }
            }
            categoryListAdmin.innerHTML = html;

            document.querySelectorAll('#categoryListAdmin .admin-small-btn[data-category]').forEach(btn => {
                btn.addEventListener('click', function() {
                    const cat = this.dataset.category;
                    if (this.classList.contains('add-acc-btn')) {
                        adminCategorySelect.value = cat;
                        refreshAdminAccounts(cat);
                    } else {
                        if (confirm(`Удалить игру "${cat}" и все аккаунты?`)) {
                            deleteCategory(cat);
                            refreshAdminUI();
                        }
                    }
                });
            });

            const select = adminCategorySelect;
            select.innerHTML = '<option value="">-- Выберите игру --</option>';
            for (const cat of categories) {
                const opt = document.createElement('option');
                opt.value = cat;
                opt.textContent = cat;
                select.appendChild(opt);
            }
            const selectedCat = select.value;
            if (selectedCat && data[selectedCat]) {
                refreshAdminAccounts(selectedCat);
            } else {
                adminAccountsList.innerHTML = '<p style="color:#6f7d95; font-size:14px;">Выберите игру.</p>';
            }
            select.onchange = function() {
                const cat = this.value;
                if (cat && data[cat]) refreshAdminAccounts(cat);
                else adminAccountsList.innerHTML = '<p style="color:#6f7d95; font-size:14px;">Выберите игру.</p>';
            };

            refreshUsersList();
            resetCategoryIconUpload();
        }

        function refreshAdminAccounts(category) {
            const catData = data[category];
            if (!catData) {
                adminAccountsList.innerHTML = '<p style="color:#6f7d95; font-size:14px;">Игра не найдена.</p>';
                return;
            }
            const accounts = catData.accounts;
            let html = '';
            if (accounts.length === 0) {
                html = '<p style="color:#6f7d95; font-size:14px;">В этой игре нет аккаунтов. Добавьте ниже.</p>';
            } else {
                for (let i = 0; i < accounts.length; i++) {
                    const acc = accounts[i];
                    const likes = acc.likes || 0;
                    const dislikes = acc.dislikes || 0;
                    html += `
                        <div class="account-item-admin">
                            <div class="acc-info">
                                <span class="login">${escHtml(acc.login)}</span>
                                <span class="pass">${escHtml(acc.password)}</span>
                                <span class="rating">👍 ${likes}  👎 ${dislikes}</span>
                            </div>
                            <button class="admin-small-btn" data-category="${escHtml(category)}" data-index="${i}" title="Удалить аккаунт"><i class="fas fa-trash"></i></button>
                        </div>
                    `;
                }
            }
            adminAccountsList.innerHTML = html;

            document.querySelectorAll('#adminAccountsList .admin-small-btn[data-category]').forEach(btn => {
                btn.addEventListener('click', function() {
                    const cat = this.dataset.category;
                    const idx = parseInt(this.dataset.index);
                    if (confirm('Удалить этот аккаунт?')) {
                        deleteAccount(cat, idx);
                        refreshAdminAccounts(cat);
                        render();
                    }
                });
            });
        }

        function refreshUsersList() {
            const userEmails = Object.keys(users);
            let html = '';
            if (userEmails.length === 0) {
                html = '<p style="color:#6f7d95; font-size:14px;">Нет зарегистрированных пользователей.</p>';
            } else {
                for (const email of userEmails) {
                    const user = users[email];
                    const vip = user.vip || false;
                    html += `
                        <div class="user-item-admin">
                            <span class="user-email">${escHtml(email)}</span>
                            <span class="user-vip">${vip ? 'VIP' : 'Обычный'}</span>
                            <div class="user-actions">
                                <button class="admin-btn ${vip ? 'danger' : 'success'}" data-email="${escHtml(email)}" style="font-size:12px; padding:2px 12px;">
                                    ${vip ? 'Снять VIP' : 'Назначить VIP'}
                                </button>
                            </div>
                        </div>
                    `;
                }
            }
            usersListAdmin.innerHTML = html;

            document.querySelectorAll('#usersListAdmin .admin-btn').forEach(btn => {
                btn.addEventListener('click', function() {
                    const email = this.dataset.email;
                    if (!users[email]) return;
                    users[email].vip = !users[email].vip;
                    saveData();
                    refreshUsersList();
                    render();
                    showToast(`VIP-статус пользователя ${email} обновлён`, 'info');
                });
            });
        }

        // --------------------------------------------------------------
        //  ДОБАВЛЕНИЕ КАТЕГОРИИ (с загрузкой изображения)
        // --------------------------------------------------------------
        function addCategory() {
            const name = newCategoryInput.value.trim();
            if (!name) { showToast('Введите название игры', 'warning'); return; }
            if (data[name]) { showToast('Такая игра уже существует', 'warning'); return; }

            const vip = newCategoryVip.checked;
            const newCat = {
                icon: 'fa-solid fa-gamepad', // fallback
                vip: vip,
                iconImage: null,
                accounts: []
            };

            // Если загружено изображение — сохраняем base64
            if (categoryIconFile) {
                const reader = new FileReader();
                reader.onload = function(e) {
                    newCat.iconImage = e.target.result;
                    data[name] = newCat;
                    saveData();
                    resetCategoryIconUpload();
                    newCategoryInput.value = '';
                    newCategoryVip.checked = false;
                    refreshAdminUI();
                    render();
                    showToast(`✅ Игра "${name}" добавлена с иконкой`, 'success');
                };
                reader.readAsDataURL(categoryIconFile);
            } else {
                // Если изображение не загружено — используем стандартную иконку
                data[name] = newCat;
                saveData();
                resetCategoryIconUpload();
                newCategoryInput.value = '';
                newCategoryVip.checked = false;
                refreshAdminUI();
                render();
                showToast(`✅ Игра "${name}" добавлена (стандартная иконка)`, 'success');
            }
        }

        // --------------------------------------------------------------
        //  ДОБАВЛЕНИЕ АККАУНТА
        // --------------------------------------------------------------
        function addAccountToCategory() {
            const category = adminCategorySelect.value;
            if (!category || !data[category]) { showToast('Сначала выберите игру', 'warning'); return; }
            const login = adminLoginInput.value.trim();
            const password = adminPassInput.value.trim();
            if (!login || !password) { showToast('Заполните логин и пароль', 'warning'); return; }
            data[category].accounts.push({ login, password, likes: 0, dislikes: 0 });
            saveData();
            adminLoginInput.value = '';
            adminPassInput.value = '';
            refreshAdminAccounts(category);
            render();
            showToast(`✅ Аккаунт "${login}" добавлен`, 'success');
        }

        // --------------------------------------------------------------
        //  АККАУНТ (статистика)
        // --------------------------------------------------------------
        function openAccountModal() {
            if (!currentUser) {
                showToast('Войдите, чтобы увидеть статистику', 'warning');
                return;
            }
            accountModal.classList.add('open');
            renderAccountStats();
        }

        function closeAccountModal() {
            accountModal.classList.remove('open');
        }

        function renderAccountStats() {
            const totalUsers = Object.keys(users).length;
            const totalGames = Object.keys(data).length;
            let totalAccs = 0;
            let totalLikes = 0;
            let totalDislikes = 0;
            for (const cat in data) {
                const accs = data[cat].accounts;
                totalAccs += accs.length;
                for (const acc of accs) {
                    totalLikes += acc.likes || 0;
                    totalDislikes += acc.dislikes || 0;
                }
            }
            const isVip = users[currentUser]?.vip || false;

            accountStatsContent.innerHTML = `
                <div class="stats-user-info">
                    <span class="id"><i class="fas fa-id-card"></i> ID: ${escHtml(currentUser)}</span>
                    <span class="vip-status">${isVip ? '👑 VIP' : 'Обычный пользователь'}</span>
                </div>
                <div class="stats-grid">
                    <div class="stats-item">
                        <div class="number">${totalUsers}</div>
                        <div class="label">Пользователей</div>
                    </div>
                    <div class="stats-item">
                        <div class="number">${totalGames}</div>
                        <div class="label">Игр</div>
                    </div>
                    <div class="stats-item">
                        <div class="number">${totalAccs}</div>
                        <div class="label">Аккаунтов</div>
                    </div>
                    <div class="stats-item">
                        <div class="number">${totalLikes}</div>
                        <div class="label">Всего лайков</div>
                    </div>
                </div>
                <p style="color:#8a9bb0; font-size:14px; text-align:center; margin-top:12px;">
                    <i class="fas fa-thumbs-up"></i> Лайков: ${totalLikes} &nbsp;|&nbsp; <i class="fas fa-thumbs-down"></i> Дизлайков: ${totalDislikes}
                </p>
            `;
        }

        // --------------------------------------------------------------
        //  TOAST
        // --------------------------------------------------------------
        function showToast(message, type = 'info') {
            const iconMap = { success: 'fa-check-circle', error: 'fa-times-circle', warning: 'fa-exclamation-triangle',
                info: 'fa-info-circle' };
            const icon = iconMap[type] || iconMap.info;
            const toast = document.createElement('div');
            toast.className = `toast ${type}`;
            toast.innerHTML = `
                <span class="toast-icon"><i class="fas ${icon}"></i></span>
                <span class="toast-msg">${message}</span>
                <button class="toast-close"><i class="fas fa-times"></i></button>
            `;
            toastContainer.appendChild(toast);
            toast.querySelector('.toast-close').addEventListener('click', () => toast.remove());
            setTimeout(() => { if (toast.parentNode) toast.remove(); }, 5000);
        }

        // --------------------------------------------------------------
        //  ВСПОМОГАТЕЛЬНЫЕ
        // --------------------------------------------------------------
        function escHtml(str) {
            if (!str) return '';
            return String(str).replace(/&/g, '&amp;').replace(/</g, '&lt;').replace(/>/g, '&gt;').replace(/"/g, '&quot;');
        }

        // --------------------------------------------------------------
        //  СОБЫТИЯ
        // --------------------------------------------------------------
        adminToggleBtn.addEventListener('click', function() {
            if (adminModal.classList.contains('open')) {
                closeAdminModal();
            } else {
                openAdminModal();
            }
        });
        modalCloseBtn.addEventListener('click', closeAdminModal);
        modalCloseBtn2.addEventListener('click', closeAdminModal);
        adminModal.addEventListener('click', function(e) { if (e.target === this) closeAdminModal(); });

        adminPasswordClose.addEventListener('click', closeAdminPasswordModal);
        adminPasswordSubmit.addEventListener('click', checkAdminPassword);
        adminPasswordInput.addEventListener('keypress', function(e) {
            if (e.key === 'Enter') checkAdminPassword();
        });
        adminPasswordModal.addEventListener('click', function(e) { if (e.target === this) closeAdminPasswordModal(); });

        addCategoryBtn.addEventListener('click', addCategory);
        newCategoryInput.addEventListener('keypress', e => { if (e.key === 'Enter') addCategory(); });

        addAccountBtn.addEventListener('click', addAccountToCategory);
        adminLoginInput.addEventListener('keypress', e => { if (e.key === 'Enter') addAccountToCategory(); });
        adminPassInput.addEventListener('keypress', e => { if (e.key === 'Enter') addAccountToCategory(); });

        authModalClose.addEventListener('click', closeAuthModal);
        authModal.addEventListener('click', function(e) { if (e.target === this) closeAuthModal(); });

        accountModalClose.addEventListener('click', closeAccountModal);
        accountModal.addEventListener('click', function(e) { if (e.target === this) closeAccountModal(); });

        // ---------- Обработка загрузки иконки ----------
        categoryIconInput.addEventListener('change', function() {
            const file = this.files[0];
            if (file) {
                if (!file.type.startsWith('image/')) {
                    showToast('Пожалуйста, выберите изображение', 'warning');
                    this.value = '';
                    categoryFileStatus.textContent = '';
                    categoryFilePreview.classList.remove('show');
                    categoryIconFile = null;
                    return;
                }
                categoryIconFile = file;
                categoryFileStatus.textContent = `✅ Файл выбран: ${file.name} (${(file.size/1024).toFixed(1)} КБ)`;
                const reader = new FileReader();
                reader.onload = function(e) {
                    categoryFilePreview.src = e.target.result;
                    categoryFilePreview.classList.add('show');
                };
                reader.readAsDataURL(file);
                const span = categoryFileLabel.querySelector('span');
                if (span) span.textContent = 'Файл загружен';
            } else {
                categoryIconFile = null;
                categoryFileStatus.textContent = '';
                categoryFilePreview.classList.remove('show');
                const span = categoryFileLabel.querySelector('span');
                if (span) span.textContent = 'Выберите файл или перетащите сюда';
            }
        });

        // Для поддержки перетаскивания (опционально)
        categoryFileLabel.addEventListener('dragover', function(e) {
            e.preventDefault();
            this.style.borderColor = '#f0c94b';
        });
        categoryFileLabel.addEventListener('dragleave', function(e) {
            e.preventDefault();
            this.style.borderColor = '#2a3342';
        });
        categoryFileLabel.addEventListener('drop', function(e) {
            e.preventDefault();
            this.style.borderColor = '#2a3342';
            const files = e.dataTransfer.files;
            if (files.length > 0) {
                categoryIconInput.files = files;
                categoryIconInput.dispatchEvent(new Event('change'));
            }
        });

        // --------------------------------------------------------------
        //  СТАРТ
        // --------------------------------------------------------------
        loadData();
        render();

        setTimeout(() => {
            if (Object.keys(data).length === 0) {
                showToast('👋 Добро пожаловать! Начните с добавления игр через админ-панель.', 'info');
            }
            if (!currentUser) {
                showToast('🔑 Войдите или зарегистрируйтесь, чтобы видеть логины и пароли.', 'info');
            }
        }, 400);
    </script>

</body>
</html>
