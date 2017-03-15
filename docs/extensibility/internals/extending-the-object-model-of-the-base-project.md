---
title: "ベースのプロジェクトのオブジェクト モデルの拡張 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "オートメーション オブジェクト モデル チャート、拡張"
  - "プロジェクトのサブタイプ、オートメーション オブジェクト モデルを拡張します。"
  - "オートメーション オブジェクト モデル"
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# ベースのプロジェクトのオブジェクト モデルの拡張
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

プロジェクトのサブタイプでは、次の場所に基本プロジェクトのオートメーション オブジェクト モデルを拡張可能性があります。  
  
-   Project.Extender ("\< ProjectSubtypeName>")-これにより、プロジェクトのサブタイプのカスタム メソッドを使用するオブジェクトを提供する、 <xref:EnvDTE.Project>します。 プロジェクトのサブタイプはオートメーション エクステンダーを使用して、公開、 `Project` オブジェクトです。  <xref:EnvDTE80.IInternalExtenderProvider>メイン プロジェクト サブタイプ アグリゲーターで実装されるインターフェイスがそのオブジェクトを提供する必要があります、 `VSHPROPID_ExtObjectCATID` から <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> (に対応する、 `itemid` VSITEMID_ROOT の値から `VSITEMID`) CATID。  
  
-   ProjectItem.Extender ("\< ProjectSubtypeName>")-これにより、カスタム メソッドの特定のオブジェクトを提供するプロジェクトのサブタイプ <xref:EnvDTE.ProjectItem> プロジェクト内のオブジェクト。 プロジェクトのサブタイプでは、オートメーション エクステンダーを使用して、このオブジェクトを公開します。  <xref:EnvDTE80.IInternalExtenderProvider> メイン プロジェクト サブタイプ アグリゲーターで実装されるインターフェイスは、そのオブジェクトを提供する必要があります、 `VSHPROPID_ExtObjectCATID` から <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (目的に対応する `VSITEMID`) CATID。  
  
-   Project.Properties – このコレクションがの構成の独立したプロパティを公開する、 `Project` オブジェクトです。 プロジェクトのプロパティの詳細については、次を参照してください。 <xref:EnvDTE.Project.Properties%2A>します。 プロジェクトのサブタイプでは、オートメーション エクステンダーを使用して、そのプロパティをこのコレクションに追加します。  <xref:EnvDTE80.IInternalExtenderProvider> メイン プロジェクト サブタイプ アグリゲーターで実装されるインターフェイスは、そのオブジェクトを提供する必要があります、 `VSHPROPID_BrowseObjectCATID` VSHPROPID2 から (に対応する、 `itemid` VSITEMID_ROOT の値から <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>) CATID。  
  
-   Configuration.Properties – このコレクションは、(たとえば、デバッグ) の特定の構成のプロジェクトの構成の依存プロパティを公開します。 詳細については、「 <xref:EnvDTE.Configuration>します。 プロジェクトのサブタイプでは、オートメーション エクステンダーを使用して、そのプロパティをこのコレクションに追加します。  <xref:EnvDTE80.IInternalExtenderProvider> メイン プロジェクト サブタイプ アグリゲーターで実装されるインターフェイスには、オブジェクト、CATID `VSHPROPID_CfgBrowseObjectCATID` (に対応する、 `itemid` の値 <xref:Microsoft.VisualStudio.VSConstants.VSITEMID_ROOT>)。  <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>インターフェイスが 1 つの構成の参照オブジェクトを区別するために使用します。  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>