---
title: プロジェクトのサブタイプ プロパティとメソッドを拡張 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, extended methods
- project subtypes, extended properties
ms.assetid: 2b9833bf-8551-4ae1-93db-197ba645c65e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 23510ffbb42e0c0c37c07e0ee80ae15f99e5df00
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="properties-and-methods-extended-by-project-subtypes"></a>プロパティとプロジェクトのサブタイプによって拡張メソッド
プロジェクトのサブタイプでは、多数の基本プロジェクトのアグリゲーターとして構成するために、プロジェクトの動作を決定するための電力があります。 このセクションでは、いくつかの拡張またはプロジェクトのサブタイプで変更できる機能をまとめたものです。  
  
## <a name="features-gained-by-aggregation"></a>集計によって得られる機能  
 次の表は、多くの集計の基本プロジェクトをオーバーライドするプロジェクトのサブタイプをできるようにするメソッドをまとめたものです。  
  
|集計によってオーバーライドされたメソッド|プロジェクトのサブタイプ|  
|---------------------------------------|---------------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A>|有効にするプロジェクトのサブタイプ<br /><br /> キャプションとプロジェクト ノードのアイコンを変更します。<br />プロジェクトを完全に上書き`Browse`オブジェクト。<br />-プロジェクトの名前を変更できるかどうかを制御します。<br />並べ替え順序を制御します。<br />ダイナミック ヘルプのユーザー コンテキストを制御します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A>|デザイナーおよびエディターにどのようなコンテキストのサービスが提供されるを制御するプロジェクトのサブタイプを有効にします。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>|有効にするプロジェクトのサブタイプ<br /><br /> -プロジェクト コマンドのコマンド ルーティングに参加します。<br />-追加、削除、またはプロジェクトのアンビエント コマンドとソリューション エクスプ ローラーのアクティブなコマンドの両方を無効にします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>|により、プロジェクトのサブタイプでユーザーに表示される内容をフィルター処理する、**新しい項目の追加** ダイアログ ボックス。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory>|有効にするプロジェクトのサブタイプ<br /><br /> -ファイル拡張子を指定された既定のジェネレーターを決定します。<br />-人間の判読できるジェネレーターの名前を COM オブジェクトにマップします。|  
  
## <a name="properties-used-by-project-subtypes"></a>プロジェクトのサブタイプで使用されるプロパティ  
 環境と基本プロジェクト システムはからプロパティを使用できます<xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID>と<xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2>列挙体をプロジェクト システムのさまざまな機能を制御するプロジェクトのサブタイプを有効にする次の表で詳しく説明します。  
  
|VSHPROPID プロパティ|プロジェクトのサブタイプ|  
|------------------------|---------------------|  
|`AddItemTemplatesGuid`|により、プロジェクトのサブタイプの内容を制御する、**項目の追加** ダイアログ ボックス。 プロジェクトのサブタイプできますテンプレート ディレクトリの新しい仕様を提供、新しい種類のアイテムの追加、既存の項目を削除および基本プロジェクトのアイテムのサブセットを再編成**項目の追加** ダイアログ ボックス。|  
|`PropertyPagesCLSIDList`|追加または構成に依存しないプロパティ ページを削除するプロジェクトのサブタイプを使用できます。|  
|`CfgPropertyPagesCLSIDList`|プロジェクトのサブタイプを追加または削除の構成に依存するプロパティ ページを使用できます。|  
|`ExtObjectCATID`|オブジェクトを提供オートメーション エクステンダー プロジェクトまたはプロジェクト項目エクステンダーの CATID を知ることによってプロジェクトのサブタイプを使用できます。 たとえば、プロジェクトのサブタイプを提供できますカスタム`Project.Extender("<subtype>")`オブジェクト。|  
|`BrowseObjectCATID`|により、プロジェクトのサブタイプのオートメーション エクステンダーを提供する、`Browse`エクステンダーの CATID を知ることによってオブジェクト。 プロジェクトのサブタイプがへの追加のプロパティを追加するなど、<xref:EnvDTE.Project.Properties%2A>コレクション。|  
|`CfgBrowseObjectCATID`|オートメーション エクステンダー プロジェクト構成の参照オブジェクトを指定するプロジェクトのサブタイプを使用できます。 プロジェクトのサブタイプがへの追加のプロパティを追加するなど、<xref:EnvDTE.Configuration.Properties%2A>コレクション。|  
|`CfgExtObjectCATID`|オートメーション エクステンダー構成オブジェクトを指定するプロジェクトのサブタイプを使用できます。|  
|`DefaultPlatformName`|プロジェクトの構成オブジェクトのプラットフォーム名を特定のプロジェクト サブタイプを使用できます。|  
  
 基本のプロジェクトでは、上記のプロパティの既定の実装を提供します。 呼び出すことで、これらの基本プロジェクト取得`QueryInterface`の<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>最も外側のプロジェクト サブタイプになり、結果のプロパティの実装をオーバーライドするプロジェクトのサブタイプ。  
  
## <a name="see-also"></a>関連項目  
 [プロジェクト サブタイプのデザイン](../../extensibility/internals/project-subtypes-design.md)