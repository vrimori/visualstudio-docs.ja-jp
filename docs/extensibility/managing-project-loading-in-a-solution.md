---
title: "ソリューションにプロジェクトの読み込みを管理します。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ソリューション、プロジェクトの読み込みを管理します。"
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# ソリューションにプロジェクトの読み込みを管理します。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio ソリューションには、多数のプロジェクトを含めることができます。 Visual Studio の既定の動作は、ソリューションを開いた時に、ソリューション内のすべてのプロジェクトを読み込むと、ユーザーはそれらのすべての読み込みが終了するまで、プロジェクトのいずれかのアクセスを許可しないです。 プロジェクトの読み込みプロセスは、2 分以内に最後は、読み込まれているプロジェクトの数とプロジェクトの合計数を示す進行状況バーが表示されます。 ユーザーは複数のプロジェクトをソリューションで作業中にプロジェクトをアンロードすることができますが、この手順ではいくつかのデメリット: アンロードされたプロジェクトがソリューションのリビルド コマンドの一部としてビルドされていないと、IntelliSense 型の記述と閉じたプロジェクトのメンバーは表示されません。  
  
 開発者は、ソリューションの読み込み時間を削減し、プロジェクトがソリューションの読み込みのマネージャーを作成することで読み込み動作を管理できます。 ソリューション負荷マネージャーは、特定のプロジェクトまたはプロジェクトの種類の優先順位を読み込む別のプロジェクトを設定、バック グラウンドのビルドを開始する前に、プロジェクトが読み込まれているように、バック グラウンド読み込みの他のバック グラウンド タスクが完了するまでの遅延、および他のプロジェクトの読み込みの管理タスクを実行ことができます。  
  
## プロジェクトの優先順位の読み込み  
 Visual Studio には、次の 4 つの別のプロジェクトの読み込みの優先順位が定義されています。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority> \(既定値\): プロジェクトが非同期的に読み込まれて、ソリューションを開いたときです。 この優先順位は、ソリューションが開いている既にアンロードされたプロジェクトに設定されている場合は、次のアイドル ポイントで、プロジェクトが読み込まれます。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: ユーザーがすべてのプロジェクトが読み込まれるまで待機することがなく読み込まれると、プロジェクトにアクセスを許可するバック グラウンドでのプロジェクトが読み込まれて、ソリューションを開いたときです。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: アクセス時にプロジェクトが読み込まれています。 ソリューションを開く \(ソリューションのユーザー オプション ファイルに保持されます\)、開いているドキュメントの一覧に表示されているため、プロジェクトに属するファイルを開いたときに、ユーザーがソリューション エクスプ ローラーでプロジェクト ノードを展開時に、プロジェクトがアクセスまたは別のプロジェクトに当てはまるは、プロジェクトに依存している読み込まれています。 ビルド プロセスを開始する前に、この種類のプロジェクトが自動的に読み込まれないソリューション負荷マネージャーは、必要なすべてのプロジェクトが読み込まれていることを防ぐ責任です。 これらのプロジェクトは、ソリューション全体のファイルの検索と置換を開始する前に読み込む必要があります。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: プロジェクトは、ユーザーが明示的に要求しない限り読み込まれます。 これは、プロジェクトは、明示的に読み込まれたときに、大文字と小文字です。  
  
## ソリューションの読み込みのマネージャーを作成します。  
 開発者マネージャーを作成できるソリューションの読み込みを実装して <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> ソリューション負荷マネージャーがアクティブである Visual Studio をようアドバイスします。  
  
#### ソリューションの負荷マネージャーのアクティブ化  
 Visual Studio では、1 つだけのソリューション負荷マネージャー、特定の時点でためソリューションの読み込みを有効にする場合は、Visual Studio を通知する必要がありますマネージャー。 2 つ目のソリューション負荷マネージャーを後でアクティブな場合は、ソリューションの負荷マネージャーが切断されます。  
  
 取得する必要があります、 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> サービスを提供し、設定、 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> プロパティ。  
  
```c#  
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution; object objLoadMgr = this;   //the class that implements IVsSolutionManager pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);  
```  
  
#### IVsSolutionLoadManager を実装します。  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnBeforeOpenProject%2A> ソリューションを開くの処理中に呼び出されます。 このメソッドを実装するには、使用する、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManagerSupport> サービスに管理するプロジェクトの種類の読み込みの優先順位を設定します。 たとえば、次のコードは、c\# プロジェクトの種類をバック グラウンドで読み込むを設定します。  
  
```c#  
Guid guidCSProjectType = new Guid("{FAE04EC0-301F-11d3-BF4B-00C04F79EFBC}"); pSLMgrSupport.SetProjectLoadPriority(guidProjectID, (uint)_VSProjectLoadPriority.PLP_BackgroundLoad);  
```  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A> Visual Studio がシャット ダウンされるとき、または別のパッケージに引き継がれたアクティブなソリューション負荷マネージャーとして呼び出すことによってときに、メソッドが呼び出されます <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> で、 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> プロパティです。  
  
#### さまざまな種類のソリューションのための戦略がマネージャーを読み込む  
 管理するものであるソリューションの種類に応じて、さまざまな方法では、ソリューションの負荷のマネージャーを実装できます。  
  
 ソリューション負荷マネージャーは、一般に読み込みソリューションを管理するものでは場合、は、VSPackage の一部として実装することができます。 パッケージは、追加することで autoload に設定する必要があります、 <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> 、値は VSPackage で <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid>します。 ソリューションの負荷の manager をアクティブ化できますし、 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> メソッドです。  
  
