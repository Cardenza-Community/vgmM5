# vgmM5 (v0.98)
vgm and mdx player for M5Stack

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

![Cardputer](card.jpg)

(English version follows below)

---

## 日本語版 (Japanese)

### 概要
vgmM5 は M5Stackシリーズで動作するVGM/VGZおよびMDX(MXDRV)ファイルプレイヤーです。
🎥 **動作風景 (Demonstration):** [https://x.com/layer812/status/2065461081305489671](https://x.com/layer812/status/2065461081305489671)

#### 対応デバイスと機能 (Supported Devices & Features)
| 機能 (Features) \ デバイス (Device) | M5Stack AtomS3R (Echo) | M5Stack Cardputer | M5Stack CoreS3 | + Audio Unit | [M5 TAB5](https://docs.m5stack.com/ja/core/Tab5) |
| :--- | :---: | :---: | :---: | :---: | :---: |
| **ステータス (Status)** | ✔️ 対応済 | ✔️ 対応済 | ✔️ 対応済 | ✔️ 対応済 | 🔮 予定 |
| **VGM/VGZ 再生** | ✔️ | ✔️ | ✔️ | ✔️ | 🔮 |
| **MDX 再生** | ✔️ | ✔️ | ✔️ | ✔️ | 🔮 |
| **内蔵フラッシュ (USB Drive)** | ✔️ | - | ✔️ | ✔️ | 🔮 |
| **MicroSD** | - | ✔️ | ✔️ | - | 🔮 |
| **オンラインモード** | - | ✔️ | - | - | 🔮 |
| **キーボード操作** | - | ✔️ | - | - | - |


#### 対応音源チップ (Supported Sound Chips)
| チップ名 (Chip) | ステータス (Status) |
| :--- | :--- |
| **YM2612 (OPN2)** | ✔️ 対応済 (Supported) |
| **YM3812 (OPL2)** | ✔️ 対応済 (Supported) |
| **SN76489 (PSG)** | ✔️ 対応済 (Supported) |
| **AY-3-8910 (SSG)** | ✔️ 対応済 (Supported) |
| **YM2203 (OPN)** | ✔️ 対応済 (Supported) |
| **YM2608 (OPNA)** | ✔️ 対応済 (Supported |
| **YM2610 (OPNB)** | ✔️ 対応済 (Supported) |
| **YM2151 (OPM)** | ✔️ 対応済 (Supported) |
| **YM2413 (OPLL)** | ✔️ 対応済 (Supported) |
| **SegaPCM** | ✔️ 対応済 (Supported) |
| **K051649 (SCC1)** | ✔️ 対応済 (Supported) |
| **MSM6258** | ✔️ 対応済 (Supported) |
| **OKIM6295** | ✔️ 対応済 (Supported) |
| **Namco C140** | ✔️ 対応済 (Supported |
| **Namco C352** | ✔️ 対応済 (Supported) |

※ いくつかのチップのサウンドテストを経た安定板（v0.98）です。ソースは近日更新します。
※ ステータスが「対応済」となっていても、もし再生時に音がおかしい・違和感があると感じた場合は、曲名とおかしい点を優しく申告していただければ対応いたします！

### 特徴
- **オンラインモード**: Wi-Fiに接続することで、VGM/VGZXファイルをダウンロードする手間なく、クラウドのファイルを指定して再生できます。
- **MDX (MXDRV) フォーマット対応**: VGM形式に加えて、X68000で広く使われたMDX形式の再生にも対応しました。
- **VGZ(GZIP圧縮)対応**: 解凍せずにそのまま再生可能。
- **軽量・高速**: M5Stackの限られたリソースに最適化。

### インストール方法 (M5 Burner)
手軽に試す場合は、M5 Burnerから以下のシェアコードでファームウェアを直接書き込めます。

- **M5Stack Cardputer用 シェアコード:** `Rvu8ybi4QoFenMNM`
- **M5Stack Atom Echo S3R用 シェアコード:** `RFZVJ0k81yqvL6BK`
- **M5Stack CoreS3用 シェアコード:** `0bmOieGu4PiD2yEZ`

---

### 操作方法

#### 💻 M5Stack Cardputer
Cardputer版はMicroSDカード内のファイル再生に加え、オンラインモードでの再生に対応しています。

**基本操作:**
- **上下 / 方向キー**: ファイルや項目の選択
- **Spaceキー**: 選択した曲の再生 / 停止
- **= キー**: 音量アップ
- **- キー**: 音量ダウン

**オンラインモードの操作:**
- Online/Local: オンラインモードとローカルモード（SDカード）を切り替えます。
- オンラインモードでは、アルバムや曲のリストを読み込み、選択するだけでジュークボックスのように自動で再生が始まります。

#### 🎧 M5Stack Atom Echo S3R
AtomS3Rは画面表示を持たず、メインボタンで操作します。起動時は無音状態で待機します。
- **1クリック**: 再生 / 停止
- **ダブルクリック**: 次の曲
- **トリプルクリック**: 前の曲
- **起動中にボタン長押し**: USBドライブモードに入り、PCから直接ファイルを追加できます。

---

## English Version

### Overview
vgmM5 is a VGM/VGZ and MDX (X68000) file player designed specifically for the M5Stack series.
🎥 **Demonstration:** [https://x.com/layer812/status/2065461081305489671](https://x.com/layer812/status/2065461081305489671)


| Features \ Device | M5Stack AtomS3R (Echo) | M5Stack Cardputer | M5Stack CoreS3 | + Audio Unit | [M5 TAB5](https://docs.m5stack.com/ja/core/Tab5) |
| :--- | :---: | :---: | :---: | :---: | :---: |
| **Status** | ✔️ Supported | ✔️ Supported | ✔️ Supported | ✔️ Supported | 🔮 Future |
| **VGM/VGZ Playback** | ✔️ | ✔️ | ✔️ | ✔️ | 🔮 |
| **MDX Playback** | ✔️ | ✔️ | ✔️ | ✔️ | 🔮 |
| **Internal Flash (USB Drive)** | ✔️ | - | ✔️ | ✔️ | 🔮 |
| **MicroSD** | - | ✔️ | ✔️ | - | 🔮 |
| **Online Mode** | - | ✔️ | - |  - | 🔮 |
| **Keyboard Control** | - | ✔️ | - | - | - |

#### Supported Sound Chips
*(Please refer to the Supported Sound Chips table in the Japanese section above)*

*Note: This is a stable version (v0.98) after sound tests on various chips.*
*Even if a chip is listed as "Supported," if you notice any strange sounds or something feels off during playback, please kindly report it (gently) with the song title and the issue, and I will address it!*

### Features
- **Online Mode (Jukebox)**: Connect via Wi-Fi to play VGM/VGZ files directly from the cloud without the need to download and save them to a MicroSD card.
- **MDX (X68000) Support**: Added playback support for the MDX format, popular on the Sharp X68000.
- **VGZ (GZIP) Support**: Plays directly without decompression.
- **Lightweight & Fast**: Highly optimized for M5Stack's limited hardware resources.

### Installation (via M5 Burner)
For a quick and easy start, you can flash the firmware directly to your device using M5 Burner with the following share codes:

- **M5Stack Cardputer Share Code:** `Rvu8ybi4QoFenMNM`
- **M5Stack Atom Echo S3R Share Code:** `RFZVJ0k81yqvL6BK`
- **M5Stack CoreS3 Share Code:** `0bmOieGu4PiD2yEZ`
---

### Controls

#### 💻 M5Stack Cardputer
The Cardputer version plays files directly from a MicroSD card and supports streaming via Online Mode.

**Basic Controls:**
- **Up/Down / Arrow Keys**: Select file or item
- **Space Key**: Play/Stop selected track
- **= Key**: Volume Up
- **- Key**: Volume Down

**Online Mode Controls:**
- Online/Local: Toggle between Online Mode and Local Mode (MicroSD).
- In Online Mode, simply browse through albums or tracks and select one to start streaming automatically like a jukebox.

#### 🎧 M5Stack Atom Echo S3R
The AtomS3R version runs headlessly and is controlled via the main screen button. It boots into a silent idle state.
- **1 Click**: Play / Stop
- **Double Click**: Next Track
- **Triple Click**: Previous Track
- **Hold while booting**: Enters USB Drive Mode to add files from your PC.

---

### License
Our original source code, modifications, and the matrix processing sound engine are released under the **MIT License**.

This project utilizes and references the following excellent libraries, code, and assets:
- [mdxtools](https://github.com/vampirefrog/mdxtools) - GPL3.0
- [M5Unified](https://github.com/m5stack/M5Unified) - MIT License
- [MAME](https://www.mamedev.org/) - GPL
- ESP-IDF (FFat / Wear Levelling) - Apache License 2.0
- Puff (zlib decompressor) by Mark Adler - zlib License
- [Misaki Font](https://littlelimit.net/misaki.htm) / Little Limit - Free Font License
- [ymfm](https://github.com/aaronsgiles/ymfm) by Aaron Giles - BSD 3-Clause License