---
title: コマンドの実装 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- commands, implementation
ms.assetid: c782175c-cce4-4bd0-8374-4a897ceb1b3d
caps.latest.revision: 25
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 46c2a944227218db2294258081fbd1af2d5f084b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49305375"
---
# <a name="command-implementation"></a>コマンドの実装
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

VSPackage のコマンドを実装するには、次のタスクを実行する必要があります。  
  
1.  .Vsct ファイルでは、コマンド グループをセットアップし、コマンドを追加します。 詳細については、次を参照してください。 [Visual Studio Command Table (します。Vsct) ファイル](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)'  
  
2.  Visual Studio でのコマンドを登録します。  
  
3.  コマンドを実装します。  
  
 次のセクションでは、登録およびコマンドを実装する方法を説明します。  
  
## <a name="registering-commands-with-visual-studio"></a>Visual Studio でのコマンドを登録します。  
 コマンドがメニューを表示するかどうか、追加する必要あります、 <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> VSPackage、およびメニューの名前またはそのリソース ID のいずれかの値として使用する  
  
```  
[ProvideMenuResource("Menus.ctmenu", 1)]  
...  
    public sealed class MyPackage : Package  
    {.. ..}  
  
```  
  
 さらでコマンドを登録する必要があります、<xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>します。 このサービスを使用して取得できます、 <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> 、VSPackage がから派生している場合、メソッド<xref:Microsoft.VisualStudio.Shell.Package>します。  
  
```  
OleMenuCommandService mcs = GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
if ( null != mcs )  
{  
    // Create the command for the menu item.  
    CommandID menuCommandID = new CommandID(guidCommandGroup, myCommandID);  
    MenuCommand menuItem = new MenuCommand(MenuItemCallback, menuCommandID );  
    mcs.AddCommand( menuItem );  
}  
  
```  
  
## <a name="implementing-commands"></a>コマンドの実装  
 さまざまなコマンドを実装する方法があります。 方法と同じメニュー上に同じを常に表示されるコマンドは、静的メニューのコマンドの場合、コマンドを使用して作成<xref:System.ComponentModel.Design.MenuCommand>前のセクションの例で示すようにします。 静的なコマンドを作成するには、コマンドの実行を担当するイベント ハンドラーを提供する必要があります。 コマンドは常に有効になっていると表示なので、Visual Studio にその状態を指定する必要はありません。 インスタンスとして、コマンドを作成するには特定の条件に応じて、コマンドの状態を変更する場合、<xref:Microsoft.VisualStudio.Shell.OleMenuCommand>クラスし、コンス トラクターでのコマンドを実行するイベント ハンドラーとビジュアルを通知する状態を照会ハンドラーに提供Studio のコマンドのステータスが変更されたとき。 実装することも<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>コマンド クラスまたはの一部を実装できる<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>プロジェクトの一部として、コマンドを指定する場合。 2 つのインターフェイスと<xref:Microsoft.VisualStudio.Shell.OleMenuCommand>クラスのすべては、Visual Studio で、コマンドの状態の変更を通知するメソッドとコマンドの実行を提供するその他の方法があります。  
  
 コマンドは、コマンド サービスに追加されて、コマンドのチェーンのいずれかになります。 特定のコマンドのみを提供して、チェーン内の他のコマンドに他のすべてのケースを渡すコマンドのステータス通知と実行メソッドを実装する場合を処理します。 コマンドを渡すには失敗した場合 (を返すことによって、通常は<xref:Microsoft.VisualStudio.OLE.Interop.Constants>)、Visual Studio が正常に動作を停止する可能性があります。  
  
## <a name="query-status-methods"></a>状態のクエリ メソッド  
 いずれかを実装している場合、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>メソッドまたは<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A>メソッドで、コマンド、コマンドが所属するセットの GUID を確認し、コマンドの ID。 次のガイドラインに従ってください。  
  
-   いずれかのメソッドの実装を返す必要があります、GUID が認識されないかどうか<xref:Microsoft.VisualStudio.OLE.Interop.Constants>します。  
  
-   いずれかのメソッドの実装、GUID は認識が、コマンドは実際に実装していない場合、メソッドが返す必要があります<xref:Microsoft.VisualStudio.OLE.Interop.Constants>します。  
  
