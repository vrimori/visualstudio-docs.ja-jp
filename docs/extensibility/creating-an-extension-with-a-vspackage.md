---
title: "VSPackage で拡張機能を作成します。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c0cc5e08-4897-44f2-8309-e3478f1f999e
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# VSPackage で拡張機能を作成します。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

このチュートリアルでは、VSIX プロジェクトを作成し、VSPackage プロジェクト項目を追加する方法を示します。 メッセージ ボックスを表示するために、UI シェル サービスを取得するのに、VSPackage を使用します。  
  
## 必要条件  
 Visual Studio 2015 以降、インストールしない、Visual Studio SDK ダウンロード センターからです。 Visual Studio のセットアップのオプション機能として含まれます。 後で、VS SDK をインストールすることもできます。 詳細については、「[Visual Studio SDK をインストールします。](../extensibility/installing-the-visual-studio-sdk.md)」を参照してください。  
  
## VSPackage を作成します。  
  
1.  という名前の VSIX プロジェクトを作成する **FirstPackage**します。 VSIX プロジェクトのテンプレートを見つけることができます、 **新しいプロジェクト** \] ダイアログ ボックス \[ **Visual c\#\/機能拡張**します。  
  
2.  プロジェクトを開いたら、という名前の Visual Studio パッケージ項目テンプレートを追加 **FirstPackage**します。**ソリューション エクスプ ローラー**, プロジェクト ノードを右クリックして、選択 **追加\/\[新しい項目の**します。**新しい項目の追加** ダイアログ ボックスに移動 **Visual c\#\/機能拡張** を選択して **Visual Studio パッケージ**します。**名** ウィンドウの下部にあるフィールドに、コマンド ファイルの名前を変更する **FirstPackage.cs**します。  
  
3.  プロジェクトをビルドし、デバッグを開始します。  
  
     Visual Studio の実験用インスタンスが表示されます。 実験用インスタンスの詳細については、次を参照してください。 [実験用インスタンス](../extensibility/the-experimental-instance.md)します。  
  
4.  実験用インスタンスで開き、 **ツール\/拡張機能と更新プログラム** ウィンドウです。 確認する必要があります、 **FirstPackage** 拡張機能は、ここです。 \(開く場合 **拡張機能と更新プログラム** 、作業には、Visual Studio のインスタンスでは表示されません **FirstPackage**\)。  
  
## VSPackage を読み込む  
 この時点で、拡張機能は、ために読み込めません原因となってを読み込むことはありません。 \(ツール ウィンドウを開き、メニュー コマンドをクリックすると、\)、UI または UI の特定のコンテキストで、VSPackage を読み込む必要がありますを指定して対話するときに一般的に、拡張機能を読み込むことができます。 Vspackage と UI のコンテキストの読み込み方法の詳細については、次を参照してください。 [Vspackage を読み込む](../extensibility/loading-vspackages.md)します。 ソリューションを開いている場合は、VSPackage を読み込む方法表示は、この手順でします。  
  
1.  FirstPackage.cs ファイルを開きます。 FirstPackage クラスの宣言を探します。 既存の属性を次に置き換えます。  
  
    ```c#  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid(FirstPackageGuids.PackageGuidString)]  
    public sealed class FirstPackage : Package  
    ```  
  
2.  VSPackage が読み込まれることを知らせるメッセージを追加してみましょう。 メソッドを使用して VSPackage の Initialize\(\)、これを行うため、VSPackage がコンテナーに配置した後にのみ、Visual Studio のサービスを取得できます。 \(サービスの取得の詳細については、次を参照してください [方法: サービスを取得](../Topic/How%20to:%20Get%20a%20Service.md)。\)。 FirstPackage の Initialize\(\) メソッドを取得するコードに置き換えます、 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> サービスを取得、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> インターフェイス、および呼び出し、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> メソッドです。  
  
    ```c#  
    protected override void Initialize()  
    {  
        base.Initialize();  
  
        IVsUIShell uiShell = (IVsUIShell)GetService(typeof(SVsUIShell));  
        Guid clsid = Guid.Empty;  
        int result;  
        Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(uiShell.ShowMessageBox(  
            0,  
            ref clsid,  
            "FirstPackage",  
             string.Format(CultureInfo.CurrentCulture, "Inside {0}.Initialize()", this.GetType().FullName),  
            string.Empty,  
            0,  
            OLEMSGBUTTON.OLEMSGBUTTON_OK,  
            OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,  
            OLEMSGICON.OLEMSGICON_INFO,  
            0,  
            out result));  
    }  
    ```  
  
3.  プロジェクトをビルドし、デバッグを開始します。 実験用インスタンスが表示されます。  
  
4.  実験用インスタンスで、ソリューションを開きます。 示すメッセージ ボックスを表示する必要があります **最初のパッケージの内部 Initialize\(\)**します。