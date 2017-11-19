---
title: "ソリューションにプロジェクトの読み込みを管理する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: solutions, managing project loading
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b28db42e17e95ea7c354f5ba4d7b0c231c2d2fe5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="managing-project-loading-in-a-solution"></a>ソリューションで管理するプロジェクトの読み込み
Visual Studio ソリューションには、多数のプロジェクトを含めることができます。 Visual Studio の既定の動作は、ソリューションを開いた時点で、ソリューション内のすべてのプロジェクトを読み込むししないユーザーにそれらのすべての読み込みが終了するまで、プロジェクトのいずれかのアクセスを許可します。 プロジェクトの読み込みプロセスは、2 分以内に最後は、読み込まれているプロジェクトの数とプロジェクトの合計数を示す進行状況バーが表示されます。 ユーザーは複数のプロジェクトをソリューションで作業中にプロジェクトをアンロードすることができますが、この手順ではいくつかの短所: アンロードされたプロジェクトがソリューションのリビルド コマンドの一部としてビルドされていないと、型の説明については IntelliSense およびメンバーの終了プロジェクトには表示されません。  
  
 開発者では、ソリューションの読み込み時間を短縮でき、プロジェクトがソリューションの読み込みのマネージャーを作成することで読み込み動作を管理することができます。 ソリューション負荷マネージャーことができます別のプロジェクトが特定のプロジェクトまたはプロジェクトの種類の優先順位の読み込みを設定、バック グラウンド ビルドを開始する前にプロジェクトが読み込まれているかどうかを確認、その他のバック グラウンド タスクが完了するまでバック グラウンドの読み込みを遅らせるおよび実行他のプロジェクトは管理タスクをロードします。  
  
## <a name="project-loading-priorities"></a>プロジェクトの優先順位の読み込み  
 Visual Studio には、次の 4 つの異なるプロジェクト読み込みの優先度が定義されています。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>(既定): プロジェクトが非同期的に読み込まれる、ソリューションを開いたときにします。 この優先順位は、ソリューションが開いている既にアンロードされたプロジェクトに設定されている場合は、次のアイドル ポイントで、プロジェクトが読み込まれます。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: ユーザーが、すべてのプロジェクトが読み込まれるまで待機することがなく読み込まれたプロジェクトにアクセスできるように、バック グラウンドでのプロジェクトが読み込まれて、ソリューションを開いたときにします。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: アクセスされるときに、プロジェクトは読み込まれます。 一覧で、開いているドキュメント (ソリューションのユーザー オプション ファイルに保持されます) になっているため、ソリューションが開いたときに、プロジェクトに属しているファイルが開かれたとき、または、ユーザーがソリューション エクスプ ローラーでプロジェクト ノードを展開ときに、プロジェクトがアクセスの別のプロジェクト読み込まれているプロジェクトに依存しています。 この種類のプロジェクトがビルド プロセスを開始する前に自動的に読み込まれていませんソリューションの読み込みマネージャーは、必要なすべてのプロジェクトが読み込まれていることを確認します。 これらのプロジェクトは、ソリューション全体におけるファイルの検索と置換を開始する前に読み込む必要があります。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: プロジェクトは、ユーザーが明示的に要求しない限りに読み込まれます。 これは、プロジェクトが明示的にアンロードされたときに、ケースです。  
  
## <a name="creating-a-solution-load-manager"></a>ソリューションの読み込みのマネージャーを作成します。  
 開発者マネージャーを作成できるソリューションの読み込みを実装して<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager>へ助言を行う Visual Studio ソリューション負荷マネージャーがアクティブであるとします。  
  
#### <a name="activating-a-solution-load-manager"></a>ソリューションの負荷マネージャーのアクティブ化  
 Visual Studio により 1 つだけソリューション ロード manager 特定の時点で、ソリューションの読み込みを有効にするときに、Visual Studio をアドバイスする必要がありますので manager できます。 2 番目のソリューション負荷マネージャーが後でアクティブな場合は、ソリューションの負荷マネージャーが切断されます。  
  
 取得する必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>サービスを提供し、設定、<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>プロパティ。  
  
```csharp  
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;  
object objLoadMgr = this;   //the class that implements IVsSolutionManager  
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);  
```  
  
#### <a name="implementing-ivssolutionloadmanager"></a>IVsSolutionLoadManager を実装します。  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnBeforeOpenProject%2A>ソリューションを開いた場合の処理中にメソッドが呼び出されます。 このメソッドを実装するには、使用する、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManagerSupport>サービスを管理するプロジェクトの種類の負荷の優先順位を設定します。 たとえば、次のコードは、c# プロジェクトの種類をバック グラウンドで読み込むを設定します。  
  
```csharp  
Guid guidCSProjectType = new Guid("{FAE04EC0-301F-11d3-BF4B-00C04F79EFBC}");  
pSLMgrSupport.SetProjectLoadPriority(guidProjectID, (uint)_VSProjectLoadPriority.PLP_BackgroundLoad);  
```  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A>メソッドは、Visual Studio がシャット ダウンされるとき、または別のパッケージが引き継いでアクティブなソリューション負荷マネージャーとして呼び出すことによってしたときに呼び出されますが<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A>で、<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>プロパティです。  
  
#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>ソリューションのさまざまな種類の戦略がマネージャーを読み込む  
 ソリューション ロード マネージャーを管理するものであるソリューションの種類に応じて、さまざまな方法で実装できます。  
  
 ソリューションの負荷マネージャー ソリューションの通常の読み込みを管理するものでは場合、は、VSPackage の一部として実装することができます。 パッケージを追加することによって autoload に設定する必要があります、<xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>の値は、VSPackage で<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid>です。 ソリューション負荷マネージャーをアクティブ化できますし、<xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>メソッドです。  
  
