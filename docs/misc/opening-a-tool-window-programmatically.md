---
title: "ツール ウィンドウをプログラムで開く | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ツール ウィンドウ、作成 (プログラムによる)"
ms.assetid: 0017441e-7aa3-4a61-9939-57af11d90d97
caps.latest.revision: 16
caps.handback.revision: 16
manager: "douge"
---
# ツール ウィンドウをプログラムで開く
ツール ウィンドウは、通常、メニューのコマンドをクリックするか、または対応するキーボード ショートカットを押して開きます。 ただし、コマンド ハンドラーを使用するときのように、プログラムを使用してツール ウィンドウを開くことが必要な場合があります。  
  
 ツール ウィンドウを提供元のマネージ VSPackage で開くには、<xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> を使用します。 別の VSPackage でツール ウィンドウを開くには、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.FindToolWindow%2A> を使用します。 いずれの場合も、必要に応じてツール ウィンドウが作成されます。  
  
 次のコードは、C\# Reference.ToolWindow のサンプルから引用しています。  
  
### ツール ウィンドウをプログラムで開くには  
  
1.  ツール ウィンドウのペイン、フレーム、およびそれらを実装する VSPackage を作成します。 詳細については、「[ツール ウィンドウを追加します。](../extensibility/adding-a-tool-window.md)」を参照してください。  
  
2.  提供元の VSPackage に、<xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> を追加します。  
  
    ```c#  
    [ProvideToolWindow(typeof(PersistedWindowPane), Style = VsDockStyle.Tabbed, Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")] [ProvideMenuResource(1000, 1)] [MsVsShell.DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\8.0Exp")] [PackageRegistration(UseManagedResourcesOnly = true)] [Guid("01069CDD-95CE-4620-AC21-DDFF6C57F012")] // your package will have a different GUID public class PackageToolWindow : Package {  
    ```  
  
     これにより、**ソリューション エクスプローラー**にドッキングして開く、ツール ウィンドウ PersistedWindowPane が登録されます。 詳細については、「[ツール ウィンドウを登録します。](../extensibility/registering-a-tool-window.md)」を参照してください。  
  
3.  <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> を使用してツール ウィンドウ ペインを検索するか、またはまだ存在しない場合には作成します。  
  
    ```vb#  
    ' Get the 1 (index 0) and only instance of our tool window. ' If it does not already exist it will get created. Dim pane As MsVsShell.ToolWindowPane = Me.FindToolWindow(GetType(PersistedWindowPane), 0, True) If pane Is Nothing Then End If  
  
    ```  
  
    ```c#  
    // Get the 1 (index 0) and only instance of our tool window. // If it does not already exist it will get created. MsVsShell.ToolWindowPane pane =     this.FindToolWindow(typeof(PersistedWindowPane), 0, true); if (pane == null) {  
    ```  
  
4.  ツール ウィンドウ ペインから、ツール ウィンドウ フレームを取得します。  
  
    ```vb#  
    Dim frame As IVsWindowFrame = TryCast(pane.Frame, IVsWindowFrame) If frame Is Nothing Then End If  
  
    ```  
  
    ```c#  
    IVsWindowFrame frame = pane.Frame as IVsWindowFrame; if (frame == null) {  
    ```  
  
5.  ツール ウィンドウを表示します。  
  
    ```vb#  
    ' Bring the tool window to the front and give it focus ErrorHandler.ThrowOnFailure(frame.Show())  
  
    ```  
  
    ```c#  
    // Bring the tool window to the front and give it focus ErrorHandler.ThrowOnFailure(frame.Show());  
    ```