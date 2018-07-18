---
title: 実行時に、プロジェクトのサブタイプを確認しています |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: b8898da6850c01c1a248b57b0fbc5f46be2a8ff4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31136830"
---
# <a name="verifying-subtypes-of-a-project-at-run-time"></a>実行時に、プロジェクトのサブタイプを確認しています
カスタム プロジェクトのサブタイプに依存する VSPackage は、サブタイプのサブタイプが存在しない場合に正常に失敗できるようにするロジックを探してを含める必要があります。 次の手順では、指定されたサブタイプの存在を確認する方法を示します。  
  
### <a name="to-verify-the-presence-of-a-subtype"></a>サブタイプの存在を確認するには  
  
1.  プロジェクトとソリューションのオブジェクトとしてから、プロジェクト階層を取得、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> VSPackage に次のコードを追加することによってオブジェクト。  
  
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
  
2.  階層のキャスト、<xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected>インターフェイスです。  
  
    ```  
    IVsAggregatableProjectCorrected AP;  
    AP = hierarchy as IVsAggregatableProjectCorrected;  
  
    ```  
  
3.  呼び出すことによってプロジェクトの種類の Guid の一覧を取得、<xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A>です。  
  
    ```  
    string projTypeGuids = AP.GetAggregateProjectTypeGuids().ToUpper();  
  
    ```  
  
4.  指定されたサブタイプの GUID の一覧を確認します。  
  
    ```  
    // Replace the string "MyGUID" with the GUID of the subtype.  
    string guidMySubtype = "MyGUID";  
    if (projTypeGuids.IndexOf(guidMySubtype) > 0)  
    {  
        // The specified subtype is present.  
    }  
    ```  
  
## <a name="see-also"></a>関連項目  
 [プロジェクトのサブタイプ](../extensibility/internals/project-subtypes.md)   
 [プロジェクトのサブタイプの設計](../extensibility/internals/project-subtypes-design.md)   
 [プロジェクト サブタイプによって拡張されるプロパティとメソッド](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)