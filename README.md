# Raspberry Pi 5 — Android 17 Rooted

Raspberry Pi 5 向けに **Android 17（AOSP）のビルド・移植方法を調査する実験プロジェクト**です。将来的には、対応するリカバリ環境やroot化手段も検証します。

> **現在の状態：計画・事前調査段階です。** Android 17・TWRP・KernelSU Next が Raspberry Pi 5 で動作済みという意味ではありません。ハードウェア対応、起動方式、デバイスツリー、カーネル互換性、リカバリ対応、root導入方法は個別に確認する必要があります。

## プロジェクトの目標
- Raspberry Pi 5 向け Android 17 AOSP のビルド環境を再現可能な形で記録する。
- Raspberry Pi 5 固有の設定、カーネル統合、ビルド記録を管理する。
- 対応するリカバリ環境をビルドまたは移植できるか調査する。
- 選択したカーネルとAndroidビルドで KernelSU Next が利用できるか検証する。
- ビルド生成物や配布権利のないファイルを混入させず、スクリプトと文書をGitで管理する。

## 現在の進捗
- [x] 公開リポジトリを作成。
- [x] 初期ドキュメントと .gitignore を追加。
- [ ] Android 17 のソースツリーと Raspberry Pi 5 用デバイス設定を確認する。
- [ ] ビルド用PCのOS、空き容量、メモリ、必要パッケージを記録する。
- [ ] root化やリカバリ変更の前に、標準状態のビルドを成功させる。
- [ ] Raspberry Pi 5 実機で標準イメージの起動を確認する。
- [ ] リカバリの選択肢を調査する（TWRP対応は未確認）。
- [ ] 対象カーネルとブートイメージに対する KernelSU Next の対応を調査する。

段階ごとの作業は[開発ロードマップ](docs/roadmap.md)、環境確認項目は[ビルド環境メモ](docs/build-environment.md)を参照してください。

## 参考にする上流プロジェクト
以下は調査の出発点であり、Android 17 との互換性を保証するものではありません。
- [Raspberry Vanilla — Raspberry Pi 5 デバイスリポジトリ](https://github.com/raspberry-vanilla/android_device_brcm_rpi5)
- [Raspberry Vanilla — Android 17 ブランチのカーネルマニフェスト](https://github.com/raspberry-vanilla/android_kernel_manifest/tree/android-17.0)
- [KonstaKANG — Raspberry Pi 5 向け Android ビルド](https://konstakang.com/devices/rpi5/)

利用前に、上流リポジトリのブランチ、ビルド手順、ライセンス、更新状況を確認してください。別のAndroidバージョン向けの設定をそのまま流用できるとは限りません。

## リポジトリ構成
    .gitignore
    README.md
    docs/
      build-environment.md
      roadmap.md
    manifests/README.md
    scripts/README.md

## 安全性・データ保護
- 実験前に、復元可能なOSイメージとバックアップを用意してください。
- 対象機種とパーティション構成を確認できていないイメージやリカバリを書き込まないでください。
- 署名鍵、アクセストークン、個人用認証情報、個人のバックアップイメージを公開しないでください。
- root化やリカバリ変更によって起動不能やデータ消失が起きる可能性があります。一度に変更する項目を絞り、ソースのリビジョンを記録してください。

## ライセンス
現時点ではライセンスを選定していません。ライセンスが追加されるまでは、このリポジトリ独自の内容を他者が自由に再利用できるとは限りません。