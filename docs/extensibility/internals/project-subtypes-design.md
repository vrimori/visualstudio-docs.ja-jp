---
title: "プロジェクトのサブタイプの設計 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "プロジェクトのサブタイプの設計"
ms.assetid: 405488bb-1362-40ed-b0f1-04a57fc98c56
caps.latest.revision: 32
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 32
---
# プロジェクトのサブタイプの設計
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

プロジェクトのサブタイプはVSPackages が Microsoft Build Engine \(MSBuild\) に基づいてプロジェクトを拡張できるようにします。  集計の使用は[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] で実行されるコア マネージ プロジェクト システムの大部分を再利用するために特定のシナリオにおける動作をカスタマイズできるようにします。  
  
 次のトピックではプロジェクトのサブタイプの基本デザインと実装の詳細 :  
  
-   プロジェクトのサブタイプのデザイン。  
  
-   複数レベルの総計。  
  
-   インターフェイスのサポート。  
  
## プロジェクトのサブタイプのデザイン  
 プロジェクトのサブタイプの初期化は <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> の主要な <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> とオブジェクトの集約します。  この集計はプロジェクトの基本機能のほとんどをオーバーライドしたりすることなくプロジェクトのサブタイプを有効にします。  プロジェクトのサブタイプは<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> と <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> を使用して <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> プロパティを使用してコマンドおよび <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> を使用してプロジェクト項目管理を行う最初の可能性を取得します。  プロジェクトのサブタイプは拡張できます :  
  
-   プロジェクト構成オブジェクト。  
  
-   構成依存のオブジェクト。  
  
-   構成に依存しないオブジェクトを参照します。  
  
-   プロジェクト オートメーション オブジェクト。  
  
-   プロジェクト オートメーションのプロパティ コレクション。  
  
 プロジェクトのサブタイプによる拡張機能の詳細については[プロパティとプロジェクトのサブタイプによって拡張メソッド](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md) を参照してください。  
  
##### ポリシー ファイル  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] の環境はポリシー ファイルの実装のプロジェクトのサブタイプを基本プロジェクト システムを拡張する例を示します。  ポリシー ファイルはソリューション エクスプローラーENT0ENT \[出力\] ダイアログ ボックス \[ENT1ENT\] ダイアログ ボックスと \[ENT2ENT\] ダイアログ ボックスのある機能を管理すること [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] の環境を可能にします。  ポリシーのサブタイプは<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg>`IOleCommandTarget` と <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> の実装によってこれらの機能をオーバーライドおよび拡張します。  
  
##### 集計の機能  
 この環境でプロジェクトのサブタイプの集計の機能は集計の複数のレベルをサポートしておりそれ以上の flavoring によって実装されている高度なサブタイプを風味が付けられたプロジェクトします。  またはプロジェクトのサブタイプをサポートするオブジェクトは<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> などレイヤー表示の複数のレベルを使用するように設計されています。  内部のサブタイプまたは基本プロジェクトを有効にする COM クライアントと COM の集計の制約の影響を受ける規則はデリゲートのメソッド呼び出しと管理の参照カウントに含めるプロジェクトのサブタイプ基本的にプロジェクトのプログラムを作成する必要があります。  つまり集約をサポートするために集計されたプロジェクトはプログラムする必要があります。  
  
 次の図は複数レベルのプロジェクトのサブタイプの集計のグラフィカル的な表現を示します。  
  
 ![Visual Studio マルチレベル projectflavor グラフィック](~/docs/extensibility/internals/media/vs_multilevelprojectflavor.gif "VS\_MultilevelProjectFlavor")  
複数レベルのプロジェクトのサブタイプ  
  
 複数レベルのプロジェクトのサブタイプの集合で 3 レベルプロジェクトのサブタイプで集計する基本プロジェクトから高度なプロジェクトのサブタイプすると集計する構成されます。  図は[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] プロジェクトのサブタイプ アーキテクチャの一部がサポートするインターフェイスの一部について説明します。  
  
##### 配置機能  
 プロジェクトのサブタイプからの基本プロジェクト システム機能の多くの内側に配置機能です。  プロジェクトのサブタイプは<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> の QueryInterface を呼び出して取得された構成インターフェイスを実装することで配置の機能に影響します \(<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> と <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> など\)。  プロジェクトのサブタイプと高度なプロジェクトのサブタイプの両方が異なる構成の実装を追加する場合高度なプロジェクトのサブタイプの `IUnknown`Foundation プロジェクトの呼び出し `QueryInterface`。  内部のプロジェクトのサブタイプを行うとプロジェクトの構成の実装が含まれている場合は実装への高度なプロジェクトの SubType デリゲートはプロジェクトのサブタイプに用意されています。  1 個の集約レベルから別の状態に維持できる状態非永続化ファイル プロジェクトにビルドするプロジェクトのサブタイプのすべてのレベル <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> 関連 XML データを実行します。  詳細については、「[MSBuild プロジェクト ファイルでデータを保持します。](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)」を参照してください。   プロジェクトのサブタイプのオートメーション エクステンダーを取得するに <xref:EnvDTE80.IInternalExtenderProvider> 機能は として実装されます。  
  
 次の図はオートメーション エクステンダーの実装にプロジェクト構成されたオブジェクトを参照しますが基本プロジェクト システムを拡張するにはプロジェクトのサブタイプに使用するついて説明します。  
  
 ![VS プロジェクト フレーバー オート エクステンダー グラフィック](~/docs/extensibility/internals/media/vs_projectflavorautoextender.gif "VS\_ProjectFlavorAutoExtender")  
