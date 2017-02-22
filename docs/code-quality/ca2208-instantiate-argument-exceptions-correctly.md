---
title: "CA2208: 引数の例外を正しくインスタンス化します | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2208"
  - "InstantiateArgumentExceptionsCorrectly"
helpviewer_keywords: 
  - "CA2208"
  - "InstantiateArgumentExceptionsCorrectly"
ms.assetid: e2a48939-d9fa-478c-b2f9-3bdbce07dff7
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2208: 引数の例外を正しくインスタンス化します
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|InstantiateArgumentExceptionsCorrectly|  
|CheckId|CA2208|  
|分類|Microsoft.Usage|  
|互換性に影響する変更点|なし|  
  
## 原因  
 考えられる原因には次の場合があります。  
  
-   [System.ArgumentException](assetId:///System.ArgumentException?qualifyHint=True&autoUpgrade=True)、またはそのクラスから派生した例外の種類の、既定 \(パラメーターなし\) のコンストラクターに対して呼び出しが行われました。  
  
-   [System.ArgumentException.](assetId:///System.ArgumentException.?qualifyHint=True&autoUpgrade=True)、またはそのクラスから派生した例外の種類の、パラメーター付きのコンストラクターに不適切な文字列型の引数が渡されました。  
  
## 規則の説明  
 既定のコンストラクターを呼び出す代わりに、より意味のある例外メッセージを表示できるコンストラクターのオーバーロードを呼び出します。  例外メッセージは開発者を対象にし、エラー条件、例外の修正方法、および例外の回避方法が明確にわかるようにします。  
  
 <xref:System.ArgumentException> および派生型の、文字列型の引数が 1 つまたは 2 つである文字列コンストラクターのシグネチャは、`message` パラメーターと `paramName` パラメーターに関して整合性が取れていません。  このようなコンストラクターは、正しい文字列型の引数で呼び出すようにします。  次のようなシグネチャがあります。  
  
 <xref:System.ArgumentException>\(string `message`\)  
  
 <xref:System.ArgumentException>\(string `message`, string `paramName`\)  
  
 <xref:System.ArgumentNullException>\(string `paramName`\)  
  
 <xref:System.ArgumentNullException>\(string `paramName`, string `message`\)  
  
 <xref:System.ArgumentOutOfRangeException>\(string `paramName`\)  
  
 <xref:System.ArgumentOutOfRangeException>\(string `paramName`, string `message`\)  
  
 <xref:System.DuplicateWaitObjectException>\(string `parameterName`\)  
  
 <xref:System.DuplicateWaitObjectException>\(string `parameterName`, string `message`\)  
  
## 違反の修正方法  
 この規則違反を修正するには、メッセージ、パラメーター名、またはその両方を使用するコンストラクターを呼び出し、呼び出される <xref:System.ArgumentException> の型に適した引数を指定します。  
  
## 警告を抑制する状況  
 パラメーター付きのコンストラクターが正しい文字列型の引数で呼び出される場合のみ、この規則による警告を抑制しても安全です。  
  
## 使用例  
 ArgumentNullException 型のインスタンスを正しくインスタンス化していないコンストラクターの例を次に示します。  
  
 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_1.cpp)]
 [!code-cs[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_1.cs)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_1.vb)]  
  
## 使用例  
 コンストラクター引数を変更することによって上の違反を修正するコード例を次に示します。  
  
 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_2.cpp)]
 [!code-cs[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_2.cs)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_2.vb)]