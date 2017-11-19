---
title: "基本のプロジェクトのオブジェクト モデルを拡張 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automation object model, extending
- project subtypes, extending automation object model
- automation object model
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b92fe7fece58dd2006507f0285d3c440af437ee4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="extending-the-object-model-of-the-base-project"></a>基本のプロジェクトのオブジェクト モデルの拡張
プロジェクトのサブタイプには、次の場所に基本プロジェクトのオートメーション オブジェクト モデルを拡張可能性があります。  
  
-   Project.Extender ("\<ProjectSubtypeName >")-これにより、カスタム メソッドからのオブジェクトを提供するプロジェクトのサブタイプ、<xref:EnvDTE.Project>です。 プロジェクトのサブタイプでは、オートメーション エクステンダーを使用して公開することができます、`Project`オブジェクト。 <xref:EnvDTE80.IInternalExtenderProvider>メイン プロジェクト サブタイプ アグリゲーター上で実装されるインターフェイスのオブジェクトを提供する必要があります、`VSHPROPID_ExtObjectCATID`から<xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2>(に対応する、 `itemid` VSITEMID_ROOT の値から`VSITEMID`) CATID です。  
  
-   ProjectItem.Extender ("\<ProjectSubtypeName >")-これにより、カスタム メソッドの特定のオブジェクトを提供するプロジェクトのサブタイプ<xref:EnvDTE.ProjectItem>プロジェクト内のオブジェクト。 プロジェクトのサブタイプでは、オートメーション エクステンダーを使用して、このオブジェクトを公開します。 <xref:EnvDTE80.IInternalExtenderProvider>メイン プロジェクト サブタイプ アグリゲーター上で実装されるインターフェイスがそのオブジェクトを提供する必要があります、`VSHPROPID_ExtObjectCATID`から<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>(目的に対応する`VSITEMID`) CATID です。  
  
-   Project.Properties - このコレクションは、の構成の独立したプロパティを公開、`Project`オブジェクト。 プロジェクトのプロパティの詳細については、次を参照してください。<xref:EnvDTE.Project.Properties%2A>です。 プロジェクトのサブタイプでは、オートメーション エクステンダーを使用して、そのプロパティをこのコレクションに追加します。 <xref:EnvDTE80.IInternalExtenderProvider>メイン プロジェクト サブタイプ アグリゲーター上で実装されるインターフェイスがそのオブジェクトを提供する必要があります、 `VSHPROPID_BrowseObjectCATID` VSHPROPID2 から (に対応する、 `itemid` VSITEMID_ROOT の値から<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>) CATID です。  
  
-   Configuration.Properties - このコレクションは、(たとえば、デバッグ) 特定の構成のプロジェクトの構成の依存するプロパティを公開します。 詳細については、「<xref:EnvDTE.Configuration>」を参照してください。 プロジェクトのサブタイプでは、オートメーション エクステンダーを使用して、そのプロパティをこのコレクションに追加します。 <xref:EnvDTE80.IInternalExtenderProvider>メイン プロジェクト サブタイプ アグリゲーター上で実装されるインターフェイスは、そのオブジェクトは CATID `VSHPROPID_CfgBrowseObjectCATID` (に対応する、`itemid`値<xref:Microsoft.VisualStudio.VSConstants.VSITEMID_ROOT>)。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>インターフェイスが別の 1 つの構成の参照オブジェクトを区別するために使用します。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>