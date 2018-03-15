---
title: "VSPackage の拡張機能の作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c0cc5e08-4897-44f2-8309-e3478f1f999e
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: df971bdf72ff52cfa6343b6237de072238087ac4
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2018
---
# <a name="creating-an-extension-with-a-vspackage"></a>VSPackage で拡張機能を作成します。
このチュートリアルでは、VSIX プロジェクトを作成し、VSPackage プロジェクト アイテムを追加する方法を示します。 メッセージ ボックスを表示するために UI シェル サービスを取得するのに VSPackage を使用します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降で、ダウンロード センターから、Visual Studio SDK をインストールするはできません。 Visual Studio のセットアップのオプション機能として含まれます。 後でまた VS SDK をインストールすることができます。 詳細については、次を参照してください。 [、Visual Studio SDK をインストールする](../extensibility/installing-the-visual-studio-sdk.md)です。  
  
## <a name="creating-a-vspackage"></a>VSPackage の作成  
  
1.  という名前の VSIX プロジェクトを作成する**FirstPackage**です。 VSIX プロジェクトのテンプレートを見つけることができます、**新しいプロジェクト**] ダイアログ ボックス [ **Visual c#/機能拡張**です。  
  
2.  プロジェクトを開いたら、という名前の Visual Studio パッケージ項目テンプレートを追加**FirstPackage**です。 **ソリューション エクスプ ローラー**プロジェクト ノードを右クリックし、選択、**追加/新しい項目の**します。 **新しい項目の追加**ダイアログ ボックスに移動して**Visual c#/機能拡張**選択**Visual Studio パッケージ**です。 **名前**ウィンドウの下部にあるフィールドに、コマンド ファイルの名前を変更する**FirstPackage.cs**です。  
  
3.  プロジェクトをビルドし、デバッグを開始します。  
  
     Visual Studio の実験用インスタンスが表示されます。 実験用インスタンスの詳細については、次を参照してください。 [、実験用インスタンス](../extensibility/the-experimental-instance.md)です。  
  
4.  実験用インスタンスの開く、**ツール/拡張機能と更新プログラム**ウィンドウです。 表示されるはずの**FirstPackage**拡張機能は、ここです。 (開く場合**拡張機能と更新**、作業には、Visual Studio のインスタンスでは表示されません**FirstPackage**)。  
  
## <a name="loading-the-vspackage"></a>VSPackage を読み込む  
 この時点で、拡張機能が読み込まれないを読み込むことが原因となる nothing を使用する必要があるためです。 (ツール ウィンドウを開き、メニュー コマンドをクリックすると、)、UI を使用した、または、VSPackage は、特定の UI コンテキストで読み込む必要がありますを指定して対話するときに一般的に、拡張機能を読み込むことができます。 Vspackage と UI コンテキストの読み込みの詳細については、次を参照してください。[読み込み Vspackage](../extensibility/loading-vspackages.md)です。 ソリューションが開いているときに VSPackage を読み込む方法表示は、この手順でします。  
  
1.  FirstPackage.cs ファイルを開きます。 FirstPackage クラスの宣言を参照してください。 既存の属性を次に置き換えます。  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid(FirstPackage.PackageGuidString)]  
    public sealed class FirstPackage : Package  
    ```  
  
2.  VSPackage が読み込まれることを知らせるメッセージを追加してみましょう。 メソッドを使用して、VSPackage の Initialize()、これを行うため、VSPackage が配置された後にのみ、Visual Studio サービスを取得することができます。 (サービスの取得の詳細については、次を参照してください[する方法: サービスを取得](../extensibility/how-to-get-a-service.md)。)。FirstPackage の Initialize() メソッドを取得するコードに置き換えます、<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>サービスを取得、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>インターフェイス、および呼び出し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A>メソッドです。  
  
    ```csharp  
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
  
4.  実験用インスタンスで、ソリューションを開きます。 示すメッセージ ボックスを表示する必要があります**最初のパッケージの内部 Initialize()**です。