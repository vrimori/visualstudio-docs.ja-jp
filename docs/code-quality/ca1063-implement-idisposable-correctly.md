---
title: "CA1063: IDisposable を正しく実装します | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ImplementIDisposableCorrectly"
  - "CA1063"
helpviewer_keywords: 
  - "CA1063"
  - "ImplementIDisposableCorrectly"
ms.assetid: 12afb1ea-3a17-4a3f-a1f0-fcdb853e2359
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1063: IDisposable を正しく実装します
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ImplementIDisposableCorrectly|  
|CheckId|CA1063|  
|分類|Microsoft.Design|  
|互換性に影響する変更点|なし|  
  
## 原因  
 `IDisposable` が適切に実装されていません。  この問題の発生には次のような原因があります。  
  
-   IDisposable がクラスに再実装されている。  
  
-   Finalize が再オーバーライドされている。  
  
-   Dispose がオーバーライドされている。  
  
-   Dispose\(\) がパブリックでないか、シールされているか、または名前付き Dispose である。  
  
-   Dispose\(bool\) が保護されていないか、仮想であるか、またはシールされていない。  
  
-   シールされていない型では、Dispose\(\) は Dispose\(true\) を呼び出す必要がある。  
  
-   シールされていない型の場合、Finalize 実装は、Dispose\(bool\) とケース クラス ファイナライザーを呼び出さない。  
  
 これらのパターンのいずれかに違反すると、この警告が生成されます。  
  
 シールされていないルート IDisposable 型は、固有の保護された仮想 void Dispose\(bool\) メソッドを提供する必要があります。  Dispose\(\) は Dipose\(true\) を呼び出す必要があり、Finalize は Dispose\(false\) を呼び出す必要があります。  シールされていないルート IDisposable 型を作成する場合は、Dispose\(bool\) を定義して呼び出す必要があります。  詳細については、.NET Framework ドキュメントの「[Framework デザイン ガイドライン](../Topic/Framework%20Design%20Guidelines.md)」セクションにある「[Cleaning Up Unmanaged Resources](../Topic/Cleaning%20Up%20Unmanaged%20Resources.md)」を参照してください。  
  
## 規則の説明  
 すべての IDisposable 型は、Dispose パターンを適切に実装する必要があります。  
  
## 違反の修正方法  
 コードを調べて、この違反を適切に修正するために次のどの解決法を選択するかを決めてください。  
  
-   {0} によって実装されたインターフェイスのリストから IDisposable を削除して、代わりに基本クラスの Dispose 実装をオーバーライドする。  
  
-   ファイナライザーを型 {0} から削除し、Dispose\(bool disposing\) をオーバーライドして、'disposing' が false であるコード パスに終了ロジックを配置する。  
  
-   {0} を削除し、Dispose\(bool disposing\) をオーバーライドして、'disposing' が true であるコード パスに破棄ロジックを配置する。  
  
-   {0} がパブリックとして、およびシールされているものとして宣言されていることを確認する。  
  
-   {0} の名前を 'Dispose' に変更し、パブリックとして、およびシールされているものとして宣言されていることを確認する。  
  
-   {0} が保護され、仮想であり、およびシールされていないものとして宣言されていることを確認する。  
  
-   Dispose\(true\) を呼び出し、次に GC.SuppressFinalize を現在のオブジェクト インスタンス \([!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] では 'this' または 'Me'\) で呼び出してから戻るように、{0} を変更する。  
  
-   Dispose\(false\) を呼び出してから戻るように、{0} を変更する。  
  
-   シールされていないルート IDisposable クラスを記述する場合は、IDisposable の実装が前述のパターンに従うように確認する。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## 擬似コードの例  
 次の擬似コードは、マネージ リソースおよびネイティブ リソースを使用するクラスに Dispose\(bool\) を実装する方法を示す一般的な例です。  
  
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