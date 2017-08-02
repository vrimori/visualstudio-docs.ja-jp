---
title: "構築するためのプロジェクトの構成 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "プロジェクト [Visual Studio SDK] を構築するための構成"
  - "ビルドのプロジェクトの構成"
ms.assetid: 2c83615d-fa4d-4b9f-b315-7a69b3000da0
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# 構築するためのプロジェクトの構成
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

特定のソリューションのソリューション構成の一覧は、ソリューション構成\] ダイアログ ボックスによって管理されます。  
  
 ユーザーは、それぞれに一意の名前を持つその他のソリューション構成を作成できます。 ユーザーは、新しいソリューション構成を作成するときは、対応する名前が存在しない場合に、IDE が \[プロジェクト、またはデバッグで対応する構成名を既定値です。 ユーザーは、必要に応じて特定の要件に対応する選択を変更できます。 この動作の唯一の例外は、プロジェクトに新しいソリューション構成の名前に一致する構成がサポートされている場合です。 たとえば、Project1 と Project2 ソリューションが含まれています。 Project1 では、デバッグ、量販店、および MyConfig1 のプロジェクト構成を持ちます。 ある Project2 では、デバッグ、量販店、および MyConfig2 のプロジェクト構成を持ちます。  
  
 ユーザーは、MyConfig2 という名前の新しいソリューション構成を作成する場合、Project1 では、ソリューションの構成、デバッグ構成を既定ではバインドします。 ある Project2 も、既定では、ソリューション構成にその MyConfig2 構成をバインドします。  
  
> [!NOTE]
>  バインディングとは区別されません。  
  
 ユーザーが選択すると、 **複数選択** 項目の構成のドロップダウン リストで、環境には利用可能な構成の一覧を提供するダイアログ ボックスが表示されます。  
  
 ![複数の構成](~/extensibility/internals/media/vsmultiplecfgs.gif "vsMultipleCfgs")  
複数の構成  
  
 このダイアログ ボックス内で、ユーザーは、1 つまたは複数の構成を選択できます。 選択すると、プロパティ ページ\] ダイアログ ボックスに表示されるプロパティの値は、選択した構成の値の積集合を反映します。  
  
 参照してください [ソリューション構成](../../extensibility/internals/solution-configuration.md) を追加し、ソリューションおよびプロジェクトの構成の名前を変更するための関連する情報をします。  
  
 プロジェクトの依存関係とビルド順序は、ソリューション構成に依存しません。 すべてソリューション内のプロジェクトの 1 つの依存関係ツリーを設定できますだけは、です。 ソリューションまたはプロジェクトを右クリックし、いずれかを選択すると、 **プロジェクトの依存関係** または **プロジェクトのビルド順序** オプションが開き、 **プロジェクトの依存関係** \] ダイアログ ボックス。 開くことができます、 **プロジェクト** メニュー。  
  
 ![プロジェクトの依存関係](~/extensibility/internals/media/vsprojdependencies.gif "vsProjDependencies")  
プロジェクトの依存関係  
  
 プロジェクトの依存関係は、プロジェクトのビルド順序を決定します。 ダイアログ ボックスで、\[ビルドの順序\] タブを使用すると、正確な順序で、ソリューション内のプロジェクトがビルド、およびビルドの順序を変更するのに依存関係\] タブを使用してを表示できます。  
  
> [!NOTE]
>  指定された明示的な依存関係のための環境で、チェック ボックスがオンだが淡色表示一覧内のプロジェクトが追加されて、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> または <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> インターフェイス、および変更することはできません。 たとえばからプロジェクトの参照を追加、 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] プロジェクトから別のプロジェクトへの参照を削除することによってのみ削除するビルドの依存関係を自動的に追加します。 こうなるため、依存関係のループがオフ、淡色表示チェック ボックスがプロジェクトを選択できません \(たとえば、Project1 は Project2、依存、Project2 は Project1 に依存\)、ビルドを停止するとします。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ビルド プロセスには、標準的なコンパイルと 1 つのビルド コマンドを使用して呼び出されるリンク操作が含まれます。 その他の 2 つのビルド プロセスもサポートされていることができます。 以前のビルドと構成の出力項目が変更される場合を判断するの最新の状態のチェックからすべての出力項目を削除するクリーン操作します。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> 対応するオブジェクトを返す <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> \(から返された <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>\)、ビルド プロセスを管理します。 構成を報告するために、ビルド操作の状態が発生しているときに呼び出しを使用する <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildStatusCallback>, 環境によって実装されるインターフェイス、およびビルドの状態のイベントに関心のあるその他のオブジェクト。  
  
 作成されると、デバッガーの制御下で実行できるかどうかを判断する構成設定を使用できます。 構成を実装 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> デバッグをサポートします。  
  
 プロジェクトの依存関係を実装したら、オートメーション モデルによる依存関係をプログラムで操作できます。 呼び出す <xref:EnvDTE.SolutionBuild.BuildDependencies%2A> オートメーション モデル。 ソリューションのビルド マネージャーの構成とそのプロパティの直接操作できる使用可能な VSIP API レベル インターフェイスはありません。  
  
 さらに、プロジェクトの依存関係\] ウィンドウでグリッドを指定できます。 詳細については、「[プロパティ グリッドの表示\]](../../extensibility/internals/properties-display-grid.md)」を参照してください。  
  
## 参照  
 [構成オプションの管理](../../extensibility/internals/managing-configuration-options.md)   
 [展開を管理するためのプロジェクトの構成](../../extensibility/internals/project-configuration-for-managing-deployment.md)   
 [出力のプロジェクト構成](../../extensibility/internals/project-configuration-for-output.md)