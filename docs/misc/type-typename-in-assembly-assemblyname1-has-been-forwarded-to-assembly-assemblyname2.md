---
title: "アセンブリ &#39;&lt;assemblyname1&gt;&#39; の型 &#39;&lt;typename&gt;&#39; は、アセンブリ &#39;&lt;assemblyname2&gt;&#39; に転送されました | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31424"
  - "bc31424"
helpviewer_keywords: 
  - "BC31424"
  - "型の転送"
ms.assetid: 0f53e613-c1cb-4722-acb5-afa3091e277b
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# アセンブリ &#39;&lt;assemblyname1&gt;&#39; の型 &#39;&lt;typename&gt;&#39; は、アセンブリ &#39;&lt;assemblyname2&gt;&#39; に転送されました
アセンブリ '\<assemblyname1\>' の型 '\<typename\>' は、アセンブリ '\<assemblyname2\>' に転送されました。 プロジェクトに '\<assemblyname2\>' への参照が見つからないか、またはアセンブリ '\<assemblyname2\>' に型 '\<typename\>' が見つかりません。  
  
 アセンブリのソース コード内の式が別のアセンブリに転送された型を参照していますが、転送先のアセンブリでその型が見つかりません。  
  
 *型の転送* とは、最初に定義されたもの以外のアセンブリにクラス、構造体、インターフェイス、デリゲート、または列挙型の定義を再割り当てすることを意味します。 これは *コードのリファクタリング* と組み合わせてよく使用され、これにより、1 つのアセンブリを 2 つ以上のアセンブリに分割したり、アセンブリ間でコードを移動したりできます。  
  
 型は一時的に元のアセンブリでも引き続き使用できますが、コードのリファクタリングによって元のアセンブリから削除されると未定義になる可能性があります。  
  
 **エラー ID:** BC31424  
  
### このエラーを解決するには  
  
-   型が転送先のアセンブリにあることを確認します。  
  
-   プロジェクトが転送先のアセンブリを参照していることを確認します。  
  
## 参照  
 <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>   
 [Type Forwarding \(C\+\+\/CLI\)](/visual-cpp/windows/type-forwarding-cpp-cli)   
 [プロジェクト内の参照の管理](../ide/managing-references-in-a-project.md)   
 [NIB 方法: &#91;参照の追加&#93; ダイアログ ボックスを使用して参照を追加または削除する](http://msdn.microsoft.com/ja-jp/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)