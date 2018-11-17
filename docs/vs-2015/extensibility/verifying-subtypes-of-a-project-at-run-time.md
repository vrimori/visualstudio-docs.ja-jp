---
title: 実行時に、プロジェクトのサブタイプの確認 |Microsoft Docs
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
- project subtypes
- check subtypes
ms.assetid: b87780ec-36a3-4e9a-9ee2-7abdc26db739
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 892ba25ff70f62f77016bea1b88436c4f5a6a5b0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51779893"
---
# <a name="verifying-subtypes-of-a-project-at-run-time"></a>実行時のプロジェクトのサブタイプの確認
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

カスタムのプロジェクト サブタイプに依存する VSPackage は、サブタイプのサブタイプが存在しない場合に適切に失敗できるようにするロジックを探してを含める必要があります。 次の手順では、指定されたサブタイプの存在を確認する方法を示します。  
  
### <a name="to-verify-the-presence-of-a-subtype"></a>サブタイプの存在を確認するには  
  
1.  プロジェクトとソリューションのオブジェクトとしてから、プロジェクト階層を取得、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> VSPackage に、次のコードを追加することによってオブジェクト。  
  
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
  
2.  階層のキャスト、<xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected>インターフェイス。  
  
    ```  
    IVsAggregatableProjectCorrected AP;  
    AP = hierarchy as IVsAggregatableProjectCorrected;  
  
    ```  
  
3.  呼び出すことによってプロジェクト型 Guid の一覧を取得、<xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A>します。  
  
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
 [プロジェクト サブタイプ](../extensibility/internals/project-subtypes.md)   
 [プロジェクト サブタイプのデザイン](../extensibility/internals/project-subtypes-design.md)   
 [プロジェクト サブタイプによって拡張されるプロパティとメソッド](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)

