---
title: "MSBuild エラー MSB3255 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSB3255"
ms.assetid: baac844e-a662-4421-bed1-2bc98f2e1cdf
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB3255
**MSB3255: ターゲット フレームワーク サブセット ファイルが、ターゲット フレームワーク ディレクトリ、または InstalledAssemblySubsetTables で指定された場所で見つかりませんでした。**  
  
 このエラーは、名前が <xref:Microsoft.Build.Tasks.ResolveAssemblyReference.FullTargetFrameworkSubsetNames%2A> プロパティに渡されたが、その名前のサブセットが見つからない場合に発生します。  
  
 [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)] は、完全な [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 3.5 ランタイム ライブラリのサブセットです。  [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)] の詳細については、「[.NET Framework Client Profile](../Topic/.NET%20Framework%20Client%20Profile.md)」を参照してください。  
  
 プロシージャ  
  
### このエラーを解決するには  
  
-   ターゲット フレームワーク フォルダーまたは <xref:Microsoft.Build.Tasks.ResolveAssemblyReference.InstalledAssemblySubsetTables%2A> に指定されているいずれかの場所に、サブセット ファイルのコピーを配置します。  
  
## 参照  
 [Project Element \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [追加のリソース](../msbuild/additional-msbuild-resources.md)