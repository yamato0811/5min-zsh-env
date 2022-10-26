ん？短時間でzshの見た目をきれいにしたい？  
じゃあたった5分で最強のzsh環境を作る方法教えてやるよぉっ！！！

## 01. iTerm2をインストールせよ
https://www.iterm2.com/

## 02. Preztoをインストールせよ
### !注意!
もし、 .zshrc、 .zprofileがある場合は、別フォルダに退避せよ！
Preztoのインストール時に、.zshrc, .zprofileがあると、Preztoの設定ファイルがうまく引き継げない場合があるぞ！
```
mkdir ~/bkp
mv .zshrc .zprofile ~/bkp
```

### インストール
Zshのフレームワーク[Prezto](https://github.com/sorin-ionescu/prezto)をインストールせよ 

まず、リポジトリーをクローンせよ
```
git clone --recursive https://github.com/sorin-ionescu/prezto.git "${ZDOTDIR:-$HOME}/.zprezto"
```
次に設定ファイルの作成をせよ(全コマンドをコピーして貼り付ければOK)
```
setopt EXTENDED_GLOB
for rcfile in "${ZDOTDIR:-$HOME}"/.zprezto/runcoms/^README.md(.N); do
  ln -s "$rcfile" "${ZDOTDIR:-$HOME}/.${rcfile:t}"
done
```
これで、再起動すればガラッと変わったプロンプトが見られる！
<img width="752" alt="スクリーンショット 2022-10-26 15 25 57" src="https://user-images.githubusercontent.com/64122953/197950731-a28fc48d-1f3b-467c-83a6-4a76e767e7eb.png">


もし、悟りを開いてアンインストールしたかったらこれだ！
```
rm -rf ~/.zprezto ~/.zlogin ~/.zlogout ~/.zpreztorc ~/.zprofile ~/.zshenv ~/.zshrc
```

## 03. テーマをIcebergに変えろ
初期設定だとターミナルの色がダサいから[Iceberg](https://github.com/Arc0re/Iceberg-iTerm2)に変えろ

ファイルダウンロード
```
curl -O https://raw.githubusercontent.com/Arc0re/Iceberg-iTerm2/master/iceberg.itermcolors
```
設定(iTerm >> Preferences >> Profiles >> Colors tab >> Color Presets.. )からIcebergをインポート

<img width="600" alt="スクリーンショット 2022-08-25 17 53 02" src="https://user-images.githubusercontent.com/64122953/186620783-ba9683b8-cb9c-4379-b537-24330cc8b8e4.png">

## 04. .zshrcに設定を反映させろ
インストールしたPureとプラグインを反映させるために以下の設定を、.zpreztorcに書き込め！

### pureテーマに変更
```
#
# Prompt
#

# Set the prompt theme to load.
# Setting it to 'random' loads a random theme.
# Auto set to 'off' on dumb terminals.
# 変更箇所
zstyle ':prezto:module:prompt' theme 'pure'
```

### 補完とシンタックスハイライトのモジュールを有効
追加するのはpromptの上だ！
```
# Set the Prezto modules to load (browse modules).
# The order matters.
zstyle ':prezto:load' pmodule \
  'environment' \
  'terminal' \
  'editor' \
  'history' \
  'directory' \
  'spectrum' \
  'utility' \
  'completion' \
  　# 追記箇所 #
  'syntax-highlighting' \
  'autosuggestions' \
　  ##########
  'prompt' \
```

ターミナルを再起動すれば反映される！

以上だ!!
