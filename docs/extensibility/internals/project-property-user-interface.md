---
title: "プロジェクトのプロパティのユーザー インターフェイス |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project properties [Visual Studio], user interface
- projects [Visual Studio SDK], properties UI
- project properties UI
ms.assetid: b6aec634-8533-476c-9ebd-36536a2288e2
caps.latest.revision: 16
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: b344731061053abb208225a0480408ebbe682050
ms.lasthandoff: 02/22/2017

---
# <a name="project-property-user-interface"></a>プロジェクト プロパティのユーザー インターフェイス
プロジェクトのサブタイプは、プロジェクトで項目を使用することができます**プロパティ ページ** ダイアログ ボックス ベースのプロジェクトで提供されますが非表示にまたは指定すると、読み取り専用コントロールとページ全体のくださいまたはプロジェクト サブタイプに固有のページを追加、**プロパティ ページ** ダイアログ ボックス。  
  
## <a name="extending-the-project-property-dialog-box"></a>プロジェクトのプロパティ ダイアログ ボックスを拡張します。  
 プロジェクトのサブタイプでは、オートメーション エクステンダーとプロジェクト構成の参照オブジェクトを実装します。 これらのエクステンダーの実装、<xref:EnvDTE.IFilterProperties>を行う特定のプロパティを非表示または読み取り専用のインターフェイス</xref:EnvDTE.IFilterProperties>。 **プロパティ ページ**ベースのプロジェクトによって実装される基本のプロジェクトのダイアログ ボックスでは、オートメーション エクステンダーによって実行されるフィルター処理します。  
  
 拡張するためのプロセス、**プロジェクト プロパティ** ダイアログ ボックスを以下に示します。  
  
-   ベースのプロジェクトからプロジェクトのサブタイプが実装することによって、エクステンダーを取得する、<xref:EnvDTE80.IInternalExtenderProvider>インターフェイス</xref:EnvDTE80.IInternalExtenderProvider>。 [参照]、プロジェクトの自動化、および基本プロジェクトのすべてのプロジェクト構成の参照オブジェクトは、このインターフェイスを実装します。  
  
-   実装<xref:EnvDTE80.IInternalExtenderProvider>プロジェクトの参照オブジェクトとプロジェクト オートメーション オブジェクトに委任の<xref:EnvDTE80.IInternalExtenderProvider>プロジェクト サブタイプ アグリゲーターの実装 (これらは、`QueryInterface`の<xref:EnvDTE80.IInternalExtenderProvider>上、<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>プロジェクト オブジェクト).</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> </xref:EnvDTE80.IInternalExtenderProvider> </xref:EnvDTE80.IInternalExtenderProvider> </xref:EnvDTE80.IInternalExtenderProvider>  
  
-   基本プロジェクト構成の参照オブジェクトも実装されて<xref:EnvDTE80.IInternalExtenderProvider>プロジェクト サブタイプ構成オブジェクトからオートメーション エクステンダーに直接接続する機能</xref:EnvDTE80.IInternalExtenderProvider>。 その実装のデリゲートを<xref:EnvDTE80.IInternalExtenderProvider>プロジェクト サブタイプ アグリゲーターによって実装されるインターフェイス</xref:EnvDTE80.IInternalExtenderProvider>。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>、プロジェクト構成参照オブジェクトを返します。 によって実装される、<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>オブジェクト。</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy></xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>、プロジェクト構成参照オブジェクトを返します。 実装しても、<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>オブジェクト。</xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg></xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>  
  
-   プロジェクトのサブタイプは、次を取得することによって実行時に基本プロジェクトのさまざまな拡張可能なオブジェクトの適切な Catid を判断できます<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>値:</xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2></xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2></xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2></xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
 これらのプロパティを取得するプロジェクトのサブタイプがプロジェクト スコープの Catid を確認するのに<xref:Microsoft.VisualStudio.VSConstants.VSITEMID_ROOT>から、 `VSITEMID``typedef`</xref:Microsoft.VisualStudio.VSConstants.VSITEMID_ROOT> 。 プロジェクトのサブタイプはこれを制御する必要もあります**プロパティ ページ**プロジェクトのダイアログ ボックスのページが表示される構成に依存して、構成に依存しません。 いくつかのプロジェクトのサブタイプは、組み込みのページを削除し、プロジェクトのサブタイプの特定のページを追加する必要があります。 これには、マネージ クライアント プロジェクトの呼び出しを有効にするために、<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>メソッドに次のプロパティ:</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>  
  
-   `VSHPROPID_PropertyPagesCLSIDList`などの構成に依存しないプロパティ ページの Clsid をセミコロンで区切られた一覧。  
  
-   `VSHPROPID_CfgPropertyPagesCLSIDList —`セミコロンで区切られた一連の構成に依存するプロパティ ページの Clsid です。  
  
 プロジェクトの集計のサブタイプであるため、<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>オブジェクトを制御するこれらのプロパティの定義よりも優先**プロパティ ページ** ダイアログ ボックスが表示されます</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>。 プロジェクトのサブタイプが内部の基本プロジェクトからこれらのプロパティを取得し、し、追加または削除できます Clsid 必要に応じて。  
  
 プロジェクトのサブタイプによって追加された新しいプロパティ ページでは、プロジェクトの基本実装からプロジェクト構成の参照オブジェクトを渡されます。 このプロジェクト構成の参照オブジェクトには、オートメーション エクステンダーがサポートしています。 AutomationExtenders の詳細については、次を参照してください。[実装とオートメーション エクステンダーを使用して](http://msdn.microsoft.com/Library/0d5c218c-f412-4b28-ab0c-33a611f62356)します。 プロジェクトのサブタイプの呼び出しによって実装されるプロパティ ページ<xref:EnvDTE.Project.Extender%2A>オブジェクトを取得する独自プロジェクト サブタイプ構成参照ベースのプロジェクトの構成の参照オブジェクトを拡張する</xref:EnvDTE.Project.Extender%2A>。  
  
## <a name="see-also"></a>関連項目  
 <xref:EnvDTE.IFilterProperties></xref:EnvDTE.IFilterProperties>   
 [プロパティ ページ ダイアログ ボックス](http://msdn.microsoft.com/en-us/4a3d34ac-ed03-45e8-ae60-a0e1aad300e4)
