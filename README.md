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

管理画面からHTMLを触らずにサイトの内容を操作可能

<img src="http://hareumi.com/githubWP/kanrigamen.jpg" width="500px">

<img src="http://hareumi.com/githubWP/kanrigamen2.jpg" width="500px">

<img src="http://hareumi.com/githubWP/kanrigamen3.jpg" width="500px">

<br>
<br>
<br>
<br>

## 2、local by flywheel を使用して環境構築


### インストール手順
<img src="https://github.com/55Kaerukun/WP/blob/master/images/wp1.png" width="500px">
<br>
サイト名を入力します。(今回は仮でauarium)
<br>
<img src="https://github.com/55Kaerukun/WP/blob/master/images/wp2.png" width="500px">
<br>
ユーザー名、パスワードを入力します。
<br>
<img src="https://github.com/55Kaerukun/WP/blob/master/images/wp3.png" width="500px">
<br>
インストール完了
<br>
<img src="https://github.com/55Kaerukun/WP/blob/master/images/wp5.png" width="500px">
<br>
管理画面の言語を日本語に設定
<img src="https://github.com/55Kaerukun/WP/blob/master/images/wp6.png" width="500px">
<br>
<br>

# テーマの適用
今回はzip形式にして管理画面からアップロードします。（アップロード後に有効化をクリック）
<img src="https://github.com/55Kaerukun/WP/blob/master/images/wp7.png" width="500px">

    
## 3、管理画面からニュースを投稿してみる

### 左メニューの「投稿」 → 「新規追加」

<img src="https://github.com/55Kaerukun/WP/blob/master/images/wpsingle.png" width="500px">


## 4、固定ページを作成してみる
左メニューの「固定ページ」 → 「新規追加」

<img src="https://github.com/55Kaerukun/WP/blob/master/images/wppage.png" width="800px">



### 表示する仕組みについて（WordPressループについて）

    <?php if (have_posts()) : ?>
	<?php while (have_posts()) : the_post(); ?>

        <!-- 投稿日時 -->
        <?php the_time('Y年m月d日') ?>
	
        <!-- 投稿のリンク先 -->
        <a href="<?php the_permalink() ?>">
	
            <!-- 投稿タイトル -->
            <?php the_title(); ?>
	    
        </a>

        <!-- 投稿内容の抜粋 -->
        <?php the_excerpt(); ?>
		
	<?php endwhile; ?>
    <?php else : ?>
	    <p>投稿が見つかりませんでした。</p>
    <?php endif; ?>

    
    
### cssで装飾できるようにカスタマイズ！！！

```

    <!-- メインループ -->
    <ul class="block-three">
    <?php if (have_posts()) : ?>
        <?php while (have_posts()) : the_post(); ?>
        <li>
	    <!-- 投稿のリンク先 -->
	    <a href="<?php the_permalink() ?>">

		<!-- サムネイルの表示 -->
		<?php the_post_thumbnail();?>

		<!-- 投稿日時 -->
		<span class="date">
			<?php the_time('Y年m月d日') ?>
		</span>

		<!-- 投稿タイトル -->
		<h2 class="blog_title">
		    <?php the_title(); ?>
		</h2>
	    </a>
	    <!-- 投稿内容の抜粋 -->
	    <?php the_excerpt(); ?>
        </li>

      <?php endwhile; ?>
      <?php else : ?>
	<p>投稿が見つかりませんでした。</p>
    <?php endif; ?>
    </ul>
<!-- /メインループ -->
     
```



## 5、プラグインについて （Contact Form 7 でお問い合わせフォーム作成）
プラグインとは？ 機能を拡張するためのツール。

<img src="http://hareumi.com/githubWP/ContactForm7.jpg" width="500px">

プラグイン → 新規追加 プラグインを検索 → Contact Form 7 → インストール → いますぐ有効化

<img src="http://hareumi.com/githubWP/cf7.jpg" width="400px">

ショートコードをコピー 

<img src="http://hareumi.com/githubWP/cf7_2.jpg" width="800px">

固定ページを作って貼り付け → 更新

<img src="http://hareumi.com/githubWP/cf7_3.jpg" width="400px">

フォーム完成！

## その他のプラグイン紹介 


・本番環境に引越しの時に便利！
All-in-One WP Migration
https://restinpeace.jp/allinone-wp-migration/

・確認画面のあるお問い合わせ
MW WP Form
https://newstd.net/user_manual/mwwpform

・SEO対策に
All in One SEO Pack
https://bazubu.com/all-in-one-seo-pack-23836.html

・カスタムフィールドを柔軟に使える
Advanced Custom Fields
https://bazubu.com/advanced-custom-fields-36452.html


