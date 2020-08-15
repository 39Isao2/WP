# WordPress入門
複数のPHPファイルでできたシステムです。

<img src="http://hareumi.com/githubWP/wpp.png" width="500px">

## １、WordPressについて 長所
当時、大学生のマット・マレンウェッグさんがブログを書くために2003年に開発。 
世界で流行。
アーティストのポートフォリオや、普通の企業サイト作成などにも使われるようになった。

    ・お知らせ、ブログ、新規商品、などの追加がHTMLを書かなくても追加&管理できる
    ・HTMLを知らなくても多少はページの内容変更可能
    ・「プラグイン」という便利機能が色々！ さくっとお問い合わせフォーム等が作成可能など (Contact Form 7など)

管理画面から操作する

<img src="http://hareumi.com/githubWP/kanrigamen.jpg" width="500px">

<img src="http://hareumi.com/githubWP/kanrigamen2.jpg" width="500px">

<img src="http://hareumi.com/githubWP/kanrigamen3.jpg" width="500px">



## 2-a、さくらサーバーにWordPressをクイックインストール
WordPressを使用するには、サーバーにインストール(ファイルのアップとデータベースの作成)とテーマの適用が必要です。

<img src="http://hareumi.com/githubWP/wp_zu.png" width="500px">

(テーマとは？)
HTML、CSS、JSで作ったサイト(静的サイトと呼びます)を.phpにしたファイルのかたまりです。

コントロールパネルからログイン
https://secure.sakura.ad.jp/rscontrol/




<img src="http://hareumi.com/githubWP/db.png" width="800px">




<img src="http://hareumi.com/githubWP/wp.png" width="800px">

サイトのタイトル、管理画面のログインパスワードなどを入力します。

<img src="http://hareumi.com/githubWP/wp_install1.jpg" width="800px">


### WordPressにログイン

http://~~~~~~~~~/wp-admin
ユーザー名またはメールアドレス
パスワード
を入力して、ログインします。


<img src="http://hareumi.com/githubWP/wp_install3.png" width="200px">

## 2-b、local by flywheel を使用して環境構築


## 3、テーマの適用

FTPソフトでテーマファイルをアップします。

超初心者向け！FileZilla（ファイルジラ）の使い方
https://techacademy.jp/magazine/2447
    
■ホスト   

FTPサーバ名     ： -----------.sakura.ne.jp

■ユーザー名

FTPアカウント   ： ------------

■パスワード

サーバパスワード： ------------

<img src="http://hareumi.com/githubWP/folder.png">

    
## 3、管理画面からニュースを投稿してみる
-----------.sakura.ne.jp/wp/wp-admin

管理画面からニュースを投稿する方法 single.php

### 左メニューの「投稿」 → 「新規追加」

<img src="http://hareumi.com/githubWP/kanrigamen3.jpg" width="800px">


表示する仕組みについて（WordPressループ）

    <?php if (have_posts()) : ?>
	<?php while (have_posts()) : the_post(); ?>

        <!-- 投稿日時 -->
        <?php the_time('Y年m月d日') ?>
	
        <!-- 投稿のリンク先 -->
        <a href="<?php the_permalink() ?>">
	
            <!-- 投稿タイトル -->
            <?php the_title(); ?>
	    
        </a>

        <!-- 投稿内容 -->
        <?php the_content(); ?>
		
	<?php endwhile; ?>
    <?php else : ?>
	    <p>投稿が見つかりませんでした。</p>
    <?php endif; ?>

    
    
今回のテーマのtable部分に使える用にカスタマイズ！！！

    <table class="text-center">
    <thead>
    <tr>
        <td>イベント名</td>
        <td>空席状況</td>
        <th>エリア</th>
        <th>日程 場所</th>
    </tr>
    </thead>
    <tbody>
    <?php if (have_posts()) : ?>
    <?php while (have_posts()) : the_post(); ?>
    <tr>
        <td><?php the_title(); ?></td>
        <td><span class="manseki"><?php the_tags(''); ?></span></td>
        <td><?php the_category(); ?></td>
        <td><?php the_content(); ?></td>
    </tr>
    <?php endwhile; ?>
    <?php endif; ?>
    </tbody>
    </table>
## 4、固定ページの作成。ページの内容の変更してみる
固定ページの作成 page.php

### 左メニューの「固定ページ」 → 「新規追加」

<img src="http://hareumi.com/githubWP/page-php.jpg" width="800px">

<img src="http://hareumi.com/githubWP/url.jpg" width="300px">

ヘッダーのURLを書き換える。

<img src="http://hareumi.com/githubWP/header.jpg" width="800px">

    <a href="<?php echo site_url();?>/about/">>シュガーリングラボについて</a>

## 5、プラグインについて （Contact Form 7 でお問い合わせフォーム作成）
プラグインとは？ 機能を拡張するためのツール！

<img src="http://hareumi.com/githubWP/ContactForm7.jpg" width="500px">

プラグイン → 新規追加 プラグインを検索 → Contact Form 7 → インストール → いますぐ有効化

<img src="http://hareumi.com/githubWP/cf7.jpg" width="400px">

ショートコードをコピー 

<img src="http://hareumi.com/githubWP/cf7_2.jpg" width="800px">

固定ページを作って貼り付け → 更新

<img src="http://hareumi.com/githubWP/cf7_3.jpg" width="400px">

フォーム完成！


contact form 7 効果的な使い方
https://bazubu.com/contact-form-7-23869.html


WP-PageNaviの使い方
https://techacademy.jp/magazine/7391



バックアップ
All-in-One WP Migration
https://restinpeace.jp/allinone-wp-migration/

local-by-flywheel
https://kumaweb-d.com/web/local-by-flywheel-howto/

