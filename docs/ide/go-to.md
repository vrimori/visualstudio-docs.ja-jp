---
title: "移動 | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 509b2107-23d1-4fb3-987f-ab99ef45b72e
author: BrianPeek
ms.author: brpeek
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 3b812629bf0f655f39c35a56eb1b3ca9113303a6
ms.openlocfilehash: 8bf6d49b21d128d15f5312fb230d4a8e7a8195af
ms.contentlocale: ja-jp
ms.lasthandoff: 03/01/2017

---

# <a name="go-to"></a>[移動]
キーボードとマウスを使って、Visual Studio IDE 内のコード間を簡単に移動する方法が多数あります。

<!-- VERSIONLESS -->
## <a name="go-to-all"></a>すべてにジャンプ
この機能は Visual Studio 2017 以降に備わっています。  コード内を移動して、探している特定の部分を検索できます。  特定の行、型、シンボル、ファイル、その他をシンプルな統一されたインターフェイスで検索できます。

### <a name="how-to-use"></a>使い方
* **キーボード**
  * **Ctrl + ,** キーまたは **Ctrl + T** キーを押します。  選ばれているプロファイルによってキーボード ショートカットが異なる場合があることに注意してください。
* **マウス**
  * **[編集] > [ジャンプ] > [すべてにジャンプ]** を選びます。

既定では IDE の右上に小さなウィンドウが表示されます。

![すべてにジャンプ](media/gotoall.png)

ここからは、複数の移動方法があります。
* プレフィックスを付けずにテキストを入力し、テキスト ボックスの下で選んだ[フィルター アイコン](#filtered-searches)を使って検索します。
* [プレフィックス](#filtered-searches)の後にテキストを入力して検索します。
* 疑問符 (?) を入力して詳しいヘルプ情報を表示します。
  ![[すべてにジャンプ] のヘルプ](media/gotoall_help.png)

### <a name="filtered-searches"></a>フィルター処理された検索
検索を特定の種類に絞り込むには、入力するときにプレフィックスを使うか、[検索] ウィンドウの下に表示される以下のアイコンを使います。

プレフィックス | アイコン | ショートカット | 説明
:----: | ---- | -------- | ---
#      | ![シンボル アイコン](media/gotoall_symbolicon.png) | Ctrl + 1、Ctrl + S | 一致するシンボルを検索します
f      | ![ファイル アイコン](media/gotoall_fileicon.png)     | Ctrl + 1、Ctrl + F | 一致するファイル名を検索します
m      | ![メンバー アイコン](media/gotoall_membericon.png) | Ctrl + 1、Ctrl + M | 一致するメンバーを検索します
t      | ![型アイコン](media/gotoall_typeicon.png)     | Ctrl + 1、Ctrl + T | 一致する型を検索します
:      | ![行アイコン](media/gotoall_lineicon.png)     | Ctrl+G         | 入力した行番号にジャンプします

### <a name="search-locations"></a>検索場所
特定の場所に検索を絞り込むには、2 つのドキュメント アイコンを使います。

アイコン | 説明
---- | ---
![現在のドキュメント](media/gotoall_currentdocument.png) | 現在のドキュメントだけを検索します
![外部ドキュメント](media/gotoall_external.png) | プロジェクト/ソリューションに含まれるドキュメントだけでなく外部のドキュメントも検索します

### <a name="settings"></a>設定
右下にある歯車アイコン ![歯車アイコン](media/gotoall_gear.png) をクリックして、この機能の動作を変更することができます。

設定 | 説明
------- | ---
プレビュー タブを使用する | 選んだ項目を IDE の [プレビュー] タブにすぐに表示します
詳細の表示    | プロジェクト、ファイル、行、およびドキュメントのコメントから取得した概要情報をウィンドウに表示します
ウィンドウを中央に   | このウィンドウを右上ではなく IDE の中央に移動します
<!-- END VERSIONLESS -->

## <a name="go-to-definition"></a>[定義へ移動]
型のソースに移動し、結果を新しいタブで開きます。

入力        | 関数 
------------ | ---
**キーボード** | 型名内のどこかにテキスト カーソルを置き、**F12** キーを押します
**マウス**    | 型名を右クリックし、**[定義へ移動]** を選びます

## <a name="peek-definition"></a>定義をここに表示
新しいタブではなくポップアップ ウィンドウで型の定義をプレビューします。

入力        | 関数 
------------ | ---
**キーボード** | 型名内のどこかにテキスト カーソルを置き、**Alt + F12** キーを押します
**マウス**    | 型名を右クリックし、**[定義をここに表示]** を選びます

ポップアップ ウィンドウから別の定義を表示する場合は、ポップアップの上に表示される円と矢印を使ってナビゲートできる階層リンク パスを開始します。  詳細については、「[方法: [定義をここに表示] を使用してコードを表示および編集する (Alt + F12)](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)」を参照してください。

## <a name="go-to-implementation"></a>実装に移動
基底クラスまたは型からその実装に移動します。  複数の実装がある場合は、**[シンボルの検索結果]** ウィンドウに一覧表示されます。

入力        | 関数 
------------ | ---
**キーボード** | 型名内のどこかにテキスト カーソルを置き、**Ctrl + F12** キーを押します
**マウス**    | 型名を右クリックし、**[実装に移動]** を選びます

## <a name="find-all-references"></a>[すべての参照の検索]
メソッド/プロパティ/変数が使われているすべての場所を検索します。  これを使って、実行されないコードを調べ、大規模なリファクタリングの副作用を確認することができます。  結果の間をジャンプするには、**F8** キーを押します。

入力        | 関数 
------------ | ---
**キーボード** | 型名内のどこかにテキスト カーソルを置き、**Ctrl + K、R** キーを押します
**マウス**    | 型名を右クリックし、**[すべての参照の検索]** を選びます

## <a name="navigating-results"></a>結果内の移動
Visual Studio のナビゲーション機能を使うと、スタックを前後に移動できます。

入力        | 関数 
------------ | ---
**Ctrl + -**          | スタックを後方に移動します
**Ctrl + Shift + -**    | スタックを前方に移動します

**[表示] > [後ろに移動する]** および **[表示] > [前に移動する]** メニュー項目を使うこともできます。
