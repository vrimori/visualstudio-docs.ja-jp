---
title: '1901: P/invoke 宣言はポータブルでは必要があります |Microsoft Docs'
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
- CA1901
- PInvokeDeclarationsShouldBePortable
helpviewer_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
ms.assetid: 90361812-55ca-47f7-bce9-b8775d3b8803
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a44e439ecafaa2e89df8cc93c131dbf2abe2dc30
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49948136"
---
# <a name="ca1901-pinvoke-declarations-should-be-portable"></a>CA1901: P/Invoke 宣言はポータブルでなければなりません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PInvokeDeclarationsShouldBePortable|
|CheckId|CA1901|
|カテゴリ|Microsoft.Portability|
|互換性に影響する変更点|– P/invoke は、アセンブリ外部から参照できる場合。 なし - P/invoke が、アセンブリの外部に表示されない場合|

## <a name="cause"></a>原因
 このルールは、各パラメーターのサイズと、P/invoke の戻り値が評価され、32 ビットおよび 64 ビット プラットフォームでは、アンマネージ コードにマーシャ リングされる場合、サイズが正しいことを確認します。 このルールの最も一般的な違反では、プラットフォームに依存するポインター-サイズの変数が必要になる固定サイズの整数を渡します。

## <a name="rule-description"></a>規則の説明
 このルールに違反している、次のシナリオのいずれかに発生します。

-   戻り値またはパラメーターとして型指定された固定サイズの整数として型指定しなければならないときに、`IntPtr`します。

-   として型指定された戻り値またはパラメーター、`IntPtr`固定サイズの整数としてときに入力する必要があります。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この違反を修正するを使用して`IntPtr`または`UIntPtr`の代わりにハンドルを表す`Int32`または`UInt32`します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この警告を抑制する必要があります。

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

 この例で、`nIconIndex`として宣言されたパラメーター、 `IntPtr`、32 ビット プラットフォームと 8 バイト、64 ビット プラットフォーム上で 4 バイトであります。 次のアンマネージの宣言でことがわかります`nIconIndex`はすべてのプラットフォームで 4 バイト符号なし整数。

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



