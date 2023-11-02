# gradle-hello

+ Gradleの使い方メモ。

## Gradle とは

+ プロジェクトのテンプレート生成、ビルド、実行、配布ツール。
+ スクリプトは Groovy または Kotlin で記述。

## ローカルディレクトリの構築メモ

### Gradle のダウンロードと実行

+ JDKにpathを通しJAVA_HOMEを設定する。
+ https://gradle.org/install/#manually の Binary-only から zip をダウンロードして展開。

実行する。

```
gradle-8.4-bin\gradle-8.4\bin\gradle -v
```

Javaアプリケーションのプロジェクトテンプレートを生成する。

```
gradle-8.4-bin\gradle-8.4\bin\gradle init

Starting a Gradle Daemon, 1 incompatible and 1 stopped Daemons could not be reused, use --status for details

Select type of project to generate:
  1: basic
  2: application
  3: library
  4: Gradle plugin
Enter selection (default: basic) [1..4] 2

Select implementation language:
  1: C++
  2: Groovy
  3: Java
  4: Kotlin
  5: Scala
  6: Swift
Enter selection (default: Java) [1..6] 3
```

あとはdefault設定で進めると、次のプロジェクトファイルが生成される。

```
.gradle/
gradle/
app/
    src/
    build.gradle.kts
.gitattributes
.gitignore
gradlew
gradlew.bat
settings.gradle.kts
```

このとき必要なプログラムが %USERPROFILE%\.gradle\caches ディレクトリにダウンロード＆キャッシュされる。

次からは生成された gradlew を使う。

ダウンロードしたzipと、展開した gradle-8.4-bin ディレクトリは削除してかまわない。

```
gradlew -v

gradlew run
```

参考

+ https://qiita.com/hatimiti/items/a127311d739c9d3e0045 Gradle (build.gradle) 読み書き入門

+ https://blog.p1ass.com/posts/gradle/ Gradle にしっかり入門する

### github アップロード

+ リモートリポジトリ作成
https://github.com/

+ ローカルリポジトリ初期化
```
git init
```

+ プロフィールを使い分ける
```
git config --local user.name "****************"
git config --local user.email "****************"
git config --local core.autocrlf true
git config --list --local
```

+ アップロード（※の前に .gitignoreがあることを確認）
```
git add .
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/morimoto-hiroshi/gradle-hello.git
git push -u origin main
```
