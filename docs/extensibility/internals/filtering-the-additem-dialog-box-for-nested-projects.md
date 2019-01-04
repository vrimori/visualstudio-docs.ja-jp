---
title: 入れ子になったプロジェクトの AddItem ダイアログ ボックスのフィルター処理 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- filtering, nested projects
- nested projects, AddItem dialog box filtering
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a3382982a529444f019cb2f97a22636375eb5145
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53857686"
---
# <a name="filter-the-additem-dialog-box-for-nested-projects"></a>入れ子になったプロジェクトの [AddItem] ダイアログ ボックスをフィルター処理します。
表示すると、 **AddItem**  ダイアログ ボックスで表示される項目をプロジェクトの入れ子になった場合、親プロジェクト ダイアログ ボックスで制御できます。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>インターフェイスでは、含まれるノードをフィルター処理することができます、 **AddItem**  ダイアログ ボックス。 子プロジェクトが表示されます、 **AddItem**ダイアログ ボックスで、親が実装できる、`IVsFilterAddProjectItemDlg`インターフェイスとフィルターの項目をそれ以外の場合、子のプロジェクトに表示されます。  
  
 プロジェクトの特定の親関数によってグループ化しているプロジェクトを実装できます`IVsFilterAddProjectItemDlg`、ユーザーが選択すると**プロジェクト項目の追加**入れ子になったプロジェクトのショートカット メニューの します。 実装する`IvsFilterAddProjectItemDlg displays`プロジェクトのみ項目またはそのグループに固有のファイルします。 その他のグループに対するプロジェクト項目は、同じディレクトリに保存されている場合でも、ダイアログ ボックスから除外されます。  
  
 ユーザーが開いたとき、 **AddItem**子、親プロジェクトの実装のためのダイアログ ボックス、`IVsFilterAddProjectItemDlg`インターフェイスが呼び出されます。  
  
 `IVsFilterAddProjectItemDlg`インターフェイスは、カテゴリによるフィルター処理も実装できます。 詳細については、次を参照してください。 [、新しい項目の追加 ダイアログ ボックスに項目を追加](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)と[プロジェクトと項目テンプレートを登録](../../extensibility/internals/registering-project-and-item-templates.md)します。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [新しい項目の追加 ダイアログ ボックスに項目の追加](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [プロジェクトと項目テンプレートを登録します。](../../extensibility/internals/registering-project-and-item-templates.md)   
 [入れ子のプロジェクト](../../extensibility/internals/nesting-projects.md)