---
title: ソリューション内のプロジェクトの読み込みを管理する |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- solutions, managing project loading
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2ead4834f1d29baff099eedbf464c1ba6344ca6c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49950200"
---
# <a name="manage-project-loading-in-a-solution"></a>管理ソリューションでプロジェクトの読み込み
Visual Studio ソリューションには、多数のプロジェクトを含めることができます。 Visual Studio の既定の動作は、ソリューションが開かれたときに、ソリューション内のすべてのプロジェクトを読み込むと、ユーザーにそれらのすべての読み込みが終了するまで、プロジェクトのいずれかのアクセスを許可しません。 プロジェクトの読み込みのプロセスが最後に 2 分以内、読み込まれているプロジェクトの数とプロジェクトの合計数を示す進行状況バーが表示されます。 ユーザーは、複数のプロジェクトをソリューションで作業中にプロジェクトをアンロードできますが、この手順ではいくつかのデメリット: アンロードされたプロジェクトは、ソリューションのリビルド コマンドの一部として組み込まれていないと、型の説明については IntelliSense およびメンバーの終了プロジェクトは表示されません。  
  
 開発者は、ソリューションの読み込み時間を短縮し、プロジェクト マネージャー ソリューション ロードを作成して読み込み動作を管理できます。 ソリューション ロード マネージャーでは、バック グラウンドのビルドを開始する前に、プロジェクトが読み込まれているかどうかを確認、バック グラウンド読み込みの他のバック グラウンド タスクが完了するまでの遅延、および他のプロジェクトの負荷の管理タスクを実行できます。  
  
## <a name="create-a-solution-load-manager"></a>マネージャーを作成するには、ソリューションの読み込み  
 開発者はマネージャーを作成ソリューション ロードを実装して<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager>アドバイスして Visual Studio ソリューション読み込みのマネージャーがアクティブであるとします。  
  
### <a name="activate-a-solution-load-manager"></a>ソリューション読み込みのマネージャーをアクティブ化します。  
 Visual Studio でソリューション ロードの 1 つだけのマネージャー特定の時点であるため、ソリューションの読み込みを有効にするときに、Visual Studio をお勧めする必要がありますマネージャー。 2 つ目のソリューション ロード マネージャーが後でアクティブの場合は、ソリューション ロードの上司が切断されます。  
  
 取得する必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>サービスし、設定、<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>プロパティ。  
  
```csharp  
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;  
object objLoadMgr = this;   //the class that implements IVsSolutionManager  
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);  
```  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A> Visual Studio のシャット ダウン時、または呼び出すことによって、アクティブなソリューション ロードのマネージャーとしての 経由で、別のパッケージが実行したときに、メソッドが呼び出されます<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A>で、<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>プロパティ。  
  
#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>さまざまな種類のソリューション読み込みのマネージャーのための戦略  
 ソリューション読み込みのマネージャーは、ソリューションを管理するが、これらの種類に応じて、さまざまな方法で実装できます。  
  
 ソリューション読み込みのマネージャーは、一般に読み込みソリューションを管理するものでは場合、は、VSPackage の一部として実装することができます。 パッケージを追加することで autoload に設定する必要があります、<xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>の値は、VSPackage に<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid>します。 ソリューション ロードのマネージャーをアクティブにできるし、<xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>メソッド。  
  
