---
title: VSPackage を使用した拡張機能の作成 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c0cc5e08-4897-44f2-8309-e3478f1f999e
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 24c09b4010be419a48d686aa0ec377d04eae68f4
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49262445"
---
# <a name="creating-an-extension-with-a-vspackage"></a>VSPackage を使用した拡張機能の作成
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このチュートリアルでは、VSIX プロジェクトを作成し、VSPackage プロジェクト項目を追加する方法を示します。 メッセージ ボックスを表示するには、UI シェル サービスを取得するのに VSPackage を使用します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 より詳細な情報については 、[Visual Studio SDK のインストール](../extensibility/installing-the-visual-studio-sdk.md) に関する記事を参照してください。  
  
## <a name="creating-a-vspackage"></a>VSPackage の作成  
  
1.  という名前の VSIX プロジェクトを作成する**FirstPackage**します。 VSIX プロジェクト テンプレートを見つけることができます、**新しいプロジェクト**] ダイアログ ボックス [ **Visual c#/機能拡張**します。  
  
2.  という名前の Visual Studio パッケージ項目テンプレートを追加、プロジェクトが開いたら、 **FirstPackage**します。 **ソリューション エクスプ ローラー**でプロジェクト ノードを右クリックし、選択**追加/新しい項目の**します。 **新しい項目の追加**ダイアログ ボックスに移動して**Visual c#/機能拡張**選択と**Visual Studio パッケージ**します。 **名前**ウィンドウの下部にあるフィールドに、コマンド ファイル名を変更して**FirstPackage.cs**します。  
  
3.  プロジェクトをビルドし、デバッグを開始します。  
  
     Visual Studio の実験用インスタンスが表示されます。 実験用インスタンスの詳細については、次を参照してください。 [、実験用インスタンス](../extensibility/the-experimental-instance.md)します。  
  
4.  実験用インスタンスの開く、**ツール/拡張機能と更新**ウィンドウ。 表示する必要があります、 **FirstPackage**拡張します。 (を開いた場合**拡張機能と更新**、Visual Studio の作業用インスタンスでは表示されません**FirstPackage**)。  
  
## <a name="loading-the-vspackage"></a>VSPackage の読み込み  
 この時点で、拡張機能は、ために読み込めませんをロードすると、そのことはありません。 (ツール ウィンドウを開き、メニュー コマンドをクリックすると、)、UI を使用した、または特定の UI コンテキストで、VSPackage を読み込む必要がありますを指定することで対話する際に一般的に、拡張機能を読み込むことができます。 Vspackage と UI のコンテキストを読み込む方法の詳細については、次を参照してください。 [Vspackage の読み込み](../extensibility/loading-vspackages.md)します。 この手順では、ソリューションが開いているときに VSPackage を読み込む方法を紹介します。  
  
1.  FirstPackage.cs ファイルを開きます。 FirstPackage クラスの宣言を探します。 既存の属性を次に置き換えます。  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid(FirstPackageGuids.PackageGuidString)]  
    public sealed class FirstPackage : Package  
    ```  
  
2.  VSPackage が読み込まれていることを知らせるメッセージを追加してみましょう。 メソッドを使用して、VSPackage の Initialize()、これを行うため、VSPackage が配置された後にのみ、Visual Studio サービスを取得できます。 (サービスの取得の詳細については、次を参照してください[方法: サービスを取得](../extensibility/how-to-get-a-service.md)。)。FirstPackage の Initialize() メソッドを取得するコードで置き換える、<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>サービスを取得、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>インターフェイス、および呼び出しの<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A>メソッド。  
  
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
  
4.  実験用インスタンスでは、ソリューションを開きます。 示すメッセージ ボックスを表示する必要があります**最初のパッケージ内で Initialize()** します。

