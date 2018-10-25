---
title: 'Ca 2139: 透過的メソッドは、HandleProcessCorruptingExceptions 属性を使用して可能性がありますされません |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2139
ms.assetid: 45a0328a-add7-40f9-8934-dff59beb02b3
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b7780698296815da73b9862b586bc256a87f7d42
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49827062"
---
# <a name="ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute"></a>CA2139: 透過的メソッドは、HandleProcessCorruptingExceptions 属性を使用してはならない
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TransparentMethodsMustNotHandleProcessCorruptingExceptions|
|CheckId|CA2139|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 透過的なメソッドが設定されて、<xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>属性。

## <a name="rule-description"></a>規則の説明
 この規則は、透過的なは、破損状態例外を使用して、プロセスを処理しようとする任意のメソッド、<xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>属性。 プロセス破損状態例外は、このような例外の CLR バージョン 4.0 例外分類<xref:System.AccessViolationException>します。 HandleProcessCorruptedStateExceptionsAttribute 属性はセキュリティ クリティカルなメソッドでのみ使用できる属性で、透過的メソッドに適用された場合は無視されます。 プロセス破損状態例外を処理するには、このメソッドは必要がありますセキュリティ クリティカルまたはセキュリティ セーフ クリティカルになります。

## <a name="how-to-fix-violations"></a>違反の修正方法
 このルールの違反を修正するには、削除、<xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>属性、または、メソッド、<xref:System.Security.SecurityCriticalAttribute>または<xref:System.Security.SecuritySafeCriticalAttribute>属性。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 この例では、透過的メソッドはでマークされた、<xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>属性し、ルールは失敗します。 メソッドをマークする必要がありますも、<xref:System.Security.SecurityCriticalAttribute>または<xref:System.Security.SecuritySafeCriticalAttribute>属性。

 [!code-csharp[FxCop.Security.CA2139.TransparentMethodsMustNotHandleProcessCorruptingExceptions#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2139.transparentmethodsmustnothandleprocesscorruptingexceptions/cs/ca2139 - transparentmethodsmustnothandleprocesscorruptingexceptions.cs#1)]



