---
title: 基本のプロジェクトのオブジェクト モデルを拡張 |Microsoft ドキュメント
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- automation object model, extending
- project subtypes, extending automation object model
- automation object model
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
caps.latest.revision: ''
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: a0fdda35744aaddf8789818afd1f938897470147
ms.sourcegitcommit: 768118d470da9c7164d2f23ca918dfe26a4be72f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/28/2018
---
# <a name="extending-the-object-model-of-the-base-project"></a>基本のプロジェクトのオブジェクト モデルの拡張

プロジェクトのサブタイプには、次の場所に基本プロジェクトのオートメーション オブジェクト モデルを拡張可能性があります。

-   Project.Extender("\<ProjectSubtypeName>") - This allows a project subtype to offer an object with custom methods from the <xref:EnvDTE.Project>. プロジェクトのサブタイプでは、オートメーション エクステンダーを使用して公開することができます、`Project`オブジェクト。 <xref:EnvDTE80.IInternalExtenderProvider>メイン プロジェクト サブタイプ アグリゲーター上で実装されるインターフェイスのオブジェクトを提供する必要があります、`VSHPROPID_ExtObjectCATID`から<xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2>(に対応する、`itemid`値[VSITEMID です。ルート](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)) CATID です。

-   ProjectItem.Extender("\<ProjectSubtypeName>") - This allows a project subtype to offer an object with custom methods from a particular <xref:EnvDTE.ProjectItem> object within the project. プロジェクトのサブタイプでは、オートメーション エクステンダーを使用して、このオブジェクトを公開します。 <xref:EnvDTE80.IInternalExtenderProvider>メイン プロジェクト サブタイプ アグリゲーター上で実装されるインターフェイスがそのオブジェクトを提供する必要があります、`VSHPROPID_ExtObjectCATID`から<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>(目的に対応する<xref:Microsoft.VisualStudio.VSConstants.VSITEMID>) CATID です。

-   Project.Properties - このコレクションは、の構成に依存しないプロパティを公開、`Project`オブジェクト。 プロジェクトのプロパティの詳細については、次を参照してください。<xref:EnvDTE.Project.Properties%2A>です。 プロジェクトのサブタイプでは、オートメーション エクステンダーを使用して、そのプロパティをこのコレクションに追加します。 <xref:EnvDTE80.IInternalExtenderProvider>メイン プロジェクト サブタイプ アグリゲーター上で実装されるインターフェイスがそのオブジェクトを提供する必要があります、 `VSHPROPID_BrowseObjectCATID` VSHPROPID2 から (に対応する、`itemid`値[VSITEMID です。ルート](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)から<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>) CATID です。

-   Configuration.Properties - このコレクションは、特定の構成 (たとえば、デバッグ) のプロジェクトの構成に依存するプロパティを公開します。 詳細については、「<xref:EnvDTE.Configuration>」を参照してください。 プロジェクトのサブタイプでは、オートメーション エクステンダーを使用して、そのプロパティをこのコレクションに追加します。 <xref:EnvDTE80.IInternalExtenderProvider>メイン プロジェクト サブタイプ アグリゲーター上で実装されるインターフェイスは、そのオブジェクトは CATID `VSHPROPID_CfgBrowseObjectCATID` (に対応する、`itemid`値[VSITEMID です。ルート](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>))。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>インターフェイスが別の 1 つの構成の参照オブジェクトを区別するために使用します。

## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>