> [!NOTE]
>  自動読み込みパッケージの詳細については、次を参照してください。 [Vspackage を読み込む](../extensibility/loading-vspackages.md)します。  
  
 Visual Studio では、前回ソリューション ロード マネージャーのみアクティブにするのには認識しているため汎用的なソリューション ロード マネージャー必要があります自体を起動する前に既存の負荷マネージャーがあるかどうか検出があります。 GetProperty\(\) サービスを呼び出すソリューションの場合 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> 返します `null`, 、負荷マネージャーのアクティブなソリューションはありません。 Null は返しません場合、は、オブジェクトは、ソリューションの負荷マネージャーと同じかどうかを確認します。  
  
 ソリューション負荷マネージャーは、ソリューションのいくつかの種類のみを管理するものでは、VSPackage を購読ソリューションの読み込みイベント \(を呼び出して <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>\)、対応するイベント ハンドラーを使用して <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> ソリューション負荷マネージャーをアクティブ化します。  
  
 ソリューションの負荷マネージャーは、特定のソリューションを管理するものでは場合、は、ソリューション ファイルの一部としてアクティブ化の情報を永続化できます。 これを行うには、呼び出す <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> ソリューションの前のセクションのです。  
  
 具体的な解決策ロード マネージャーは自体を非アクティブ化する必要があります、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> イベント ハンドラー、他のソリューションの読み込みマネージャーと競合しないようにします。  
  
 グローバル プロジェクト読み込みの優先順位 \(プロパティのオプション ページの設定など\) を保持するためのソリューションの読み込みマネージャーは、アクティブ化することのみソリューション負荷マネージャーが必要な場合、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> イベント ハンドラーは、ソリューションのプロパティの設定を保持し、ソリューションの負荷マネージャーを非アクティブ化します。  
  
## ソリューションの読み込みイベントの処理  
 ソリューションの読み込みイベントをサブスクライブする <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> ソリューション ロード上司アクティブにするとします。 実装する場合 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents>, 、優先順位を読み込み、別のプロジェクトに関連するイベントに応答できます。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: これは、ソリューションが開かれる前に発生します。 ソリューション内のプロジェクトの優先順位を読み込み、プロジェクトを変更するのにには、それを使用できます。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: これは、解決するには完全に読み込まれるが、バック グラウンドの前にプロジェクトの読み込みを再開した後に発生します。 たとえば、ユーザーの読み込みの優先順位は LoadIfNeeded、プロジェクトがアクセスした可能性がありますか、ソリューション負荷マネージャーは、BackgroundLoad で、そのプロジェクトのバック グラウンド読み込みを開始するようにプロジェクトの読み込みの優先順位変更可能性がありますされました。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: このイベントが発生するソリューションは最初に完全に読み込まれるとソリューション負荷マネージャーがあるかどうか。 それは、ソリューションが完全に読み込まれるときに、バック グラウンド読み込みまたは要求が読み込まれた後にも発生します。 同時に <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> が再アクティブ化します。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: これは、プロジェクト \(プロジェクト\) の読み込み前に発生します。 プロジェクトが読み込まれる前に、その他のバック グラウンド プロセスが完了したことを確認するには設定 `pfShouldDelayLoadToNextIdle` に **true**します。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: これは、プロジェクトのバッチが読み込まれるときに発生します。 場合 `fIsBackgroundIdleBatch` が true の場合、プロジェクトが読み込まれるバック グランドで場合 `fIsBackgroundIdleBatch` が false の場合、プロジェクトでは、ユーザーの要求の結果として同期的に読み込まれたなどのあるかどうか、ユーザーがソリューション エクスプ ローラーで保留中のプロジェクトを展開します。 これをそれ以外の場合は行う必要がある高価な作業を実装する <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterOpenProject%2A>です。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: これは、プロジェクトのバッチが読み込まれた後に発生します。  
  
## 検出して、ソリューションとプロジェクトの読み込みを管理します。  
 プロジェクトおよびソリューションの読み込み状態を検出するために呼び出す <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> に次の値。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` 返します `true` ソリューションとそのすべてのプロジェクトが読み込まれている場合、それ以外の場合 `false`します。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` 返します `true` かどうかのプロジェクトのバッチ中に現在読み込まれて、バック グラウンドでは、それ以外の場合 `false`します。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` 返します `true` かどうかプロジェクトのバッチが現在読み込み中に同期的にユーザー コマンドまたはその他の明示的な読み込みの結果としてそれ以外の場合 `false`します。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>: `var` 返します `true` 場合は、ソリューションが現在停止されて、それ以外の場合 `false`します。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>: `var` 返します `true` ソリューションは、現在されて開かれている場合、それ以外の場合 `false`します。  
  
 また、\(プロジェクトの読み込みの優先度とは\) に関係なく、プロジェクトおよびソリューションが読み込まれているを呼び出して次のいずれかの。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: このメソッドを呼び出して強制的に、メソッドが戻る前に、読み込むをソリューション内のプロジェクトです。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: 強制的にプロジェクトにこのメソッドを呼び出す `guidProject` メソッドが戻る前に読み込めません。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: このメソッドを呼び出すことで、プロジェクトを強制的 `guidProjectID` メソッドが戻る前に読み込めません。  
  
> [!NOTE]
>  . 既定では、デマンドが指定されているプロジェクトだけを読み込んで場合は、バック グラウンド読み込みの優先順位が読み込まれる、 <xref:Microsoft.VisualStudio.Shell.Interop.__VSBSLFLAGS> フラグがメソッドに渡されたを明示的に読み込むとマークされているものを除くすべてのプロジェクトが読み込まれます。