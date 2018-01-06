---
title: "Project 型のサブタイプ デザイン |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: project subtypes, design
ms.assetid: 405488bb-1362-40ed-b0f1-04a57fc98c56
caps.latest.revision: "32"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 126bee146d1f53233db3c14672f80da4c0d60e9e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="project-subtypes-design"></a>プロジェクトのサブタイプの設計
プロジェクトのサブタイプは、Microsoft Build Engine (MSBuild) に基づくプロジェクトを拡張する Vspackage を使用できます。 集計の使用、コア管理プロジェクト システムで実装の大部分を再利用できます。[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]まだ特定のシナリオの動作をカスタマイズします。  
  
 次のトピックでは、基本的な設計と実装のプロジェクト サブタイプのについて詳しく説明します。  
  
-   プロジェクトのサブタイプ設計します。  
  
-   複数レベルの集計です。  
  
-   インターフェイスをサポートします。  
  
## <a name="project-subtype-design"></a>プロジェクトのサブタイプの設計  
 プロジェクトのサブタイプの初期化は、メインを集計することによって実現<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>オブジェクト。 この集計は、プロジェクトのサブタイプをオーバーライドしたり、ほとんどの基本プロジェクトの機能を拡張したりできます。 プロジェクトのサブタイプを使用してプロパティを処理する最初の機会を取得する<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>、コマンドを使用して<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>、プロジェクト項目を使用して管理および<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>です。 プロジェクトのサブタイプを拡張することがもできます。  
  
-   プロジェクト構成オブジェクト。  
  
-   構成に依存するオブジェクト。  
  
-   構成に依存しない参照オブジェクト。  
  
-   オートメーション オブジェクトを射影します。  
  
-   プロジェクトのオートメーション プロパティのコレクション。  
  
 プロジェクトのサブタイプで拡張機能の詳細については、次を参照してください。[プロパティとメソッドは、プロジェクトのサブタイプで拡張](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)です。  
  
##### <a name="policy-files"></a>ポリシー ファイル  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]環境には、ポリシー ファイルの実装でのプロジェクト サブタイプに基本プロジェクト システムの拡張の例が用意されています。 ポリシー ファイルを使用しての整形、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ソリューション エクスプ ローラーが含まれた機能を管理することによって環境**プロジェクトの追加**ダイアログ ボックスで、**新しい項目の追加** ダイアログ ボックスおよび**プロパティ** ダイアログ ボックス。 ポリシー サブタイプが上書きされ、これらの機能を強化<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg>、`IOleCommandTarget`と<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>実装します。  
  
##### <a name="aggregation-mechanism"></a>集計メカニズム  
 環境内のプロジェクト サブタイプ集計メカニズムには、複数レベルのため、高度なサブタイプさらに flavoring フレーバー プロジェクトによって実装されることが、集計がサポートしています。 また、プロジェクトのサポート オブジェクトは、サブタイプなど<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>、重ね順の複数のレベルを許可するよう設計されています。 COM と COM の制約に従って集計ルール、プロジェクトのサブタイプと基本プロジェクト必要がありますに正しく参加メソッドの呼び出しを委任し、参照カウントを管理するには、内部のサブタイプまたはベースのプロジェクトを有効に協調的なプログラムを作成するには. 集計するプロジェクトは、集計をサポートするためにプログラムを作成します。  
  
 次の図は、複数レベルのプロジェクト サブタイプ集計の概略表現を示します。  
  
 ![Visual Studio マルチレベル projectflavor グラフィック](../../extensibility/internals/media/vs_multilevelprojectflavor.gif "VS_MultilevelProjectFlavor")  
複数レベルのプロジェクト サブタイプ  
  
 複数レベルのプロジェクト サブタイプ集計は、基本プロジェクト、プロジェクトのサブタイプを使用して集計し、さらに、高度なプロジェクトのサブタイプを使用して集計する、3 つのレベルで構成されます。 一部として用意されているサポート インターフェイスの一部で、図に焦点を当てています、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]プロジェクトのサブタイプ アーキテクチャ。  
  
##### <a name="deployment-mechanisms"></a>展開メカニズム  
 基本プロジェクト システムの多くの間では、プロジェクトのサブタイプで強化された機能は、展開の機構です。 プロジェクトのサブタイプ構成インターフェイスを実装することによって展開メカニズムに影響を与えます (など<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>) での QueryInterface を呼び出すことにより取得される<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>です。 基本のプロジェクトを呼び出すシナリオでは、プロジェクトのサブタイプと高度なプロジェクトのサブタイプの両方が別の構成の実装を追加する場所、`QueryInterface`で高度なプロジェクトのサブタイプの`IUnknown`します。 内部のプロジェクトのサブタイプに基本プロジェクトが要求している構成の実装が含まれている場合、高度なプロジェクトのサブタイプは、内部のプロジェクトのサブタイプで提供される実装に委任されます。 1 つの集計レベルから別の状態を維持するためのメカニズム、全レベルのプロジェクト サブタイプ実装<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>ビルド非永続化するには、プロジェクト ファイルに XML データを関連します。 詳細については、次を参照してください。 [MSBuild プロジェクト ファイル内のデータの永続化](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)です。 <xref:EnvDTE80.IInternalExtenderProvider>プロジェクト サブタイプからオートメーション エクステンダーを取得するためのメカニズムとして実装されます。  
  
 次の図は、焦点を当てていますプロジェクト構成の参照オブジェクトをオートメーション エクステンダー実装の具体的には、プロジェクトのサブタイプ基本プロジェクト システムを拡張するために使用します。  
  
 ![VS プロジェクト フレーバー オート エクステンダー グラフィック](../../extensibility/internals/media/vs_projectflavorautoextender.gif "VS_ProjectFlavorAutoExtender")  
