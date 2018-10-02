---
title: '1401: P/invoke はなりません表示 |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- PInvokesShouldNotBeVisible
- CA1401
helpviewer_keywords:
- CA1401
- PInvokesShouldNotBeVisible
ms.assetid: 0f4d96c1-f9de-414e-b223-4dc7f691bee3
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8c376c2ae8a1d09ff040d9929617c75037ac5d28
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589226"
---
# <a name="ca1401-pinvokes-should-not-be-visible"></a>CA1401: P/Invoke は参照可能になりません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[CA1401: P/invoke は参照できないように](https://docs.microsoft.com/visualstudio/code-quality/ca1401-p-invokes-should-not-be-visible)します。

|||
|-|-|
|TypeName|PInvokesShouldNotBeVisible|
|CheckId|CA1401|
|カテゴリ|Microsoft.Interoperability|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 パブリック型の public または protected のメソッドには、<xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>属性 (によって実装されることも、`Declare`キーワード[!INCLUDE[vbprvb](../includes/vbprvb-md.md)])。

## <a name="rule-description"></a>規則の説明
 マークされているメソッド、<xref:System.Runtime.InteropServices.DllImportAttribute>属性 (またはを使用して定義されているメソッド、`Declare`キーワード[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) プラットフォーム呼び出しサービスを使用して、アンマネージ コードにアクセスします。 このようなメソッドは公開しないでください。 プライベートまたは内部には、これらのメソッドを保持することで呼び出し元がそれ以外の場合、呼び出しできなかったアンマネージ Api にアクセスできるようにしてセキュリティを侵害するライブラリを使用できないことを確認します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、メソッドのアクセス レベルを変更します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 次の例では、この規則に違反するメソッドを宣言します。

 [!code-csharp[FxCop.Interoperability.DllImports#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DllImports/cs/FxCop.Interoperability.DllImports.cs#1)]
 [!code-vb[FxCop.Interoperability.DllImports#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DllImports/vb/FxCop.Interoperability.DllImports.vb#1)]