プロジェクトのサブタイプのオートメーション エクステンダー。  
  
 プロジェクトのサブタイプはオートメーション オブジェクト モデルを拡張することにより基本プロジェクト システムを拡張できます。  これらがとして DTE オートメーション オブジェクトの部分定義されプロジェクトのオブジェクト`ProjectItem` のオブジェクトと `Configuration` のオブジェクトを拡張するために使用されます。  詳細については、「[ベースのプロジェクトのオブジェクト モデルの拡張](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)」を参照してください。  
  
## 複数レベルの集計  
 低レベルのプロジェクトのサブタイプをラップするプロジェクトのサブタイプの実装はプロジェクトのサブタイプが正しく機能する協調的に設定する必要があります。  プログラミングの責任の一覧を次に示します。:  
  
-   内部のサブタイプをラップするプロジェクトのサブタイプの <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> の実装は <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> に <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A><xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> とメソッドの両方の内部のプロジェクトのサブタイプの実装に代入する必要があります。  
  
-   ラッパーのプロジェクトのサブタイプの <xref:EnvDTE80.IInternalExtenderProvider> の実装はプロジェクトのサブタイプのスキーマに移動する必要があります。  特に名前の文字列を内部のプロジェクトのサブタイプから取得しエクステンダーとして追加する文字列を連結する必要の <xref:EnvDTE80.IInternalExtenderProvider.GetExtenderNames%2A> を実装します。  
  
-   ラッパーのプロジェクトのサブタイプの <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> の実装はラッパーのプロジェクトの SubType 構成オブジェクトであることを行うとプロジェクトの構成オブジェクトに直接対応のためのプロジェクト内部のサブタイプの <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> のオブジェクトをインスタンス化しプライベート デリゲートとして適用する必要があります。  アンマネージ プロジェクトのサブタイプは最初に直接処理する構成インターフェイスをクリックし内部のプロジェクトのサブタイプの <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg.get_CfgType%2A> の実装に他の処理します。  
  
## インターフェイスのサポート  
 基本プロジェクトは実装のさまざまな側面を拡張するプロジェクトのサブタイプによって追加されたサポートするインターフェイスの呼び出しに委任します。  これは拡張プロジェクト構成オブジェクトとさまざまなプロパティ ブラウザーのオブジェクトが含まれます。  これらのインターフェイスは最も外側のプロジェクトのサブタイプ アグリゲーターの `punkOuter` \(`IUnknown` へのポインター\) `QueryInterface` を呼び出して取得されます。  
  
|Interface|サブタイプを参照してください|  
|---------------|--------------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>|プロジェクトのサブタイプを使用する :<br /><br /> -   <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> の実装を用意します。<br />-   プロジェクトのサブタイプを <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> の独自の実装を提供することによってデバッガーの起動を制御します。<br />-   適切に <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.QueryDebugLaunch%2A> の実装の `DBGLAUNCH_DesignTimeExprEval` の例を処理することにより無効のデザイン時の式評価。|  
|<xref:EnvDTE80.IInternalExtenderProvider>|プロジェクトのサブタイプを使用する :<br /><br /> -   プロジェクト構成の個別のプロパティを追加または削除するプロジェクトの <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> を拡張します。<br />-   プロジェクトのオートメーション オブジェクト <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>\(\) を拡張します。<br /><br /> 上のプロパティ値は <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> の列挙体から取得されます。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>|プロジェクトのサブタイプを参照するオブジェクトを <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> にプロジェクト構成を持つオブジェクトを割り当てることができます。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBrowseObject>|プロジェクトのサブタイプを <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> にマップするようにまたはプロジェクトの構成が `VSITEMID` のオブジェクトでオブジェクトを参照します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>|プロジェクトのサブタイプを任意の XML の構造化データをプロジェクト ファイルに保持できるようにします \(.csproj または .vbproj\)。  このデータはMSBuild に表示されません。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>|プロジェクトのサブタイプを使用する :<br /><br /> -   保存する MSBuild の新しいプロパティを追加します。<br />-   MSBuild からの削除の不要なプロパティ。<br />-   MSBuild プロパティの現在の値を照会します。<br />-   MSBuild プロパティの現在の値を変更します。|  
  
## 参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>