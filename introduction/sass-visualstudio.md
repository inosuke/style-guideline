## Sass導入-VisualStudio編

__Visual Studio 2015よりSassに対応しています。__    
Visual Studioでは、Sassのシンタックスハイライトやコード補完がサポートされています。  
Sassのコンパイルは非対応のため、拡張機能を使用する必要があります。  

### コンパイル環境の設定  
#### Web Compilerのインストール  
「ツール」->「拡張機能と更新プログラム」からWeb Compilerをインストールします。  
インストール後、VisualStudioを再起動し変更を反映させます。  

### Web Compilerの環境設定  
任意のフォルダにscssスタイルシートを追加する。  
追加したscssファイルを右クリックし、Web Compiler->Compile fileを選択する。  
コンパイルが実行され、compilerconfig.json compilerconfig.json.defaults の2ファイルが
自動で追加されます。  

#### compilerconfig.json  
このファイルには、コンパイル対象のファイルが登録されています。  
登録されているファイルは、ファイルを変更して保存するたびに自動コンパイルされます。  
コンパイル対象を事前に登録することで、最初から自動コンパイルすることができます。  

``` json
[
	{
		"outputFile": "css/style.css",
		"inputFile": "sass/style.scss"
	}
]
```

#### compilerconfig.json.defaults  
各種設定が記載されています。  
sass以外の設定も記載されていますが、必要に応じて設定を変更してください。   

``` json
"sass": {
  "includePath": "",
  "indentType": "space",
  "indentWidth": 2,
  "outputStyle": "nested",
  "Precision": 5,
  "relativeUrls": true,
  "sourceMapRoot": "",
  "sourceMap": false
}
```

* __outputStyle__  
CSS出力時の形式を選択できます。  
expandedが最も可読性が高い状態で出力されます。  

| 設定名           | 設定内容       |
| --------------- |---------------|
|nested     |Sassのネストを保ったままインデントします。| 
|compact    |セレクタとプロパティが1行になります。|
|compressed |CSSを1行に圧縮します。コメントなど削除されます。|
|expanded   |セレクタとプロパティを1行ずつ改行します。|  
<br>

---
Web Compilerについて詳しく知りたい場合は、githubを参照してください。
https://github.com/madskristensen/WebCompiler