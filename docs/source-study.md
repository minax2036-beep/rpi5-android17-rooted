# 既存ROMのソース調査ガイド

## この段階の目的

現在の開発機は Raspberry Pi 5（RAM 8GB）で、追加ストレージもありません。そのため、まずはAndroid全体のビルドを行わず、公開されているソースファイルを少量ずつ読み、構成を理解して記録します。

AOSP公式の現行要件では、ビルド用PCに64ビットx86環境、空き容量400GB以上、RAM 64GB以上が示されています。現状のPi 5をフルビルド機として扱うのではなく、調査・文書作成用として使います。

## 調査対象

以下は Android 17 の Raspberry Vanilla プロジェクトにある主な調査先です。ブランチは `android-17.0` です。

- [Pi 5 デバイス設定](https://github.com/raspberry-vanilla/android_device_brcm_rpi5/tree/android-17.0)
- [Androidローカルマニフェスト](https://github.com/raspberry-vanilla/android_local_manifest/tree/android-17.0)
- [カーネルマニフェスト](https://github.com/raspberry-vanilla/android_kernel_manifest/tree/android-17.0)
- [既存の Android 17 Pi 5 ビルド](https://konstakang.com/devices/rpi5/AOSP17/)

## 読む順番

### 1. `README.md`

まず上流プロジェクトのREADMEを読み、必要な環境、対象デバイス、ビルドの流れを把握します。説明されている手順が、現在のブランチに対するものかも確認します。

### 2. `AndroidProducts.mk` と `aosp_rpi5.mk`

- `AndroidProducts.mk`：ビルド対象として登録される製品構成を確認する。
- `aosp_rpi5.mk`：Pi 5 向けAndroid製品に何が含まれるかを確認する。

### 3. `device.mk`

デバイス固有の設定、コピーするファイル、含めるパッケージなどを確認します。最初は変更せず、分からない項目をメモします。

### 4. `BoardConfig.mk`

ボード、アーキテクチャ、パーティション、カーネルやイメージ生成に関係する設定を調べます。設定値を別の機種からそのままコピーしないでください。

### 5. `mkimg.sh` と `manifest_brcm_rpi.xml`

- `mkimg.sh`：ビルド成果物からイメージを組み立てる流れを確認する。実行する前に内容を読む。
- `manifest_brcm_rpi.xml`：ビルドに必要な追加リポジトリと、それらの取得先を確認する。

## Raspberry Pi 5 上での作業

### まず環境を記録する

次のコマンドは情報を表示するだけで、システムを変更しません。

```bash
uname -a
cat /etc/os-release
free -h
df -h
lsblk -o NAME,SIZE,FSTYPE,MOUNTPOINTS,MODEL
```

出力から、OS、CPUアーキテクチャ、メモリ、各ストレージの容量と空き容量を記録します。個人情報や接続先などが出力に含まれる場合は、公開前に伏せてください。

### ソースはブラウザで少しずつ読む

最初はGitHubのファイル画面で上記のファイルを開き、重要な設定や用語を `docs/source-notes.md` に要約します。Android全体のソース同期やフルビルドはまだ行いません。

## 記録テンプレート

調査したファイルごとに次を記録してください。

- ファイル名とURL：
- 対象ブランチ：`android-17.0`
- このファイルの役割：
- 重要な設定・参照先：
- 分からなかった点：
- 次に調べること：

## この段階ではしないこと

- Pi 5 の現在のストレージを消去・再パーティション化する。
- ソースをすべて取得してフルビルドを開始する。
- 読んでいない書き込み用スクリプトやフラッシュ用コマンドを実行する。
- TWRPやKernelSU Nextがこの構成で動作すると、検証前に断定する。

## 次の到達目標

主要な設定ファイルの役割を説明できるようになり、上流ソースのブランチ、コミット、ライセンス、ビルド方法をこのリポジトリに記録することです。