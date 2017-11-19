---
title: "入れ子になったプロジェクトに対して、AddItem ダイアログ ボックスをフィルタ リング |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- filtering, nested projects
- nested projects, AddItem dialog box filtering
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 392f2f33d792c4e8f31ff0423b68a28a68797818
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
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