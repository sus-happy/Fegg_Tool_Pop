# Fegg Tool Pop

POPサーバに接続し、メールの受信・削除を行う[Fegg](https://github.com/genies-inc/Fegg)向けの拡張ライブラリです。

## 使い方例

    // クラス準備
    $pop = $this->getClass( 'Tool/Pop' );

    // 接続情報
    $pop->host = 'mail.example.com';
    $pop->user = 'mail_user';
    $pop->pass = 'mail_pass';
    $pop->host = '110';

    // 接続
    $pop->connect();

    // メール取得
    while( $pop->fetch() ) {
        // ヘッダー
        $header = $pop->getHeader();
        // メール本文
        $body = $pop->getBody();
        // 添付ファイル
        $attches = $pop->getAttachFile();

        // メール削除
        $pop->delete();
    }
    
    // 切断
    $pop->close();

## 注意

* `getAttachFile`で取得したファイルは、セッション終了までに別ディレクトリに移動させないと自動的に削除します。
