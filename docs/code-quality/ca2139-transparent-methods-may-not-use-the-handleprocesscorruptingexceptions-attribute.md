---
title: 'CA2139: 透過的メソッドは、HandleProcessCorruptingExceptions 属性を使用してはならない'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2139
ms.assetid: 45a0328a-add7-40f9-8934-dff59beb02b3
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f10eca96b9a55d6dfd8d5550bcf7b2d5c08a1a5b
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute"></a>CA2139: 透過的メソッドは、HandleProcessCorruptingExceptions 属性を使用してはならない
|||
|-|-|
|TypeName|TransparentMethodsMustNotHandleProcessCorruptingExceptions|
|CheckId|CA2139|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 透過的なメソッドが付いて、<xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>属性。

## <a name="rule-description"></a>規則の説明
 この規則は、透過的し、プロセスを使用して、破損状態例外を処理しようとしています。 すべてのメソッド、<xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>属性。 プロセス破損状態例外は、このような例外の CLR バージョン 4.0 例外分類<xref:System.AccessViolationException>です。 HandleProcessCorruptedStateExceptionsAttribute 属性はセキュリティ クリティカルなメソッドでのみ使用できる属性で、透過的メソッドに適用された場合は無視されます。 プロセス破損状態例外を処理するには、このメソッドは必要がありますセキュリティ クリティカルまたはセキュリティ上安全-重要になります。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を解決するには、削除、<xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>属性、またはを使用してメソッドをマーク、<xref:System.Security.SecurityCriticalAttribute>または<xref:System.Security.SecuritySafeCriticalAttribute>属性。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 この例では、透過的メソッドが付いて、<xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>属性があり、規則は失敗します。 メソッドをマークする必要がありますも、<xref:System.Security.SecurityCriticalAttribute>または<xref:System.Security.SecuritySafeCriticalAttribute>属性。

 [!code-csharp[FxCop.Security.CA2139.TransparentMethodsMustNotHandleProcessCorruptingExceptions#1](../code-quality/codesnippet/CSharp/ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute_1.cs)]