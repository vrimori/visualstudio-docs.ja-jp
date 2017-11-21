---
title: "同期の種類とファイル名 - リファクタリング (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ff86d7bd-837b-4664-b0ea-d3ee0c52fe87
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs: VB
ms.openlocfilehash: da6f39dd3573d361c1da579eb3d84c2c8ceeb517
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="sync-a-type-to-a-filename-or-a-filename-to-a-type-in-visual-basic"></a>ファイル名、または Visual Basic の型にファイル名には、タイプを同期します。

<!-- VERSIONLESS -->
**この機能は、Visual Studio 2017 で使用できる以降です。さらに、標準の .NET プロジェクトはまだサポートされていませんこのリファクタリングします。**

**新機能:**ファイル名と一致する型の名前を変更または名前が含まれている型と一致するファイル名を変更することができます。

****ファイルまたは型の名前を変更したし、対応するファイルまたは一致する種類はまだ更新されていません。 

**理由:**ファイルが別の名前、またはその逆を行う、探しているものを検索するが困難で型を配置することです。  型またはファイル名のいずれかの名前を変更するには、読みやすく理解しやすくするコードになります。

**どう：**

1. 強調表示またはカーソルを置き、テキスト内を同期する型の名前。

   ![強調表示されたコード](media/synctype_highlight.png)

1. 次に、次のいずれかの操作を行います。
   * **キーボード**
     * キーを押して**Ctrl + です。** トリガーに、**クイック アクションとリファクタリング**メニュー**に名前を変更するファイル*TypeName*.vb**プレビュー ウィンドウから、 *TypeName* 、選択した種類の名前を指定します。
     * キーを押して**Ctrl + です。** トリガーに、**クイック アクションとリファクタリング**メニューを選択**する型の名前を変更_Filename_** プレビュー ウィンドウのポップアップから場所*ファイル名* 、現在のファイルの名前を指定します。
   * **マウス**
     * コードを右クリックし、選択、**クイック アクションとリファクタリング**メニューのおよび選択**に名前を変更するファイル*TypeName*.vb**プレビュー ウィンドウから、 *TypeName*選択した種類の名前を指定します。
     * コードを右クリックし、選択、**クイック アクションとリファクタリング**メニューのおよび選択**する型の名前を変更_Filename_** プレビュー ウィンドウから場所*Filename*現在のファイルの名前を指定します。

   型またはファイルが即座に名前を変更します。  次の例で、ファイルで**Employee.vb**に名前が変更された**Person.vb**型名と一致します。

   ![Inline 結果](media/synctype_result.png)

## <a name="see-also"></a>関連項目  
[リファクタリング (Visual Basic)](../refactoring-vb.md)