-   かどうかには、いずれかのメソッドの実装は、GUID と、コマンドの両方を認識し、メソッドは、すべてのコマンドのコマンド フラグ フィールドを設定する必要があります (で、`prgCmds`パラメーター)、次のフラグを使用しています。  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> 場合は、コマンドがサポートされています。  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> 場合は、コマンドは表示されません。  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> コマンドがオンにし、あると思われる場合はチェックされています。  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> 場合は、コマンドが有効になっているとします。  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> ショートカット メニューに表示される場合、コマンドを非表示にする場合。  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> コマンドがメニュー コント ローラーが有効でないかどうかが、ドロップダウン メニューからリストが空でないとは引き続き使用できます。 (このフラグはあまり使用されません。)  
  
-   コマンドを使用して、.vsct ファイルで定義したかどうか、`TextChanges`フラグは、次のパラメーターを設定します。  
  
    -   設定、`rgwz`の要素、`pCmdText`パラメーターをコマンドの新しいテキスト。  
  
    -   設定、`cwActual`の要素、`pCmdText`パラメーターをコマンド文字列のサイズ。  
  
 オートメーション機能を処理するために、コマンドの目的は特にない限りは、現在のコンテキストは、automation 関数ではないことを確認しますをことも。  
  
 特定のコマンドをサポートすることを示す、返す<xref:Microsoft.VisualStudio.VSConstants.S_OK>します。 その他のすべてのコマンドでは、返す<xref:Microsoft.VisualStudio.OLE.Interop.Constants>します。  
  
 次の例では、クエリ状態メソッド最初は、コンテキストは、automation 関数ではありませんし、適切なコマンド セットの GUID とコマンド ID を検索してください。 コマンド自体は、有効にされ、サポートに設定されます。 その他のコマンドがサポートされていません。  
  
```  
public int QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)  
{  
    if (!VsShellUtilities.IsInAutomationFunction(m_provider.ServiceProvider))  
    {  
        if (pguidCmdGroup == VSConstants.VSStd2K && cCmds > 0)  
        {  
            // make the Right command visible   
            if ((uint)prgCmds[0].cmdID == (uint)VSConstants.VSStd2KCmdID.RIGHT)  
            {  
                prgCmds[0].cmdf = (int)Microsoft.VisualStudio.OLE.Interop.Constants.MSOCMDF_ENABLED | (int)Microsoft.VisualStudio.OLE.Interop.Constants.MSOCMDF_SUPPORTED;  
                return VSConstants.S_OK;  
            }  
        }  
        return Constants.OLECMDERR_E_NOTSUPPORTED;  
    }  
}  
  
```  
  
## <a name="execution-methods"></a>Execution メソッド  
 Execute メソッドの実装では、クエリの状態のメソッドの実装に似ています。 最初に、コンテキストは、automation 関数ではないことを確認します。 GUID とコマンド ID の両方をテストし、 場合、GUID またはコマンドの ID が認識されていません、返す<xref:Microsoft.VisualStudio.OLE.Interop.Constants>します。  
  
 コマンドを処理することを実行し、返す<xref:Microsoft.VisualStudio.VSConstants.S_OK>実行が成功した場合。 コマンドはエラーの検出と通知; 担当したがって、実行に失敗した場合は、エラー コードを返します。 次の例では、実行メソッドを実装する方法を示します。  
  
```  
public int Exec(ref Guid pguidCmdGroup, uint nCmdID, uint nCmdexecopt, IntPtr pvaIn, IntPtr pvaOut)  
{  
    if (!VsShellUtilities.IsInAutomationFunction(m_provider.ServiceProvider))  
    {  
        if (pguidCmdGroup == VSConstants.GUID_VSStandardCommandSet97)  
        {  
             if (nCmdID ==(uint) uint)VSConstants.VSStd2KCmdID.RIGHT)  
            {  
                //execute the command  
                return VSConstants.S_OK;  
            }  
        }  
    }  
    return Constants.OLECMDERR_E_NOTSUPPORTED;  
}  
  
```  
  
## <a name="see-also"></a>関連項目  
 [VSPackage でユーザー インターフェイス要素を追加する方法](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

