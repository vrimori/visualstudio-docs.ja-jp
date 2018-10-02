---
title: '方法: AsyncPackage を使用して、バック グラウンドで Vspackage を読み込む |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dedf0173-197e-4258-ae5a-807eb3abc952
caps.latest.revision: 9
ms.author: gregvanl
ms.openlocfilehash: 5c37ba734da58b1681f2eb70c106bd9cdac7c89b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47544515"
---
# <a name="how-to-use-asyncpackage-to-load-vspackages-in-the-background"></a>方法: AsyncPackage を使用して、バック グラウンドで Vspackage を読み込む
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: バック グラウンドで Vspackage をロードを使用して AsyncPackage](https://docs.microsoft.com/visualstudio/extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background)します。  
  
読み込みと初期化 VS パッケージは、ディスク I/O 結果ことができます。 このような I/O が UI スレッドで発生した場合、応答性の問題になることができます。 これに対処すると、Visual Studio 2015 が導入された、<xref:Microsoft.VisualStudio.Shell.AsyncPackage>バック グラウンド スレッドでのパッケージの読み込みができるようにするクラス。  
  
## <a name="creating-an-asyncpackage"></a>Asyncpackage から作成します。  
 VSIX プロジェクトを作成することができます (**ファイル/新しい/プロジェクト/Visual c#/機能拡張/VSIX プロジェクト**) VSPackage をプロジェクトに追加して (、プロジェクトを右クリックし、**追加、新しい項目/c# 項目/拡張機能/visualパッケージを studio**)。 サービスを作成し、それらのサービスをパッケージに追加することができます。  
  
1.  パッケージからの派生<xref:Microsoft.VisualStudio.Shell.AsyncPackage>します。  
  
2.  場合は、パッケージを読み込む可能性がクエリを実行するサービスを提供します。  
  
     この動作を有効にして、パッケージがバック グラウンド読み込みの安全である Visual Studio に示すために、<xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>設定する必要があります**AllowsBackgroundLoading**属性コンス トラクターで true に設定します。  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]  
  
    ```  
  
     バック グラウンド スレッドで、サービスのインスタンスを作成しても安全であることを示す Visual Studio に設定する必要があります、<xref:Microsoft.VisualStudio.Shell.ProvideServiceAttributeBase.IsAsyncQueryable%2A>プロパティを true に、<xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>コンス トラクター。  
  
    ```csharp  
    [ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]  
  
    ```  
  
3.  UI のコンテキストを使用して読み込むかどうかは、指定する必要があります**PackageAutoLoadFlags.BackgroundLoad**の<xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>またはフラグに値 (0x2)、パッケージの自動読み込みエントリの値として書き込まれます。  
  
    ```csharp  
    [ProvideAutoLoad(UIContextGuid, PackageAutoLoadFlags.BackgroundLoad)]  
  
    ```  
  
4.  非同期初期化作業を行う場合は、オーバーライド<xref:Microsoft.VisualStudio.Shell.AsyncPackage.InitializeAsync%2A>します。 削除、 **Initialize()** VSIX のテンプレートによって提供されるメソッド。 (、 **Initialize()** メソッド**AsyncPackage**がシールされている)。 いずれかを使用することができます、<xref:Microsoft.VisualStudio.Shell.AsyncPackage.AddService%2A>非同期のサービスをパッケージに追加する方法。  
  
     注: 呼び出す**ベース。InitializeAsync()**、ソース コードを変更することができます。  
  
    ```csharp  
    await base.InitializeAsync(cancellationToken, progress);  
    ```  
  
5.  非同期初期化コードから Rpc (プロシージャ コールの削除) が作成されないように注意する必要があります (で**InitializeAsync**)。 これらを呼び出すときに発生することが<xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>直接的または間接的にします。  使用して負荷が同期が必要なときは、UI スレッドをブロック<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>します。 既定のブロックしているモデルには、Rpc が無効にします。 つまりする場合は、非同期タスクから RPC を使用しようとすると、するデッドロックが発生、UI スレッドが、パッケージを読み込むを待つ自体の場合。 ようなものを使用して必要な場合は、UI スレッドにコードをマーシャ リングする一般的な方法が**結合可能なタスク ファクトリ**の<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>または RPC を使用しないその他のいくつかのメカニズムです。  使用しない**ThreadHelper.Generic.Invoke**または一般的に、UI スレッドへの取得を待機している呼び出し元のスレッドをブロックします。  
  
     注: を使用しないように**GetService**または**QueryService**で、 **InitializeAsync**メソッド。 使用する場合は、まず、UI スレッドに切り替える必要があります。 使用する方法が<xref:Microsoft.VisualStudio.Shell.AsyncServiceProvider.GetServiceAsync%2A>から、 **AsyncPackage** (にキャストすることによって<xref:Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider>)。  
  
 C#: asyncpackage からを作成します。  
  
```csharp  
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]       
[ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]   
public sealed class TestPackage : AsyncPackage   
{   
    protected override Task InitializeAsync(System.Threading.CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)   
    {               
        this.AddService(typeof(SMyTestService), CreateService, true);   
        return Task.FromResult<object>(null);   
    }   
}  
```  
  
## <a name="convert-an-existing-vspackage-to-asyncpackage"></a>AsyncPackage を既存の VSPackage に変換します。  
 作業の大部分は、新しいを作成すると同じ**AsyncPackage**します。 1 ~ 5 の上記の手順に従う必要があります。 また、次のように特別な注意を実行する必要があります。  
  
1.  必ず削除してください、**初期化**オーバーライドは、パッケージにする必要があります。  
  
2.  デッドロックを回避する: 可能性があります Rpc を非表示に、コードはバック グラウンド スレッドで発生するようになりました。 RPC を行う場合は、ことを確認する必要があります (例: **GetService**)、いずれか (1) スイッチをメイン スレッドにする必要がある、または (2) を使用した場合は、1 つの API の非同期バージョンが存在します (例: **GetServiceAsync**)。  
  
3.  頻度が高すぎるのスレッド間で切り替えないでください。 バック グラウンド スレッドで実行できる作業をローカライズしてみてください。 これには、読み込み時間が短縮されます。  
  
## <a name="querying-services-from-asyncpackage"></a>AsyncPackage からサービスのクエリを実行します。  
 **AsyncPackage**可能性がありますまたは呼び出し元によって非同期的に読み込まれないことができます。 例えば  
  
-   呼び出し元が呼び出された場合**GetService**または**QueryService** (両方の同期 Api) または  
  
-   呼び出し元が呼び出された場合**IVsShell::LoadPackage** (または**IVsShell5::LoadPackageWithContext**) または  
  
-   負荷は、UI コンテキストによってトリガーされますが、UI コンテキストのメカニズムが非同期的に読み込むことが指定されていません  
  
 パッケージは、同期的に読み込まれます。  
  
 その作業の完了のパッケージもは営業案件 (非同期の初期化フェーズ) で作業を実行する、UI スレッドが UI スレッドがブロックされます。 呼び出し元が使用している場合**IAsyncServiceProvider**サービスの非同期的にクエリし、ロード テストおよび初期化は行われます非同期的にすぐに結果として得られるタスク オブジェクトをブロックしないと仮定するとします。  
  
 C#: サービスを非同期的に照会する方法。  
  
```csharp  
using Microsoft.VisualStudio.Shell;   
using Microsoft.VisualStudio.Shell.Interop;   
  
IAsyncServiceProvider asyncServiceProvider = Package.GetService(typeof(SAsyncServiceProvider)) as IAsyncServiceProvider;   
IMyTestService testService = await ayncServiceProvider.GetServiceAsync(typeof(SMyTestService)) as IMyTestService;  
```

