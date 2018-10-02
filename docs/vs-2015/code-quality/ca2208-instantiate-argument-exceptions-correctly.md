---
title: '2208: が引数の例外を正しくインスタンス化 |Microsoft Docs'
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
- CA2208
- InstantiateArgumentExceptionsCorrectly
helpviewer_keywords:
- InstantiateArgumentExceptionsCorrectly
- CA2208
ms.assetid: e2a48939-d9fa-478c-b2f9-3bdbce07dff7
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ba99cddfe42e1b6699dba4fa665302581aa68cdc
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591935"
---
# <a name="ca2208-instantiate-argument-exceptions-correctly"></a>CA2208: 引数の例外を正しくインスタンス化します
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[CA2208: 引数の例外を正しくインスタンス化します。](https://docs.microsoft.com/visualstudio/code-quality/ca2208-instantiate-argument-exceptions-correctly)します。

|||
|-|-|
|TypeName|InstantiateArgumentExceptionsCorrectly|
|CheckId|CA2208|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因
 考えられる原因は、次の状況を含めます。

-   または、[System.ArgumentException] から派生した例外の種類の既定の (パラメーターなしの) コンス トラクターの呼び出し (<!-- TODO: review code entity reference <xref:assetId:///System.ArgumentException?qualifyHint=True&amp;autoUpgrade=True>  -->)。

-   または、[System.ArgumentException。] から派生した例外の種類のパラメーター化されたコンス トラクターに無効な文字列引数を渡す(<!-- TODO: review code entity reference <xref:assetId:///System.ArgumentException.?qualifyHint=True&amp;autoUpgrade=True>  -->)

## <a name="rule-description"></a>規則の説明
 既定のコンス トラクターを呼び出す代わりには、によりより意味のある例外メッセージを指定するコンス トラクターのオーバー ロードのいずれかを呼び出します。 例外メッセージは、開発者を対象し、明確に、エラー条件および修正するか、例外を回避する方法を説明する必要があります。

 1 つまたは複数の文字列のコンス トラクターのシグネチャ<xref:System.ArgumentException>、その派生型を一貫していない、`message`と`paramName`パラメーター。 これらのコンス トラクターが正しい文字列引数を使用して呼び出されることを確認します。 署名は次のとおりです。

 <xref:System.ArgumentException>(文字列`message`)

 <xref:System.ArgumentException>(文字列`message`、文字列`paramName`)

 <xref:System.ArgumentNullException>(文字列`paramName`)

 <xref:System.ArgumentNullException>(文字列`paramName`、文字列`message`)

 <xref:System.ArgumentOutOfRangeException>(文字列`paramName`)

 <xref:System.ArgumentOutOfRangeException>(文字列`paramName`、文字列`message`)

 <xref:System.DuplicateWaitObjectException>(文字列`parameterName`)

 <xref:System.DuplicateWaitObjectException>(文字列`parameterName`、文字列`message`)

## <a name="how-to-fix-violations"></a>違反の修正方法
 このルールの違反を修正するには、メッセージ、パラメーター名、またはその両方を受け取るコンス トラクターを呼び出すし、引数が型の適切なことを確認<xref:System.ArgumentException>が呼び出されます。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 パラメーター化されたコンス トラクターが正しい文字列引数で呼び出された場合にのみ、この規則による警告を抑制するのには安全です。

## <a name="example"></a>例
 次の例では、ArgumentNullException 型のインスタンスを正しくインスタンス化するコンス トラクターを示します。

 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cpp/FxCop.Usage.InheritedPublic.cpp#1)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cs/FxCop.Usage.InheritedPublic.cs#1)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/vb/FxCop.Usage.InstantiateArgumentExceptionsCorrectly.vb#1)]

## <a name="example"></a>例
 次の例では、コンス トラクターの引数の切り替えを上記の違反を修正します。

 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cpp/FxCop.Usage.InheritedPublic.cpp#2)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cs/FxCop.Usage.InheritedPublic.cs#2)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/vb/FxCop.Usage.InstantiateArgumentExceptionsCorrectly.vb#2)]



