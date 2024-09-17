飲み屋ViewIndexの計算手順
1. 対象エリア内に円を敷き詰める。
2.生成した各円の範囲で店舗を検索する
3.各店舗の混雑率を取得する
4.混雑率をfoliumにヒートマップとしてプロットする

# 1. 対象エリア内に円を敷き詰める。
### generate-circle.ipynbを実行する
- ./data/tokuyama-grid.csvに保存

# 2. 生成した各円の範囲で店舗を検索する
### search-locations.ipynbを実行する
- ./data/tokuyama-grid.csvから円を読み込み
- それぞれの円の範囲で店舗を検索
- ./data/results.geojsonに店舗情報を保存

# 3. 各店舗の混雑率を取得する
### get_popular_time.ipynbを実行する
- ./data/results.geojsonから店舗情報を読み込み
- 各店舗のplace_idを用いて店舗のrating(レビュー（星１から星５）) , rating_n （レビューの総数）, populartimes（月曜から日曜までの１時間ごとの混雑率）を取得
- 4時間ごとに混雑率を平均化する
- ./data/populartimes.geojsonに保存する
