---
title: ユーザー インターフェイスの更新 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- user interfaces, updating
- commands, updating UI
ms.assetid: 376e2f56-e7bf-4e62-89f5-3dada84a404b
caps.latest.revision: 42
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c77fa7407c6c271b66104ed6d835bc516a40c288
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47548416"
---
# <a name="updating-the-user-interface"></a>ユーザー インターフェイスの更新
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ユーザー インターフェイスの更新](https://docs.microsoft.com/visualstudio/extensibility/updating-the-user-interface)します。  
  
コマンドを実装した後は、新しいコマンドの状態で、ユーザー インターフェイスを更新するコードを追加できます。  
  
 一般的な Win32 アプリケーションでコマンド セットを継続的にポーリングすることができ、ユーザーがそれらを閲覧している個々 のコマンドの状態を調整することができます。 ただし、ため、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]シェルは、Vspackage の無制限の数をホストできる、広範なポーリング応答性、特にマネージ コードと COM の間の相互運用機能アセンブリの間でポーリングが低下する可能性  
  
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
  
         場合のパラメーター、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> 0 以外の場合 (`TRUE`)、同期的に、すぐに更新プログラムが実行されます。 0 を渡すことをお勧めします。 (`FALSE`) 良好なパフォーマンスを維持するためには、このパラメーターにします。 キャッシュしないようにする場合は、適用、 `DontCache` .vsct ファイルで、コマンドを作成するときにフラグを設定します。 ただし、フラグは慎重に使用して、またはパフォーマンスが低下する可能性があります。 コマンドのフラグの詳細については、次を参照してください。、 [Command Flag 要素](../extensibility/command-flag-element.md)ドキュメント。  
  
    -   Vspackage では、ウィンドウで、インプレース アクティブ化モデルを使用して ActiveX コントロールをホストする、便利な場合があります、<xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A>メソッド。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A>メソッドで、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>インターフェイスと<xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A>メソッドで、<xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager>インターフェイスが機能的に同等です。 両方には、すべてのコマンドの状態を再クエリするための環境が発生します。 通常、更新プログラムはすぐに実行されません。 代わりに、更新プログラムは、アイドル時間まで延期します。 シェルでは、良好なパフォーマンスを維持するためにコマンドの状態をキャッシュします。 キャッシュしないようにする場合は、適用、 `DontCache` .vsct ファイルで、コマンドを作成するときにフラグを設定します。 ただし、慎重に使用して、フラグのため、パフォーマンスが低下する可能性があります。  
  
         取得することに注意してください、<xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager>インターフェイスを呼び出すことによって、`QueryInterface`メソッドを<xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager>オブジェクトまたはからインターフェイスを取得して、<xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager>サービス。  
  
## <a name="see-also"></a>関連項目  
 [Vspackage がユーザー インターフェイス要素を追加する方法](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [実装](../extensibility/internals/command-implementation.md)

