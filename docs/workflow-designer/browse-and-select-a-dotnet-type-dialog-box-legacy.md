---
title: "参照し、選択 .NET 型 ダイアログ ボックス (レガシ) |Microsoft ドキュメント"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Workflow.ComponentModel.Design.TypeBrowserDialog.UI
helpviewer_keywords:
- Browse and Select a .NET Type dialog box
ms.assetid: 1e66c9bc-94b2-46e2-bedf-871752e5f917
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 3cdc5d3928cd436d86d529e667f99251e1e7cc95
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2018
---
# <a name="browse-and-select-a-net-type-dialog-box-legacy"></a>[.NET 型の参照と選択] ダイアログ ボックス (レガシ)
このトピックについて説明する方法を使用して、**を参照して .NET 型を選択**従来の Windows ワークフロー デザイナー ダイアログ ボックス。 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] または [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] を対象とする必要がある場合は、従来の[!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)]を使用します。

 **プロパティ**ウィンドウで、省略記号、参照されたアセンブリで .NET Framework の型を使用するプロパティを選択すると**[...]**プロパティのテキスト ボックスの端に表示されます。 クリックすると、 **[...]**開きます、**を参照して .NET 型を選択** ダイアログ ボックス。 このダイアログ ボックスで、参照アセンブリのツリー表示から型を選択できます。 たとえば、使用する場合、アクティビティ デザイナーで、**プロパティ**ウィンドウで、をクリックして、**基本クラスの**省略記号**[...]**参照アセンブリ ツリーから別の基本アクティビティ クラスを選択します。

 次の表は、ユーザー インターフェイス (UI) 要素の**を参照して .NET 型を選択** ダイアログ ボックス。

|UI 要素|説明|
|----------------|-----------------|
|**型名:**|現在選択されている型の名前。|
|**Type**|左側のペインには、参照アセンブリがツリー表示されます。 右側のペインには、左側のペインで選択した参照アセンブリから選択可能な型が表示されます。|

## <a name="see-also"></a>関連項目

- [従来のアクティビティ デザイナーの使用](../workflow-designer/using-the-legacy-activity-designer.md)