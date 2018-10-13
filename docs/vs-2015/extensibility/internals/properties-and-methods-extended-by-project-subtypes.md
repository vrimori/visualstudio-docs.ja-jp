---
title: プロジェクト サブタイプによってプロパティとメソッドの拡張 |Microsoft Docs
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
- project subtypes, extended methods
- project subtypes, extended properties
ms.assetid: 2b9833bf-8551-4ae1-93db-197ba645c65e
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7c589c6d40e49bf064c805c35e88433556f7b677
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49260211"
---
# <a name="properties-and-methods-extended-by-project-subtypes"></a>プロジェクト サブタイプによって拡張されるプロパティとメソッド
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

プロジェクト サブタイプが、多くの基本プロジェクトのアグリゲーターとして構成するために、プロジェクトの動作を制御する能力です。 このセクションでは、いくつかのプロジェクト サブタイプによって変更または拡張が可能な機能をまとめたものです。  
  
## <a name="features-gained-by-aggregation"></a>集計によって得られた機能  
 次の表は、集計により、プロジェクトのサブタイプ基本プロジェクト内でオーバーライドするメソッドの多くをまとめたものです。  
  
|集計によってオーバーライドされたメソッド|プロジェクト サブタイプ|  
|---------------------------------------|---------------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A>|有効にするプロジェクト サブタイプ<br /><br /> キャプションとプロジェクト ノードのアイコンを変更します。<br />プロジェクトを完全にオーバーライド`Browse`オブジェクト。<br />-プロジェクトの名前を変更できるかどうかを制御します。<br />並べ替え順序を制御します。<br />ダイナミック ヘルプのユーザー コンテキストを制御します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A>|どのようなコンテキストのサービスを提供するデザイナーとエディターを制御するためのプロジェクト サブタイプを有効にします。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>|有効にするプロジェクト サブタイプ<br /><br /> -プロジェクトのコマンドのコマンドのルーティングに参加します。<br />追加、削除、またはアンビエント コマンドのプロジェクトとソリューション エクスプ ローラーのアクティブなコマンドの両方を無効にします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>|プロジェクトのサブタイプをで表示されるユーザーをフィルター処理できるように、**新しい項目の追加** ダイアログ ボックス。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory>|有効にするプロジェクト サブタイプ<br /><br /> ファイル拡張子を指定された既定のジェネレーターを決定します。<br />-COM オブジェクトへの読み取り可能な人間のジェネレーターの名前をマップします。|  
  
## <a name="properties-used-by-project-subtypes"></a>プロジェクト サブタイプによって使用されるプロパティ  
 環境と基本プロジェクト システムからプロパティを使用できます<xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID>と<xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2>列挙型のプロジェクト システムのさまざまな機能を制御するためのプロジェクト サブタイプを有効にする次の表で詳しく説明します。  
  
|VSHPROPID プロパティ|プロジェクト サブタイプ|  
|------------------------|---------------------|  
|`AddItemTemplatesGuid`|内容を制御するためのプロジェクト サブタイプを許可、**項目の追加** ダイアログ ボックス。 プロジェクト サブタイプできますテンプレート ディレクトリの新しい仕様を提供する、新しい種類の項目を追加、既存の項目を削除および基本プロジェクトのアイテムのサブセットを再構成**項目の追加** ダイアログ ボックス。|  
|`PropertyPagesCLSIDList`|プロジェクト サブタイプを追加または削除の構成に依存しないプロパティ ページを使用できます。|  
|`CfgPropertyPagesCLSIDList`|プロジェクト サブタイプを追加または削除の構成に依存するプロパティ ページを使用できます。|  
|`ExtObjectCATID`|プロジェクトのサブタイプが提供するオートメーション エクステンダー プロジェクトまたはプロジェクト項目オブジェクト エクステンダーの CATID を理解していることを許可します。 たとえば、プロジェクトのサブタイプがカスタムを提供できます`Project.Extender("<subtype>")`オブジェクト。|  
|`BrowseObjectCATID`|により、プロジェクトのサブタイプのオートメーション エクステンダーを提供する、 `Browse` Extender の CATID を知ることによってオブジェクト。 プロジェクト サブタイプがへの追加のプロパティを追加するなど、<xref:EnvDTE.Project.Properties%2A>コレクション。|  
|`CfgBrowseObjectCATID`|オートメーション エクステンダー プロジェクト構成の参照オブジェクトを指定するプロジェクトのサブタイプを使用できます。 プロジェクト サブタイプがへの追加のプロパティを追加するなど、<xref:EnvDTE.Configuration.Properties%2A>コレクション。|  
|`CfgExtObjectCATID`|構成オブジェクトのオートメーション エクステンダーを提供するプロジェクトのサブタイプを使用できます。|  
|`DefaultPlatformName`|プロジェクトの構成オブジェクトのプラットフォーム名を特定のプロジェクト サブタイプを使用できます。|  
  
 基本のプロジェクトでは、上記のプロパティの既定の実装を提供します。 基本プロジェクトが呼び出すことで、これらを取得`QueryInterface`の<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>最も外側のプロジェクト サブタイプでプロットできます。 つまり、プロパティの実装をオーバーライドするプロジェクトのサブタイプ。  
  
## <a name="see-also"></a>関連項目  
 [プロジェクト サブタイプのデザイン](../../extensibility/internals/project-subtypes-design.md)

