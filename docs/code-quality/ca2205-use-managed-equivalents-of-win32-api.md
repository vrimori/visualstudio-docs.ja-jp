---
title: "CA2205: Win32 API に相当するマネージ API を使用します | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UseManagedEquivalentsOfWin32Api"
  - "CA2205"
helpviewer_keywords: 
  - "CA2205"
  - "UseManagedEquivalentsOfWin32Api"
ms.assetid: 1c65ab59-3e50-4488-a727-3969c7f6cbe4
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 13
---
# CA2205: Win32 API に相当するマネージ API を使用します
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UseManagedEquivalentsOfWin32Api|  
|CheckId|CA2205|  
|分類|Microsoft.Usage|  
|互換性に影響する変更点|なし|  
  
## 原因  
 プラットフォーム呼び出しメソッドが定義されましたが、同等の機能を持つメソッドが [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] クラス ライブラリに存在します。  
  
## 規則の説明  
 プラットフォーム呼び出しメソッドは、アンマネージ DLL 関数を呼び出すときに使用されます。また、<xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> 属性 \(Visual Basic では `Declare` キーワード\) を使用して定義されます。  プラットフォーム呼び出しメソッドの定義を誤ると、実行時に例外が発生することがあります。原因は、関数名の誤り、パラメーターと戻り値のデータ型のマッピング エラー、呼び出し規約や文字セットのようなフィールド仕様の誤りなどです。  一般に、可能であれば同等のマネージ メソッドを呼び出す方が、アンマネージ メソッドの定義と呼び出しを直接行うよりも、簡単でミスも少なくなります。  また、プラットフォーム呼び出しメソッドは、その他のセキュリティ問題の原因にもなり、そのための対処が必要です。  
  
## 違反の修正方法  
 この規則違反を修正するには、アンマネージ関数の呼び出しを同等のマネージ関数の呼び出しに置換します。  
  
## 警告を抑制する状況  
 置換できる機能を持つマネージ関数がない場合は、この規則による警告を抑制します。  
  
## 使用例  
 この規則に違反するプラットフォーム呼び出しメソッドの定義を次の例に示します。  また、このプラットフォーム呼び出しメソッドと同等の機能を持つマネージ メソッドも含まれます。  
  
 [!code-cs[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/CSharp/ca2205-use-managed-equivalents-of-win32-api_1.cs)]
 [!code-vb[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/VisualBasic/ca2205-use-managed-equivalents-of-win32-api_1.vb)]  
  
## 関連規則  
 [CA1404: P\/Invoke の直後に GetLastError を呼び出します](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)  
  
 [CA1060: P\/Invoke を NativeMethods クラスに移動します](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)  
  
 [CA1400: P\/Invoke エントリ ポイントは存在しなければなりません](../Topic/CA1400:%20P-Invoke%20entry%20points%20should%20exist.md)  
  
 [CA1401: P\/Invoke は参照可能になりません](../Topic/CA1401:%20P-Invokes%20should%20not%20be%20visible.md)  
  
 [CA2101: P\/Invoke 文字列引数に対してマーシャリングを指定します](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)