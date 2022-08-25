## 01. iTerm2をインストールせよ
https://www.iterm2.com/

## 02. Oh My Zshのインストールせよ
Zshのフレームワーク[Oh My Zsh](https://github.com/ohmyzsh/ohmyzsh)をインストールせよ 

```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```
<img width="655" alt="スクリーンショット 2022-08-25 17 32 24" src="https://user-images.githubusercontent.com/64122953/186616180-751a62a0-d39a-45f0-ad9c-981bbd10bce9.png">

もし、悟りを開いてアンインストールしたかったらこれだ！
```
uninstall_oh_my_zsh
Are you sure you want to remove Oh My Zsh? [y/N] y
```

## 03. Pureをインストールせよ
[Pure](https://github.com/sindresorhus/pure)はシンプルなプロンプトだ。  
ごちゃごちゃした見た目のプロンプトを使っているやつは漢じゃねぇ！シンプルこそ正義だ！

```
brew install pure
```

## テーマをIcebergに変えろ
初期設定だとターミナルの色がダサいから[Iceberg](https://github.com/Arc0re/Iceberg-iTerm2)に変えろ

ファイルダウンロード
```
curl -O https://raw.githubusercontent.com/Arc0re/Iceberg-iTerm2/master/iceberg.itermcolors
```
設定(iTerm >> Preferences >> Profiles >> Colors tab >> Color Presets.. )からIcebergをインポート

<img width="600" alt="スクリーンショット 2022-08-25 17 53 02" src="https://user-images.githubusercontent.com/64122953/186620783-ba9683b8-cb9c-4379-b537-24330cc8b8e4.png">


## 04 補完やシンタックスハイライトを有効にするためプラグインをインストールせよ
```
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
git clone https://github.com/zsh-users/zsh-completions ~/.oh-my-zsh/custom/plugins/zsh-completions
git clone https://github.com/zsh-users/zsh-history-substring-search ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-history-substring-search
```

## 05. .zshrcに設定を反映させろ
インストールしたPureとプラグインを反映させるために以下の設定を.zshrcに書き込め！
```
# Pureテーマ
ZSH_THEME="refined"
# プラグインを有効化
plugins=(zsh-autosuggestions zsh-syntax-highlighting zsh-completions history-substring-search)
autoload -U compinit && compinit
```
ターミナルを再起動すれば反映される！

以上だ!!
