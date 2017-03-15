---
title: "プロジェクト項目に属性を追加します。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "プロジェクト項目に追加する属性 [Visual Studio]"
ms.assetid: 404a71d5-cce5-44e7-9eaf-d747c794fedb
caps.latest.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 4
---
# プロジェクト項目に属性を追加します。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

メソッドの <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetItemAttribute%2A> と <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> はプロジェクト項目の属性の値を取得および設定します。  SetItemAttribute が既にあるプロジェクト項目メタデータに追加する属性を作成します。  
  
## プロジェクト項目に属性を追加します。  
  
#### 属性をプロジェクト項目に追加するには  
  
-   次のコードは <xref:EnvDTE.DTE> のオートメーション オブジェクトやプロジェクト項目に属性を追加するには <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> のメソッドを使用します。  プロジェクト項目 ID はプロジェクト項目名 「 program.cs 」から派生します。  属性 「」 MyAttribute はこのプロジェクト項目に追加し値 「」 MyValue されます。  
  
    ```  
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
  
## 参照  
 [MSBuild プロジェクト ファイルでデータを保持します。](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)