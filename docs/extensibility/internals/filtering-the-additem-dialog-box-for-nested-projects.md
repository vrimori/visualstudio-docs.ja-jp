---
title: 入れ子になったプロジェクトに対して、AddItem ダイアログ ボックスをフィルタ リング |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: 50a9491dad92e4f1dd090a6de1ebf48ef1b88085
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="filtering-the-additem-dialog-box-for-nested-projects"></a>入れ子になったプロジェクトに対して、AddItem ダイアログ ボックスのフィルター処理
表示するとき、 **AddItem**親プロジェクトは、入れ子になったプロジェクト ダイアログ ボックスは、ダイアログ ボックスに表示される項目を制御できます。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>インターフェイスに含まれるノードをフィルター処理することができます、 **AddItem**  ダイアログ ボックス。 子プロジェクトを表示するとき、 **AddItem**ダイアログ ボックスで、親を実装できる、`IVsFilterAddProjectItemDlg`それ以外の場合、子のプロジェクトに表示されるインターフェイスとフィルターの項目。  
  
 プロジェクトの特定の親関数によっては、プロジェクトがグループ化を実装できます`IVsFilterAddProjectItemDlg`、ユーザーが選択すると**プロジェクト項目の追加**入れ子にされたプロジェクトのショートカット メニューの します。 実装する`IvsFilterAddProjectItemDlg displays`プロジェクトのみ項目またはファイルをそのグループに特定します。 グループの他のプロジェクト項目は、同じディレクトリに保存されている場合でも、ダイアログ ボックスから除外されます。  
  
 ユーザーが開いたとき、 **AddItem** 、親プロジェクトの実装の子のダイアログ ボックス、`IVsFilterAddProjectItemDlg`インターフェイスが呼び出されます。  
  
 `IVsFilterAddProjectItemDlg`インターフェイスは、カテゴリをフィルター処理も実装できます。 詳細については、次を参照してください。[新しい項目の追加 ダイアログ ボックスに追加する項目](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)と[を登録するプロジェクトと項目テンプレート](../../extensibility/internals/registering-project-and-item-templates.md)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [項目を追加する、新しい項目の追加 ダイアログ ボックス](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [プロジェクトと項目テンプレートの登録](../../extensibility/internals/registering-project-and-item-templates.md)   
 [入れ子になったプロジェクト](../../extensibility/internals/nesting-projects.md)