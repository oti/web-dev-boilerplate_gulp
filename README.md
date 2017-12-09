# website-dev-startkit

ウェブサイト作るときによくある自動化タスクをプリセットしたスタートキット。

これですべてができるというものではなくて、これをベースにタスクを足したり引いたりして使う用のもの。

これをクローンして `.git` 以外をプロジェクトルートにコピーし、新たに `git init` して使う。

## HTML

Pugを使用。

- [gulp-pug](https://www.npmjs.com/package/gulp-pug)

```
gulp html
```

## CSS

プリプロセッサーはSassを使用。Autoprefixerで下位ブラウザ対応。gulp-merge-media-queriesでMedia Queriesの記述をファイルの後ろにまとめている。最後にgulp-cssoで圧縮。

- [gulp-sass](https://www.npmjs.com/package/gulp-sass)
- [gulp-autprefixer](https://www.npmjs.com/package/gulp-autoprefixer)
- [gulp-merge-media-queries](https://www.npmjs.com/package/gulp-merge-media-queries)
- [gulp-csso](https://www.npmjs.com/package/gulp-csso)

```
gulp style
```

## JS（vendor）

jQueryやLodash.jsなどのライブラリは `src/js/vendor/` に格納し、`dist/js/vendor.js` に結合圧縮される想定。

- [gulp-concat](https://www.npmjs.com/package/gulp-concat)
- [gulp-uglify](https://www.npmjs.com/package/gulp-uglify)
- [gulp-jshint](https://www.npmjs.com/package/gulp-jshint)
- [jshint-stylish](https://github.com/sindresorhus/jshint-stylish)

```
gulp jsVendors // -> build vendor.js
```

## JS（BabelJS）

ES6構文で書くJSはbabelifyでbundleする。監視はwatchify。このタスクのみnpm run-scriptで行う。

- babel
- babel-core
- babel-preset-env
- babelify
- watchify
- exorcist

```
npm run babelify // -> build script.js
```

## img

`src/img/` 配下をすべて個別に圧縮して `htdocs/img/` に出力する。

- [gulp-imagemin](https://www.npmjs.com/package/gulp-imagemin)

```
gulp image
```

## ローカルサーバー

browser-sync使用。でローカルサーバー起動とライブリロード

- [brower-sync](https://www.npmjs.com/package/browser-sync)

```
gulp server
```

## 監視

gulp-watch使用。

- [gulp-watch](https://www.npmjs.com/package/gulp-watch)

```
gulp watch
```

## ビルド

pug,scss,js,image

```
gulp build
```

## npm run script

```
npm start
```

呼び出しているのは `gulp default` タスク。
