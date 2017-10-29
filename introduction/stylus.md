## Stylus導入

#### Stylusのインストール
* Node.jsのインストール  
Stylus（スタイラス） は Node.js のモジュールとして動作します。  
[Node.jsのサイト](https://nodejs.org/ja/)よりNode.jsをダウンロードします。  

　　ダウンロードが完了したら、Node.jsがインストールされているか確認します。
 
```
    node -v  
```

　　コマンドプロンプトを開き上記のコマンドを実行します。  

```
    v6.10.0
```

　　バージョン情報が表示されれば、Node.jsのインストールは正しく完了しています。  
    

* Stylusのインストール  
次にパッケージ管理ツール npm のコマンドを使って、Stylusのモジュールのインストールを行います。   

```
    npm install stylus -g
```

　　上記のコマンドを実行します。  
　　-gオプションをつけてインストールすると、グローバルインストールとなり  
　　パスの設定まで行ってくれます。

```
    C:\Users\xxxx>npm install stylus -g
    C:\Users\xxxx\AppData\Roaming\npm\stylus -> 
    C:\Users\xxxx\AppData\Roaming\npm\node_modules\stylus\bin\stylusstylus@0.54.5   
    C:\Users\xxxx\AppData\Roaming\npm\node_modules\stylus  
    ├── css-parse@1.7.0
    ├── debug@3.1.0 (ms@2.0.0)
    ├── mkdirp@0.5.1 (minimist@0.0.8)
    ├── glob@7.0.6 (path-is-absolute@1.0.1, inherits@2.0.3, fs.realpath@1.0.0, inflight@1.0.6, once@1.4.0, minimatch@3.0.4)
    ├── sax@0.5.8
    └── source-map@0.1.43 (amdefine@1.0.1)
```

　　インストールエラーが出る場合  
　　プロキシサーバを利用されている方は、上記コマンドを打つ前に以下のコマンドを実行してみてください。  
　　(※以下はWindowsの例、アドレスとポートと番号の部分はご自身の環境に置き換えてください)。  

```
    set http_proxy=http://プロキシサーバのアドレス:ポート番号
```

　　Stylusがインストールされているか確認します。
  
```
    stylus -v
```

　　コマンドプロンプトを開き上記のコマンドを実行します。
  
```
    0.54.5
```

　　バージョン情報が表示されれば、Stylusのインストールは正しく完了しています。
  
#### Stylusのコンパイル
* 拡張子stylファイルを作成する  
Stylusのファイルを作成します。  
拡張子は**styl**であることに注意してください。

　test.styl
```stylus
    fonts = helvetica, arial, sans-serif

    body {
        padding: 50px;
        font: 14px/1.4 fonts;
    }
```
　　このファイルを任意のフォルダに保存します。
  
* stylファイルのコンパイル

```
    stylus test.styl
```

　　コマンドプロンプトを開き、test.stylを保存したディレクトリに移動します。  
　　移動後、上記のコマンドを実行します。  
   
　　すると同ディレクトリにtest.cssというコンパイルされたCSSファイルが作成されます。
  
　test.css
```css
    body {
        padding: 50px;
        font: 14px/1.4 helvetica, arial, sans-serif;
    }
```

---
#### Stylusの自動コンパイル設定
* gulpのインストール  
自動コンパイルの設定にgulpを使用します。

```
    npm install gulp -g
```

　　コマンドプロンプトを開き上記のコマンドを実行します。
  
　　gulpがインストールされているか確認します。

```
    gulp -v  
```

　　上記のコマンドを実行します。  

```
    [21:57:50] CLI version 3.9.1
```

　　バージョン情報が表示されれば、gulpのインストールは正しく完了しています。  
  
* 自動コンパイル設定  
gulpを使用した自動コンパイルの設定を行っていきます。

```
    mkdir stylus css
```

　　コマンドプロンプトを開き設定したいプロジェクトのディレクトリに移動します。  
　　上記のコマンドを実行します。  
　　プロジェクトフォルダにstylus、cssフォルダを作成します。
  
```
    npm install --save-dev gulp
```

　　上記のコマンドを実行します。  
　　gulpをプロジェクトにインストールします。
  
```
    npm install gulp-stylus
```

　　上記のコマンドを実行します。  
　　gulpのstylusプラグインをインストールします。  
  
  
　　gulpfile.jsファイルを作成します。  

　gulpfile.js
```js
    var gulp = require('gulp');
    var stylus = require('gulp-stylus');

    //stylus
    gulp.task('stylus', function() {
        gulp.src('stylus/*')
            .pipe(stylus())
            .pipe(gulp.dest('css/'));
    });

    //watch
    gulp.task('watch', function() {
        gulp.watch('stylus/*.styl', ['stylus']);
    });

    //default
    gulp.task('default', ['stylus']);
```  
  
  
　　テスト用にStylusファイルを作成します。  
　　「stylus」フォルダ内に作成してください。
  
　test.styl
```stylus
    fonts = helvetica, arial, sans-serif

    body {
        padding: 50px;
        font: 14px/1.4 fonts;
    }
```

```
    gulp stylus
```

　　上記のコマンドを実行します。  
　　gulpが起動し、stylusフォルダ内の全てのstylファイルのコンパイルが実行されます。  
　　cssフォルダにtest.cssが作成されていれば成功です。  
　　※コンパイルのみを実行したい場合に、上記のコマンドを使用してしてください。
   
```
    gulp watch
```

　　上記のコマンドを実行します。  
　　stylファイルの変更で自動コンパイルを行うようになります。