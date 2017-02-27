---
title: "CA2201: 予約された例外の種類を発生させません | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotRaiseReservedExceptionTypes"
  - "CA2201"
helpviewer_keywords: 
  - "CA2201"
  - "DoNotRaiseReservedExceptionTypes"
ms.assetid: dd14ef5c-80e6-41a5-834e-eba8e2eae75e
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA2201: 予約された例外の種類を発生させません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotRaiseReservedExceptionTypes|  
|CheckId|CA2201|  
|分類|Microsoft.Usage|  
|互換性に影響する変更点|あり|  
  
## 原因  
 メソッドによって、汎用的すぎる例外の種類、またはランタイムによって予約されている例外の種類が発生しています。  
  
## 規則の説明  
 次の例外の種類は汎用的すぎて、ユーザーに与える情報が不十分です。  
  
-   <xref:System.Exception?displayProperty=fullName>  
  
-   <xref:System.ApplicationException?displayProperty=fullName>  
  
-   <xref:System.SystemException?displayProperty=fullName>  
  
 次の例外の種類は共通言語ランタイムによって予約済みであり、共通言語ランタイムのみがスローします。  
  
-   <xref:System.ExecutionEngineException?displayProperty=fullName>  
  
-   <xref:System.IndexOutOfRangeException?displayProperty=fullName>  
  
-   <xref:System.NullReferenceException?displayProperty=fullName>  
  
-   <xref:System.OutOfMemoryException?displayProperty=fullName>  
  
 **汎用的な例外をスローしないでください**  
  
 ライブラリまたはフレームワークの <xref:System.Exception> や <xref:System.SystemException> などの汎用的な例外の種類をスローする場合、コンシューマーは、処理方法のわからない不明な例外を含むすべての例外をキャッチするよう強制されます。  
  
 代わりに、フレームワーク内の既存の派生型をスローするか、または <xref:System.Exception> から派生する独自の型を作成してください。  
  
 **特定の例外をスローします**  
  
 次の表は、パラメーターおよびパラメーターの検証時にスローする例外を示しています。プロパティの set アクセサーの値パラメーターも記載されています。  
  
|パラメーターの説明|Exception|  
|---------------|---------------|  
|`null` 参照|<xref:System.ArgumentNullException?displayProperty=fullName>|  
|有効値の範囲外 \(コレクションまたは一覧のインデックスなど\)|<xref:System.ArgumentOutOfRangeException?displayProperty=fullName>|  
|無効な `enum` 値|<xref:System.ComponentModel.InvalidEnumArgumentException?displayProperty=fullName>|  
|メソッドのパラメーターの仕様に一致していない書式 \(`ToString(String)` の書式文字列など\) が含まれます。|<xref:System.FormatException?displayProperty=fullName>|  
|それ以外の場合は無効|<xref:System.ArgumentException?displayProperty=fullName>|  
  
 オブジェクトの現在の状態に対して操作が無効な場合    <xref:System.InvalidOperationException?displayProperty=fullName> をスローします。  
  
 破棄されたオブジェクトで操作が実行される場合    <xref:System.ObjectDisposedException?displayProperty=fullName> をスローします。  
  
 操作がサポートされない場合 \(読み取り用として開かれたストリームのオーバーライドされた **Stream.Write** など\)    <xref:System.NotSupportedException?displayProperty=fullName> をスローします。  
  
 変換によってオーバーフローが発生する場合 \(明示的なキャスト演算子のオーバーロードなど\)    <xref:System.OverflowException?displayProperty=fullName> スローします。  
  
 その他のすべての状況では、<xref:System.Exception> から派生する独自の型の作成を検討し、その型をスローしてください。  
  
## 違反の修正方法  
 この規則違反を修正するには、スローされる例外の種類を、予約済みの種類ではない特定の種類に変更します。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## 関連規則  
 [CA1031: 一般的な例外の種類はキャッチしません](../Topic/CA1031:%20Do%20not%20catch%20general%20exception%20types.md)