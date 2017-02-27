---
title: "CA2222: 継承されたメンバーの参照範囲を縮小しません | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotDecreaseInheritedMemberVisibility"
  - "CA2222"
helpviewer_keywords: 
  - "CA2222"
  - "DoNotDecreaseInheritedMemberVisibility"
ms.assetid: 066c8675-381f-43cc-956c-d757cc494028
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 14
---
# CA2222: 継承されたメンバーの参照範囲を縮小しません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotDecreaseInheritedMemberVisibility|  
|CheckId|CA2222|  
|分類|Microsoft.Usage|  
|互換性に影響する変更点|なし|  
  
## 原因  
 シールされていない型のプライベート メソッドに、基本型で宣言されたパブリック メソッドと同一のシグネチャがあります。  プライベート メソッドは final ではありません。  
  
## 規則の説明  
 継承メンバーのアクセス修飾子は変更しないでください。  継承メンバーをプライベートに変更しても、呼び出し元はメソッドの基本クラスの実装にアクセスできます。  メンバーをプライベートにして型をシールしない場合、型の継承によって、継承階層で最後に当たるメソッドのパブリック実装が呼び出される可能性があります。  アクセス修飾子を変更する必要がある場合、メソッドを final とマークするか、型をシールして、メソッドがオーバーライドされないようにします。  
  
## 違反の修正方法  
 この規則違反を修正するには、アクセスをプライベート以外に変更します。  または、プログラミング言語でサポートされていれば、メソッドを final にします。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## 使用例  
 この規則に違反する型を次の例に示します。  
  
 [!code-vb[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/VisualBasic/ca2222-do-not-decrease-inherited-member-visibility_1.vb)]
 [!code-cs[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/CSharp/ca2222-do-not-decrease-inherited-member-visibility_1.cs)]