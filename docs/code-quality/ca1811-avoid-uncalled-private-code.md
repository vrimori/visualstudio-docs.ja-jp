---
title: "CA1811: 呼び出されていないプライベート コードを使用しません | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AvoidUncalledPrivateCode"
  - "CA1811"
helpviewer_keywords: 
  - "CA1811"
  - "AvoidUncalledPrivateCode"
ms.assetid: aadbba74-7821-475f-8980-34d17c0a0a8b
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 20
---
# CA1811: 呼び出されていないプライベート コードを使用しません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidUncalledPrivateCode|  
|CheckId|CA1811|  
|分類|Microsoft.Performance|  
|互換性に影響する変更点|なし|  
  
## 原因  
 プライベート メンバーまたは内部 \(アセンブリ レベル\) メンバーは、アセンブリ内、共通言語ランタイム、およびデリゲートのいずれからも呼び出されていません。  次のメンバーは、この規則でチェックされません。  
  
-   明示的なインターフェイス メンバー  
  
-   静的コンストラクター  
  
-   シリアル化コンストラクター  
  
-   <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> または <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> でマークされたメソッド  
  
-   オーバーライドのメンバー  
  
## 規則の説明  
 この規則では、規則の論理で識別できないエントリ ポイントがある場合、誤って規則違反が報告されることがあります。  また、コンパイラによって、呼び出すことができないコードがアセンブリに挿入されることもあります。  
  
## 違反の修正方法  
 この規則違反を修正するには、呼び出すことのできないコードを削除するか、そのコードを呼び出すコードを追加します。  
  
## 警告を抑制する状況  
 この規則による警告を抑制しても安全です。  
  
## 関連規則  
 [CA1812: インスタンス化されていない内部クラスを使用しないでください](../Topic/CA1812:%20Avoid%20uninstantiated%20internal%20classes.md)  
  
 [CA1801: 使用されていないパラメーターを再確認します](../Topic/CA1801:%20Review%20unused%20parameters.md)  
  
 [CA1804: 使用されていないローカルを削除します](../code-quality/ca1804-remove-unused-locals.md)