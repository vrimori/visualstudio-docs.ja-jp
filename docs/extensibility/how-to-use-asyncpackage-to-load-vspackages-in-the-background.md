---
title: '方法: AsyncPackage を使用して、バック グラウンドで Vspackage を読み込む |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.technology: vs-ide-sdk
ms.assetid: dedf0173-197e-4258-ae5a-807eb3abc952
author: gregvanl
ms.author: gregvanl
ms.workload:
- vssdk
ms.openlocfilehash: bc014b2072c5e6472d17095f0c0789c35116a3c6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-use-asyncpackage-to-load-vspackages-in-the-background"></a>方法: AsyncPackage を使用して、バック グラウンドで Vspackage を読み込む
読み込みと初期化 VS パッケージは、ディスク I/O になります。 UI スレッドでこのような I/O が発生した場合、応答性の問題になることができます。 これに対処するには、Visual Studio 2015 が導入された、<xref:Microsoft.VisualStudio.Shell.AsyncPackage>をバック グラウンド スレッドでパッケージの読み込みを有効にするクラス。  
  
## <a name="creating-an-asyncpackage"></a>作成するため、asyncpackage から  
 VSIX プロジェクトを作成することができます (**ファイル > 新規 > プロジェクト > Visual c# > 機能拡張 > VSIX プロジェクト**) VSPackage をプロジェクトに追加して (プロジェクトを右クリックし、**追加/新規項目/c# 項目/Extensibility/Visual Studio パッケージ**)。 サービスを作成し、それらのサービスをパッケージに追加できます。  
  
1.  パッケージを派生させる<xref:Microsoft.VisualStudio.Shell.AsyncPackage>です。  
  
2.  場合は、パッケージを読み込むが発生する可能性がありますがクエリを実行するサービスを提供します。  
  
     この動作を選択して、パッケージがバック グラウンドで読み込まないに対して安全である Visual Studio に示すために、<xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>設定する必要があります**AllowsBackgroundLoading**属性コンス トラクターで true に設定します。  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]  
  
    ```  
  
     Visual Studio にあることを示す、サービス、バック グラウンド スレッドでインスタンス化に設定する必要があります、<xref:Microsoft.VisualStudio.Shell.ProvideServiceAttributeBase.IsAsyncQueryable%2A>プロパティを true に、<xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>コンス トラクターです。  
  
    ```csharp  
    [ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]  
  
    ```  
  
3.  UI コンテキスト経由で読み込もうとしているかどうかは、指定する必要があります**PackageAutoLoadFlags.BackgroundLoad**の<xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>またはフラグに値 (0x2)、パッケージの自動読み込みエントリの値として書き込まれます。  
  
    ```csharp  
    [ProvideAutoLoad(UIContextGuid, PackageAutoLoadFlags.BackgroundLoad)]  
  
    ```  
  
4.  オーバーライドする必要がある場合は非同期の初期化作業を行うには、<xref:Microsoft.VisualStudio.Shell.AsyncPackage.InitializeAsync%2A>です。 削除、 **Initialize()** VSIX テンプレートによって提供されるメソッド。 (、 **Initialize()**メソッド**AsyncPackage**が封印されている)。 いずれかを使用することができます、<xref:Microsoft.VisualStudio.Shell.AsyncPackage.AddService%2A>非同期サービスをパッケージに追加する方法です。  
  
     注: 呼び出す**ベースです。InitializeAsync()**、ソース コードを変更することができます。  
  
    ```csharp  
    await base.InitializeAsync(cancellationToken, progress);  
    ```  
  
5.  非同期の初期化コードから Rpc (リモート プロシージャ コール) が作成されないようにする注意する必要があります (で**InitializeAsync**)。 これらを呼び出すときに発生することが<xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>直接的または間接的にします。  使用して、UI スレッドをブロック負荷が同期が必要なときは、<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>です。 既定のブロックしているモデルには、Rpc が無効にします。 つまり、ある場合は、非同期タスクから RPC を使用しようとすると、するデッドロックは発生 UI スレッドがそれ自体を読み込むパッケージを待機している場合。 一般的な代替手段はのようなものを使用して必要な場合は、UI スレッドにコードをマーシャ リングする**参加可能なタスク ファクトリ**の<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>または RPC を使用しないその他の機構です。  使用しないでください**ThreadHelper.Generic.Invoke**または一般に、UI スレッドへの取得を待機している呼び出し元のスレッドをブロックします。  
  
     注: を使用しないように**GetService**または**QueryService**で、 **InitializeAsync**メソッドです。 使用した場合は最初、UI スレッドに切り替える必要があります。 代替手段は、使用する<xref:Microsoft.VisualStudio.Shell.AsyncServiceProvider.GetServiceAsync%2A>から、 **AsyncPackage** (でキャストを<xref:Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider>)。  
  
 C# の場合: ため、asyncpackage からを作成します。  
  
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
  
 その作業の完了をメモするパッケージが営業案件 (非同期の初期化フェーズ) で作業を実行する UI スレッドを関連付けずが UI スレッドがブロックされます。 呼び出し元で使用する場合**IAsyncServiceProvider**サービスの非同期的にクエリし、読み込みと初期化、行われます非同期的にすぐに結果として得られるタスク オブジェクトをブロックしないと仮定しています。  
  
 C# の場合: サービスに非同期で照会する方法。  
  
```csharp  
using Microsoft.VisualStudio.Shell;   
using Microsoft.VisualStudio.Shell.Interop;   
  
IAsyncServiceProvider asyncServiceProvider = Package.GetService(typeof(SAsyncServiceProvider)) as IAsyncServiceProvider;   
IMyTestService testService = await asyncServiceProvider.GetServiceAsync(typeof(SMyTestService)) as IMyTestService;  
```
  
