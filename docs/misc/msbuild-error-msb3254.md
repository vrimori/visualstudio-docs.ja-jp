---
title: "MSBuild エラー MSB3254 | Microsoft Docs"
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
  - "MSB3254"
ms.assetid: cb9636b2-d9b3-466d-959c-14c7c8017a78
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB3254
**MSB3254: ファイル \<名前\> は、読み取れないため無視されます。  このファイルは、InstalledAssemblySubsetTables に渡されたか、TargetFrameworkDirectories の \<名前\> フォルダーの検索によって見つかりました。**  
  
 このエラーは、[!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)] XML ファイルである client.xml を読み込むことができない場合に発生します。  このファイルは、破損、ロック、またはその他の問題が原因で読み取ることができません。  
  
 [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)] は、完全な [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 3.5 ランタイム ライブラリのサブセットです。  [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)] の詳細については、「[.NET Framework Client Profile](../Topic/.NET%20Framework%20Client%20Profile.md)」を参照してください。  
  
 プロシージャ  
  
### このエラーを解決するには  
  
-   ファイルに対する完全なアクセス許可とフル アクセスが与えられていることを確認します。または、[!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)] 再頒布可能なランタイム ライブラリを再インストールして、破損ファイルを置き換えます。  
  
## 参照  
 [Project Element \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [追加のリソース](../msbuild/additional-msbuild-resources.md)