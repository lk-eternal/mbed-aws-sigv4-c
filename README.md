# mbed-aws-sigv4-c

##機能：
署名バージョン4を使用してAWSリクエストに署名する(S3ダウンロードとアップロードに必要)
署名バージョン4参考：https://docs.aws.amazon.com/ja_jp/general/latest/gr/sigv4_signing.html

##ベースソースコード：
aws-sigv4-c:
https://github.com/sidbai/aws-sigv4-c#8fc8b7cb9775667e6ac955d37f941cf3e7fe88fb

##変更内容：
- opensslからmbedtlsに変更
- hmac-sha256結果コピーのバグ修正(get_signing_key関数：aws_sigv4_sprintf→memcpy)
- payloadがx-amz-content-sha256に変更し、sha256に計算せず単純にcanonical_requestに追加(単純の文字の場合("UNSIGNED-PAYLOAD")があるから)
- 署名にアップロードに必要の署名HTTPヘッダーを追加(x-amz-content-sha256、x_amz_decoded_content_length)

##差分ファイル：
- \aws_sigv4-c\aws_sigv4.c.html
- \aws_sigv4-c\aws_sigv4.h.html