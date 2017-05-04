---
title: "方法: AsyncPackage を使用して、バック グラウンドで Vspackage を読み込む |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dedf0173-197e-4258-ae5a-807eb3abc952
caps.latest.revision: 8
ms.author: gregvanl
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: c9df048a49580f3526b48e29041ef3758722ed27
ms.openlocfilehash: bcfdf6991c12affc1000ace72b16f97be9de469a
ms.lasthandoff: 05/03/2017

---
# <a name="how-to-use-asyncpackage-to-load-vspackages-in-the-background"></a>方法: AsyncPackage を使用して、バック グラウンドで Vspackage を読み込む
読み込みと初期化 VS パッケージは、ディスク I/O になります。 UI スレッドでこのような I/O が発生した場合、応答性の問題になることができます。 これに対処するには、Visual Studio 2015 には、< xref:Microsoft.VisualStudio.Shell.AsyncPackage > クラスをパッケージのバック グラウンド スレッドでの読み込みを有効にするが導入されました。  
  
## <a name="creating-an-asyncpackage"></a>作成するため、asyncpackage から  
 VSIX プロジェクトを作成することができます (**ファイル/新しい/プロジェクト/Visual c#/機能拡張/VSIX プロジェクト**)、VSPackage をプロジェクトに追加して (、プロジェクトを右クリックし、**追加/新規項目/c# 項目/拡張機能/visual Studio パッケージ**)。 サービスを作成し、それらのサービスをパッケージに追加できます。  
  
1.  パッケージは、< xref:Microsoft.VisualStudio.Shell.AsyncPackage > から派生します。  
  
2.  場合は、パッケージを読み込むが発生する可能性がありますがクエリを実行するサービスを提供します。  
  
     < Xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute > を設定すると、この動作を選択、そのパッケージがバック グラウンドで読み込まないに対して安全では、Visual studio を示すために**AllowsBackgroundLoading**属性コンス トラクターで true に設定します。  
  
    ```c#  
    [PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]  
  
    ```  
  
     Visual Studio にあることを示す、サービス、バック グラウンド スレッドでインスタンス化、< xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute > コンス トラクターで true に < xref:Microsoft.VisualStudio.Shell.ProvideServiceAttributeBase.IsAsyncQueryable%2A > プロパティを設定する必要があります。  
  
    ```c#  
    [ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]  
  
    ```  
  
3.  UI コンテキスト経由で読み込もうとしているかどうかは、指定する必要があります**PackageAutoLoadFlags.BackgroundLoad** < xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute > の値 (0x2) フラグにパッケージの自動読み込みエントリの値として書き込まれますか。  
  
    ```c#  
    [ProvideAutoLoad(UIContextGuid, PackageAutoLoadFlags.BackgroundLoad)]  
  
    ```  
  
4.  非同期の初期化を行うには作業をした場合は、< xref:Microsoft.VisualStudio.Shell.AsyncPackage.InitializeAsync%2A > をオーバーライドする必要があります。 削除、 **Initialize()** VSIX テンプレートによって提供されるメソッド。 (、 **Initialize()**メソッド**AsyncPackage**が封印されている)。 非同期のサービスをパッケージに追加するのにには、< xref:Microsoft.VisualStudio.Shell.AsyncPackage.AddService%2A > メソッドのいずれかを使用できます。  
  
     注: 呼び出す**ベースです。InitializeAsync()**、ソース コードを変更することができます。  
  
    ```c#  
    await base.InitializeAsync(cancellationToken, progress);  
    ```  
  
5.  非同期の初期化コードから Rpc (リモート プロシージャ コール) が作成されないようにする注意する必要があります (で**InitializeAsync**)。 これらは、直接または間接的に < xref:Microsoft.VisualStudio.Shell.Package.GetService%2A > を呼び出すときに発生します。  負荷が同期が必要なときは、< xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory > を使用して、UI スレッドがブロックされます。 既定のブロックしているモデルには、Rpc が無効にします。 つまり、ある場合は、非同期タスクから RPC を使用しようとすると、するデッドロックは発生 UI スレッドがそれ自体を読み込むパッケージを待機している場合。 一般的な代替手段はのようなものを使用して必要な場合は、UI スレッドにコードをマーシャ リングする**参加可能なタスク ファクトリ**の < xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A > または RPC を使用しないその他の機構です。  使用しないでください**ThreadHelper.Generic.Invoke**または一般的に、UI スレッドへの取得を待機している呼び出し元のスレッドをブロックします。  
  
     注: を使用しないように**GetService**または**QueryService**で、 **InitializeAsync**メソッドです。 使用した場合は最初、UI スレッドに切り替える必要があります。 代替手段がから < xref:Microsoft.VisualStudio.Shell.AsyncServiceProvider.GetServiceAsync%2A > を使用するには、 **AsyncPackage** (キャストして、< xref:Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider > にします)。  
  
 C# の場合: ため、asyncpackage からを作成します。  
  
```c#  
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
  
## <a name="convert-an-existing-vspackage-to-asyncpackage"></a>既存の VSPackage を AsyncPackage に変換します。  
 作業の大部分は、新たに作成すると同じ**AsyncPackage**です。 1 ~ 5 の上記の手順に従う必要があります。 また、次のように慎重を実行する必要があります。  
  
1.  必ず削除してください、**初期化**オーバーライドがパッケージにする必要があります。  
  
2.  デッドロックを回避する: 可能性がある Rpc を非表示に、コードはバック グラウンド スレッドで発生するようになりました。 RPC を作成している場合は、ことを確認する必要があります (例: **GetService**)、いずれか (1) のスイッチはメイン スレッドをする必要がありますか (2) 使用する場合は 1 つの API の非同期バージョンが存在する (例: **GetServiceAsync**)。  
  
3.  頻度が高すぎるのスレッド間で切り替えないでください。 バック グラウンド スレッドで発生することがある作業をローカライズするを再試行してください。 これにより、読み込み時間が短縮されます。  
  
## <a name="querying-services-from-asyncpackage"></a>AsyncPackage からサービスに照会します。  
 **AsyncPackage**でも、呼び出し元によって非同期的に読み込まれないことができます。 例えば  
  
-   呼び出し元が呼び出された場合**GetService**または**QueryService** (両方の同期 Api) または  
  
-   呼び出し元が呼び出された場合**IVsShell::LoadPackage** (または**IVsShell5::LoadPackageWithContext**) または  
  
-   負荷は、UI コンテキストによってトリガーされますが、UI コンテキストのメカニズムが非同期的にロードするを指定していません。  
  
 パッケージは、同期的に読み込まれます。  
  
 その作業の完了をメモするパッケージが営業案件 (非同期の初期化フェーズ) で作業を実行する UI スレッドを関連付けずが UI スレッドがブロックされます。 呼び出し元で使用する場合**IAsyncServiceProvider**サービスの非同期的にクエリを読み込みと初期化を行います非同期的にすぐに結果として得られるタスク オブジェクトをブロックしないと仮定しています。  
  
 C# の場合: サービスに非同期で照会する方法。  
  
```c#  
using Microsoft.VisualStudio.Shell;   
using Microsoft.VisualStudio.Shell.Interop;   
  
IAsyncServiceProvider asyncServiceProvider = Package.GetService(typeof(SAsyncServiceProvider)) as IAsyncServiceProvider;   
IMyTestService testService = await ayncServiceProvider.GetServiceAsync(typeof(SMyTestService)) as IMyTestService;  
```

