# API一覧

## 共通仕様

Headerに指定されたAPI_KEYをX-Safie-API-KEYとして設定してください。


# GET /v1/devices

デバイス一覧の取得

## パラメータ

| Name   | Description                   |
|--------|-------------------------------|
| offset | オフセット（任意　デフォルト: 0）  |

## レスポンス
```
{
    "record" : [
                   {
                   "model_id" : モデルID,
                   "serial" : シリアル番号,
                   "device_id" : デバイスID,
                   "user_id" : ユーザーID,
                   "mail_address" : ユーザーメールアドレス,
                   "fw_version" : ファームウェアバージョン
                   },
                   ..........
               ],
    "offset" : offset,
    "count"  : count
}
```



# GET /v1/setting

デバイスのセッティング情報の取得

## パラメータ

| Name      | Description                   |
|-----------|-------------------------------|
| device_id | 取得対象デバイスID              |

## レスポンス
```
{
    "setting" : {
                "name" : デバイス名,
                "recording" : 録画設定（True/False）,
                "motion"    : モーション検知（True/False）,
                "sound"     : サウンド検知（True/False）,
                "face"      : 顔認証（True/False）,
                "attribute" : 属性（True/False）,
                "mail"      : メール送信設定（True/False）,
                "push"      : プッシュ通知設定（True/False）
                },
     "status" : {
                "connection" : サーバー接続状態（"disconnect", "idle", "connect"）,
                "streaming" : 動画配信状態（"off"/"audio"/"video"/"video_audio"）,
                }
}
```

# GET /v1/shares

デバイスの共有情報の取得

## パラメータ

| Name      | Description                   |
|-----------|-------------------------------|
| device_id | DeviceID                      |
| offset    | オフセット                      |

## レスポンス
```
{
    "record" : [
                {
                "user_id" : ユーザーID,
                "mail_address" : メールアドレス,
                "permissions" : [
                                 "live",
                                 "vod",
                                 "movieclip",
                                 ......
                                ]
               ]
    "offset" : オフセット,
    "count"  : 総エントリ数
}
```

# GET /v1/subscriptions

デバイスの加入プラン情報の取得

## パラメータ

| Name      | Description                   |
|-----------|-------------------------------|
| device_id | DeviceID                      |
| offset    | オフセット                      |

## レスポンス
```
{
    "record" : [
                {
                "plan_id" : 加入プランID,
                "description" : 加入プラン名,
                "created_on" : プラン加入日,
                "expired_on" : プラン終了予定日
               ]
    "offset" : オフセット,
    "count"  : 総エントリ数
}
```


# GET /v1/data_records

デバイスの録画状況の取得

## パラメータ

| Name      | Description                   |
|-----------|-------------------------------|
| device_id | DeviceID                      |
| date      | 取得日                         |

## レスポンス
```
{
    "record" : [
                {
                "timestamp" : 録画データチャンク開始時間,
                "duration"  : 録画データ長さ（秒）
               ]
}
```