> [!NOTE]
>  自動読み込みパッケージの詳細については、次を参照してください。[読み込み Vspackage](../extensibility/loading-vspackages.md)です。  
  
 Visual Studio には、前回ソリューション ロード マネージャーのみをアクティブ化が認識しているので負荷マネージャーの一般的なソリューションは常を検出自身をアクティブ化する前に、既存のロード マネージャーがあるかどうか。 に対するサービスのソリューション GetProperty() を呼び出している場合は<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>返します`null`、負荷マネージャーのアクティブなソリューションはありません。 Null は返しません場合、は、オブジェクトは、ソリューションの負荷マネージャーと同じかどうかを確認します。  
  
 ソリューション負荷マネージャーは、いくつかの種類のソリューションのみを管理することを意図した場合、VSPackage は、ソリューションの読み込みイベントにサブスクライブできます (を呼び出して<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>)、対応するイベント ハンドラーを使用して<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>ソリューション負荷マネージャーをアクティブ化します。  
  
 ソリューション負荷マネージャーが特定のソリューションを管理することを意図した場合、は、ソリューション ファイルの一部として、アクティブ化情報を永続化できます。 これを行うには、呼び出す<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A>前のソリューション セクションのです。  
  
 自体で特定のソリューションの読み込みのマネージャーを非アクティブ化、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A>イベント ハンドラー、他のソリューションの読み込みマネージャーと競合しないようにします。  
  
 グローバル プロジェクト読み込みの優先度 (プロパティ、オプション ページで設定など) を保持するためのソリューションの読み込みマネージャーをアクティブにできるだけソリューション負荷マネージャーが必要な場合、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>イベント ハンドラーで、ソリューションのプロパティの設定を保持ソリューションの負荷マネージャーを非アクティブ化します。  
  
## <a name="handling-solution-load-events"></a>ソリューションの読み込みイベントの処理  
 ソリューションの読み込みイベントをサブスクライブする<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>ソリューション負荷の上司をアクティブにする場合。 実装する場合<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents>、別のプロジェクトの優先順位の読み込みに関連するイベントに応答することができます。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: これは、ソリューションが開かれる前に発生します。 ソリューション内のプロジェクトの優先順位を読み込み、プロジェクトを変更するのにには、これを使用できます。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: これは、解決するには完全に読み込まれるが、バック グラウンドの前にプロジェクトの読み込みをもう一度開始後に発生します。 たとえば、ユーザー ロード優先度が LoadIfNeeded、プロジェクトがアクセスした可能性がまたはソリューション負荷マネージャー可能性があります変更されてプロジェクト読み込みの優先度 BackgroundLoad で、そのプロジェクトのバック グラウンド読み込みを開始します。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: これが発生した、ソリューションは、最初に完全に読み込まれた後、ソリューションの負荷マネージャーがあるかどうか。 バック グラウンド ロードまたは必要に応じて読み込むと、ソリューションが完全に読み込まれるたびにも発生します。 同時に、<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid>の再アクティブ化します。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: これは、、または複数のプロジェクト) の読み込みの前に発生します。 プロジェクトが読み込まれる前に、他のバック グラウンド プロセスが完了したことには、次のように設定します。`pfShouldDelayLoadToNextIdle`に**true**です。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: これは、プロジェクトのバッチが読み込まれるときに発生します。 場合`fIsBackgroundIdleBatch`が true の場合、プロジェクトが読み込まれる; バック グラウンドで場合`fIsBackgroundIdleBatch`が false の場合、プロジェクトが読み込まれる同期的に要求の結果として、ユーザー、たとえば、ユーザーがソリューション エクスプ ローラーで保留中のプロジェクトを展開するかどうかは。 これで完了するようにそれを必要とする高価な作業を行うために実装することができます<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>です。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: これは、プロジェクトのバッチが読み込まれた後に発生します。  
  
## <a name="detecting-and-managing-solution-and-project-loading"></a>検出して、ソリューションとプロジェクトの読み込みを管理します。  
 プロジェクトおよびソリューションの読み込み状態を検出するために呼び出す<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A>次の値。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>:`var`返します`true`ソリューションとそのすべてのプロジェクトは読み込まれている場合、それ以外の場合`false`です。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>:`var`返します`true`かどうか、バッチのプロジェクトの中に現在読み込まれて、バック グラウンドそれ以外の場合`false`です。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>:`var`返します`true`かどうかのプロジェクトのバッチが現在読み込まれて同期的に、user コマンドまたはその他の明示的なロードの結果としてそれ以外の場合`false`です。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>:`var`返します`true`場合は、ソリューションは現在閉じられて、それ以外の場合`false`です。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>:`var`返します`true`ソリューション現在開いている場合は、それ以外の場合`false`です。  
  
 また、(プロジェクトの読み込みの優先度とは) に関係なく、プロジェクトおよびソリューションが読み込まれているを呼び出して次のいずれかの。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: このメソッドを呼び出して強制的に、メソッドを返します前に、読み込むソリューション内のプロジェクトです。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: 強制的内のプロジェクトにこのメソッドを呼び出す`guidProject`を読み込む前に、このメソッドを返します。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: このメソッドを呼び出すことで、プロジェクトを強制的`guidProjectID`を読み込む前に、このメソッドを返します。  
  
> [!NOTE]
>  。 既定では、要求のプロジェクトのみを読み込んで場合は、バック グラウンド読み込みの優先順位が読み込まれる、<xref:Microsoft.VisualStudio.Shell.Interop.__VSBSLFLAGS>フラグがメソッドに渡された、明示的に読み込むとしてマークされているものを除くすべてのプロジェクトが読み込まれます。