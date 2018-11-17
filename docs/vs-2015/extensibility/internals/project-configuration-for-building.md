---
title: プロジェクトのビルドの構成 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], configuration for building
- project configurations, building
ms.assetid: 2c83615d-fa4d-4b9f-b315-7a69b3000da0
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ef43fe505e859cb32f7c0fbe407bcc73c4f4e0e8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51725518"
---
# <a name="project-configuration-for-building"></a>ビルドのためのプロジェクト構成
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

特定のソリューションのソリューション構成の一覧は、ソリューション構成 ダイアログ ボックスによって管理されます。  
  
 ユーザーは、それぞれ独自の一意の名前を持つその他のソリューション構成を作成できます。 ユーザーは、新しいソリューション構成を作成するときは、対応する名前が存在しない場合に、IDE が プロジェクト、またはデバッグに対応する構成名を既定値です。 ユーザーには、必要に応じて特定の要件を満たすために選択を変更できます。 この動作の唯一の例外は、プロジェクトに新しいソリューション構成の名前に一致する構成がサポートされている場合です。 たとえば、ソリューションには、Project1 と Project2 が含まれています。 Project1 では、デバッグ、製品版、および MyConfig1 のプロジェクト構成を持ちます。 Project2 では、デバッグ、製品版、および MyConfig2 のプロジェクト構成を持ちます。  
  
 ユーザーは、MyConfig2 という名前の新しいソリューション構成を作成する場合 Project1 は既定ではソリューションの構成のデバッグ構成をバインドします。 Project2 も、既定では、ソリューション構成にその MyConfig2 構成をバインドします。  
  
> [!NOTE]
>  バインディングでは大文字です。  
  
 ユーザーが選択すると、**複数選択**項目構成ドロップダウン リストで、環境には使用可能な構成の一覧を提供するダイアログ ボックスが表示されます。  
  
 ![複数の構成](../../extensibility/internals/media/vsmultiplecfgs.gif "vsMultipleCfgs")  
複数の構成  
  
 このダイアログ ボックス内で、ユーザーは、1 つまたは複数の構成を選択できます。 選択すると、プロパティ ページ ダイアログ ボックスに表示されるプロパティの値は、選択した構成の値の積集合を反映します。  
  
 参照してください[ソリューション構成](../../extensibility/internals/solution-configuration.md)を追加し、ソリューションとプロジェクトの構成の名前を変更に関する情報についてはします。  
  
 プロジェクトの依存関係とビルドの順序は、独立したソリューション構成: ソリューション内のプロジェクトのすべての 1 つの依存関係ツリーを設定できますのみ、します。 ソリューションまたはプロジェクトを右クリックし、いずれかを選択すると、**プロジェクトの依存関係**または**プロジェクトのビルド順序**オプションが表示されます、**プロジェクトの依存関係** ダイアログ ボックス。 開くこともできます、**プロジェクト**メニュー。  
  
 ![プロジェクトの依存関係](../../extensibility/internals/media/vsprojdependencies.gif "vsProjDependencies")  
プロジェクトの依存関係  
  
 プロジェクトの依存関係は、プロジェクトのビルド順序を決定します。 ダイアログ ボックスで、ビルドの順序 タブを使用すると、ソリューション内のプロジェクトはビルド、および依存関係 タブを使用して、ビルドの順序を変更するのには、正確な順序を表示できます。  
  
> [!NOTE]
>  指定された明示的な依存関係のための環境で、チェック ボックスが選択されているが淡色表示の一覧でのプロジェクトが追加されました、<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency>または<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency>インターフェイス、および変更することはできません。 たとえばからのプロジェクト参照を追加、[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]別のプロジェクトにプロジェクト参照を削除することによってのみ削除できるビルドの依存関係を自動的に追加します。 依存関係のループの作成はそうために、プロジェクトがオフ、淡色表示のチェック ボックスを選択できません (Project2、時に依存する Project1 および Project1 に依存する Project2 など)、ビルドを停止するとします。  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ビルド プロセスには、一般的なコンパイルとリンクに関する単一のビルド コマンドで呼び出される操作が含まれます。 その他の 2 つのビルド プロセスもサポートされていることができます。 前回のビルドと構成の出力項目が変更された場合を決定する、最新の状態のチェックからすべての出力項目を削除するクリーン操作。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> 対応するオブジェクトを返します<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>(から返された<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>)、ビルド プロセスを管理します。 構成を使用する呼び出しが発生しているときに、ビルド操作の状態を報告、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildStatusCallback>、環境によって実装されるインターフェイスおよびビルド ステータス イベントに関心があるその他のオブジェクト。  
  
 作成されると、デバッガーの制御下で実行できるかどうかを判断する構成設定を使用できます。 構成の実装<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>デバッグをサポートします。  
  
 プロジェクトの依存関係を実装したら、オートメーション モデルでの依存関係をプログラムで操作できます。 呼び出す<xref:EnvDTE.SolutionBuild.BuildDependencies%2A>オートメーション モデル。 ソリューションのビルド マネージャーの構成とそのプロパティの直接操作できる使用可能な API レベルの VSIP インターフェイスはありません。  
  
 さらに、プロジェクトの依存関係 ウィンドウのグリッドを行うことができます。 詳細については、次を参照してください。[プロパティ表示グリッド](../../extensibility/internals/properties-display-grid.md)します。  
  
## <a name="see-also"></a>関連項目  
 [構成オプションの管理](../../extensibility/internals/managing-configuration-options.md)   
 [展開を管理するためのプロジェクト構成](../../extensibility/internals/project-configuration-for-managing-deployment.md)   
 [出力のためのプロジェクト構成](../../extensibility/internals/project-configuration-for-output.md)

