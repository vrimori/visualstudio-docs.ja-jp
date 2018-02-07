---
title: "型とファイル名の同期 (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 02/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 93e1b1f446dc330b2c2c1c1e5b36e6a21e64f521
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2018
---
# <a name="sync-a-type-to-a-filename-or-a-filename-to-a-type-in-visual-basic"></a>型からファイル名、またはファイル名から型への同期 (Visual Basic)

<!-- VERSIONLESS -->
**この機能は Visual Studio 2017 以降で使用できます。また、.NET Standard プロジェクトでは、このリファクタリングはまだサポートされていません。**

**機能:** 型名をファイル名と一致するように変更、またはファイル名を含まれている型と一致するように変更できます。

**条件:** ファイルまたは型の名前を変更したが、対応するファイルまたは型を一致するようにまだ更新していないとき。 

**理由:** 型が別の名前のファイルに (またはその逆に) 配置されていると、検索が困難になります。  型またはファイルどちらかの名前を変更することで、コードが読みやすくナビゲートしやすくなります。

**方法:**

1. 同期する型の名前を強調表示するか、名前の内側にテキスト カーソルを置きます。

   ![強調表示されたコード](media/synctype-highlight-vb.png)

1. 次に、以下のいずれかを実行します。
   * **キーボード**
     * **Ctrl + .** キーを押して、 **[クイック アクションとリファクタリング]** メニューをトリガーし、[プレビュー] ウィンドウ ポップアップから **[Rename file to *TypeName*.vb]\(ファイルの名前を TypeName.vb に変更\)** を選択します。ここで、*TypeName* は選択した型の名前です。
     * **Ctrl + .** キーを押して、 **[クイック アクションとリファクタリング]** メニューをトリガーし、[プレビュー] ウィンドウ ポップアップ から **[型の名前を _Filename_ に変更]** を選択します。ここで、*Filename* は現在のファイルの名前です。
   * **マウス**
     * コードを右クリックして **[クイック アクションとリファクタリング]** メニューを選択し、[プレビュー] ウィンドウ ポップアップ から **[Rename file to *TypeName*.vb]\(ファイルの名前を TypeName.vb に変更\)** を選択します。ここで、*TypeName* は選択した型の名前です。
     * コードを右クリックして **[クイック アクションとリファクタリング]** メニューを選択し、[プレビュー] ウィンドウ ポップアップから **[型の名前を _Filename_ に変更]** を選択します。ここで、*Filename* は現在のファイルの名前です。

   型またはファイルの名前がすぐに変更されます。  次の例で、ファイル **Employee.vb** は型名と一致する **Person.vb** に名前が変更されました。

   ![インラインの結果](media/synctype-result-vb.png)

## <a name="see-also"></a>関連項目

[リファクタリング](../refactoring-in-visual-studio.md)
