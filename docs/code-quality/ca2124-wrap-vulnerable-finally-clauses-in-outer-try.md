---
title: 'CA2124: 脆弱性のある finally 句の外側を try ブロックでラップします'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
helpviewer_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
ms.assetid: 82efd224-9e60-4b88-a0f5-dfabcc49a254
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 50c03a16af9562df40dc04a431fac157c1321fbb
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47860083"
---
# <a name="ca2124-wrap-vulnerable-finally-clauses-in-outer-try"></a>CA2124: 脆弱性のある finally 句の外側を try ブロックでラップします

|||
|-|-|
|TypeName|WrapVulnerableFinallyClausesInOuterTry|
|CheckId|CA2124|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因
 バージョン 1.0 および 1.1 の .NET Framework では、パブリックまたはプロテクト メソッドを含む、 `try` / `catch` / `finally`ブロックします。 `finally`ブロックをセキュリティの状態をリセットしてで囲まれていない、`finally`ブロックします。

## <a name="rule-description"></a>規則の説明
 このルールでは検索`try` / `finally`をバージョン 1.0 および 1.1 の脆弱性のある悪意のある例外フィルターが呼び出し履歴に存在する可能性がある .NET Framework を対象とするコードをブロックします。 偽装などの機密情報の操作が、try ブロックで発生して、例外がスローされた、フィルターが実行する前に、`finally`ブロックします。 権限借用の使用例、フィルターが権限を借用したユーザーとして実行されていることを意味します。 フィルターは、現在、Visual Basic でのみ実装できます。

> [!NOTE]
> バージョンの .NET Framework 2.0 以降では、ランタイムが自動的に保護する、 `try` / `catch` /  `finally`メソッド内で直接、リセットが発生した場合、悪意のある例外フィルターを禁止します。例外ブロックが含まれています。

## <a name="how-to-fix-violations"></a>違反の修正方法
 配置、ラップされていない`try` / `finally` try ブロックの外側でします。 次の 2 つ目の例を参照してください。 これにより、`finally`フィルター コードの前に実行します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 この規則による警告は抑制しないでください。

## <a name="pseudo-code-example"></a>擬似コードの例

### <a name="description"></a>説明

次の擬似コードでは、このルールにより検出されたパターンを示しています。

```csharp
try {
   // Do some work.
   Impersonator imp = new Impersonator("John Doe");
   imp.AddToCreditCardBalance(100);
}
finally {
   // Reset security state.
   imp.Revert();
}
```

次の擬似コードでは、コードを保護して、このルールを満たすために使用できるパターンを示します。

```csharp
try {
     try {
        // Do some work.
     }
     finally {
        // Reset security state.
     }
}
catch()
{
    throw;
}
```