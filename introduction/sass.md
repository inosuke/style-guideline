## Sass導入

#### Sassのインストール
* Node.jsのインストール  
Sassは、LibSassを使用します。LibSassをコンパイルするのにNode.js(node-sassライブラリ)を使用します。  
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
    

* node-sassのインストール  
次にパッケージ管理ツール npm のコマンドを使って、node-sassライブラリのインストールを行います。   

```
    npm install node-sass -g
```

　　上記のコマンドを実行します。  
　　-gオプションをつけてインストールすると、グローバルインストールとなり  
　　パスの設定まで行ってくれます。

```
    C:\Users\xxxx\AppData\Roaming\npm\node-sass -> C:\Users\xxxx\AppData\Roaming\npm\node_modules\node-sass\bin\node-sass

    > node-sass@4.5.3 install C:\Users\xxxx\AppData\Roaming\npm\node_modules\node-sass
    > node scripts/install.js

    Downloading binary from https://github.com/sass/node-sass/releases/download/v4.5.3/win32-x64-46_binding.node
    Download complete
    Binary saved to C:\Users\xxxx\AppData\Roaming\npm\node_modules\node-sass\vendor\win32-x64-46\binding.node
    Caching binary to C:\Users\xxxx\AppData\Roaming\npm-cache\node-sass\4.5.3\win32-x64-46_binding.node

    > node-sass@4.5.3 postinstall C:\Users\xxxx\AppData\Roaming\npm\node_modules\node-sass
    > node scripts/build.js

    Binary found at C:\Users\xxxx\AppData\Roaming\npm\node_modules\node-sass\vendor\win32-x64-46\binding.node
    Testing binary
    Binary is fine
    node-sass@4.5.3 C:\Users\xxxx\AppData\Roaming\npm\node_modules\node-sass
    ├── get-stdin@4.0.1
    ├── lodash.assign@4.2.0
    ├── lodash.clonedeep@4.5.0
    ├── lodash.mergewith@4.6.0
    ├── async-foreach@0.1.3
    ├── in-publish@2.0.0
    ├── chalk@1.1.3 (escape-string-regexp@1.0.5, ansi-styles@2.2.1, supports-color@2.0.0, has-ansi@2.0.0, strip-ansi@3.0.1)
    ├── mkdirp@0.5.1 (minimist@0.0.8)
    ├── nan@2.7.0
    ├── cross-spawn@3.0.1 (lru-cache@4.1.1, which@1.3.0)
    ├── glob@7.1.2 (path-is-absolute@1.0.1, inherits@2.0.3, fs.realpath@1.0.0, once@1.4.0, inflight@1.0.6, minimatch@3.0.4)
    ├── stdout-stream@1.4.0 (readable-stream@2.3.3)
    ├── npmlog@4.1.2 (set-blocking@2.0.0, console-control-strings@1.1.0, are-we-there-yet@1.1.4, gauge@2.7.4)
    ├── meow@3.7.0 (trim-newlines@1.0.0, decamelize@1.2.0, map-obj@1.0.1, object-assign@4.1.1, camelcase-keys@2.1.0, minimist@1.2.0, loud-rejection@1.6.0, normalize-package-data@2.4.0, redent@1.0.0, read-pkg-up@1.0.1)
    ├── request@2.83.0 (aws-sign2@0.7.0, tunnel-agent@0.6.0, forever-agent@0.6.1, oauth-sign@0.8.2, is-typedarray@1.0.0, caseless@0.12.0, safe-buffer@5.1.1, stringstream@0.0.5, aws4@1.6.0, isstream@0.1.2, json-stringify-safe@5.0.1, extend@3.0.1, performance-now@2.1.0, uuid@3.1.0, qs@6.5.1, combined-stream@1.0.5, mime-types@2.1.17, tough-cookie@2.3.3, form-data@2.3.1, hawk@6.0.2, http-signature@1.2.0, har-validator@5.0.3)
    ├── node-gyp@3.6.2 (graceful-fs@4.1.11, rimraf@2.6.2, semver@5.3.0, which@1.3.0, osenv@0.1.4, minimatch@3.0.4, fstream@1.0.11, tar@2.2.1, nopt@3.0.6)
    ├── sass-graph@2.2.4 (scss-tokenizer@0.2.3, yargs@7.1.0, lodash@4.17.4)
    └── gaze@1.1.2 (globule@1.2.0)
```

