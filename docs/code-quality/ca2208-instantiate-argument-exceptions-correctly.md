---
title: 'CA2208: 引数の例外を正しくインスタンス化します'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2208
- InstantiateArgumentExceptionsCorrectly
helpviewer_keywords:
- InstantiateArgumentExceptionsCorrectly
- CA2208
ms.assetid: e2a48939-d9fa-478c-b2f9-3bdbce07dff7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cc4a13746182136e10cb550bb7235a8bad2528fd
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31919128"
---
# <a name="ca2208-instantiate-argument-exceptions-correctly"></a>CA2208: 引数の例外を正しくインスタンス化します
|||
|-|-|
|TypeName|InstantiateArgumentExceptionsCorrectly|
|CheckId|CA2208|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因
 考えられる原因には、次の状況が含まれます。

-   かから派生する例外の種類の既定の (パラメーターなし) コンス トラクターの呼び出しが行われた<xref:System.ArgumentException>です。

-   またはから派生される例外の型のパラメーター化されたコンス トラクターに不適切な文字列引数を渡す<xref:System.ArgumentException>です。

## <a name="rule-description"></a>規則の説明
 既定のコンス トラクターを呼び出す代わりに提供する意味のある例外メッセージは、コンス トラクターのオーバー ロードのいずれかを呼び出します。 例外メッセージは、開発者を対象し、エラー条件および修正するか、例外を回避する方法を明確に説明する必要があります。

 1 つと 2 つの文字列のコンス トラクターのシグネチャ<xref:System.ArgumentException>その派生型はに関して一貫していない、`message`と`paramName`パラメーター。 これらのコンス トラクターは、正しい文字列引数で呼び出されることを確認してください。 シグネチャは次のとおりです。

 <xref:System.ArgumentException>(文字列`message`)

 <xref:System.ArgumentException>(文字列`message`、文字列`paramName`)

 <xref:System.ArgumentNullException>(文字列`paramName`)

 <xref:System.ArgumentNullException>(文字列`paramName`、文字列`message`)

 <xref:System.ArgumentOutOfRangeException>(文字列`paramName`)

 <xref:System.ArgumentOutOfRangeException>(文字列`paramName`、文字列`message`)

 <xref:System.DuplicateWaitObjectException>(文字列`parameterName`)

 <xref:System.DuplicateWaitObjectException>(文字列`parameterName`、文字列`message`)

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、メッセージ、パラメーター名、またはその両方を受け取るコンス トラクターを呼び出すし、引数が型の適切なことを確認<xref:System.ArgumentException>呼び出されています。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 正しい文字列引数でパラメーター化されたコンス トラクターが呼び出された場合にのみこの規則による警告を抑制しても安全です。

## <a name="example"></a>例
 次の例では、ArgumentNullException 型のインスタンスを正しくインスタンス化するコンス トラクターを示します。

 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_1.cpp)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_1.cs)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_1.vb)]

## <a name="example"></a>例
 次の例では、コンス トラクターの引数を切り替えることで、上記の違反を修正します。

 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_2.cpp)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_2.cs)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_2.vb)]