---
title: プロジェクト サブタイプの設計 |Microsoft Docs
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
- project subtypes, design
ms.assetid: 405488bb-1362-40ed-b0f1-04a57fc98c56
caps.latest.revision: 33
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 96ab44df6512b4288cf01f4c1f99d435a9c24bd5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51806127"
---
# <a name="project-subtypes-design"></a>プロジェクト サブタイプのデザイン
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

プロジェクト サブタイプは、Microsoft Build Engine (MSBuild) に基づくプロジェクトを拡張する Vspackage を使用できます。 集計の使用では、実装で管理されているコア プロジェクト システムの大部分を再利用できます。[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]まだ特定のシナリオの動作をカスタマイズします。  
  
 次のトピックでは、基本的な設計とプロジェクト サブタイプの実装について詳しく説明します。  
  
-   プロジェクト サブタイプのデザイン。  
  
-   複数レベルの集計。  
  
-   インターフェイスをサポートします。  
  
## <a name="project-subtype-design"></a>プロジェクト サブタイプのデザイン  
 プロジェクト サブタイプの初期化はメイン集約することによって実現<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>オブジェクト。 この集計は、プロジェクトのサブタイプをオーバーライドしたり、基本プロジェクトの機能の大半を強化したりできます。 プロジェクト サブタイプの取得を使用してプロパティを処理するためにファースト チャンス<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>、コマンドを使用して<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>、使用してプロジェクト項目の管理と<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>します。 プロジェクト サブタイプを拡張することがもできます。  
  
- プロジェクト構成オブジェクト。  
  
- 構成に依存するオブジェクト。  
  
- 構成に依存しない参照オブジェクト。  
  
- プロジェクト オートメーション オブジェクト。  
  
- プロジェクトのオートメーション プロパティのコレクション。  
  
  プロジェクト サブタイプによって拡張機能の詳細については、次を参照してください。[プロパティとメソッドは、プロジェクト サブタイプによって拡張](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)します。  
  
##### <a name="policy-files"></a>ポリシー ファイル  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]環境は、ポリシー ファイルの実装でのプロジェクト サブタイプに基本プロジェクト システムの拡張の例を示します。 ポリシー ファイルは、の構造化、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]のソリューション エクスプ ローラーで、機能を管理することで環境**プロジェクトの追加**ダイアログ ボックスで、**新しい項目の追加** ダイアログ ボックスおよび**プロパティ** ダイアログ ボックス。 ポリシーのサブタイプをオーバーライドし、これらの機能を強化<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg>、`IOleCommandTarget`と<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>実装します。  
  
##### <a name="aggregation-mechanism"></a>集計メカニズム  
 環境のプロジェクト サブタイプ集計メカニズムには、複数レベルの集計、ので、さらに flavoring フレーバー プロジェクトによって実装される、高度なサブタイプがサポートしています。 また、サポート対象のオブジェクトをプロジェクトのサブタイプなど<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>、複数のレベルの階層化を許可することになっています。 COM と COM の制約に合わせて集計ルール、プロジェクトのサブタイプと基本プロジェクト必要がありますに正しく参加メソッドの呼び出しを委任し、参照カウントを管理するには、内部のサブタイプまたはベースのプロジェクトを有効にする協調的なプログラムを作成するには. これは、集計対象のプロジェクトに集計をサポートするためにプログラムを作成します。  
  
 次の図は、複数レベルのプロジェクト サブタイプの集計を図式化を示します。  
  
 ![Visual Studio の複数レベルのプロジェクト フレーバーのグラフィック](../../extensibility/internals/media/vs-multilevelprojectflavor.gif "VS_MultilevelProjectFlavor")  
複数レベルのプロジェクト サブタイプ  
  
 複数レベルのプロジェクト サブタイプの集計は、基本プロジェクトのプロジェクト サブタイプの場合は、によって集計し、さらに、高度なプロジェクト サブタイプによって集計される、3 つのレベルで構成されます。 一部として提供されるサポート インターフェイスの一部に焦点を当てています、図、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]プロジェクト サブタイプのアーキテクチャ。  
  
##### <a name="deployment-mechanisms"></a>展開メカニズム  
 基本プロジェクト システムの多くは、プロジェクト サブタイプによって拡張機能は、展開の機構です。 プロジェクト サブタイプ構成インターフェイスを実装することによって展開メカニズムに影響を与えます (など<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>) の QueryInterface を呼び出すことによって取得される<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>します。 ベースのプロジェクトを呼び出すシナリオでは、プロジェクトのサブタイプと高度なプロジェクト サブタイプの両方が別の構成の実装を追加する場所、`QueryInterface`で高度なプロジェクト サブタイプの`IUnknown`します。 内部のプロジェクト サブタイプに基本プロジェクトが求める構成の実装が含まれている場合、高度なプロジェクトのサブタイプは内部のプロジェクト サブタイプによって提供される実装に委任されます。 プロジェクト サブタイプのすべてのレベルの実装として 1 つの集計レベルから別の状態を維持するためのメカニズム、<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>非ビルドを保持するプロジェクト ファイルに XML データに関連します。 詳細については、次を参照してください。 [MSBuild プロジェクト ファイル内のデータの永続化](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)します。 <xref:EnvDTE80.IInternalExtenderProvider> プロジェクト サブタイプからオートメーション エクステンダーを取得するためのメカニズムとして実装されます。  
  
 次の図について重点的にオートメーション エクステンダーの実装、プロジェクト構成の参照オブジェクト具体的には、プロジェクトのサブタイプ基本プロジェクト システムを拡張するために使用します。  
  
 ![VS プロジェクト フレーバー オート エクステンダー グラフィック](../../extensibility/internals/media/vs-projectflavorautoextender.gif "VS_ProjectFlavorAutoExtender")  
