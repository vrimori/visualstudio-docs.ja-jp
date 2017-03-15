---
title: "CA2232: Windows フォームのエントリ ポイントを STAThread に設定します | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MarkWindowsFormsEntryPointsWithStaThread"
  - "CA2232"
helpviewer_keywords: 
  - "CA2232"
  - "MarkWindowsFormsEntryPointsWithStaThread"
ms.assetid: a3c95130-8e7f-4419-9fcd-b67d077e8efb
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA2232: Windows フォームのエントリ ポイントを STAThread に設定します
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkWindowsFormsEntryPointsWithStaThread|  
|CheckId|CA2232|  
|分類|Microsoft.Usage|  
|互換性に影響する変更点|なし|  
  
## 原因  
 アセンブリが <xref:System.Windows.Forms> 名前空間を参照し、そのエンド ポイントが <xref:System.STAThreadAttribute?displayProperty=fullName> 属性でマークされていません。  
  
## 規則の説明  
 <xref:System.STAThreadAttribute> は、アプリケーションの COM スレッド処理モデルがシングルスレッド アパートメントであることを示します。  この属性は、Windows フォームを使用するすべてのアプリケーションのエントリ ポイントに指定する必要があります。省略すると、Windows コンポーネントが正常に機能しないことがあります。  属性がない場合、アプリケーションではマルチスレッドのアパートメント モデルを使用します。このモデルは、Windows フォームでサポートされていません。  
  
> [!NOTE]
>  アプリケーション フレームワークを使用する [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] プロジェクトでは、**Main** メソッドを STAThread でマークする必要はありません。  [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] コンパイラで自動的に行われます。  
  
## 違反の修正方法  
 この規則違反を修正するには、エントリ ポイントに <xref:System.STAThreadAttribute> 属性を追加します。  <xref:System.MTAThreadAttribute?displayProperty=fullName> 属性がある場合、削除します。  
  
## 警告を抑制する状況  
 <xref:System.STAThreadAttribute> 属性が不要でサポートされていない、.NET Compact Framework 向けに開発している場合、この規則による警告を抑制しても安全です。  
  
## 使用例  
 <xref:System.STAThreadAttribute> の正しい使用方法を次の例に示します。  
  
 [!code-cs[FxCop.Usage.StaThread#1](../code-quality/codesnippet/CSharp/ca2232-mark-windows-forms-entry-points-with-stathread_1.cs)]
 [!code-vb[FxCop.Usage.StaThread#1](../code-quality/codesnippet/VisualBasic/ca2232-mark-windows-forms-entry-points-with-stathread_1.vb)]