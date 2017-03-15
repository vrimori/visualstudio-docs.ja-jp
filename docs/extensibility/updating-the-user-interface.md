---
title: "ユーザー インターフェイスの更新 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ユーザー インターフェイスの更新"
  - "UI の更新コマンド"
ms.assetid: 376e2f56-e7bf-4e62-89f5-3dada84a404b
caps.latest.revision: 41
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 41
---
# ユーザー インターフェイスの更新
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

コマンドを実装した後は、新しいコマンドの状態で、ユーザー インターフェイスを更新するコードを追加できます。  
  
 典型的な Win32 アプリケーションでコマンド セットを継続的にポーリングしてユーザーを閲覧して、個々 のコマンドの状態を調整することができます。 ただし、あるため、 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] シェルが vspackages にある数は無制限をホストできる、特にマネージ コードと COM の間で相互運用機能アセンブリにまたがってポーリングの応答性の減少が広範なポーリング  
  
### UI を更新するには  
  
1.  次のいずれかの操作を実行します。  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> メソッドを呼び出します。  
  
         <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> からインターフェイスを取得できます、 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> サービスを次のようにします。  
  
        ```c#  
        void UpdateUI(Microsoft.VisualStudio.Shell.ServiceProvider sp)  
        {  
            IVsUIShell vsShell = (IVsUIShell)sp.GetService(typeof(IVsUIShell));  
            if (vsShell != null)  
            {  
                int hr = vsShell.UpdateCommandUI(0);  
                Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr);  
            }  
        }  
  
        ```  
  
         場合のパラメーター、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> ゼロ以外 \(`TRUE`\)、同期と、すぐに更新プログラムが実行されます。 0 を渡すことをお勧め \(`FALSE`\) 適切なパフォーマンスを維持するためには、このパラメーターにします。 キャッシュしないようにする場合は、適用、 `DontCache` .vsct ファイルで、コマンドを作成するときにフラグを設定します。 ただし、慎重に行って、フラグを使用して、またはパフォーマンスが低下する可能性があります。 コマンドのフラグの詳細については、次を参照してください。、 [コマンドのフラグ要素](../extensibility/command-flag-element.md) ドキュメントです。  
  
    -   ウィンドウで埋め込みモデルを使用して ActiveX コントロールをホストしている vspackages にあるで使用した方が簡単な場合があります、 <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> メソッドです。<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> メソッドで、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> インターフェイスおよび <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> メソッドで、 <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> インターフェイスは機能的に同等です。 どちらも発生するすべてのコマンドの状態を再クエリするための環境。 通常、更新プログラムはすぐに実行されません。 代わりに、更新プログラムは、アイドル時間まで延期します。 シェルでは、良好なパフォーマンスを維持するためにコマンドの状態をキャッシュします。 キャッシュしないようにする場合は、適用、 `DontCache` .vsct ファイルで、コマンドを作成するときにフラグを設定します。 ただし、慎重に使用して、フラグのためパフォーマンスが低下する可能性があります。  
  
         取得することに注意してください、 <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> インターフェイスを呼び出して、 `QueryInterface` メソッドを <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager> からインターフェイスを取得して、オブジェクト、または、 <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> サービスです。  
  
## 参照  
 [Vspackage でのユーザー インターフェイス要素を追加する方法](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [実装](../extensibility/internals/command-implementation.md)