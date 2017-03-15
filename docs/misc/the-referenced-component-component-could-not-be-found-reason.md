---
title: "The referenced component &#39;component&#39; could not be found. &lt;reason&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.referencenotfound"
ms.assetid: 35491b4d-e3e4-4e7c-8ac1-3adb09c1ef58
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The referenced component &#39;component&#39; could not be found. &lt;reason&gt;
プロジェクト システムが特定の参照を解決できませんでした。  このタスク一覧の項目をダブルクリックすると、ソリューション エクスプローラーにフォーカスが移り、解決されなかった参照が選択されます。  
  
 適切なディレクトリがパスに含まれるように [ReferencePaths](http://msdn.microsoft.com/ja-jp/8e549b39-7256-456a-8fd7-089b23facf9c) プロパティを編集してください。  
  
 このエラーは、別のコンピューターにプロジェクトを移動した場合に発生することがあります。  `ReferencePath` プロパティは、絶対パスとして格納されます。  参照 R1 がコンピューター A の "c:\\R\\R1.dll" に存在する場合、.vbproj.user ファイルまたは .csproj.user ファイルでは、"c:\\R" が `ReferencePath` プロパティの一部として格納されます。  しかし、コンピューター B で R1 が "d:\\R\\R1.dll" に存在する場合、"d:\\R" は Reference Path には含まれないため、プロジェクト システムは R1 を見つけることができません。  
  
 同様のシナリオとして、ソース コード管理のシナリオがあります。  プロジェクトに参加する場合、ソース コード管理には .vbproj.user \(または .csproj.user\) ファイルが格納されていないため、これらファイルはコンピューターにコピーされません。  したがって、`ReferencePath` プロパティの初期値は空白になり、解決に `ReferencePath` を使用するすべての参照が解決されなくなります。  詳細については、「Visual Studio .NET と Visual SourceSafe を使用したチーム開発」の「依存関係の管理」を参照してください。  
  
 このエラーは、参照されたプロジェクトが現在のソリューションに存在しない場合にも発生することがあります。  
  
 このエラーが発生した場合、プロジェクトがビルドされない可能性があります。  
  
 アセンブリの参照を解決する方法の詳細については、「[壊れた参照のトラブルシューティング](../ide/troubleshooting-broken-references.md)」を参照してください。  
  
## 参照  
 [プロジェクト内の参照の管理](../ide/managing-references-in-a-project.md)