プロジェクト サブタイプのオートメーション エクステンダー。  
  
 プロジェクト サブタイプは、オートメーション オブジェクト モデルを拡張することによって、基本プロジェクト システムをさらに拡張できます。 これらは DTE オートメーション オブジェクトの一部として定義され、プロジェクトのオブジェクトを拡張するために使用、`ProjectItem`オブジェクトと`Configuration`オブジェクト。 詳細については、「[ベース プロジェクトのオブジェクト モデルの拡張](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)します。  
  
## <a name="multi-level-aggregation"></a>複数レベルの集計  
 下位レベルのプロジェクト サブタイプをラップするプロジェクト サブタイプの実装では、適切に機能する内部のプロジェクト サブタイプを許可する協調的なプログラムを作成する必要があります。 責任のプログラミングの一覧は次のとおりです。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>を内部のサブタイプで折り返されるプロジェクト サブタイプの実装に委任する必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>両方の内部のプロジェクト サブタイプの実装<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A>と<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A>メソッド。  
  
-   <xref:EnvDTE80.IInternalExtenderProvider>その内部のプロジェクト サブタイプのラッパーのプロジェクト サブタイプの実装に委任する必要があります。 具体的には、実装で<xref:EnvDTE80.IInternalExtenderProvider.GetExtenderNames%2A>エクステンダーとして追加する文字列を連結し、内部のプロジェクト サブタイプから名の文字列を取得する必要があります。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>ラッパー プロジェクト サブタイプの実装のインスタンスを作成する必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>オブジェクト、内部のプロジェクトのサブタイプ、押したままに、プライベート デリゲートでは、ためベースのプロジェクトのプロジェクト構成オブジェクトを直接知っているだけで、ラッパープロジェクト サブタイプの構成オブジェクトが存在します。 外部プロジェクト サブタイプが最初に、直接処理する構成インターフェイスを選択およびの内部のプロジェクト サブタイプの実装に残りの部分を委任し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg.get_CfgType%2A>します。  
  
## <a name="supporting-interfaces"></a>インターフェイスのサポート  
 基本プロジェクトは、その実装のさまざまな側面を拡張するインターフェイスのプロジェクト サブタイプの場合は、追加のサポートへの呼び出しを代行させます。 これは、プロジェクト構成のオブジェクトとさまざまなプロパティ ブラウザーのオブジェクトの拡張が含まれます。 これらのインターフェイスを呼び出すことによって取得されて`QueryInterface`で`punkOuter`(へのポインター、 `IUnknown`) の最も外側にあるプロジェクトのサブタイプ アグリゲーター。  
  
|Interface|プロジェクト サブタイプ|  
|---------------|---------------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>|プロジェクト サブタイプに使用できます。<br /><br /> -の実装を提供する<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>します。<br />-独自の実装を提供するプロジェクトのサブタイプを許可することで、デバッガーの起動を制御する<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>します。<br />-適切に処理することによって、デザイン時の式の評価を無効に、`DBGLAUNCH_DesignTimeExprEval`の実装で大文字と小文字<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.QueryDebugLaunch%2A>します。|  
|<xref:EnvDTE80.IInternalExtenderProvider>|プロジェクト サブタイプに使用できます。<br /><br /> -拡張、<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>のプロジェクトを追加または削除、プロジェクトの独立したプロパティを構成します。<br />、プロジェクト オートメーション オブジェクトを拡張する (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>) のプロジェクト。<br /><br /> 上記のプロパティ値から取得されます<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>列挙体。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>|により、プロジェクトのサブタイプにマップする、<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>プロジェクト構成の参照オブジェクトを指定したオブジェクト。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBrowseObject>|により、プロジェクトのサブタイプにマップする、<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>または`VSITEMID`プロジェクト構成の参照オブジェクトを指定しているオブジェクト。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>|任意の XML の構造化データ、プロジェクト ファイル (.vbproj または .csproj) を保持するプロジェクトのサブタイプを使用できます。 このデータは、MSBuild には表示されません。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>|プロジェクト サブタイプに使用できます。<br /><br /> -永続化する新しい MSBuild プロパティを追加します。<br />-MSBuild から不要なプロパティを削除します。<br />-現在、MSBuild プロパティの値を照会します。<br />-現在、MSBuild プロパティの値を変更します。|  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>

