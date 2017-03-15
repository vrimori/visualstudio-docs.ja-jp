---
title: "コマンドの実装 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, implementation
ms.assetid: c782175c-cce4-4bd0-8374-4a897ceb1b3d
caps.latest.revision: 24
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: bd3c23baffe767083bc541fa9e2e8718834b3ee1
ms.lasthandoff: 02/22/2017

---
# <a name="command-implementation"></a>コマンドの実装
VSPackage でコマンドを実装するには、次のタスクを実行する必要があります。  
  
1.  .Vsct ファイルでは、コマンド グループを設定し、コマンドを追加します。 詳細については、次を参照してください。 [Visual Studio コマンド テーブル (します。Vsct) ファイル](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)'  
  
2.  Visual Studio でのコマンドを登録します。  
  
3.  コマンドを実装します。  
  
 次のセクションでは、登録して、コマンドを実装する方法を説明します。  
  
## <a name="registering-commands-with-visual-studio"></a>Visual Studio でのコマンドを登録します。  
 <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute>Vs パッケージ、および値のいずれか、メニューまたはそのリソース id。 の名前として使用する</xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute>追加する必要があります、コマンドをメニューに表示される場合は、  
  
```  
[ProvideMenuResource("Menus.ctmenu", 1)]  
...  
    public sealed class MyPackage : Package  
    {.. ..}  
  
```  
  
 さらに、 <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>。</xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>コマンドを登録する必要があります。 このサービスは<xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>、VSPackage が<xref:Microsoft.VisualStudio.Shell.Package>。</xref:Microsoft.VisualStudio.Shell.Package>から派生している場合、メソッド</xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>を使用して取得できます。  
  
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
 さまざまなコマンドを実装する方法があります。 方法と同じメニュー上に同じを常に表示されるコマンドでは、静的メニュー コマンドを追加するコマンドを使用して作成<xref:System.ComponentModel.Design.MenuCommand>前のセクションの例に示すようにします</xref:System.ComponentModel.Design.MenuCommand>。 静的なコマンドを作成するには、コマンドの実行を担当するイベント ハンドラーを指定する必要があります。 コマンドが常に有効になっていると表示されているのでは、Visual Studio にその状態を入力する必要はありません。 インスタンスとして、コマンドを作成するには特定の条件に応じてコマンドの状態を変更する場合、<xref:Microsoft.VisualStudio.Shell.OleMenuCommand>クラスし、コンス トラクターでのコマンドを実行するイベント ハンドラーとコマンドの状態が変更されたときに Visual Studio に通知する状態を照会ハンドラーに提供します</xref:Microsoft.VisualStudio.Shell.OleMenuCommand>。 実装することも<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>コマンド クラスの一部が実装できるよう<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>プロジェクトの一部として、コマンドを指定するかどうか</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy></xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>。 2 つのインターフェイスと<xref:Microsoft.VisualStudio.Shell.OleMenuCommand>、コマンドのステータスの変更、Visual Studio に通知するメソッドとコマンドの実行を提供するその他のメソッドにすべてのクラスがある</xref:Microsoft.VisualStudio.Shell.OleMenuCommand>。  
  
 コマンドは、コマンドのサービスに追加されて、コマンドのチェーンのいずれかになります。 コマンドのステータス通知と実行メソッドを実装するときに対処をチェーンに、他のコマンドに他のすべてのケースを渡すと特定のコマンドのだけを実現します。 のコマンドを渡すに失敗した場合 (を返すことによって通常<xref:Microsoft.VisualStudio.OLE.Interop.Constants>)、Visual Studio が正常に動作を停止する可能性があります</xref:Microsoft.VisualStudio.OLE.Interop.Constants>。  
  
## <a name="query-status-methods"></a>クエリの状態メソッド  
 いずれかを実装する場合、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>メソッドまたは<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A>メソッドは、コマンド、コマンドが属しているセットの GUID をチェックし、コマンドの ID</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> </xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 。 次のガイドラインに従ってください。  
  
-   GUID は、認識されない場合、いずれかのメソッドの実装が<xref:Microsoft.VisualStudio.OLE.Interop.Constants>。</xref:Microsoft.VisualStudio.OLE.Interop.Constants>を返す必要があります。  
  
-   いずれかのメソッドの実装が GUID の認識が、コマンドは実際に実装していない場合は、メソッドは返される<xref:Microsoft.VisualStudio.OLE.Interop.Constants>。</xref:Microsoft.VisualStudio.OLE.Interop.Constants>  
  
-   かどうかには、いずれかのメソッドの実装は、GUID と、コマンドの両方を認識し、メソッドは、すべてのコマンドのコマンド フラグ フィールドを設定する必要があります (で、`prgCmds`パラメーター) 次のフラグを使用します。  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>場合は、コマンドはサポートされています。</xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>場合は、コマンドは、参照するできません。</xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>コマンドは、オンにし、あると思われる場合はチェックされています。</xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>場合は、コマンドが有効にします。</xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>ショートカット メニューに表示される場合は、コマンドを非表示にする場合。</xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>コマンドはメニュー コント ローラーであり、有効ではなくが、ドロップダウン メニューの一覧が空でないとは引き続き使用できます。</xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> (このフラグは、ほとんど使用しません。)  
  
-   .Vsct ファイルのコマンドを定義したかどうか、`TextChanges`フラグは、次のパラメーターを設定します。  
  
    -   設定、`rgwz`の要素、`pCmdText`コマンドの新しいテキスト パラメーターです。  
  
    -   設定、`cwActual`の要素、`pCmdText`コマンド文字列のサイズのパラメーターです。  
  
 コマンドの目的は具体的には自動化機能を処理する場合を除きは、現在のコンテキストは、オートメーション関数ではないことを確認を行うもします。  
  
 特定のコマンドをサポートすることを示す、 <xref:Microsoft.VisualStudio.VSConstants.S_OK>。</xref:Microsoft.VisualStudio.VSConstants.S_OK>を返す その他のすべてのコマンドを返す<xref:Microsoft.VisualStudio.OLE.Interop.Constants>。</xref:Microsoft.VisualStudio.OLE.Interop.Constants>  
  
 次の例では、状態を照会メソッド最初は、コンテキストがオートメーション関数ではありませんし、正しいコマンド セットの GUID とコマンド ID を検索してください。 有効にしてサポートするのには、コマンド自体は設定されています。 その他のコマンドがサポートされていません。  
  
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
  
## <a name="execution-methods"></a>実行メソッド  
 Execute メソッドの実装では、状態を照会メソッドの実装に似ています。 最初に、コンテキストがオートメーション関数でないことを確認します。 GUID とコマンド ID の両方をテストします。 場合、GUID または ID が認識されないコマンド<xref:Microsoft.VisualStudio.OLE.Interop.Constants>.</xref:Microsoft.VisualStudio.OLE.Interop.Constants>を取得します。  
  
 コマンドを処理することを実行し、返す<xref:Microsoft.VisualStudio.VSConstants.S_OK>実行が成功した場合</xref:Microsoft.VisualStudio.VSConstants.S_OK>。 コマンドは、エラーの検出と通知します。したがって、実行が失敗した場合は、エラー コードを返します。 次の例では、実行メソッドを実装する方法を示します。  
  
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
 [Vspackage でのユーザー インターフェイス要素を追加する方法](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
