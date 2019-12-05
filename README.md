# wp_template
初めから用意されるもの
- wordpress
- mysql
- phpunit
- wp-cli

## 使い方
（docker composeはインストール済みとして進めて参ります。）

1.作業を進めやすいディレクトリを用意して、zipでダウンロードするか、クローンしてください。

2.Dockerfileと同じ階層で以下のコマンドを入力。
`docker-compose up -d`

3.以下のURLでwordpressの動作確認
http://localhost:9000

## 自作プラグイン開発手順
自作プラグインを開発するのにちょうど良いので利用してみてください。

1.プラグイン作成
`docker-compose exec wordpress wp scaffold plugin my-plugin --allow-root`

2.開発用環境のセットアップ
`docker-compose exec wordpress bash -c "/var/www/html/wp-content/plugins/my-plugin/bin/install-wp-tests.sh wordpress_test root somewordpress db latest"`

3.phpunitの動作確認
`docker-compose exec wordpress bash -c "cd /var/www/html/wp-content/plugins/my-plugin; phpunit ./tests/test-sample"`
