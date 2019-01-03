---
title: 実行時に、プロジェクトのサブタイプの確認 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes
- check subtypes
ms.assetid: b87780ec-36a3-4e9a-9ee2-7abdc26db739
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 98d4e020cfd93c75c22583b763ae3b1873765598
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53913583"
---
# <a name="verify-subtypes-of-a-project-at-run-time"></a>実行時に、プロジェクトのサブタイプを確認します。
カスタムのプロジェクト サブタイプに依存する VSPackage は、サブタイプのサブタイプが存在しない場合に適切に失敗できるようにするロジックを探してを含める必要があります。 次の手順では、指定されたサブタイプの存在を確認する方法を示します。  
  
### <a name="to-verify-the-presence-of-a-subtype"></a>サブタイプの存在を確認するには  
  
1.  プロジェクトとソリューションのオブジェクトとしてから、プロジェクト階層を取得、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> VSPackage に、次のコードを追加することによってオブジェクト。  
  
    ```csharp  
    EnvDTE.DTE dte;  
    dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));  
  
    EnvDTE.Project project;  
    project = dte.Solution.Projects.Item(1);  
  
    IVsSolution solution;  
    solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));  
  
    IVsHierarchy hierarchy;  
    hierarchy = solution.GetProjectOfUniqueName(project.UniqueName);  
  
    ```  
  
2.  階層のキャスト、<xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected>インターフェイス。  
  
    ```csharp  
    IVsAggregatableProjectCorrected AP;  
    AP = hierarchy as IVsAggregatableProjectCorrected;  
  
    ```  
  
3.  呼び出すことによってプロジェクト型 Guid の一覧を取得、<xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A>します。  
  
    ```csharp  
    string projTypeGuids = AP.GetAggregateProjectTypeGuids().ToUpper();  
  
    ```  
  
4.  指定されたサブタイプの GUID の一覧を確認します。  
  
    ```csharp  
    // Replace the string "MyGUID" with the GUID of the subtype.  
    string guidMySubtype = "MyGUID";  
    if (projTypeGuids.IndexOf(guidMySubtype) > 0)  
    {  
        // The specified subtype is present.  
    }  
    ```  
  
## <a name="see-also"></a>関連項目  
 [プロジェクト サブタイプ](../extensibility/internals/project-subtypes.md)   
 [プロジェクト サブタイプのデザイン](../extensibility/internals/project-subtypes-design.md)   
 [プロパティとプロジェクト サブタイプによって拡張メソッド](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)