# ツール

## 動作確認した環境

- WSL2上の Ubuntu 20.04

## セットアップ

### Pythonのインストール

Linux環境を起動し、各種ツールをインストール。

```shell
$ sudo apt update && sudo apt upgrade -y
$ sudo apt install -y build-essential python3 python3-pip python3-venv libpython3-dev
```

### venv上に必要なツールをインストール

```shell
$ python3 -m venv venv-tools
$ source venv-tools/bin/activate
(venv-tools) $ pip3 install -r requirements.txt
```

## Jupyterでツール実行

### JupyterLab を起動

```shell
$ source venv-tools/bin/activate
(venv-tools) $ jupyter lab --no-browser --notebook-dir=..
```

### スクリプト実行

表示されたURLをブラウザで開き、tools/ フォルダ下の ipynb ファイルを開いて 'Run' => 'Run All Cells' メニューを実行する。

## CLIでツール実行

### ipynbをpyファイルに変換してからスクリプト実行

```shell
$ source venv-tools/bin/activate
(venv-tools) $ jupyter nbconvert --output tmp/tmp.py --to python make-zip.ipynb
(venv-tools) $ python tmp/tmp.py
```

### ipynbを直接スクリプト実行

ipynb を実行する。

```shell
$ source venv-tools/bin/activate
(venv-tools) $ papermill --log-output make-zip.ipynb tmp/tmp.ipynb
```
