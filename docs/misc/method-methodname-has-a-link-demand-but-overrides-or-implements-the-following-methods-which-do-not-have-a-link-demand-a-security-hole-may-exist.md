---
title: "メソッド &#39;&lt;methodname&gt;&#39; にはリンク確認要求が指定されていますが、このメソッドは、リンク確認要求が指定されていない以下のメソッドをオーバーライドまたは実装します。 セキュリティ ホールが存在する可能性があります。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc42200"
  - "vbc42200"
helpviewer_keywords: 
  - "BC42200"
ms.assetid: c79d672e-638c-4d87-9b93-edf12ce84a52
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# メソッド &#39;&lt;methodname&gt;&#39; にはリンク確認要求が指定されていますが、このメソッドは、リンク確認要求が指定されていない以下のメソッドをオーバーライドまたは実装します。 セキュリティ ホールが存在する可能性があります。
セキュリティのリンク確認要求アクションがメソッドに追加されました。 ただし、このメソッドはリンク確認要求がないメソッドをオーバーライドまたは実装します。 そのためオーバーライドまたは実装されたメソッドを不十分なアクセス許可で呼び出すことができ、セキュリティ上の問題を引き起こす可能性があります。  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「[Visual Basic での警告の構成](../ide/configuring-warnings-in-visual-basic.md)」を参照してください。  
  
 **エラー ID:** BC42200  
  
### このエラーを解決するには  
  
-   オーバーライドまたは実装されたメソッドにリンク確認要求を追加します。  
  
## 参照  
 [リンク確認要求](../Topic/Link%20Demands.md)   
 [Demand とLinkDemand](http://msdn.microsoft.com/ja-jp/1ab877f2-70f4-4e0d-8116-943999dfe8f5)   
 [セキュリティの最適化](http://msdn.microsoft.com/ja-jp/cf255069-d85d-4de3-914a-e4625215a7c0)