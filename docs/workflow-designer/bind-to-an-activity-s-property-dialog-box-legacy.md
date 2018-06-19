---
title: ワークフロー デザイナーでは、アクティビティにバインド&#39;s プロパティ ダイアログ ボックス (レガシ)
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Workflow.ComponentModel.Design.ActivityBindForm.UI
helpviewer_keywords:
- Bind to an Activity's Property dialog box
ms.assetid: 19ebb207-e0a9-4642-8f5f-a5e31395c683
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8922864a32c08d8feaed11e530314176557a785f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31970986"
---
# <a name="bind-to-an-activitys-property-dialog-box-legacy"></a>[アクティビティのプロパティへのバインド] ダイアログ ボックス (レガシ)

このトピックについて説明する方法を使用して、**アクティビティのプロパティにバインド**従来の Windows ワークフロー デザイナー ダイアログ ボックス。 .NET Framework version 3.5、または、WinFX を対象とする必要がある場合は、従来のワークフロー デザイナーを使用します。

 依存関係プロパティのインスタンス型は、別のアクティビティのパブリック プロパティまたはイベントにバインドすることができます。 アクティビティのバインドの詳細については、次を参照してください。[依存関係プロパティの使用](http://go.microsoft.com/fwlink?LinkID=65007)です。

 使用してバインドするプロパティを選択する、**アクティビティのプロパティにバインド** ダイアログ ボックス。 省略記号ボタンをクリックしてこのダイアログ ボックスを開く **[...]** で選択したプロパティのテキスト ボックスの最後に、**プロパティ**ウィンドウか、プロパティ ブラウザでプロパティ名の横に表示される青い感嘆符アイコンをクリックします。

 次の表は、ユーザー インターフェイス (UI) 要素の**アクティビティのプロパティにバインド** ダイアログ ボックス。

|UI 要素|説明|
|----------------|-----------------|
|**既存のメンバーへのバインドします。**|ツリー表示ペインで、バインド先となるメンバーを選択します。 ツリー表示の下にあるペインには、そのメンバーがバインド先として有効な型であるかどうかを示すメッセージが表示されます。 をクリックして**OK**選択されている有効なメンバーにバインドします。|
|**新しいメンバーへのバインドします。**|バインド先となる新しいメンバー フィールドまたはプロパティを作成します。 入力、**新しいメンバー名**です。 選択して、依存関係プロパティまたはパブリック フィールドを作成するかどうかを選択して**フィールドの作成**または**プロパティの作成**です。 をクリックして**OK**新しいメンバーを作成します。|

## <a name="see-also"></a>関連項目

- [アクティビティのプロパティを使用します。](http://go.microsoft.com/fwlink?LinkID=65013)
- [依存関係プロパティの使用](http://go.microsoft.com/fwlink?LinkID=65007)
- [従来の Designer for Windows Workflow Foundation UI ヘルプ](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)