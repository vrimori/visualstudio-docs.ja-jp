---
title: "実行時に、プロジェクトのサブタイプを確認します。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "プロジェクトのサブタイプ"
  - "サブタイプをチェックします。"
ms.assetid: b87780ec-36a3-4e9a-9ee2-7abdc26db739
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# 実行時に、プロジェクトのサブタイプを確認します。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

カスタム プロジェクト サブタイプに依存している VSPackage では、サブタイプが存在しない場合に正常にフェールオーバーできるにするためのサブタイプを検索するロジックを含める必要があります。 次の手順では、指定したサブタイプの存在を確認する方法を示します。  
  
### サブタイプの存在を確認するには  
  
1.  プロジェクトとソリューションのオブジェクトとしてから、プロジェクト階層を取得、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 、VSPackage に次のコードを追加することによってオブジェクトです。  
  
    ```  
    EnvDTE.DTE dte;  
    dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));  
  
    EnvDTE.Project project;  
    project = dte.Solution.Projects.Item(1);  
  
    IVsSolution solution;  
    solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));  
  
    IVsHierarchy hierarchy;  
    hierarchy = solution.GetProjectOfUniqueName(project.UniqueName);  
  
    ```  
  
2.  階層のキャスト、 <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected> インターフェイスです。  
  
    ```  
    IVsAggregatableProjectCorrected AP;  
    AP = hierarchy as IVsAggregatableProjectCorrected;  
  
    ```  
  
3.  起動してプロジェクトの種類の Guid の一覧を取得、 <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A>です。  
  
    ```  
    string projTypeGuids = AP.GetAggregateProjectTypeGuids().ToUpper();  
  
    ```  
  
4.  指定したサブタイプの GUID の一覧を確認します。  
  
    ```  
    // Replace the string "MyGUID" with the GUID of the subtype.  
    string guidMySubtype = "MyGUID";  
    if (projTypeGuids.IndexOf(guidMySubtype) > 0)  
    {  
        // The specified subtype is present.  
    }  
    ```  
  
## 参照  
 [プロジェクトのサブタイプ](../extensibility/internals/project-subtypes.md)   
 [プロジェクトのサブタイプの設計](../extensibility/internals/project-subtypes-design.md)   
 [プロパティとプロジェクトのサブタイプによって拡張メソッド](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)