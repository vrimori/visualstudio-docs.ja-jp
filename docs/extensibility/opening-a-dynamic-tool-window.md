---
title: 動的なツール ウィンドウを開く |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, dynamic
ms.assetid: 21547ba7-6e81-44df-9277-265bf34f877a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b6e44a0f1be3c9ac48ad41c5b74562059f60d3f9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54945152"
---
# <a name="open-a-dynamic-tool-window"></a>動的なツール ウィンドウを開く
ツール ウィンドウは通常、対応するキーボード ショートカットやメニューのコマンドから開きます。 ただし、する必要がありますツール ウィンドウを開くたびに、UI の特定のコンテキストが適用され、UI コンテキストが適用されなくなったときに閉じます。 ツール ウィンドウのこれらの型と呼ばれます*動的*または*自動表示*します。  
  
> [!NOTE]
>  定義済みの UI コンテキストの一覧は、次を参照してください。<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT>します。  
  
 起動時に、動的なツール ウィンドウを開くと、作成が失敗する可能性があります、実装する必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx>インターフェイスし、テストでエラー条件、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx.QueryShowTool%2A>メソッド。 シェルの起動時に開く必要がある動的なツール ウィンドウがあることを把握するためには、追加する必要があります、`SupportsDynamicToolOwner`パッケージ登録の値 (1 に設定)。 この値は、標準の一部ではない<xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>ので、それを追加するカスタム属性を作成する必要があります。 カスタム属性の詳細については、次を参照してください。[カスタム登録属性を使用して、拡張機能の登録](../extensibility/registering-and-unregistering-vspackages.md#using-a-custom-registration-attribute-to-register-an-extension)します。  
  
 使用<xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A>ツール ウィンドウを開きます。 必要に応じてツール ウィンドウが作成されます。  
  
> [!NOTE]
>  ユーザーが、動的なツール ウィンドウを終了できます。 ユーザーがツール ウィンドウを開くことができますので、メニュー コマンドを作成する場合は、ツール ウィンドウ、および無効になっていますそれ以外の場合に表示される同じ UI コンテキスト内でメニュー コマンドが有効にする必要があります。  
  
## <a name="to-open-a-dynamic-tool-window"></a>動的なツール ウィンドウを開く  
  
1.  という名前の VSIX プロジェクトを作成する**DynamicToolWindow**という名前のツール ウィンドウの項目テンプレートを追加および*DynamicWindowPane.cs*します。 詳細については、次を参照してください。[ツール ウィンドウで拡張機能を作成する](../extensibility/creating-an-extension-with-a-tool-window.md)します。  
  
2.  *DynamicWindowPanePackage.cs*ファイル、DynamicWindowPanePackage 宣言を検索します。 追加、<xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute>と<xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute>ツール ウィンドウを登録する属性。  
  
    ```vb  
    [ProvideToolWindow(typeof(DynamicWindowPane)]  
    [ProvideToolWindowVisibility(typeof(DynamicWindowPane), VSConstants.UICONTEXT.SolutionExists_string)]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    [ProvideToolWindow(typeof(DynamicToolWindow.DynamicWindowPane))]  
    [Guid(DynamicWindowPanePackage.PackageGuidString)]  
    public sealed class DynamicWindowPanePackage : Package  
    {. . .}  
    ```  
  
     上記の属性は、Visual Studio を閉じてから再び開くときに永続化されていません、一時的なウィンドウとして DynamicWindowPane をという名前のツール ウィンドウを登録します。 DynamicWindowPane が開かれるたびに<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_string>が適用され、それ以外の場合に終了します。  
  
3.  プロジェクトをビルドし、デバッグを開始します。 実験用インスタンスが表示されます。 ツール ウィンドウが表示されません。  
  
4.  実験用インスタンスでプロジェクトを開きます。 ツール ウィンドウが表示されます。