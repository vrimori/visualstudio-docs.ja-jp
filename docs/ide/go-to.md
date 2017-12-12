---
title: "移動コマンドを使用したコードの検索 | Microsoft Docs"
ms.custom: 
ms.date: 09/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 509b2107-23d1-4fb3-987f-ab99ef45b72e
helpviewer_keywords:
- code editor, go to
- code editor, go to line
- go to line
- go to
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 15b222eaa3e03a44f99f64e86f9c88d125e41f98
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="find-code-using-go-to-commands"></a>移動コマンドを使用したコードの検索  
Visual Studio の **[移動]** コマンドは、特定の項目をすばやく検索できるように、コードのフォーカス検索を行います。 統一されたシンプルなインターフェイスで、特定の行、型、シンボル、ファイル、メンバーに移動できます。 この機能は Visual Studio 2017 以降に備わっています。  

### <a name="how-to-use-it"></a>使用方法  

入力        | 関数 
------------ | ---
**キーボード** | **Ctrl + t** キーを押すか、または **Ctrl + ,** キーを押します。     
**マウス**    | **[編集]**、**[ジャンプ]**、**[すべてにジャンプ]** の順に選択します。  

既定ではコード エディターの右上に小さなウィンドウが表示されます。  

![すべてにジャンプ](media/gotoall.png)

テキスト ボックスに入力すると、テキスト ボックスの下のドロップダウン リストに結果が表示されます。 要素に移動するには、一覧の要素を選択します。    

![[移動] ウィンドウ](../ide/media/vside_navigatetowindow.png "[移動] ウィンドウ")  

疑問符 (?) を入力して詳しいヘルプ情報を表示することもできます。  

  ![[すべてにジャンプ] のヘルプ](media/gotoall_help.png)

### <a name="filtered-searches"></a>フィルター処理された検索  
既定では、指定した項目がソリューションのすべての項目から検索されます。 ただし、検索語句の前に特定の文字を付けることで、コード検索の対象を特定の種類の要素に限定できます。 [移動] ダイアログ ボックスのツール バーでボタンを選択して、簡単に検索フィルターを変更することもできます。 タイプ フィルターを変更するボタンが左側にあり、検索の範囲を変更するボタンが右側にあります。  

![メンバーに移動する](../ide/media/vside_navigation_toolbar.png)

#### <a name="filter-to-a-specific-type-of-code-element"></a>フィルター処理して特定の種類のコード要素に絞り込む  
特定の種類のコード要素に検索を絞り込むには、[検索] ボックスでプレフィックスを指定するか、次の 5 つのフィルター アイコンのいずれかを選択します。  

プレフィックス | アイコン | ショートカット | 説明
:----: | ---- | -------- | ---
\#      | ![シンボル アイコン](media/gotoall_symbolicon.png) | Ctrl + 1、Ctrl + S | 指定したシンボルに移動します。
f      | ![ファイル アイコン](media/gotoall_fileicon.png)     | Ctrl + 1、Ctrl + F | 指定したファイルに移動します。
m      | ![メンバー アイコン](media/gotoall_membericon.png) | Ctrl + 1、Ctrl + M | 指定したメンバーに移動します。
t      | ![型アイコン](media/gotoall_typeicon.png)     | Ctrl + 1、Ctrl + T | 指定した型に移動します。
:      | ![行アイコン](media/gotoall_lineicon.png)     | Ctrl + G         | 指定した行番号に移動します。

#### <a name="filter-to-a-specific-location"></a>フィルター処理して特定の場所に絞り込む    
特定の場所に検索を絞り込むには、次の 2 つのドキュメント アイコンのいずれかを選択します。  

アイコン | 説明
---- | ---
![現在のドキュメント](media/gotoall_currentdocument.png) | 現在のドキュメントだけを検索します
![外部ドキュメント](media/gotoall_external.png) | プロジェクト/ソリューションに含まれるドキュメントだけでなく外部のドキュメントも検索します  

### <a name="camel-casing"></a>camel 規約に従った大文字小文字の使い分け  
コード内で [camel 規約に従った大文字小文字の使い分け](https://en.wikipedia.org/wiki/Camel_case)を使用している場合は、コード要素名の大文字のみを入力することにより、コードの検索が速くなります。 たとえばコードで `CredentialViewModel` という型を使用している場合は、[移動] ダイアログ ボックスで型フィルター ("t") を選択し、名前に含まれる大文字 (`CVM`) だけを入力します。 この機能は、コード中に長い名前がある場合に便利です。  

![[移動] ウィンドウ - 大文字を使用した検索](../ide/media/vside_capitalsearch.png)

### <a name="settings"></a>設定  
歯車アイコンを選択すると、 ![歯車アイコン](media/gotoall_gear.png) この機能の動作を変更することができます。  

設定 | 説明
------- | ---
プレビュー タブを使用する | 選んだ項目を IDE の [プレビュー] タブにすぐに表示します
詳細の表示    | プロジェクト、ファイル、行、およびドキュメントのコメントから取得した概要情報をウィンドウに表示します。
ウィンドウを中央に   | このウィンドウをコード エディターの右上ではなく、中央に移動します。   

## <a name="see-also"></a>関連項目  
[コード間の移動](../ide/navigating-code.md)  
[[定義へ移動] と [定義をここに表示]](../ide/go-to-and-peek-definition.md)  