---
title: プロジェクト項目に属性が追加 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- attributes [Visual Studio], adding to a project item
ms.assetid: 404a71d5-cce5-44e7-9eaf-d747c794fedb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d601a4cb3a7804520f0c9c95e746275e27db4bcd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="adding-an-attribute-to-a-project-item"></a>プロジェクト項目に属性を追加します。
メソッド<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetItemAttribute%2A>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A>を取得し、プロジェクト項目の属性の値を設定します。 SetItemAttribute を作成、属性が既にがない場合、プロジェクト項目のメタデータに追加します。  
  
## <a name="adding-an-attribute-to-a-project-item"></a>プロジェクト項目に属性を追加します。  
  
#### <a name="to-add-an-attribute-to-a-project-item"></a>プロジェクト項目に属性を追加するには  
  
-   次のコードでは、<xref:EnvDTE.DTE>オートメーション オブジェクト、および<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A>プロジェクト項目に属性を追加するメソッド。 プロジェクト項目の ID は、プロジェクト アイテム名"program.cs"から取得されます。 属性"MyAttribute"がこのプロジェクト項目に追加され、"MyValue"の値を指定します。  
  
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