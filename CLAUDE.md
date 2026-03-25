# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## プロジェクト概要

**ミルログ**（iOS 音声操作対応の授乳管理アプリ）のランディングページ。ビルドシステム・パッケージマネージャー・フレームワークなし。全ファイルをそのまま静的配信している。

## 開発

**ローカルでプレビュー:**
```bash
npx serve .          # または任意の静的サーバー
python3 -m http.server 8080
```

ビルド・lint・テストコマンドなし — 純粋な HTML/CSS/JS。

## サイト構成

- `/` — ランディングページ（`index.html` + `style.css`）
- `/privacy/` — プライバシーポリシー（`privacy/index.html`、スタイルはインライン）
- `/assets/images/` — アプリアイコン・App Store バッジ・スクリーンショット

## アーキテクチャ

**シングルページのマーケティングサイト**。セクション構成: hero → 課題カード → 機能紹介 → CTA → フッター。

**CSS デザイントークン**（`style.css` 冒頭で定義）:
```css
--blue: #61A3F2
--peach: #FBB99E
--lavender: #C2AEEB
--bg: #F2F2F7
--text-primary: #3D4554
--text-secondary: #757F93
```

**レスポンシブブレークポイント:** 768px（タブレット）・1024px（デスクトップ）。`clamp()` で流体タイポグラフィ、CSS Grid `auto-fit` でカードレイアウト。

**インタラクション**はバニラ JS のみ — ハンバーガーメニューが nav 要素に `.is-open` を付け外しし、CSS トランジションでアニメーション。

**プライバシーポリシー**（`privacy/index.html`）はスタイルをインラインで持つ独立ファイル。`style.css` は読み込んでいない。
