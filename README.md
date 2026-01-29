# サーフトリップ記事 作成・デプロイ運用フロー

本リポジトリは、サーフトリップ記事を  
**メモ → 下書き → 提案 → 最終版 → WordPress公開**  
という段階的なプロセスで管理することを目的としています。

---

## 全体の流れ

1. ローカルに旅行ディレクトリを作成し、画像とメタ情報を整理
2. Google Drive に画像・メタファイルをアップロード
3. Apps Script で draft（下書き）HTML を生成
4. 生成AI（ChatGPT / Gemini）で proposed（原案）HTML を作成
5. 手動で校正し finalized（成案）HTML を作成
6. デプロイスクリプトで画像と HTML を WordPress に反映
7. WordPress に公開された内容はすべて Git に保存

---

## 1. ローカルでのディレクトリ構成
作業ルート：C:\Users\atsuk\Documents\Blog\drive\surfing_marine

### 奄美トリップの例

```text
./
./202601_amami                          # YYYYMM_{場所}
./202601_amami/0105                     # MMDD
./202601_amami/0105/0105_files.txt      # 表示させる画像ファイル名リスト
./202601_amami/0105/0105_summary.txt    # その日のサマリ文章
./202601_amami/0105/IMG_0307.JPEG       # 画像ファイル
./202601_amami/0105/IMG_0307.txt        # 画像の説明（rough コメント）
./202601_amami/0105/IMG_0310.JPEG
./202601_amami/0106
./202601_amami/0106/0106.txt
./202601_amami/0106/0106_files.txt
./202601_amami/0106/0106_summary.txt
./202601_amami/0106/IMG_0349.JPEG
```

画像ごとのコメントや、その日のメモは meta ファイルに rough（ラフ）に記述

この段階では文章の完成度は問わない

## 2. Google Drive へのアップロード
画像ファイル

メタファイル（summary / files / 画像説明）

を Google Drive にアップロードする。

Google Drive フォルダ:https://drive.google.com/drive/folders/129Us5IQ8k99n2ScO-u7SksI6N3hhx20G

## 3. Apps Script による draft HTML 生成

Google Drive 上の画像・メタファイルを元に

draft（下書き）HTML を自動生成する。

Apps Script:https://script.google.com/home/projects/1IAJDpTKpyb_RUKdYCiTZ_kzzR0DQ6A6mxRa3CY5sxoyRzjgxmtOW3VRm/edit

すべての元データ（画像・コメント）は Google Drive に残る

ここで生成される HTML は「構造を確認するための原文」

## 4. 生成AIによる proposed HTML 作成

draft HTML を ChatGPT または Gemini に渡す

記事構成・流れ・表現を対話しながら調整

proposed（原案）HTML を生成する

※ この段階では「完成させる」よりも全体構成を固めることを重視

## 5. finalized HTML の作成

proposed HTML を自分で最終校正

表現・構成・不要要素を調整

finalized（成案）HTML として保存

この時点で「公開可能な品質」とする。

## 6. デプロイ方針（要検討）

内容がリリース可能になったら：

デプロイスクリプトで画像を Google Drive から Git 管理へ移行

デプロイ時に画像を Google Drive から WordPress サーバへアップロード

HTML を WordPress に反映

※ 実装方法は今後検討

## 7. Git 管理の方針

WordPress に公開されているものは 必ず Git に残す

公開後の記事・画像は履歴管理・再利用・再デプロイ可能な状態にする

# oceanmarinejp アカウントの wordpress

WebUI:https://oceanmarinejp.wordpress.com/

管理画面:https://oceanmarinejp.wordpress.com/wp-admin/index.php
