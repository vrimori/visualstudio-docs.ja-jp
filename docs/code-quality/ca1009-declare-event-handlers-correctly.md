---
title: "CA1009: イベント ハンドラーを正しく宣言します | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1009"
  - "DeclareEventHandlersCorrectly"
helpviewer_keywords: 
  - "CA1009"
  - "DeclareEventHandlersCorrectly"
ms.assetid: ab65c471-1449-49d2-9896-7b9af74284b4
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# CA1009: イベント ハンドラーを正しく宣言します
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DeclareEventHandlersCorrectly|  
|CheckId|CA1009|  
|分類|Microsoft.Design|  
|互換性に影響する変更点|あり|  
  
## 原因  
 パブリック イベントまたはプロテクト イベントを処理するデリゲートに、適切なシグネチャ、戻り値の型、またはパラメーター名がありません。  
  
## 規則の説明  
 イベント ハンドラー メソッドでは 2 つのパラメーターを使用します。  1 つ目は <xref:System.Object?displayProperty=fullName> 型で、"sender" という名前です。  これは、イベントを発生させるオブジェクトです。  2 つ目は <xref:System.EventArgs?displayProperty=fullName> 型で、"e" という名前です。  これは、イベントに関連付けられるデータです。  たとえば、ファイルが開かれるたびにイベントが発生する場合、一般に、イベント データにはファイル名が含まれます。  
  
 イベント ハンドラー メソッドでは値を返さないでください。  C\# プログラミング言語では、これは戻り値の型 `void` で示されます。  イベント ハンドラーは、複数のオブジェクトで複数のメソッドを呼び出すことができます。  メソッドで値を返すことが許可された場合、イベントごとに複数の値が返り、呼び出された最後のメソッドの値のみが使用できるようになります。  
  
## 違反の修正方法  
 この規則違反を修正するには、デリゲートのシグネチャ、戻り値の型、またはパラメーター名を正しく指定します。  詳細については、以下の例を参照してください。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## 使用例  
 イベント処理に適したデリゲートを次の例に示します。  このイベント ハンドラーで呼び出せるメソッドは、デザイン ガイドラインで指定したシグネチャに一致します。  `AlarmEventHandler` はデリゲートの型名です。  `AlarmEventArgs` はイベント データの基本クラス <xref:System.EventArgs> から派生し、警告イベント データを保持します。  
  
 [!code-cpp[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/CPP/ca1009-declare-event-handlers-correctly_1.cpp)]
 [!code-cs[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/CSharp/ca1009-declare-event-handlers-correctly_1.cs)]
 [!code-vb[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/VisualBasic/ca1009-declare-event-handlers-correctly_1.vb)]  
  
## 関連規則  
 [CA2109: 表示するイベント ハンドラーを確認します](../code-quality/ca2109-review-visible-event-handlers.md)  
  
## 参照  
 <xref:System.EventArgs?displayProperty=fullName>   
 <xref:System.Object?displayProperty=fullName>   
 [イベントとデリゲート](http://msdn.microsoft.com/ja-jp/d98fd58b-fa4f-4598-8378-addf4355a115)