---
title: "動的なツール ウィンドウを開く | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "動的なツール ウィンドウ"
ms.assetid: 21547ba7-6e81-44df-9277-265bf34f877a
caps.latest.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 21
---
# 動的なツール ウィンドウを開く
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ツール ウィンドウは通常、メニュー、または対応するキーボード ショートカット コマンドから開きます。 時々、ただし、必要がありますツール ウィンドウを開くたびに、UI の特定のコンテキストが適用され、UI コンテキストが適用されなくなったときに閉じます。 上記のようなツール ウィンドウと呼びます *動的* または *自動的に表示されている*します。  
  
> [!NOTE]
>  定義済み UI コンテキストの一覧は、次を参照してください。 <xref:Microsoft.VisualStudio.VSConstants.UIContext>します。 に対して、  
  
 起動時に、動的なツール ウィンドウを開くと作成が失敗する可能性が、実装する必要があります、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx> インターフェイス、およびテストの失敗条件、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx.QueryShowTool%2A> メソッドです。 シェルの起動時に開く必要があります、動的なツール ウィンドウがあることを知るためには、追加する必要があります、 `SupportsDynamicToolOwner` 値 \(1 に設定\)、パッケージを登録します。 この値は、標準の一部ではない <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>, ので、それを追加するカスタム属性を作成する必要があります。 カスタム属性に関する詳細については、次を参照してください。 [カスタム登録属性を使用した拡張機能の登録](/visual-cpp/misc/using-a-custom-registration-attribute-to-register-an-extension)します。  
  
 使用する <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> ツール ウィンドウを開きます。 必要に応じて、ツール ウィンドウが作成されます。  
  
> [!NOTE]
>  ユーザーは、動的なツール ウィンドウを閉じたことができます。 ユーザーがツール ウィンドウを開くことができますので、メニュー コマンドを作成する場合は、メニュー コマンドは、ツール ウィンドウとそれ以外の場合無効が表示された同じ UI コンテキストで有効にする必要があります。  
  
### 動的なツール ウィンドウを開く  
  
1.  という名前の VSIX プロジェクトを作成する **DynamicToolWindow** という名前のツール ウィンドウの項目テンプレートを追加および **DynamicWindowPane.cs**します。 詳細については、「[ツール ウィンドウで、拡張機能を作成します。](../extensibility/creating-an-extension-with-a-tool-window.md)」を参照してください。  
  
2.  DynamicWindowPanePackage.cs ファイルで DynamicWindowPanePackage 宣言を検索します。 追加、 <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> と T:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute 属性ツール ウィンドウを登録します。  
  
    ```vb  
    [[ProvideToolWindow(typeof(DynamicWindowPane)] [ProvideToolWindowVisibility(typeof(DynamicWindowPane), VSConstants.UICONTEXT.SolutionExists_string)] [PackageRegistration(UseManagedResourcesOnly = true)] [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About [ProvideMenuResource("Menus.ctmenu", 1)] [ProvideToolWindow(typeof(DynamicToolWindow.DynamicWindowPane))] [Guid(DynamicWindowPanePackageGuids.PackageGuidString)] public sealed class DynamicWindowPanePackage : Package {. . .}  
    ```  
  
     これは、Visual Studio を閉じてから再度開くときに永続化されていません一時的なウィンドウとして DynamicWindowPane をという名前のツール ウィンドウを登録します。 DynamicWindowPane が開かれるたびに <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_string> が適用され、それ以外の場合に終了します。  
  
3.  プロジェクトをビルドし、デバッグを開始します。 実験用インスタンスが表示されます。 ツール ウィンドウが表示されません。  
  
4.  実験用インスタンスで、プロジェクトを開きます。 ツール ウィンドウが表示されます。