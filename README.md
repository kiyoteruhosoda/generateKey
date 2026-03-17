# generateKey

## Azure Pipelines での Variable Group エラー対策

`azure-pipelines.yml` では、Variable Group 名をパラメータ化しています。

- `androidSecretsGroup`
- `iosSecretsGroup`

どちらもデフォルトは空文字です。空文字のときは `group:` を読み込まないため、
`Variable group ... could not be found` による **YAML の定義エラーを回避**できます。

### 実運用での設定例

1. Azure DevOps Library に Variable Group を作成
2. Pipeline から該当 Variable Group を authorize
3. 実行時パラメータで以下を指定
   - `androidSecretsGroup: flutterbase-android-secrets`
   - `iosSecretsGroup: flutterbase-ios-secrets`

> 既存の Variable Group 名を変更した場合は、パラメータ値だけ差し替えれば対応できます。
