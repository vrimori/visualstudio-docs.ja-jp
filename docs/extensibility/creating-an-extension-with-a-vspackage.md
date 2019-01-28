---
title: VSPackage を使用した拡張機能の作成 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c0cc5e08-4897-44f2-8309-e3478f1f999e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 04a31171b2aca3de8284bb93257c106b80780242
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55040814"
---
# <a name="create-an-extension-with-a-vspackage"></a>VSPackage を使用した拡張機能を作成します。
このチュートリアルでは、VSIX プロジェクトを作成し、VSPackage プロジェクト項目を追加する方法を示します。 メッセージ ボックスを表示するには、UI シェル サービスを取得するのに VSPackage を使用します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 詳細については、"[Visual Studio SDK をインストール](../extensibility/installing-the-visual-studio-sdk.md)"を参照してください。  
  
## <a name="create-a-vspackage"></a>VSPackage を作成します。  
  
1.  という名前の VSIX プロジェクトを作成する**FirstPackage**します。 VSIX プロジェクト テンプレートを見つけることができます、**新しいプロジェクト**] ダイアログ ボックス [ **Visual c#** > **Extensibility**します。  
  
2.  という名前の Visual Studio パッケージ項目テンプレートを追加、プロジェクトが開いたら、 **FirstPackage**します。 **ソリューション エクスプ ローラー**でプロジェクト ノードを右クリックし、選択**追加** > **新しい項目の**します。 **新しい項目の追加**ダイアログ ボックスに移動して**Visual c#** > **拡張**選択と**Visual Studio パッケージ**。 **名前**ウィンドウの下部にあるフィールドに、コマンド ファイル名を変更して*FirstPackage.cs*します。  
  
3.  プロジェクトをビルドし、デバッグを開始します。  
  
     Visual Studio の実験用インスタンスが表示されます。 実験用インスタンスの詳細については、次を参照してください。[実験用インスタンス](../extensibility/the-experimental-instance.md)します。  
  
4.  実験用インスタンスの開く、**ツール** > **拡張機能と更新**ウィンドウ。 表示する必要があります、 **FirstPackage**拡張します。 (を開いた場合**拡張機能と更新**、Visual Studio の作業用インスタンスでは表示されません**FirstPackage**)。  
  
## <a name="load-the-vspackage"></a>VSPackage を読み込む  
 この時点で、拡張機能は、ために読み込めませんをロードすると、そのことはありません。 (ツール ウィンドウを開き、メニュー コマンドをクリックすると、)、UI を使用した、または特定の UI コンテキストで、VSPackage を読み込む必要がありますを指定することで対話する際に一般的に、拡張機能を読み込むことができます。 Vspackage と UI のコンテキストを読み込む方法の詳細については、次を参照してください。 [Vspackage の読み込み](../extensibility/loading-vspackages.md)します。 この手順では、ソリューションが開いているときに VSPackage を読み込む方法を紹介します。  
  
1.  開く、 *FirstPackage.cs*ファイル。 宣言を探して、`FirstPackage`クラス。 既存の属性を次に置き換えます。  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid(FirstPackage.PackageGuidString)]  
    public sealed class FirstPackage : Package  
    ```  
  
2.  VSPackage が読み込まれていることを知らせるメッセージを追加してみましょう。 使用して、VSPackage の`Initialize()`メソッドには、Visual Studio を入手するため、サービス、VSPackage が配置された後のみです。 (サービスの取得の詳細については、次を参照してください。[方法。サービスを取得](../extensibility/how-to-get-a-service.md))。置換、`Initialize()`メソッドの`FirstPackage`を取得するコードを含む、<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>サービスを取得、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>インターフェイス、および呼び出しその<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A>メソッド。  
  
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