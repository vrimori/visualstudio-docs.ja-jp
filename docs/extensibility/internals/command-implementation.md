---
title: "コマンドの実装 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: commands, implementation
ms.assetid: c782175c-cce4-4bd0-8374-4a897ceb1b3d
caps.latest.revision: "24"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0128db8288f83ab09ffe82acd66431ea6ed9da1a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="command-implementation"></a>コマンドの実装
VSPackage のコマンドを実装するには、次のタスクを行う必要があります。  
  
1.  .Vsct ファイルでは、コマンド グループを設定し、コマンドを追加します。 詳細については、次を参照してください。 [Visual Studio コマンド テーブル (です。Vsct) ファイル](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)'  
  
2.  Visual Studio でのコマンドを登録します。  
  
3.  コマンドを実装します。  
  
 次のセクションでは、登録して、コマンドを実装する方法を説明します。  
  
## <a name="registering-commands-with-visual-studio"></a>Visual Studio でのコマンドを登録します。  
 コマンドがメニューに表示するかどうか、追加する必要あります、 <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> VSPackage、およびメニューの名前またはそのリソース ID のいずれかの値として使用する  
  
```  
[ProvideMenuResource("Menus.ctmenu", 1)]  
...  
    public sealed class MyPackage : Package  
    {.. ..}  
  
```  
  
 さらに、コマンドを登録する必要があります、<xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>です。 使用してこのサービスを取得することができます、<xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>メソッドの場合は、VSPackage に由来<xref:Microsoft.VisualStudio.Shell.Package>です。  
  
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
  
## <a name="implementing-commands"></a>コマンドを実装します。  
 さまざまなコマンドを実装する方法があります。 これが常に同じ方法と同じメニュー コマンドには、静的なメニュー コマンドを追加する場合を使用してコマンドを作成<xref:System.ComponentModel.Design.MenuCommand>前のセクションの例に示すようにします。 静的なコマンドを作成するには、コマンドの実行を担当するイベント ハンドラーを指定する必要があります。 ため、コマンドは、常に有効になっていると表示されているがありませんを Visual Studio にその状態を提供します。 インスタンスとして、コマンドを作成するには特定の条件に応じてコマンドの状態を変更する場合、<xref:Microsoft.VisualStudio.Shell.OleMenuCommand>クラスし、そのコンス トラクターでコマンドを実行するイベント ハンドラーと Visual に通知するクエリ ステータス ハンドラーを提供Studio のコマンドのステータスが変更されたときにします。 実装することも<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>コマンド クラスかの一部を実装できるよう<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>コマンドは、プロジェクトの一部として提供する場合。 2 つのインターフェイスと<xref:Microsoft.VisualStudio.Shell.OleMenuCommand>すべてのクラスは、Visual Studio で、コマンドの状態の変更を通知するメソッドとコマンドの実行を提供するその他のメソッドがあります。  
  
 コマンドは、コマンドのサービスに追加されて、コマンドのチェーンのいずれかになります。 コマンドの状態の通知と実行メソッドを実装するときに注意をその特定のコマンドのみ提供し、チェーンの他のコマンドに他のすべてのケースを渡す。 コマンドを渡すに失敗した場合 (を返すことによって通常<xref:Microsoft.VisualStudio.OLE.Interop.Constants>)、Visual Studio が正常に動作を停止する可能性があります。  
  
## <a name="query-status-methods"></a>クエリ ステータス メソッド  
 いずれかを実装する場合、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>メソッドまたは<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A>メソッドは、コマンド、コマンドが属しているセットの GUID をチェックし、コマンドの ID。 次のガイドラインに従ってください。  
  
-   いずれかのメソッドの実装を返す必要があります、GUID が認識されないかどうか<xref:Microsoft.VisualStudio.OLE.Interop.Constants>です。  
  
-   いずれかのメソッドの実装、GUID の認識が、コマンドは実際に実装していない場合、メソッドが返す必要があります<xref:Microsoft.VisualStudio.OLE.Interop.Constants>です。  
  
-   かどうかには、いずれかのメソッドの実装は、GUID と、コマンドの両方を認識し、メソッドは、すべてのコマンドのコマンド フラグ フィールドを設定する必要があります (で、`prgCmds`パラメーター)、次のフラグを使用しています。  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>場合は、コマンドはサポートされています。  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>場合は、コマンドを表示することはできません。  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>コマンドがトグルされ、あると思われる場合はチェックされています。  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>場合は、コマンドが有効になっているとします。  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>ショートカット メニューに表示される場合は、コマンドを非表示にする場合。  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>かどうか、コマンドはメニュー コント ローラーが有効でないが、ドロップダウン メニュー リストが空でないは引き続き使用できます。 (このフラグはほとんど使用しません。)  
  
-   コマンドを使用して、.vsct ファイルで定義したかどうか、`TextChanges`フラグは、次のパラメーターを設定します。  
  
    -   設定、`rgwz`の要素、`pCmdText`コマンドの新しいテキストへのパラメーターです。  
  
    -   設定、`cwActual`の要素、`pCmdText`コマンド文字列のサイズのパラメーターです。  
  
 コマンドは、オートメーション機能を処理するためのもので具体的にはしない限りは、現在のコンテキストがオートメーション関数でないことを確認もします。  
  
 特定のコマンドをサポートすることを示す、返す<xref:Microsoft.VisualStudio.VSConstants.S_OK>です。 その他のすべてのコマンドでは、返す<xref:Microsoft.VisualStudio.OLE.Interop.Constants>です。  
  
 次の例では、クエリ ステータス メソッド最初によってコンテキストがオートメーション関数ではありませんし、適切なコマンド セット GUID とコマンド ID を検索してください。 コマンド自体は、有効にし、サポートに設定されます。 その他のコマンドはサポートされていません。  
  
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
 Execute メソッドの実装では、クエリ ステータス メソッドの実装に似ています。 最初に、コンテキストがオートメーション関数でないことを確認します。 その後、GUID とコマンド ID の両方のテストします。 場合、GUID またはコマンド ID は認識されません、返す<xref:Microsoft.VisualStudio.OLE.Interop.Constants>です。  
  
 コマンドを処理するためにそれを実行し、返す<xref:Microsoft.VisualStudio.VSConstants.S_OK>実行が成功した場合。 コマンドは、エラーの検出と通知されます。したがって、実行が失敗した場合は、エラー コードを返します。 次の例では、実行メソッドを実装する方法を示します。  
  
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