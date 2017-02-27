---
title: "方法: 入れ子になったプロジェクトの実施 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "実装する入れ子になったプロジェクト"
  - "入れ子のプロジェクト [Visual Studio SDK]"
ms.assetid: d20b8d6a-f0e0-4115-b3a3-edda893ae678
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# 方法: 入れ子になったプロジェクトの実施
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

入れ子になったプロジェクトを作成するときに実行する必要があるいくつかの追加の手順です。  親プロジェクトがソリューションに入れ子 \(子\) のプロジェクトの場合と同じ役割の一部になります。  親プロジェクトはソリューションと同様のプロジェクトのコンテナーです。  特に入れ子になったソリューションとプロジェクト階層の親プロジェクトをビルドして複数のイベントを発生させる必要があります。  これらのイベントは入れ子になったプロジェクトを作成するための次の手順で説明します。  
  
### 作成するにはプロジェクトになった  
  
1.  統合開発環境 \(\(IDE\) <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> のインターフェイスを呼び出して親プロジェクトのプロジェクト ファイルとスタートアップ情報を読み込みます。  親プロジェクトが作成されソリューションに追加されます。  
  
    > [!NOTE]
    >  この時点では入れ子になったプロジェクトを作成するには親プロジェクトのプロセスへの子プロジェクトを作成する前に親プロジェクトを作成する必要があるため非常に高速です。  この手順の後に親プロジェクトはプロジェクトに設定を適用して子プロジェクトは親プロジェクトから情報を取得できる必要に応じて。  このシーケンスはソース・コード管理とソリューション エクスプローラーなどのクライアントいる場合 \(SCC\) に必要です。  
  
     親プロジェクトは入れ子 \(子\) のプロジェクトを作成する前にIDE を呼び出す <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> のメソッドを待機する必要があります。  
  
2.  IDE で <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject> の親プロジェクトの `QueryInterface` を呼び出します。  この呼び出しが成功した場合は親プロジェクトのすべてのプロジェクトを開くために親 <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> のメソッドを呼び出します。  
  
3.  親プロジェクトは入れ子になったプロジェクトが作成されることを通知するために <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnBeforeOpeningChildren%2A> リスナーのメソッドを呼び出します。  SCC はそのイベントのソリューションとプロジェクトの作成プロセスのステップの順序で発生しているかどうかを確認するためにリッスンします。  ステップが失敗する場合はソリューションがソース・コード管理システムによって正しく登録されていない可能性があります。  
  
4.  親プロジェクトはプロジェクトの <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProject%2A> の <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProjectEx%2A> のメソッドまたはメソッドを呼び出します。  
  
     `AddVirtualProject` の仮想メソッド \(\) に入れ子になったプロジェクトがソース・コード管理に追加されたビルドから除外するプロジェクトのウィンドウに追加する必要があることを示すために <xref:Microsoft.VisualStudio.Shell.Interop.__VSADDVPFLAGS> を渡します。  `VSADDVPFLAGS` は入れ子になったプロジェクトの表示を制御しそれらの機能が関連付けられているかを示すことができます。  
  
     親プロジェクト ファイルに格納されているプロジェクトの GUID を持つ前に既存の子プロジェクトを再度読み込む場合は親プロジェクト `AddVirtualProjectEx` を呼び出します。  `AddVirtualProject` と `AddVirtualProjectEX` の唯一の違いは`AddVirtualProjectEX` に正しく機能することを <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfGuid%2A> と <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfProjref%2A> できる子プロジェクトのインスタンス `guidProjectID` ごとのを指定する親プロジェクトを有効にするパラメーターがあります。  
  
     GUID が利用できる状態でなければなど親に追加されると入れ子になった新しいプロジェクトを追加するとソリューションはプロジェクトの 1 種類を作成します。  これはプロジェクト ファイルでプロジェクトの GUID を保持する親プロジェクトが行います。  入れ子になったプロジェクトを削除するとそのプロジェクトの GUID も削除できます。  
  
5.  IDE では親プロジェクトの各子プロジェクトの `M:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren` のメソッドを呼び出します。  
  
     親プロジェクトがプロジェクトに入れ子には `IVsParentProject` を実装する必要があります。  ただし親プロジェクトはその下にある親プロジェクトがある場合でも `IVsParentProject` の `QueryInterface` を呼び出していません。  ソリューションは `IVsParentProject` の呼び出しを処理し入れ子になったプロジェクトを作成する場合は`OpenChildren` を呼び出します。  `AddVirtualProjectEX` は `OpenChildren` 必ずから呼び出されます。  これは順序で階層の作成イベントを保持する親プロジェクトによって呼び出される必要があります。  
  
6.  IDE はプロジェクトの <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> のメソッドを呼び出します。  
  
7.  親プロジェクトは親の子プロジェクトが作成されたことを通知するために <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpeningChildren%2A> リスナーのメソッドを呼び出します。  
  
8.  IDE ではすべての子プロジェクトを開いた後親プロジェクト <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpenProject%2A> のメソッドを呼び出します。  
  
     これが存在しない場合は親プロジェクトは `CoCreateGuid` を呼び出して入れ子のプロジェクトの GUID を作成します。  
  
    > [!NOTE]
    >  `CoCreateGuid` はGUID を作成するときに呼び出される COM API です。  詳細についてはMSDN ライブラリの `CoCreateGuid` および GUID を参照してください。  
  
     親プロジェクトは次に取得する IDE で開かれたプロジェクト ファイルでGUID を格納します。  子プロジェクトの `guidProjectID` を取得するに `AddVirtualProjectEX` の呼び出しに関して詳細については手順 4 を参照してください。  
  
9. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> のメソッドは規則では入れ子になったプロジェクトに代入する親 ItemID によって呼び出されます。  <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> は親呼び出されるとデリゲートするプロジェクトにあるノードのプロパティを取得します。  
  
     親と子のプロジェクトがプログラムによってインスタンス化されるため入れ子になったプロジェクトのプロパティはこの時点にできます。  
  
    > [!NOTE]
    >  入れ子になったプロジェクトのコンテキスト情報を受け取る double親プロジェクトに <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> をチェックしてその項目のコンテキストがあるかどうかを確認することができます。  このようにユーザーによってプロジェクトに固有の追加のダイナミック ヘルプの属性とメニュー オプションを追加できます。  
  
10. 階層は <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A> のメソッドの呼び出しにソリューション エクスプローラーに表示するためにビルドされます。  
  
     `GetNestedHierarchy` して環境にはソリューション エクスプローラーの表示の階層を構築するための階層を渡します。  これによりソリューションはプロジェクトを実行するかまたはビルド マネージャーによってビルドのマネージ ソース・コード管理下にあるプロジェクトのファイルを選択できるようにすることができます。  
  
11. Project1 のすべての入れ子になったプロジェクトが作成されるとコントロールはソリューションに渡されプロセスは Project2 に繰り返されます。  
  
     入れ子になったプロジェクトを作成するためのこのプロセスは子が指定されている子プロジェクトに発生します。  この場合Project1 の子である BuildProject1 に子プロジェクトがある場合はBuildProject1 の後Project2 を作成します。  プロセスは再帰的であり階層は上から順にビルドされます。  
  
     ユーザーが特定のソリューションまたはプロジェクト自体を閉じるため入れ子になったプロジェクトを閉じると`IVsParentProject`<xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.CloseChildren%2A> の他のメソッドを呼び出します。  親プロジェクトは <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeClosingChildren%2A> と <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterClosingChildren%2A> のメソッドの <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.RemoveVirtualProject%2A> のメソッドは入れ子になったプロジェクトが閉じているソリューションのイベントのリスナーに通知するために呼び出しをラップします。  
  
 次のトピックでは他の概念を入れ子になったプロジェクトを実行するときに考慮する処理 :  
  
 [入れ子になったプロジェクトのアンロードと再ロードに関する考慮事項](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)  
  
 [ウィザードでサポートされる入れ子のプロジェクト](../../extensibility/internals/wizard-support-for-nested-projects.md)  
  
 [入れ子になったプロジェクトに対するコマンド処理を実装します。](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)  
  
 [入れ子になったプロジェクトを AddItem\] ダイアログ ボックスのフィルター処理](../Topic/Filtering%20the%20AddItem%20Dialog%20Box%20for%20Nested%20Projects.md)  
  
## 参照  
 [項目を追加、新しい項目の追加\] ダイアログ ボックス](../Topic/Adding%20Items%20to%20the%20Add%20New%20Item%20Dialog%20Boxes.md)   
 [プロジェクトおよび項目テンプレートを登録します。](../../extensibility/internals/registering-project-and-item-templates.md)   
 [チェックリスト: 新しいプロジェクトの種類を作成します。](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [コンテキスト パラメーター](../../extensibility/internals/context-parameters.md)   
 [ウィザード \(します。Vsz\) ファイル](../../extensibility/internals/wizard-dot-vsz-file.md)