---
title: ユーザー インターフェイスの更新 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, updating
- commands, updating UI
ms.assetid: 376e2f56-e7bf-4e62-89f5-3dada84a404b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6b3bc8c4b87aefe62cbd27e64fc426ddb7abf96e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="updating-the-user-interface"></a>ユーザー インターフェイスの更新
コマンドを実装した後は、新しいコマンドの状態で、ユーザー インターフェイスを更新するコードを追加できます。  
  
 一般的な Win32 アプリケーションでコマンド セットを継続的にポーリングしてユーザーを閲覧して、個々 のコマンドの状態を調整することができます。 ただし、ため、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]シェルは、Vspackage の無制限の数をホストできる、マネージ コードと COM の間の相互運用機能アセンブリ間で特にポーリングの応答性が低下する可能性広範なポーリング  
  
### <a name="to-update-the-ui"></a>UI を更新するには  
  
1.  次のいずれかの操作を実行します。  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> メソッドを呼び出します。  
  
         <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>インターフェイスから取得できます、<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>サービスを次のようにします。  
  
        ```csharp  
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
  
         場合のパラメーター、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A>ゼロ以外 (`TRUE`)、同期的に、すぐに更新プログラムが実行されます。 0 を渡すことをお勧め (`FALSE`) 良好なパフォーマンスを維持するためにこのパラメーターにします。 キャッシュを回避する場合は、適用、 `DontCache` .vsct ファイルで、コマンドを作成する場合にフラグを設定します。 それにもかかわらず、フラグは慎重に使用して、またはパフォーマンスが低下する可能性があります。 コマンドのフラグの詳細については、次を参照してください。、[コマンド フラグ要素](../extensibility/command-flag-element.md)ドキュメント。  
  
    -   Vspackage では、ウィンドウで、インプレース アクティブ化モデルを使用して ActiveX コントロールをホストする、使いやすい場合があります、<xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A>メソッドです。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A>メソッドで、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>インターフェイスおよび<xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A>メソッドで、<xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager>インターフェイスが機能的に同等です。 両方が、再度すべてのコマンドの状態をクエリするための環境があります。 通常、更新プログラムはすぐに実行されません。 代わりに、更新プログラムは、アイドル時間まで延期します。 シェルは、良好なパフォーマンスを維持するためにコマンドの状態をキャッシュします。 キャッシュを回避する場合は、適用、 `DontCache` .vsct ファイルで、コマンドを作成する場合にフラグを設定します。 ただし、慎重に使用して、フラグのため、パフォーマンスが低下する可能性があります。  
  
         取得することに注意してください、<xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager>インターフェイスを呼び出して、`QueryInterface`メソッドを<xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager>からインターフェイスを取得して、オブジェクト、または、<xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager>サービス。  
  
## <a name="see-also"></a>関連項目  
 [Vspackage がユーザー インターフェイス要素を追加する方法](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [実装](../extensibility/internals/command-implementation.md)