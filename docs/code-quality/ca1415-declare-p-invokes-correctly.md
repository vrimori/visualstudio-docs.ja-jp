---
title: "CA1415: P/Invoke を正しく宣言します | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1415"
  - "DeclarePInvokesCorrectly"
helpviewer_keywords: 
  - "CA1415"
  - "DeclarePInvokesCorrectly"
ms.assetid: 42a90796-0264-4460-bf97-2fb4a093dfdc
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1415: P/Invoke を正しく宣言します
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DeclarePInvokesCorrectly|  
|CheckId|CA1415|  
|分類|Microsoft.Interoperability|  
|互換性に影響する変更点|なし \- パラメーターを宣言する P\/Invoke がアセンブリの外部で参照できない場合  あり \- パラメーターを宣言する P\/Invoke がアセンブリの外部で参照できる場合|  
  
## 原因  
 プラットフォーム呼び出しメソッドの宣言が正しくありません。  
  
## 規則の説明  
 プラットフォーム呼び出しメソッドは、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] の `Declare` キーワードまたは <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> を使用して、アンマネージ コードにアクセスし、定義されます。  現在この規則では、OVERLAPPED 構造体パラメーターへのポインターを持ち、対応するマネージ型パラメーターが <xref:System.Threading.NativeOverlapped?displayProperty=fullName> 構造体へのポインターではない Win32 関数に対するプラットフォーム呼び出しメソッドが対象になります。  
  
## 違反の修正方法  
 この規則違反を修正するには、プラットフォーム呼び出しメソッドを正しく宣言します。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## 使用例  
 規則に違反するプラットフォーム呼び出しメソッドと、規則を満たすプラットフォーム呼び出しメソッドを次の例に示します。  
  
 [!CODE [FxCop.Interoperability.DeclarePInvokes#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DeclarePInvokes#1)]  
  
## 参照  
 [アンマネージ コードとの相互運用](../Topic/Interoperating%20with%20Unmanaged%20Code.md)