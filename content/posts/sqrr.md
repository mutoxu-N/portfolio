---
# description: ""
showTableOfContents: true
tags: ["Rust", "egui", "QRコード"]
title: "画面上のQRコードを読み取るアプリ「sqrr」"
type: "post"
date: 2026-06-04
---

## 概要

画面上のQRコードを読むためデスクトップアプリ。

![アプリアイコン](/portfolio/images/posts/sqrr/icon.png)

## 主な機能

- **ホットキー起動:** `Ctrl+Shift+Q` を押すだけで、いつでもキャプチャを開始できます。
- **直感的な範囲選択:** マウスをドラッグして、QRコードが含まれる領域を選択できます。
- **QR読み取り:**
  - 読み取った内容がURLの場合、自動的にデフォルトのブラウザで開きます。
  - テキストデータの場合、クリップボードにコピーします。
- **タスクトレイ常駐:** アプリはバックグラウンドで動作します。タスクトレイからアプリを閉じることができます。

## 動機

- eguiを触ってみたかった
- 就活中のオンラインイベントで画面上のQRを読み取る機会が多く、PCで簡単に読み取りたかった

## 技術

RustのeguiというUIフレームワークを使用しています。
{{< linkcard "https://www.egui.rs/" >}}

RustではTauriというフレームワークが人気ですが、
どうしてもWeb技術を触る必要があります。
一方で、eguiはRustだけで完結しており、常駐アプリ向けに省メモリで動作する点から採用しました。

QR処理には[rqrr](https://docs.rs/rqrr/latest/rqrr/)と[rxing](https://docs.rs/rxing/latest/rxing/)というクレートを使っており、`rqrr`で読み取れなかった場合に`rxing`を使うようにしています。

## プログラム

{{< linkcard "https://github.com/mutoxu-N/sqrr" >}}
ソースコード: [GitHub](https://github.com/mutoxu-N/sqrr)
