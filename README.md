# README
表示・登録・編集・削除機能を備えた
Twitterライクなアプリケーション


# 環境
言語: ruby 2.5.1p57 
Webフレームワーク: Ruby on Rails 5.2.3
DBMS: mysql  Ver 14.14 Distrib 5.6.43
コード管理: Git
コード共有: GitHub
CSS フレームワーク
Twitter Bootstrap4

# 仕様(機能)

１ ユーザーの新規登録機能
詳細:
　　●ユーザーはメールアドレス、パスワード、username(アカウント名)を登録できる（必須項目）

２ ユーザーのログイン・ログアウト機能
詳細:
　　●メールアドレスとパスワードでログイン
●ログイン・登録周りはSorceryというGemを使用してください

3 短文投稿機能
詳細:
　●140字以内の短文を投稿できる
　●自分の投稿を削除できる
●投稿時、削除、編集時にフラッシュメッセージを表示させる
　●ユーザーごとのつぶやき一覧ページ（1ページ25件)
●登録ユーザーのみ投稿削除が可能で他人の投稿を編集、削除は禁止にする
● 投稿は新しい投稿順で並べる

* データベース概要
## usersテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false,index: true|
|email|string|null: false, unique: true|
|password|string|null: false|
### Association
- has_many :tweets
- has_many :comments

## tweetsテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|references|null: false, foreign_key: true|
|text|string|null: false|
|image|string||
### Association
- belongs_to :user
- has_many :comments

## commentsテーブル
|Column|Type|Options|
|------|----|-------|
|text|string||
|user_id|references|null: false, foreign_key: true|
|tweet_id|references|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :tweet
