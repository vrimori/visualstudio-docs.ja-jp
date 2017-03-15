---
title: "方法: AsyncPackage を使用して、バック グラウンドである Vspackage を読み込む | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dedf0173-197e-4258-ae5a-807eb3abc952
caps.latest.revision: 8
ms.author: "gregvanl"
caps.handback.revision: 8
---
# 方法: AsyncPackage を使用して、バック グラウンドである Vspackage を読み込む
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

読み込んで VS パッケージを初期化するディスク I\/O が発生します。 このような I\/O は、UI スレッドでは、応答性の問題になることができます。 これに対処するために Visual Studio 2015 で、 <xref:Microsoft.VisualStudio.Shell.AsyncPackage> バック グラウンド スレッドでパッケージの読み込みをできるようにするクラス。  
  
## AsyncPackage を作成します。  
 VSIX プロジェクトを作成することができます \(**ファイル\/\[新しい\/プロジェクト\/Visual c\#\/機能拡張\/VSIX プロジェクト**\) VSPackage をプロジェクトに追加して \(、プロジェクトを右クリックし、 **追加\]、\[新しい項目\/c\# 項目\/拡張機能\/visual Studio パッケージ**\)。 サービスを作成し、それらのサービスをパッケージに追加することができます。  
  
1.  パッケージからの派生 <xref:Microsoft.VisualStudio.Shell.AsyncPackage>します。  
  
2.  サービスのクエリを実行する場合、パッケージを読み込むがあります。 指定する場合  
  
     この動作を選択して、パッケージがバック グラウンド読み込みに対して安全である Visual Studio に示すために、 <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> 設定する必要があります **AllowsBackgroundLoading** 属性コンス トラクターで true に設定します。  
  
    ```c#  
    [PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]  
  
    ```  
  
     Visual Studio にバック グラウンド スレッドで、サービスのインスタンスを作成しても安全であると示さに設定する必要があります、 <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttributeBase.IsAsyncQueryable%2A> プロパティを true に、 <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> コンス トラクターです。  
  
    ```c#  
    [ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]  
  
    ```  
  
3.  UI のコンテキストを使用する読み込もうとしているかどうかは、指定する必要があります **PackageAutoLoadFlags.BackgroundLoad** の <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> またはフラグに値 \(0x2\)、パッケージを自動的に読み込むエントリの値として書き込まれます。  
  
    ```c#  
    [ProvideAutoLoad(UIContextGuid, PackageAutoLoadFlags.BackgroundLoad)]  
  
    ```  
  
4.  オーバーライドする場合は、非同期初期化処理がある場合は、 <xref:Microsoft.VisualStudio.Shell.AsyncPackage.InitializeAsync%2A>です。 削除、 **Initialize\(\)** VSIX のテンプレートによって提供されるメソッドです。 \(、 **Initialize\(\)** メソッド **AsyncPackage** が封印されている\)。 いずれかを使用することができます、 <xref:Microsoft.VisualStudio.Shell.AsyncPackage.AddService%2A> 非同期のサービスをパッケージに追加する方法です。  
  
     注:を呼び出す **ベースです。InitializeAsync\(\)**, 、ソース コードを変更することができます。  
  
    ```c#  
    await base.InitializeAsync(cancellationToken, progress);  
    ```  
  
5.  必要があります \(削除プロシージャ コール\) の Rpc に加えないで非同期初期化コードから \(で **InitializeAsync**\)。 これらを呼び出すときに発生することが <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> 直接的または間接的にします。  使用して、UI スレッドをブロック負荷が同期が必要なときは、 <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>です。 既定のブロックしているモデルには、Rpc が無効にします。 つまり、非同期タスクから RPC を使用しようとすると、するデッドロックは発生、UI スレッドがそれ自体を読み込むパッケージを待機している場合。 一般的な代替手段はのようなものを使用するために必要な場合、コードを UI スレッドにマーシャ リングする **結合可能タスク ファクトリ**の <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> または RPC を使用しないその他のメカニズムです。  使用しないで **ThreadHelper.Generic.Invoke** または一般的に、UI スレッドへを待機して呼び出し元のスレッドをブロックします。  
  
     注: を使用しないように **GetService** または **QueryService** で、 **InitializeAsync** メソッドです。 それらがある場合は最初に、UI スレッドに切り替える必要があります。 使用する方法、 <xref:Microsoft.VisualStudio.Shell.AsyncServiceProvider.GetServiceAsync%2A> から、 **AsyncPackage** \(にキャストして <xref:Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider>.\)  
  
 C\# の場合: AsyncPackage を作成します。  
  
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
  
## AsyncPackage を既存の VSPackage に変換します。  
 処理の大部分は、新しいを作成すると同じ **AsyncPackage**します。 1 ~ 5 の上記の手順に従う必要があります。 次のように慎重を実行する必要があります。  
  
1.  必ず削除してください、 **初期化** 上書きが、パッケージにする必要があります。  
  
2.  デッドロックを回避: 可能性がある Rpc を非表示に、コードはバック グラウンド スレッドで発生するようになりました。 RPC を行っている場合を確認する必要があります \(例: **GetService**\) いずれか \(1\) メイン スレッドに切り替える必要がある、または \(2\) 使用する場合は、1 つの API の非同期バージョンが存在する \(例: **GetServiceAsync**\)。  
  
3.  頻度が高すぎるのスレッド間で切り替えられない。 バック グラウンド スレッドで発生することがある作業をローカライズしてください。 読み込み時間を短縮できます。  
  
## AsyncPackage からサービスに照会します。  
 **AsyncPackage** 、呼び出し元によって非同期的に読み込まれないことができます。 たとえば、  
  
-   呼び出し元が呼び出された場合 **GetService** または **QueryService** \(両方の同期 Api\) または  
  
-   呼び出し元が呼び出された場合 **IVsShell::LoadPackage** \(または **IVsShell5::LoadPackageWithContext**\) または  
  
-   負荷は、UI コンテキストによってトリガーされますが、UI コンテキストのメカニズムが非同期的にロードするが指定されていません  
  
 パッケージは、同期的に読み込まれます。  
  
 注パッケージされていること、機会 \(非同期の初期化フェーズ\) で作業を実行する UI スレッドが UI スレッドは、その作業の完了がブロックされます。 呼び出し元で使用する場合 **IAsyncServiceProvider** するために、サービスの非同期的にクエリし、ロード テストおよび初期化が行う非同期的に結果として得られるタスク オブジェクトですぐにブロックしないと仮定しています。  
  
 C\# の場合: サービスに非同期的に照会する方法。  
  
```c#  
using Microsoft.VisualStudio.Shell;   
using Microsoft.VisualStudio.Shell.Interop;   
  
IAsyncServiceProvider asyncServiceProvider = Package.GetService(typeof(SAsyncServiceProvider)) as IAsyncServiceProvider;   
IMyTestService testService = await ayncServiceProvider.GetServiceAsync(typeof(SMyTestService)) as IMyTestService;  
```