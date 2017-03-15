---
title: "MSBuild エラー MSB3253 | Microsoft Docs"
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
  - "MSB3253"
ms.assetid: d4b5eb5b-703b-4b80-aa5d-6c70ff9fe84d
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB3253
**MSB3254: 参照アセンブリ \<name\> は .NET Framework Client Profile の一部として一覧表示されていない \<name\> に依存しています。**  
  
 プロジェクトで参照されているいずれかのアセンブリまたは依存アセンブリが、[!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)] に含まれていない別のアセンブリに依存しています。  
  
 このメッセージは、通常、プロジェクトが、外部アセンブリを参照するサード パーティ製コントロールまたは DLL を参照している場合に表示されます。  たとえば、プロジェクトで使用しているコントロールが、完全な [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] に含まれている機能を使用しています。  アプリケーションが [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)] に対して再ターゲットされ、[!INCLUDE[net_v35_long](../misc/includes/net_v35_long_md.md)] を実装していないシステムにインストールされた場合、[!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)] サブセットに含まれない機能にアクセスしようとすると、アプリケーションが正しく動作しないことがあります。  
  
 この "エラー" メッセージは警告を表示するだけで、アプリケーションのコンパイルは行われます。  ただし、後でコントロールや DLL によって存在しないアセンブリの機能が参照されると、アプリケーションでエラーが発生することがあります。  
  
 [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)] は、完全な [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 3.5 ランタイム ライブラリのサブセットです。  [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)] の詳細については、「[.NET Framework Client Profile](../Topic/.NET%20Framework%20Client%20Profile.md)」を参照してください。  
  
### このエラーを解決するには  
  
-   指定されたアセンブリ参照をプロジェクトから削除するか、プロジェクトの対象を、[!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)] のサブセット ライブラリではなく完全な [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] にします。  完全な [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] を対象にする方法の詳細については、「[方法: .NET Framework のバージョンをターゲットにする](../ide/how-to-target-a-version-of-the-dotnet-framework.md)」を参照してください。  
  
## 参照  
 [ターゲット フレームワークおよびターゲット プラットフォーム](../msbuild/msbuild-target-framework-and-target-platform.md)   
 [Project Element \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [追加のリソース](../msbuild/additional-msbuild-resources.md)