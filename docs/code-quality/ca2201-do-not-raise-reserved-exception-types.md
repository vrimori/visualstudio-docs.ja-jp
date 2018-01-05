---
title: "Ca 2201: 予約済みの例外の種類を発生させません |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotRaiseReservedExceptionTypes
- CA2201
helpviewer_keywords:
- CA2201
- DoNotRaiseReservedExceptionTypes
ms.assetid: dd14ef5c-80e6-41a5-834e-eba8e2eae75e
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 11e00594c1cf279fb6b07791bb48f2222cc9c79b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ca2201-do-not-raise-reserved-exception-types"></a>CA2201: 予約された例外の種類を発生させません
|||  
|-|-|  
|TypeName|DoNotRaiseReservedExceptionTypes|  
|CheckId|CA2201|  
|カテゴリ|Microsoft.Usage|  
|互換性に影響する変更点|あり|  
  
## <a name="cause"></a>原因  
 メソッドは、一般的すぎるか、ランタイムによって予約されている例外の種類を発生させます。  
  
## <a name="rule-description"></a>規則の説明  
 次の例外の種類をユーザーに十分な情報を提供する汎用的なのとおりです。  
  
-   <xref:System.Exception?displayProperty=fullName>  
  
-   <xref:System.ApplicationException?displayProperty=fullName>  
  
-   <xref:System.SystemException?displayProperty=fullName>  
  
 次の例外の種類は予約されていると、共通言語ランタイムによってのみスローされる必要があります。  
  
-   <xref:System.ExecutionEngineException?displayProperty=fullName>  
  
-   <xref:System.IndexOutOfRangeException?displayProperty=fullName>  
  
-   <xref:System.NullReferenceException?displayProperty=fullName>  
  
-   <xref:System.OutOfMemoryException?displayProperty=fullName>  
  
 **汎用的な例外をスローしないでください。**  
  
 など、一般的な例外型をスローするかどうか<xref:System.Exception>または<xref:System.SystemException>コンシューマーすべてをキャッチするように強制ライブラリまたはフレームワークでの処理方法がわからない不明な例外を含む例外。  
  
 代わりに、フレームワークに既に存在するより強い派生型をスローするか作成から派生する独自の型<xref:System.Exception>です。  
  
 **特定の例外をスローします。**  
  
 次の表に、パラメーターおよびプロパティの set アクセサー内で、値パラメーターを含め、パラメーターを検証する場合にスローされる例外。  
  
|パラメーターの説明|例外|  
|---------------------------|---------------|  
|`null`参照|<xref:System.ArgumentNullException?displayProperty=fullName>|  
|(コレクションまたは一覧のインデックス) などの値の許容範囲外|<xref:System.ArgumentOutOfRangeException?displayProperty=fullName>|  
|無効な`enum`値|<xref:System.ComponentModel.InvalidEnumArgumentException?displayProperty=fullName>|  
|メソッドのパラメーターの仕様を満たしていない形式が含まれています (などの書式指定文字列`ToString(String)`)|<xref:System.FormatException?displayProperty=fullName>|  
|それ以外の場合が無効です。|<xref:System.ArgumentException?displayProperty=fullName>|  
  
 操作がオブジェクト throw の現在の状態に対して無効な場合<xref:System.InvalidOperationException?displayProperty=fullName>  
  
 破棄されたオブジェクトで操作が実行されるとスローします。<xref:System.ObjectDisposedException?displayProperty=fullName>  
  
 操作がサポートされていない場合 (など、オーバーライドされた**Stream.Write**読み取り用に開くストリームの) スロー<xref:System.NotSupportedException?displayProperty=fullName>  
  
 スローする変換を実行すると、オーバーフロー (明示的なキャスト演算子のオーバー ロードなど) があるとき<xref:System.OverflowException?displayProperty=fullName>  
  
 その他のすべての状況から派生する独自の型の作成を検討して<xref:System.Exception>をスローします。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するには、予約済みの種類のいずれかではない特定の種類にスローされた例外の種類を変更します。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## <a name="related-rules"></a>関連規則  
 [CA1031: 一般的な例外の種類はキャッチしません](../code-quality/ca1031-do-not-catch-general-exception-types.md)