> [!NOTE]
>  自動読み込みパッケージの詳細については、次を参照してください。 [Vspackage の読み込み](../extensibility/loading-vspackages.md)します。  
  
 Visual Studio で認識、前回ソリューション ロード マネージャーのみを有効にするため負荷マネージャーの全般的なソリューションは自身のアクティブ化する前に既存のロード マネージャーがあるかどうか検出は常に。 呼び出す場合`GetProperty()`ソリューション用サービスに対する<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>返します`null`、負荷マネージャーのアクティブなソリューションはありません。 これが null を返さない場合は、オブジェクトは、ソリューション ロードのマネージャーと同じかどうかを確認します。  
  
 ソリューション読み込みのマネージャーは、ソリューションのいくつかの型のみを管理するものでは場合、VSPackage は、ソリューションの読み込みイベントをサブスクライブできます (呼び出して<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>)、イベントのイベント ハンドラーを使用して<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>ソリューション ロードのマネージャーをアクティブ化します。  
  
 アクティブ化の情報を呼び出すことによって、ソリューション ファイルの一部として保持できますソリューション ロード マネージャーは、特定のソリューションのみを管理するものでは場合、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A>前のソリューション セクション。  
  
 特定のソリューション読み込みの管理者を自身で非アクティブ化、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A>他のソリューション読み込みのマネージャーと競合しないように、イベント ハンドラー。  
  
 プロジェクトのグローバル ロード プロパティ (プロパティのオプション ページの設定など) を保持するためのソリューション ロードのマネージャーをアクティブ化できますのみソリューション ロードのマネージャーが必要な場合、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>イベント ハンドラーで、ソリューションのプロパティの設定を永続化ソリューション読み込みのマネージャーが非アクティブ化します。  
  
## <a name="handle-solution-load-events"></a>ソリューションの読み込みイベントを処理します。  
 ソリューション読み込みのイベントをサブスクライブする<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>上司ソリューション ロードをアクティブにする場合。 実装する場合<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents>、別のプロジェクト プロパティの読み込みに関連するイベントに応答できます。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: このイベントは、ソリューションが開かれる前に発生します。
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>します。 解決するには、完全に読み込まれるが、バック グラウンドの前にプロジェクトの読み込みをもう一度開始このイベントが発生します。
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: ソリューション読み込みのマネージャーがあるかどうか、ソリューションが最初に完全に読み込まれた後このイベントが発生しました。 これは、ソリューションが完全に読み込まれるたびに、バック グラウンド負荷または需要が読み込まれた後も発生します。 同時に、<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid>が再アクティブ化します。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: このイベントは、プロジェクト (またはプロジェクト) の読み込み前に発生します。 プロジェクトが読み込まれる前に、その他のバック グラウンド プロセスが完了したことを確認するには設定`pfShouldDelayLoadToNextIdle`に**true**します。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: このイベントは、プロジェクトのバッチが読み込まれるときに発生します。 場合`fIsBackgroundIdleBatch`が true の場合、プロジェクトが読み込まれる。 バック グラウンドで場合`fIsBackgroundIdleBatch`が false の場合、プロジェクトが読み込まれる、ユーザーの要求の結果として同期的になど、ユーザーがソリューション エクスプ ローラーでの保留中のプロジェクトを展開する場合は。 実行する必要がありますそれ以外の場合のコストの作業を行うには、このイベントを処理できる<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>します。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: このイベントは、プロジェクトのバッチが読み込まれた後に発生します。  
  
## <a name="detect-and-manage-solution-and-project-loading"></a>検出して管理ソリューションとプロジェクトの読み込み  
 プロジェクトとソリューションの読み込み状態を検出するために呼び出す<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A>次の値。  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>:`var`返します`true`ソリューションとそのすべてのプロジェクトが読み込まれている場合、それ以外の場合`false`します。  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>:`var`返します`true`かどうかのプロジェクトのバッチが現在読み込まれる、バック グラウンドでそれ以外の場合`false`します。  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>:`var`返します`true`かどうかプロジェクトのバッチが現在が読み込まれる同期的に結果として、ユーザー コマンドやその他の明示的な読み込み、それ以外の場合`false`します。  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>:`var`返します`true`ソリューションが現在されて閉じられた場合、それ以外の場合`false`します。  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>:`var`返します`true`ソリューションが現在いる開かれた場合、それ以外の場合`false`します。  
  
  次の方法の 1 つを呼び出すことによって、プロジェクトとソリューションが読み込まれていることを確認できます。  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: このメソッドが強制的に読み込むメソッドが戻る前に、ソリューション内のプロジェクト。  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: このメソッドを呼び出すことでプロジェクトを強制的`guidProject`メソッドが戻る前に読み込めません。  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: このメソッドを呼び出すことで、プロジェクトを強制的`guidProjectID`メソッドが戻る前に読み込めません。  
