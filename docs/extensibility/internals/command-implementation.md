---
title: コマンドの実装 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, implementation
ms.assetid: c782175c-cce4-4bd0-8374-4a897ceb1b3d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8f002e660b2c3b745e4a7ea67f715b613b96bd0a
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2018
ms.locfileid: "39510440"
---
# <a name="command-implementation"></a>コマンドの実装
VSPackage のコマンドを実装するには、次のタスクを実行する必要があります。  
  
1.  *.Vsct*ファイルおよびコマンド グループをセットアップし、コマンドを追加します。 詳細については、次を参照してください。 [Visual Studio コマンド テーブル (.vsct) ファイル](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)します。
  
2.  Visual Studio でのコマンドを登録します。  
  
3.  コマンドを実装します。  
    
次のセクションでは、登録およびコマンドを実装する方法を説明します。  
  
## <a name="register-commands-with-visual-studio"></a>Visual Studio で登録するコマンド  
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
  
## <a name="implement-commands"></a>コマンドの実装  
 さまざまなコマンドを実装する方法があります。 方法と同じメニュー上に同じを常に表示されるコマンドは、静的メニューのコマンドの場合、コマンドを使用して作成<xref:System.ComponentModel.Design.MenuCommand>前のセクションの例で示すようにします。 静的なコマンドを作成するには、コマンドの実行を担当するイベント ハンドラーを提供する必要があります。 コマンドは常に有効になっていると表示なので、Visual Studio にその状態を指定する必要はありません。 インスタンスとして、コマンドを作成するには特定の条件に応じて、コマンドの状態を変更する場合、<xref:Microsoft.VisualStudio.Shell.OleMenuCommand>クラスし、そのコンス トラクターでコマンドを実行するイベント ハンドラーを提供、 `QueryStatus` Visual に通知するハンドラーStudio のコマンドのステータスが変更されたとき。 実装することも<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>コマンド クラスまたはの一部を実装できる<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>プロジェクトの一部として、コマンドを指定する場合。 2 つのインターフェイスと<xref:Microsoft.VisualStudio.Shell.OleMenuCommand>クラスのすべては、Visual Studio で、コマンドの状態の変更を通知するメソッドとコマンドの実行を提供するその他の方法があります。  
  
 コマンドは、コマンド サービスに追加されて、コマンドのチェーンのいずれかになります。 特定のコマンドのみを提供して、チェーン内の他のコマンドに他のすべてのケースを渡すコマンドのステータス通知と実行メソッドを実装する場合を処理します。 コマンドを渡すには失敗した場合 (を返すことによって、通常は<xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>)、Visual Studio が正常に動作を停止する可能性があります。  
  
## <a name="querystatus-methods"></a>QueryStatus メソッド  
 いずれかを実装している場合、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>メソッドまたは<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A>メソッドで、コマンド、コマンドが所属するセットの GUID を確認し、コマンドの ID。 次のガイドラインに従ってください。  
  
-   いずれかのメソッドの実装を返す必要があります、GUID が認識されないかどうか<xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_UNKNOWNGROUP>します。  
  
-   いずれかのメソッドの実装、GUID を認識して、コマンドが実装していない場合、メソッドが返す必要があります<xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>します。  
  
-   かどうかには、いずれかのメソッドの実装は、GUID と、コマンドの両方を認識し、メソッドは、すべてのコマンドのコマンド フラグ フィールドを設定する必要があります (で、`prgCmds`パラメーター)、次を使用して<xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>フラグ。  
  
    -   `OLECMDF_SUPPORTED`: このコマンドはサポートされます。  
  
    -   `OLECMDF_INVISIBLE`: このコマンドは表示されません。  
  
    -   `OLECMDF_LATCHED`: このコマンドは、がオンにし、をオンになっているが表示されます。  
  
    -   `OLECMDF_ENABLED`: このコマンドは有効です。  
  
    -   `OLECMDF_DEFHIDEONCTXTMENU`: このコマンドは、ショートカット メニューに表示される場合、非表示にする必要があります。  
  
    -   `OLECMDF_NINCHED`: このコマンドはメニュー コント ローラーで、が有効でないが、そのドロップダウン メニューからリストが空でないとは引き続き使用できます。 (このフラグはあまり使用されません。)  
  
-   コマンドが定義されている場合、 *.vsct*ファイルと、`TextChanges`フラグは、次のパラメーターを設定します。  
  
    -   設定、`rgwz`の要素、`pCmdText`パラメーターをコマンドの新しいテキスト。  
  
    -   設定、`cwActual`の要素、`pCmdText`パラメーターをコマンド文字列のサイズ。  
  

また、必ず、現在のコンテキストは、automation 関数ではないことオートメーション機能を処理するために、コマンドの目的は具体的にはしない限り。  
  
特定のコマンドをサポートすることを示す、返す<xref:Microsoft.VisualStudio.VSConstants.S_OK>します。 その他のすべてのコマンドでは、返す<xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>します。  
  
次の例では、`QueryStatus`メソッドはまず、コンテキストは、automation 関数ではありませんし、適切なコマンド セットの GUID とコマンド ID を検索してください。 コマンド自体は、有効にされ、サポートに設定されます。 その他のコマンドがサポートされていません。  
  
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
 実装、`Exec`メソッドの実装に似ています、`QueryStatus`メソッド。 最初に、コンテキストは、automation 関数ではないことを確認します。 次に、GUID とコマンド ID の両方のテストします。 場合、GUID またはコマンドの ID が認識されていません、返す<xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>します。  
  
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
 [Vspackage がユーザー インターフェイス要素を追加する方法](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)