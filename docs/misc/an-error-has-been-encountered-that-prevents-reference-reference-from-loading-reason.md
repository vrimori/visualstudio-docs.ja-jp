---
title: "An error has been encountered that prevents reference &#39;reference&#39; from loading. &lt;reason&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.reference_load_error"
ms.assetid: 0e922611-197b-4607-bc31-03f80bd3e7e1
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# An error has been encountered that prevents reference &#39;reference&#39; from loading. &lt;reason&gt;
プロジェクト ファイルから参照を解除するときに致命的なエラーが発生しました。  このエラーの原因は、\<理由\> に表示されます。次のことが考えられます。  
  
-   参照の GUID が不適切である。  これは、COM 参照の場合にだけ適用されます。  
  
-   ラップ ツールが不適切である。  現在、ラップ ツールで有効なプロパティは、tlbimp、aximp、または primary のいずれかです。  これは、COM 参照の場合にだけ適用されます。  
  
-   プロジェクトの参照文字列が不適切である。  これは、プロジェクト対プロジェクトの参照の場合にだけ適用されます。  
  
 **このエラーを解決するには**  
  
-   このエラーを解決するには、プロジェクトに参照を追加します。  
  
     この診断が表示される参照は、プロジェクトに読み込まれません。  
  
## 参照  
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/ja-jp/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)