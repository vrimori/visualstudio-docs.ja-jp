---
title: デザイナー サポート提供元に戻す |Microsoft Docs
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
- designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 07fb73b5a469cca5afc39160feae96f18ee37d86
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49873436"
---
# <a name="supplying-undo-support-to-designers"></a>デザイナー向けの元に戻す操作のサポート提供
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

通常、デザイナー、エディターなどは、コード要素を変更するときに、ユーザーは、最近の変更を取り消すことができるように、元に戻す操作をサポートする必要があります。  
  
 Visual Studio で実装されたほとんどのデザイナーでは、環境によって自動的に提供元に戻す機能があります。  
  
 元に戻す機能のサポートを提供する必要があるデザイナーの実装:  
  
- 抽象基本クラスを実装して元に戻す管理を提供します。 <xref:System.ComponentModel.Design.UndoEngine>  
  
- 実装によって永続化を指定し、CodeDOM のサポート、<xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>と<xref:System.ComponentModel.Design.IComponentChangeService>クラス。  
  
  デザイナーを使用して記述の詳細については[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]を参照してください[デザイン時サポートの拡張](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)します。  
  
  [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]によって既定の元に戻すインフラストラクチャを提供します。  
  
- 管理の実装を提供する元に戻す、<xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>と<xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>クラス。  
  
- 永続性と既定のを通じて CodeDOM のサポートを提供する<xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>と<xref:System.ComponentModel.Design.IComponentChangeService>実装します。  
  
## <a name="obtaining-undo-support-automatically"></a>取り消しのサポートを自動的に取得します。  
 デザイナーで作成した[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]自動および完全な取り消しのサポートを持つ場合、デザイナー。  
  
-   利用、<xref:System.Windows.Forms.Control>ベースのユーザー インターフェイスのクラス。  
  
-   コードの生成と永続化は、標準の CodeDOM に基づくコードの生成と解析システムを採用しています。  
  
     Visual Studio の CodeDOM のサポートの操作方法の詳細については、次を参照してください[動的ソース コードの生成とコンパイル。](http://msdn.microsoft.com/library/d077a3e8-bd81-4bdf-b6a3-323857ea30fb)  
  
## <a name="when-to-use-explicit-designer-undo-support"></a>明示的なデザイナーの取り消しのサポートを使用する場合  
 以外から提供されたいずれかのビューのアダプターと呼ばれる、グラフィカル ユーザー インターフェイスを使用している場合、デザイナーは、独自の元に戻す管理を指定する必要があります<xref:System.Windows.Forms.Control>します。  
  
 この例は、web ベースのグラフィカル デザイン インターフェイスを備えた製品を作成可能性がありますがなく[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]ベースのグラフィカル インターフェイスです。  
  
 このような場合は、このビューのアダプターを登録する必要が 1 つは[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]を使用して<xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute>、元に戻すの明示的な管理を提供します。  
  
 デザイナーは、CodeDOM と永続化は使用しない場合にサポートを提供する必要があります、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]コード生成のモデルで提供される、<xref:System.CodeDom>名前空間を作成します。  
  
## <a name="undo-support-features-of-the-designer"></a>デザイナーのサポート機能を元に戻す  
 環境の SDK には、提供するために必要なインターフェイスの既定の実装を使用していないデザイナーで使用できるサポートを元に戻す<xref:System.Windows.Forms.Control>ベースのユーザー インターフェイスや標準の CodeDOM と永続化モデルのクラス。  
  
 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>クラスから派生、 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] <xref:System.ComponentModel.Design.UndoEngine>クラスの実装を使用して、<xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>元に戻す操作を管理するクラス。  
  
 Visual Studio には、デザイナーの元に戻すには、次の機能が用意されています。  
  
- リンク元に戻す機能を複数のデザイナー。  
  
- デザイナー内で子ユニットが実装することで親と対話できます<xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>と<xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit>で<xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>します。  
  
  環境の SDK では、CodeDOM と永続化を指定してサポートを提供します。  
  
- <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> 実装として、 <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
  A<xref:System.ComponentModel.Design.IComponentChangeService>によって提供される、 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]' のデザイン ホスト。  
  
## <a name="using-the-environment-sdk-features-to-supply-undo-support"></a>取り消しのサポートを提供する環境の SDK の機能を使用します。  
 取り消しのサポートを取得するには、と、デザイナーを実装するオブジェクトが必要です。  
  
- インスタンス化しのインスタンスを初期化、<xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>有効なクラス<xref:System.IServiceProvider>実装します。  
  
- これは、<xref:System.IServiceProvider>クラスは、次のサービスを提供する必要があります。  
  
  -   <xref:System.ComponentModel.Design.IDesignerHost>。  
  
  -   <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
       デザイナーを使用して[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]CodeDOM シリアル化を使用することもできます<xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>で提供される、[!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]の実装として、<xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>します。  
  
       ここで、<xref:System.IServiceProvider>クラスに提供される、<xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>コンス トラクターの実装としてこのオブジェクトを返す必要があります、<xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>クラス。  
  
  -   <xref:System.ComponentModel.Design.IComponentChangeService>  
  
       既定値を使用するデザイナー<xref:System.ComponentModel.Design.DesignSurface>によって提供される、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]デザイン ホストの既定の実装をさせることが保証されます、<xref:System.ComponentModel.Design.IComponentChangeService>クラス。  
  
  デザイナーを実装する、<xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>に基づいて元に戻すメカニズムは、場合に自動的に変更を追跡します。  
  
- プロパティの変更がによる、<xref:System.ComponentModel.TypeDescriptor>オブジェクト。  
  
- <xref:System.ComponentModel.Design.IComponentChangeService> イベントは、取り消し可能な変更がコミットされたときに手動で生成されます。  
  
- コンテキスト内で作成された、デザイナーでの変更、<xref:System.ComponentModel.Design.DesignerTransaction>します。  
  
- いずれかを使用して元に戻す単位の実装によって提供される標準的な取り消し単位を明示的に作成する、デザイナーで選択されます<xref:System.ComponentModel.Design.UndoEngine.UndoUnit>または Visual Studio に固有の実装<xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>から派生した<xref:System.ComponentModel.Design.UndoEngine.UndoUnit>も用意されていて、両方の実装<xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>と<xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit>します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ComponentModel.Design.UndoEngine>   
 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>   
 [デザイン時サポートの拡張](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)

