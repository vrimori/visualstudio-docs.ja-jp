---
title: "プロジェクトのビルドの構成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], configuration for building
- project configurations, building
ms.assetid: 2c83615d-fa4d-4b9f-b315-7a69b3000da0
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2d8f37068d197d133ba8798703c8f82093261aca
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="project-configuration-for-building"></a>構築するためのプロジェクトの構成
特定のソリューションのソリューション構成の一覧は、ソリューション構成 ダイアログ ボックスによって管理されます。  
  
 ユーザーは、それぞれ独自の一意の名前に追加のソリューション構成を作成できます。 ユーザーは、新しいソリューション構成を作成するときは、対応する名前が存在しない場合に、IDE が プロジェクト、またはデバッグで対応する構成名を既定値です。 ユーザーは、必要に応じて特定の要件に対応する選択を変更できます。 この動作の唯一の例外は、プロジェクトに新しいソリューション構成の名前に一致する構成がサポートされている場合です。 たとえば、Project1 と Project2 ソリューションが含まれています。 Project1 には、デバッグ、量販店、および MyConfig1 プロジェクト構成があります。 Project2 は、デバッグ、量販店、および MyConfig2 のプロジェクト構成を持ちます。  
  
 ユーザーは、MyConfig2 をという名前の新しいソリューション構成を作成する場合 Project1 は既定では、ソリューション構成をデバッグ構成をバインドします。 Project2 も、既定では、ソリューション構成にその MyConfig2 構成をバインドします。  
  
> [!NOTE]
>  バインディングとは区別されません。  
  
 ユーザーが選択すると、**複数選択**項目構成 ドロップダウン リストで、環境には使用可能な構成の一覧を提供するダイアログ ボックスが表示されます。  
  
 ![複数の構成](../../extensibility/internals/media/vsmultiplecfgs.gif "vsMultipleCfgs")  
複数の構成  
  
 このダイアログ ボックス内で、ユーザーは、1 つまたは複数の構成を選択できます。 このオプションを選択すると、プロパティ ページ ダイアログ ボックスに表示されるプロパティの値は、選択した構成値の積集合を反映します。  
  
 参照してください[ソリューション構成](../../extensibility/internals/solution-configuration.md)についての追加とソリューションおよびプロジェクトの構成の名前変更に関連します。  
  
 プロジェクトの依存関係とビルドの順序は、ソリューション構成に依存しません: ソリューション内のプロジェクトのすべての 1 つの依存関係ツリーを設定できますのみつまり、します。 ソリューションまたはプロジェクトを右クリックし、いずれかを選択すると、**プロジェクトの依存関係**または**プロジェクトのビルド順序**オプションが開き、**プロジェクトの依存関係** ダイアログ ボックス。 開くこともできます、**プロジェクト**メニュー。  
  
 ![プロジェクトの依存関係](../../extensibility/internals/media/vsprojdependencies.gif "vsProjDependencies")  
プロジェクトの依存関係  
  
 プロジェクトの依存関係は、プロジェクトのビルド順序を決定します。 ダイアログ ボックスで、ビルドの順序 タブを使用すると、正確な順序で、ソリューション内のプロジェクトがビルド、およびビルド順序を変更するのに依存関係 タブを使用してを表示できます。  
  
> [!NOTE]
>  一覧のプロジェクトに、そのチェック ボックスをオンだが淡色表示で指定された明示的な依存関係により、環境によって追加された、<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency>または<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency>インターフェイス、および変更することはできません。 たとえばからプロジェクトの参照を追加、[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]プロジェクトから別のプロジェクトへの参照を削除することによってのみ削除可能なビルドの依存関係を自動的に追加されます。 なるため、これにより、依存関係のループは、チェック ボックスがクリアされ、淡色表示のプロジェクトを選択することはできません (たとえば、Project1 に Project2 に依存して Project2 は Project1 に依存)、ビルドを停止するとします。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ビルド プロセスには、標準的なコンパイルとは、1 つのビルド コマンドで起動するリンク操作が含まれます。 その他の 2 つのビルド プロセスもサポートされていることができます。 以前のビルドと構成の出力項目が変更された場合を決定する、最新の状態チェックからすべての出力項目を削除するクリーン操作します。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>対応するオブジェクトを返す<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>(から返された<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>)、ビルド プロセスを管理します。 呼び出しを作成する構成の実行中に、ビルド操作のステータスをレポートする<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildStatusCallback>、環境によって実装されるインターフェイスおよびビルドの状態のイベントに関心のあるその他のオブジェクト。  
  
 作成されると、デバッガーの制御下で実行できるかどうかを決定する構成設定を使用できます。 構成を実装<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>デバッグをサポートします。  
  
 プロジェクトの依存関係を実装した後に、オートメーション モデルからの依存関係をプログラムで操作できます。 呼び出す<xref:EnvDTE.SolutionBuild.BuildDependencies%2A>オートメーション モデル。 ソリューションのビルド マネージャーの構成とそのプロパティの直接操作できる使用可能な API レベルの VSIP インターフェイスはありません。  
  
 さらに、プロジェクトの依存関係ウィンドウ内のグリッドを指定できます。 詳細については、次を参照してください。[プロパティ グリッドの表示](../../extensibility/internals/properties-display-grid.md)です。  
  
## <a name="see-also"></a>参照  
 [構成オプションの管理](../../extensibility/internals/managing-configuration-options.md)   
 [展開を管理するためのプロジェクトの構成](../../extensibility/internals/project-configuration-for-managing-deployment.md)   
 [出力のためのプロジェクト構成](../../extensibility/internals/project-configuration-for-output.md)