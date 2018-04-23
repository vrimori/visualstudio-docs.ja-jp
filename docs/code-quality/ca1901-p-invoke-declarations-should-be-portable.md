---
title: 'Ca 1901: プラットフォーム呼び出しの宣言はポータブルでなければなりません'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
helpviewer_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
ms.assetid: 90361812-55ca-47f7-bce9-b8775d3b8803
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 45adbedf9318c70b1e73088765cf5487d997d1e3
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="ca1901-pinvoke-declarations-should-be-portable"></a>CA1901: P/Invoke 宣言はポータブルでなければなりません
|||
|-|-|
|TypeName|PInvokeDeclarationsShouldBePortable|
|CheckId|CA1901|
|カテゴリ|Microsoft.Portability|
|互換性に影響する変更点|–、P/invoke は、アセンブリ外部から参照できる場合です。 なし -、P/invoke がアセンブリの外側に表示されていない場合。|

## <a name="cause"></a>原因
 このルールは、各パラメーターのサイズ、P/invoke の戻り値を評価し、32 ビットおよび 64 ビット プラットフォームでは、アンマネージ コードにマーシャ リングされる場合、そのサイズが正しいことを確認します。 このルールの最も一般的な違反では、プラットフォームに依存し、ポインター サイズの変数が必要な場所に固定サイズの整数を渡します。

## <a name="rule-description"></a>規則の説明
 このルールに違反する次のシナリオのいずれかが発生します。

-   戻り値またはパラメーターとして型指定された固定サイズの整数として型指定しなければならないときに、`IntPtr`です。

-   戻り値またはパラメーターとして型指定されて、`IntPtr`固定サイズの整数としてときに入力する必要があります。

## <a name="how-to-fix-violations"></a>違反の修正方法
 使用してこの違反を修正する`IntPtr`または`UIntPtr`の代わりにハンドルを表す`Int32`または`UInt32`です。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この警告は抑制しないでください。

## <a name="example"></a>例
 次の例では、この規則違反を示します。

```csharp
internal class NativeMethods
{
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]
    internal static extern IntPtr ExtractIcon(IntPtr hInst,
        string lpszExeFileName, IntPtr nIconIndex);
}
```

 この例では、`nIconIndex`として宣言されたパラメーター、 `IntPtr`、これは、32 ビット プラットフォームと 64 ビット プラットフォームで 8 バイトに 4 バイト。 宣言では、アンマネージに続くことがわかります`nIconIndex`は、すべてのプラットフォームで 4 バイト符号なし整数。

```csharp
HICON ExtractIcon(HINSTANCE hInst, LPCTSTR lpszExeFileName,
    UINT nIconIndex);
```

## <a name="example"></a>例
 違反を修正するには、宣言を次のように変更します。

```csharp
internal class NativeMethods{
    [DllImport("shell32.dll", CharSet=CharSet.Auto)] 
    internal static extern IntPtr ExtractIcon(IntPtr hInst,
        string lpszExeFileName, uint nIconIndex);
}
```

## <a name="see-also"></a>関連項目
 [Portability Warnings](../code-quality/portability-warnings.md)