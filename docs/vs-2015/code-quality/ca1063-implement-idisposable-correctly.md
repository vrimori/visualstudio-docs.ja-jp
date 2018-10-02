---
title: 'CA1063: 実装 IDisposable 正しく |Microsoft Docs'
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
- ImplementIDisposableCorrectly
- CA1063
helpviewer_keywords:
- CA1063
- ImplementIDisposableCorrectly
ms.assetid: 12afb1ea-3a17-4a3f-a1f0-fcdb853e2359
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ed6b7832f17a39c145452d0bbfecfbda9be98547
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589130"
---
# <a name="ca1063-implement-idisposable-correctly"></a>CA1063: IDisposable を正しく実装します
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[CA1063: IDisposable の実装正しく](https://docs.microsoft.com/visualstudio/code-quality/ca1063-implement-idisposable-correctly)します。

|||
|-|-|
|TypeName|ImplementIDisposableCorrectly|
|CheckId|CA1063|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 `IDisposable` 正しく実装されていません。 この問題のいくつかの理由を以下に示します。

-   IDisposable は、クラスで再実装します。

-   最終処理が再オーバーライドします。

-   Dispose をオーバーライドします。

-   Dispose() がパブリックではないがシールされているか、Dispose をという名前です。

-   Dispose (bool) は、保護された、仮想、または封印されていないではありません。

-   封印されていない種類は、Dispose() が dispose (true) を呼び出す必要があります。

-   封印されていない型の場合、Finalize 実装は呼び出しませんいずれかまたは両方の dispose (bool) またはケースのクラスのファイナライザー。

 この警告は、これらのパターンのいずれかの違反がトリガーされます。

 すべて封印されていないルート IDisposable 型は、独自プロテクト仮想 void dispose (bool) メソッドを提供する必要があります。 Dispose() Dipose(true) を呼び出す必要があり、Finalize が dispose (false) を呼び出す必要があります。 封印されていないルートの IDisposable 型を作成する場合は、dispose (bool) の定義し、それを呼び出す必要があります。 詳細については、次を参照してください。[アンマネージ リソースのクリーンアップ](http://msdn.microsoft.com/library/a17b0066-71c2-4ba4-9822-8e19332fc213)で、 [Framework デザイン ガイドライン](http://msdn.microsoft.com/library/5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b)、.NET Framework のドキュメントのセクション。

## <a name="rule-description"></a>規則の説明
 すべての IDisposable 型は、Dispose パターンを適切に実装する必要があります。

## <a name="how-to-fix-violations"></a>違反の修正方法
 コードを調べて、この違反を修正する次の解決方法のうちはします。

-   によって実装されるインターフェイスのリストから IDisposable を削除{0}を代わりに、基底クラス Dispose の実装をオーバーライドします。

-   型からファイナライザーを削除{0}Dispose (bool disposing) をオーバーライドし、'disposing' が false のコード パスに finalization 論理を配置します。

-   削除{0}Dispose (bool disposing) をオーバーライドし、'disposing' が true に、コード パスに dispose 論理を入れます。

-   いることを確認{0}は public として宣言され、シールします。

-   名前を変更{0}を 'Dispose' public およびシールドとして宣言されているかどうかを確認します。

-   必ず{0}が保護されを virtual と宣言し、封印されていません。

-   変更{0}GC を呼び出して dispose (true) を呼び出すようにします。オブジェクトの現在のインスタンスで SuppressFinalize ('this' または 'Me' で[!INCLUDE[vbprvb](../includes/vbprvb-md.md)])、しを返します。

-   変更{0}ように dispose (false) を呼び出すし、返します。

-   封印されていないルートの IDisposable クラスを作成する場合は、IDisposable の実装が、このセクションで既に説明したパターンに従うことを確認します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。

## <a name="pseudo-code-example"></a>擬似コードの例
 次の擬似コードでは、管理を使用するクラスで dispose (bool) を実装する方法と、ネイティブ リソースの一般的な例を示します。

```
public class Resource : IDisposable
{
    private IntPtr nativeResource = Marshal.AllocHGlobal(100);
    private AnotherResource managedResource = new AnotherResource();

// Dispose() calls Dispose(true)
    public void Dispose()
    {
        Dispose(true);
        GC.SuppressFinalize(this);
    }
    // NOTE: Leave out the finalizer altogether if this class doesn't
    // own unmanaged resources itself, but leave the other methods
    // exactly as they are.
    ~Resource()
    {
        // Finalizer calls Dispose(false)
        Dispose(false);
    }
    // The bulk of the clean-up code is implemented in Dispose(bool)
    protected virtual void Dispose(bool disposing)
    {
        if (disposing)
        {
            // free managed resources
            if (managedResource != null)
            {
                managedResource.Dispose();
                managedResource = null;
            }
        }
        // free native resources if there are any.
        if (nativeResource != IntPtr.Zero)
        {
            Marshal.FreeHGlobal(nativeResource);
            nativeResource = IntPtr.Zero;
        }
    }
}
```