プロジェクトのサブタイプのオートメーション エクステンダーです。  
  
 プロジェクトのサブタイプは、オートメーション オブジェクト モデルを拡張することにより、基本プロジェクト システムをさらに拡張できます。 これらは DTE オートメーション オブジェクトの一部として定義され、プロジェクト オブジェクトを拡張するために使用、`ProjectItem`オブジェクトおよび`Configuration`オブジェクト。 詳細については、「[ベース プロジェクトのオブジェクト モデルの拡張](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)です。  
  
## <a name="multi-level-aggregation"></a>複数レベルの集計  
 下位レベルのプロジェクト サブタイプをラップするプロジェクトのサブタイプ実装は、内部のプロジェクトのサブタイプが正常に機能を使用できるように協調的なプログラムを作成する必要があります。 プログラミングの責任の一覧は次のとおりです。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>に代行させる内部のサブタイプの折り返しはプロジェクトのサブタイプの実装、<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>両方の内部プロジェクトのサブタイプの実装<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A>と<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A>メソッドです。  
  
-   <xref:EnvDTE80.IInternalExtenderProvider>ラッパー プロジェクトのサブタイプの実装をその内部のプロジェクト サブタイプに委任する必要があります。 特にの実装で<xref:EnvDTE80.IInternalExtenderProvider.GetExtenderNames%2A>内部プロジェクトのサブタイプから名の文字列を取得し、extender として追加する文字列を連結する必要があります。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>ラッパー プロジェクト サブタイプの実装のインスタンスを作成する必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>オブジェクト、内部のプロジェクトのサブタイプ、押したままにプライベートのデリゲートとして後だけで、基本プロジェクトのプロジェクト構成のオブジェクトが直接ことを認識ラッパープロジェクトのサブタイプ構成オブジェクトが存在します。 外部プロジェクトのサブタイプを直接処理する必要がある構成インターフェイスを最初に選択しの内部のプロジェクト サブタイプの実装に残りの部分を委任<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg.get_CfgType%2A>です。  
  
## <a name="supporting-interfaces"></a>インターフェイスのサポート  
 基本のプロジェクトは、その実装のさまざまな側面を拡張するインターフェイスのプロジェクトのサブタイプで追加のサポートへの呼び出しを代行させます。 これには、プロジェクト構成のオブジェクトとさまざまなプロパティ ブラウザーのオブジェクトの拡張が含まれます。 これらのインターフェイスを呼び出すことによって取得されます`QueryInterface`で`punkOuter`(へのポインター、 `IUnknown`) 最も外側のプロジェクト サブタイプ アグリゲーターのです。  
  
|Interface|プロジェクトのサブタイプ|  
|---------------|---------------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>|プロジェクトのサブタイプを使用できます。<br /><br /> -の実装を提供する<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>です。<br />-独自の実装を提供するプロジェクトのサブタイプを許可することで、デバッガーの起動を制御する<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>です。<br />-無効にするデザイン時の式評価適切に処理することによって、`DBGLAUNCH_DesignTimeExprEval`の実装でケース<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.QueryDebugLaunch%2A>です。|  
|<xref:EnvDTE80.IInternalExtenderProvider>|プロジェクトのサブタイプを使用できます。<br /><br /> -拡張、<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>のようにプロジェクトを追加または削除するプロジェクトの独立したプロパティを構成します。<br />、プロジェクトのオートメーション オブジェクトを拡張する (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>) のプロジェクトです。<br /><br /> 上記のプロパティ値から取得されます<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>列挙します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>|により、プロジェクトのサブタイプがへのマッピングに、<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>プロジェクト構成の参照オブジェクトを指定されたオブジェクト。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBrowseObject>|により、プロジェクトのサブタイプがへのマッピングに、<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>または`VSITEMID`プロジェクト構成の参照オブジェクトを指定されたオブジェクト。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>|プロジェクト ファイル (.vbproj ファイルまたは .csproj) に任意の XML の構造化データを保持するプロジェクトのサブタイプを使用できます。 このデータでは、MSBuild に表示されません。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>|プロジェクトのサブタイプを使用できます。<br /><br /> -永続化する新しい MSBuild プロパティを追加します。<br />-MSBuild から不要なプロパティを削除します。<br />MSBuild プロパティの現在の値をクエリします。<br />-MSBuild プロパティの現在の値を変更します。|  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>