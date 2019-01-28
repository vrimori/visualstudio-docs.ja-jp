---
title: プロジェクト アイテムへの属性の追加 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- attributes [Visual Studio], adding to a project item
ms.assetid: 404a71d5-cce5-44e7-9eaf-d747c794fedb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c1195299ae63ddb2e14d36fffe79bbc06b909072
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55003046"
---
# <a name="add-an-attribute-to-a-project-item"></a>プロジェクト項目に属性を追加します。
メソッド<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetItemAttribute%2A>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A>を取得し、プロジェクト項目の属性の値を設定します。 SetItemAttribute 属性を作成、それが存在しない場合、プロジェクト項目のメタデータに追加すること。  
  
## <a name="add-an-attribute-to-a-project-item"></a>プロジェクト項目に属性を追加します。  
  
-   次のコードでは、<xref:EnvDTE.DTE>オートメーション オブジェクト、<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A>プロジェクト項目に属性を追加します。 プロジェクト項目の ID は、プロジェクト項目の名前"program.cs"から取得されます。 属性"MyAttribute"がこのプロジェクト アイテムに追加され、"MyValue"の値を指定します。  
  
    ```csharp  
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));  
    EnvDTE.Project project = dte.Solution.Projects.Item(1);  
  
    string uniqueName = project.UniqueName;  
    IVsSolution solution =     (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));  
    IVsHierarchy hierarchy;  
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);  
    IVsBuildPropertyStorage buildPropertyStorage = hierarchy as IVsBuildPropertyStorage;  
    if (buildPropertyStorage != null)  
    {  
        uint itemId;  
        string fullPath =         (string)project.ProjectItems.Item("Program.cs").Properties.Item("FullPath").Value;  
        hierarchy.ParseCanonicalName(fullPath, out itemId);  
        buildPropertyStorage.SetItemAttribute(  
            itemId, "MyAttribute", "MyValue");  
    }  
  
    ```  
  
## <a name="see-also"></a>関連項目  
 [MSBuild プロジェクト ファイル内のデータを永続化します。](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)