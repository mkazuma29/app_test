# API一覧

挙動がおかしい場合はご指摘ください。

## 共通仕様

指定されたAPI_KEYをリクエストヘッダにX-Safie-API-KEYとして設定してください。


# GET /v1/devices

デバイス一覧の取得

## レスポンス
```
{
    "record" : [
                   {
                   "device_id" : デバイスID,
                   },
                   ..........
               ],
    "count"  : count // 総デバイス数
}
```



# GET /v1/image/<device_id>

デバイスのサムネイル取得

## レスポンス
```
JPEG形式のサムネイルデータ
```

# GET /v1/stream/<device_id>/stream_.m3u8

デバイスの動画再生

## レスポンス
```
HLS形式でのストリーム開始
```