　　インストールエラーが出る場合  
　　プロキシサーバを利用されている方は、上記コマンドを打つ前に以下のコマンドを実行してみてください。  
　　(※以下はWindowsの例、アドレスとポートと番号の部分はご自身の環境に置き換えてください)。  

```
    set http_proxy=http://プロキシサーバのアドレス:ポート番号
```

　　node-sassがインストールされているか確認します。
  
```
    node-sass -v
```

　　コマンドプロンプトを開き上記のコマンドを実行します。
  
```
    node-sass       4.5.3   (Wrapper)       [JavaScript]
    libsass         3.5.0.beta.2    (Sass Compiler) [C/C++]
```

　　バージョン情報が表示されれば、node-sassのインストールは正しく完了しています。
  
#### Sassのコンパイル
* 拡張子scssファイルを作成する  
Sassのファイルを作成します。  
拡張子は**scss**であることに注意してください。

　test.scss
```sass
    $black: #000;

    #main {
        width: 600px;
        p {
            margin: 0 0 1em;
            border: 2px solid $black;
        }
    }
```
　　このファイルを任意のフォルダに保存します。
  
* sassファイルのコンパイル

```
    node-sass test.scss test.css
```

　　コマンドプロンプトを開き、test.scssを保存したディレクトリに移動します。  
　　移動後、上記のコマンドを実行します。  
   
　　すると同ディレクトリにtest.cssというコンパイルされたCSSファイルが作成されます。
  
　test.css
```css
    #main {
        width: 600px; }
        #main p {
            margin: 0 0 1em;
            border: 2px solid #000; }
```

---
#### Sassの自動コンパイル設定
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
    mkdir sass css
```

　　コマンドプロンプトを開き設定したいプロジェクトのディレクトリに移動します。  
　　上記のコマンドを実行します。  
　　プロジェクトフォルダにsass、cssフォルダを作成します。
  
```
    npm install --save-dev gulp
```

　　上記のコマンドを実行します。  
　　gulpをプロジェクトにインストールします。
  
```
    npm install gulp-sass
```

　　上記のコマンドを実行します。  
　　gulpのsassプラグインをインストールします。  
  
  
　　gulpfile.jsファイルを作成します。  

　gulpfile.js
```js
    var gulp = require('gulp');
    var sass = require('gulp-sass');

    //sass
    gulp.task('sass', function() {
        gulp.src('sass/*')
            .pipe(sass({outputStyle: 'expanded'}))
            .pipe(gulp.dest('css/'));
    });

    //watch
    gulp.task('sass:watch', function() {
        gulp.watch('sass/*.scss', ['sass']);
    });

    //default
    gulp.task('default', ['sass']);
```  
  
  
　　テスト用にsassファイルを作成します。  
　　「sass」フォルダ内に作成してください。
  
　test.scss
```sass
    $black: #000;

    #main {
        width: 600px;
        p {
            margin: 0 0 1em;
            border: 2px solid $black;
        }
    }
```

```
    gulp sass
```

　　上記のコマンドを実行します。  
　　gulpが起動し、sassフォルダ内の全てのscssファイルのコンパイルが実行されます。  
　　cssフォルダにtest.cssが作成されていれば成功です。  
　　※コンパイルのみを実行したい場合に、上記のコマンドを使用してしてください。
   
```
    gulp watch
```

　　上記のコマンドを実行します。  
　　scssファイルの変更で自動コンパイルを行うようになります。