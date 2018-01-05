---
title: "Ca 1063: 実装 IDisposable 正しく |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ImplementIDisposableCorrectly
- CA1063
helpviewer_keywords:
- CA1063
- ImplementIDisposableCorrectly
ms.assetid: 12afb1ea-3a17-4a3f-a1f0-fcdb853e2359
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 33c9b3d7b3cdcfc49c3fac14e5ba3a2dcfc2fc49
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ca1063-implement-idisposable-correctly"></a>CA1063: IDisposable を正しく実装します
|||  
|-|-|  
|TypeName|ImplementIDisposableCorrectly|  
|CheckId|CA1063|  
|カテゴリ|Microsoft.Design|  
|互換性に影響する変更点|なし|  
  
## <a name="cause"></a>原因  
 `IDisposable`正しく実装されていません。 この問題のいくつかの理由は次のとおりです。  
  
-   IDisposable は、クラスで再実装です。  
  
-   最終処理が再オーバーライドします。  
  
-   Dispose をオーバーライドします。  
  
-   Dispose() がパブリックでないシールされているか、Dispose をという名前です。  
  
-   Dispose (bool) は、保護された、仮想、または封印されていないではありません。  
  
-   封印されていない型で Dispose() が dispose (true) を呼び出す必要があります。  
  
-   Unsealed 型は、最終処理の実装は呼び出しませんいずれかまたは両方の dispose (bool) または大文字のクラスのファイナライザー。  
  
 これらのパターンのいずれかの違反は、この警告をトリガーします。  
  
 すべての封印されていないルート IDisposable 型必要があります手段独自保護された仮想 void dispose (bool) です。 Dispose() Dipose(true) を呼び出す必要があり、Finalize が dispose (false) を呼び出す必要があります。 封印されていないルート IDisposable 型を作成する場合は、dispose (bool) を定義およびそれを呼び出す必要があります。 詳細については、次を参照してください。[アンマネージ リソースのクリーンアップ](/dotnet/standard/garbage-collection/unmanaged)で、 [Framework デザイン ガイドライン](/dotnet/standard/design-guidelines/index)、.NET Framework のドキュメントの「します。  
  
## <a name="rule-description"></a>規則の説明  
 すべての IDisposable 型は、Dispose パターンを適切に実装する必要があります。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 コードをチェックし、この違反が、解決策は次の解決を決定します。  
  
-   {0} によって実装され、代わりに、基底クラス Dispose の実装をオーバーライドするインターフェイスのリストから IDisposable を削除します。  
  
-   {0} 型からファイナライザーを削除、Dispose (bool disposing) をオーバーライドし、'disposing' が false のコード パスに finalization 論理を追加します。  
  
-   {0} 削除、Dispose (bool disposing) をオーバーライドし、'disposing' が true に、コード パスに dispose 論理を入れます。  
  
-   {0} が public および sealed として宣言されていることを確認します。  
  
-   {0} を 'Dispose' の名前を変更し、public および sealed として宣言されているかどうかを確認します。  
  
-   宣言されているように保護されていることを確認して、仮想と封印されていないためです。  
  
-   {0} を変更して、呼び出す dispose (true)、その後、GC を呼び出すようにします。現在のオブジェクト インスタンスで SuppressFinalize ('this' または 'Me' で[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)])、しを返します。  
  
-   {0} を変更して、dispose (false) を呼び出し、を返します。  
  
-   封印されていないルート IDisposable クラスを作成している場合は、IDisposable の実装がここでは、上記のパターンに従うことを確認します。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## <a name="pseudo-code-example"></a>擬似コードの例  
 次の擬似コードは、管理を使用するクラスで dispose (bool) を実装する方法とネイティブ リソースの一般的な例を提供します。  
  
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