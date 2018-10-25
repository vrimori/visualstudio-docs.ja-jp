---
title: プロジェクト アイテムへの属性の追加 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes [Visual Studio], adding to a project item
ms.assetid: 404a71d5-cce5-44e7-9eaf-d747c794fedb
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3c5e1cba339ab89957a942968acbb88f2204a6af
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49907860"
---
# <a name="adding-an-attribute-to-a-project-item"></a>プロジェクト項目への属性の追加
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

メソッド<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetItemAttribute%2A>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A>を取得し、プロジェクト項目の属性の値を設定します。 SetItemAttribute 属性を作成、それが存在しない場合、プロジェクト項目のメタデータに追加すること。  
  
## <a name="adding-an-attribute-to-a-project-item"></a>プロジェクト アイテムへの属性の追加  
  
#### <a name="to-add-an-attribute-to-a-project-item"></a>プロジェクト項目に属性を追加するには  
  
-   次のコードでは、<xref:EnvDTE.DTE>オートメーション オブジェクト、<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A>プロジェクト項目に属性を追加します。 プロジェクト項目の ID は、プロジェクト項目の名前"program.cs"から取得されます。 属性"MyAttribute"がこのプロジェクト アイテムに追加され、"MyValue"の値を指定します。  
  
    ```  
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));  
    EnvDTE.Project project = dte.Solution.Projects.Item(1);  
  
    string uniqueName = project.UniqueName;  
    IVsSolution solution =     (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));  
    IVsHierarchy hierarchy;  
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);  
    IVsBuildPropertyStorage buildPropertyStorage = hierarchy as IVsBuildPropertyStorage;  
    if (buildPropertyStorage != null)  
    {  
        uint itemId;  
        string fullPath =         (string)project.ProjectItems.Item("Program.cs").Properties.Item("FullPath").Value;  
        hierarchy.ParseCanonicalName(fullPath, out itemId);  
        buildPropertyStorage.SetItemAttribute(  
            itemId, "MyAttribute", "MyValue");  
    }  
  
    ```  
  
## <a name="see-also"></a>関連項目  
 [MSBuild プロジェクト ファイルでのデータの保持](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)

