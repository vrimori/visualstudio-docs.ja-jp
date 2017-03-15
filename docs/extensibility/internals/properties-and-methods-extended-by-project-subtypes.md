---
title: "プロパティとメソッドは、プロジェクトのサブタイプによって拡張 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project subtypes, extended methods
- project subtypes, extended properties
ms.assetid: 2b9833bf-8551-4ae1-93db-197ba645c65e
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 38bb86636edeaeda4485b7ebe6c8a6349450343c
ms.lasthandoff: 02/22/2017

---
# <a name="properties-and-methods-extended-by-project-subtypes"></a>プロパティとプロジェクトのサブタイプによって拡張メソッド
プロジェクトのサブタイプがの動作を決定する、プロジェクトのベースのプロジェクトの集合として構成するための強力な道具です。 このセクションでは、いくつかの拡張またはプロジェクトのサブタイプによって変更できる機能をまとめたものです。  
  
## <a name="features-gained-by-aggregation"></a>集計によって得られる機能  
 次の表は、多くの集計に基本プロジェクト内でオーバーライド プロジェクト サブタイプができるようにする方法をまとめたものです。  
  
|集計によってオーバーライドされたメソッド|プロジェクトのサブタイプ|  
|---------------------------------------|---------------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>::</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>から<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A>|有効にするプロジェクトのサブタイプ<br /><br /> -キャプションとプロジェクト ノードのアイコンを変更します。<br />プロジェクトを完全にオーバーライド`Browse`オブジェクトです。<br />-プロジェクトの名前を変更できるかどうかを制御します。<br />並べ替え順序を制御します。<br />ダイナミック ヘルプのユーザー コンテキストを制御します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>::</xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>から<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A>|デザイナーとエディターにどのようなコンテキストのサービスが提供されるかを制御するプロジェクトのサブタイプを有効にします。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>::</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>から<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A></xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A></xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>|有効にするプロジェクトのサブタイプ<br /><br /> -プロジェクトのコマンドは、コマンドのルーティングに参加します。<br />追加、削除、またはプロジェクト アンビエント コマンドとソリューション エクスプ ローラーのアクティブなコマンドの両方を無効にします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2></xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>|により、プロジェクトのサブタイプをで表示される内容をフィルター処理、**新しい項目の追加** ダイアログ ボックス。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory></xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory>|有効にするプロジェクトのサブタイプ<br /><br /> -ファイルの拡張子を指定した既定のジェネレーターを確認します。<br />-人間の読み取り可能なジェネレーターの名前を COM オブジェクトにマップします。|  
  
## <a name="properties-used-by-project-subtypes"></a>プロジェクトのサブタイプで使用されるプロパティ  
 環境とベースのプロジェクト システムはからプロパティを使用できます<xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID>と<xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2>列挙体をプロジェクト システムのさまざまな機能を制御するプロジェクトのサブタイプを有効にする次の表で詳しく説明します</xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2></xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID>。  
  
|VSHPROPID プロパティ|プロジェクトのサブタイプ|  
|------------------------|---------------------|  
|`AddItemTemplatesGuid`|により、プロジェクトのサブタイプの内容を制御する、**項目の追加** ダイアログ ボックス。 プロジェクトのサブタイプできますテンプレート ディレクトリの新しい仕様を提供、新しい種類の項目を追加、既存の項目を削除および基本プロジェクトの項目のサブセットを再編成**項目の追加** ダイアログ ボックス。|  
|`PropertyPagesCLSIDList`|により、プロジェクトのサブタイプが追加または構成に依存しないプロパティ ページを削除できます。|  
|`CfgPropertyPagesCLSIDList`|により、プロジェクトのサブタイプが追加または構成に依存するプロパティ ページを削除できます。|  
|`ExtObjectCATID`|オートメーション エクステンダーにやすいプロジェクトまたはプロジェクト アイテム オブジェクト エクステンダーの CATID を知ることによってプロジェクトのサブタイプを許可します。 たとえば、プロジェクトのサブタイプがカスタムを提供できます`Project.Extender("<subtype>")`オブジェクトです。|  
|`BrowseObjectCATID`|により、プロジェクトのサブタイプのオートメーション エクステンダーを提供する、`Browse`エクステンダーの CATID を知ることによってオブジェクトです。 プロジェクトのサブタイプに追加のプロパティを追加するなど、<xref:EnvDTE.Project.Properties%2A>コレクション</xref:EnvDTE.Project.Properties%2A>。|  
|`CfgBrowseObjectCATID`|プロジェクト構成の参照オブジェクトのオートメーション エクステンダーを提供するプロジェクトのサブタイプを許可します。 プロジェクトのサブタイプに追加のプロパティを追加するなど、<xref:EnvDTE.Configuration.Properties%2A>コレクション</xref:EnvDTE.Configuration.Properties%2A>。|  
|`CfgExtObjectCATID`|構成オブジェクトのオートメーション エクステンダーを提供するプロジェクトのサブタイプを許可します。|  
|`DefaultPlatformName`|プラットフォーム名、プロジェクトの構成オブジェクトを判断するプロジェクトのサブタイプを許可します。|  
  
 基本プロジェクトでは、上記のプロパティの既定の実装を提供します。 ベースのプロジェクトが呼び出すことで、これらを取得`QueryInterface`の<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>最も外側のプロジェクトのサブタイプになり、結果のプロパティの実装をオーバーライドするプロジェクトのサブタイプ</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>。  
  
## <a name="see-also"></a>関連項目  
 [プロジェクトのサブタイプの設計](../../extensibility/internals/project-subtypes-design.md)
