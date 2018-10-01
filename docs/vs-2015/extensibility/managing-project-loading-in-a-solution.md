---
title: ソリューション内のプロジェクトの読み込みを管理する |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- solutions, managing project loading
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: dab040cc22375244d0a091eeb63d8ad011c3b12f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47535342"
---
# <a name="managing-project-loading-in-a-solution"></a>ソリューションでのプロジェクトの読み込みの管理
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ソリューションでプロジェクトの読み込みを管理する](https://docs.microsoft.com/visualstudio/extensibility/managing-project-loading-in-a-solution)します。  
  
Visual Studio ソリューションには、多数のプロジェクトを含めることができます。 Visual Studio の既定の動作は、ソリューションが開かれたときに、ソリューション内のすべてのプロジェクトを読み込むと、ユーザーにそれらのすべての読み込みが終了するまで、プロジェクトのいずれかのアクセスを許可しません。 プロジェクトの読み込みのプロセスが最後に 2 分以内、読み込まれているプロジェクトの数とプロジェクトの合計数を示す進行状況バーが表示されます。 ユーザーは、複数のプロジェクトをソリューションで作業中にプロジェクトをアンロードできますが、この手順ではいくつかのデメリット: アンロードされたプロジェクトは、ソリューションのリビルド コマンドの一部として組み込まれていないと、型の説明については IntelliSense およびメンバーの終了プロジェクトは表示されません。  
  
 開発者は、ソリューションの読み込み時間を短縮し、プロジェクト マネージャー ソリューション ロードを作成して読み込み動作を管理できます。 ソリューション ロード マネージャーできます特定のプロジェクトまたはプロジェクトの種類の優先順位を読み込む別のプロジェクトの設定、バック グラウンドのビルドを開始する前に、プロジェクトが読み込まれているかどうかを確認、バック グラウンド読み込みの他のバック グラウンド タスクが完了するまでの遅延および実行その他のプロジェクトは管理タスクをロードします。  
  
## <a name="project-loading-priorities"></a>プロジェクトの読み込みの優先順位  
 Visual Studio では、4 つの異なるプロジェクト読み込みの優先度を定義します。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority> (既定値): プロジェクトが非同期的に読み込まれているソリューションが開かれたときにします。 この優先順位は、ソリューションが開いている既にアンロードされたプロジェクトに設定されている場合は、[次へ] のアイドル ポイントに、プロジェクトが読み込まれます。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: ユーザーがすべてのプロジェクトが読み込まれるまで待機することがなくに読み込まれると、プロジェクトにアクセスできるように、バック グラウンドで、プロジェクトが読み込まれたソリューションが開かれたときにします。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: アクセスされるときに、プロジェクトが読み込まれます。 (ソリューションのユーザー オプション ファイルに保存されます)、開いているドキュメント一覧されているため、ソリューションが開いたときに、プロジェクトに属するファイルを開くとき、またはユーザーがソリューション エクスプ ローラーでプロジェクト ノードを展開時に、プロジェクトはアクセスが別のプロジェクト読み込まれているプロジェクトに依存しています。 この種類のプロジェクトがビルド プロセスを開始する前に自動的に読み込まれていません。ソリューション ロード マネージャーは、必要なすべてのプロジェクトが読み込まれていることを確認します。 これらのプロジェクトがソリューション全体におけるファイルの検索と置換を開始する前に読み込むことも必要があります。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: プロジェクトは、ユーザーが明示的に要求しない限り読み込まれます。 これは、プロジェクトは、明示的にアンロードされるときに、大文字と小文字です。  
  
## <a name="creating-a-solution-load-manager"></a>ソリューションの読み込みのマネージャーを作成します。  
 開発者はマネージャーを作成ソリューション ロードを実装して<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager>アドバイスして Visual Studio ソリューション読み込みのマネージャーがアクティブであるとします。  
  
#### <a name="activating-a-solution-load-manager"></a>ソリューション読み込みのマネージャーをアクティブ化します。  
 Visual Studio でソリューション ロードの 1 つだけのマネージャー特定の時点であるため、ソリューションの読み込みを有効にするときに、Visual Studio をお勧めする必要がありますマネージャー。 2 つ目のソリューション ロード マネージャーが後でアクティブの場合は、ソリューション ロードの上司が切断されます。  
  
 取得する必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>サービスし、設定、<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>プロパティ。  
  
```csharp  
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;  
object objLoadMgr = this;   //the class that implements IVsSolutionManager  
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);  
```  
  
#### <a name="implementing-ivssolutionloadmanager"></a>IVsSolutionLoadManager を実装します。  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnBeforeOpenProject%2A>のソリューションを開くプロセス中にメソッドが呼び出されます。 このメソッドを実装するには、使用する、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManagerSupport>サービスを管理するプロジェクトの種類の読み込みの優先順位を設定します。 たとえば、次のコードは、c# プロジェクトの種類をバック グラウンドで読み込むを設定します。  
  
```csharp  
Guid guidCSProjectType = new Guid("{FAE04EC0-301F-11d3-BF4B-00C04F79EFBC}");  
pSLMgrSupport.SetProjectLoadPriority(guidProjectID, (uint)_VSProjectLoadPriority.PLP_BackgroundLoad);  
```  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A> Visual Studio のシャット ダウン時、または呼び出すことによって、アクティブなソリューション ロードのマネージャーとしての 経由で、別のパッケージが実行したときに、メソッドが呼び出されます<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A>で、<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>プロパティ。  
  
#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>さまざまな種類のソリューション読み込みのマネージャーのための戦略  
 ソリューション読み込みのマネージャーは、ソリューションを管理するが、これらの種類に応じて、さまざまな方法で実装できます。  
  
 ソリューション読み込みのマネージャーは、一般に読み込みソリューションを管理するものでは場合、は、VSPackage の一部として実装することができます。 パッケージを追加することで autoload に設定する必要があります、<xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>の値は、VSPackage に<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid>します。 ソリューション ロードのマネージャーをアクティブにできるし、<xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>メソッド。  
  
> [!NOTE]
>  自動読み込みパッケージの詳細については、次を参照してください。 [Vspackage の読み込み](../extensibility/loading-vspackages.md)します。  
  
 Visual Studio で認識、前回ソリューション ロード マネージャーのみを有効にするため負荷マネージャーの全般的なソリューションは自身のアクティブ化する前に既存のロード マネージャーがあるかどうか検出は常に。 ソリューションのサービスに対する GetProperty() を呼び出す場合<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>返します`null`、負荷マネージャーのアクティブなソリューションはありません。 これが null を返さない場合は、オブジェクトは、ソリューション ロードのマネージャーと同じかどうかを確認します。  
  
 ソリューション読み込みのマネージャーは、ソリューションのいくつかの型のみを管理するものでは場合、VSPackage は、ソリューションの読み込みイベントをサブスクライブできます (呼び出して<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>)、イベントのイベント ハンドラーを使用して<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>ソリューション ロードのマネージャーをアクティブ化します。  
  
 ソリューション読み込みのマネージャーは、特定のソリューションのみを管理するものでは場合、は、ソリューション ファイルの一部としてアクティブ化の情報を保持できます。 これを行うには、呼び出す<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A>前のソリューション セクション。  
  
 特定のソリューション読み込みの管理者を自身で非アクティブ化、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A>他のソリューション読み込みのマネージャーと競合しないように、イベント ハンドラー。  
  
 グローバル プロジェクト読み込みの優先順位 (プロパティのオプション ページの設定など) を保持するためのソリューション ロードのマネージャーをアクティブ化できますのみソリューション ロードのマネージャーが必要な場合、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents2.OnAfterOpenProject%2A>イベント ハンドラーで、ソリューションのプロパティの設定を永続化ソリューション読み込みのマネージャーが非アクティブ化します。  
  
## <a name="handling-solution-load-events"></a>ソリューションの読み込みイベントの処理  
 ソリューション読み込みのイベントをサブスクライブする<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>上司ソリューション ロードをアクティブにする場合。 実装する場合<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents>、読み込みの優先度別のプロジェクトに関連するイベントに応答できます。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: これは、ソリューションが開かれる前に発生します。 ソリューション内のプロジェクトの優先順位を読み込み、プロジェクトを変更するのにには、これを使用できます。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: これは、ソリューションが完全に読み込まれたですが、バック グラウンドの前にプロジェクトの読み込みをもう一度開始後に発生します。 などのロード優先度が LoadIfNeeded、プロジェクトにアクセスしたユーザーまたはソリューション ロード マネージャーは、BackgroundLoad で、そのプロジェクトのバック グラウンド読み込みを開始するようにプロジェクトの読み込みの優先順位変更可能性があります。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: これが発生した、ソリューションが最初に完全に読み込まれた後ソリューション ロードのマネージャーがあるかどうか。 これは、ソリューションが完全に読み込まれるたびに、バック グラウンド負荷または需要が読み込まれた後も発生します。 同時に、<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid>が再アクティブ化します。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: これは、プロジェクト (またはプロジェクト) の読み込み前に発生します。 プロジェクトが読み込まれる前に、その他のバック グラウンド プロセスが完了したことを確認するには設定`pfShouldDelayLoadToNextIdle`に**true**します。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: これは、プロジェクトのバッチが読み込まれるときに発生します。 場合`fIsBackgroundIdleBatch`が true の場合、プロジェクトが読み込まれる。 バック グラウンドで場合`fIsBackgroundIdleBatch`が false の場合、プロジェクトが読み込まれる、ユーザーの要求の結果として同期的になど、ユーザーがソリューション エクスプ ローラーでの保留中のプロジェクトを展開する場合は。 これで実行する必要がありますそれ以外の場合のコストの作業を行うを実装する<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>します。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: これは、プロジェクトのバッチが読み込まれた後に発生します。  
  
## <a name="detecting-and-managing-solution-and-project-loading"></a>検出および管理ソリューションとプロジェクトの読み込み  
 プロジェクトとソリューションの読み込み状態を検出するために呼び出す<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A>次の値。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>:`var`返します`true`ソリューションとそのすべてのプロジェクトが読み込まれている場合、それ以外の場合`false`します。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>:`var`返します`true`かどうかのプロジェクトのバッチが現在読み込まれる、バック グラウンドでそれ以外の場合`false`します。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>:`var`返します`true`かどうかのプロジェクトのバッチが現在読み込み中に同期的にユーザー コマンドまたはその他の明示的な読み込み、結果としてそれ以外の場合`false`します。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>:`var`返します`true`ソリューションが現在されて閉じられた場合、それ以外の場合`false`します。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>:`var`返します`true`ソリューションが現在いる開かれた場合、それ以外の場合`false`します。  
  
 (プロジェクトの読み込みの優先度とは) 場合でも、プロジェクトとソリューションが読み込まれているを確認、次のメソッドのいずれかを呼び出すことができますも。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: このメソッドが強制的に読み込むメソッドが戻る前に、ソリューション内のプロジェクト。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: このメソッドを呼び出すことでプロジェクトを強制的`guidProject`メソッドが戻る前に読み込めません。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: このメソッドを呼び出すことで、プロジェクトを強制的`guidProjectID`メソッドが戻る前に読み込めません。  
  
> [!NOTE]
>  . 既定では、必要に応じて、プロジェクトのみを読み込むし、場合は、バック グラウンド読み込みの優先順位が読み込まれて、<xref:Microsoft.VisualStudio.Shell.Interop.__VSBSLFLAGS>フラグ メソッドに渡されるを明示的に読み込むとマークされているもの以外のすべてのプロジェクトが読み込まれます。

