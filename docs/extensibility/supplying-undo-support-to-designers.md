---
title: "デザイナーにサポート提供する元に戻す |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 95e6873d0a3b254fa8f34144253a44c0a8cab60d
ms.lasthandoff: 02/22/2017

---
# <a name="supplying-undo-support-to-designers"></a>デザイナーに取り消しのサポートを提供します。
通常、デザイナー、エディターのようには、コード要素を変更するときに、ユーザーは最近の変更内容を取り消すことができるように、元に戻す操作をサポートする必要があります。  
  
 Visual Studio で実装されたほとんどのデザイナーでは、取り消しのサポート、環境によって自動的に提供があります。  
  
 元に戻す機能のサポートを提供する必要があるデザイナーの実装:  
  
-   抽象基本クラスを実装することにより元に戻す管理を提供します。<xref:System.ComponentModel.Design.UndoEngine></xref:System.ComponentModel.Design.UndoEngine>  
  
-   指定の永続化および CodeDOM を実装することによってサポート、<xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>と<xref:System.ComponentModel.Design.IComponentChangeService>クラス</xref:System.ComponentModel.Design.IComponentChangeService></xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>。  
  
 使用するデザイナーの作成の詳細については[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]を参照してください[デザイン時サポートを拡張する](http://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)です。  
  
 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]によって既定の元に戻すインフラストラクチャを提供します。  
  
-   を通じて管理の実装を提供する元に戻す、<xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>と<xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>クラス</xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit></xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>。  
  
-   永続化と既定値を通じて CodeDOM サポートを提供する<xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>と<xref:System.ComponentModel.Design.IComponentChangeService>の実装</xref:System.ComponentModel.Design.IComponentChangeService></xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>。  
  
## <a name="obtaining-undo-support-automatically"></a>取り消しのサポートを自動的に取得します。  
 すべてのデザイナーで作成した[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]自動的かつ完全取り消しのサポートを持つ場合、デザイナー。  
  
-   は、使用、<xref:System.Windows.Forms.Control>ベースのユーザー インターフェイスのクラス</xref:System.Windows.Forms.Control>。  
  
-   コードの生成と永続化の標準の CodeDOM に基づくコードの生成と解析システムを採用しています。  
  
     Visual Studio の CodeDOM サポートを扱う方法の詳細については、次を参照してください[動的ソース コードの生成とコンパイル。](http://msdn.microsoft.com/Library/d077a3e8-bd81-4bdf-b6a3-323857ea30fb)  
  
## <a name="when-to-use-explicit-designer-undo-support"></a>明示的なデザイナーの取り消しのサポートを使用する場合  
 <xref:System.Windows.Forms.Control>。</xref:System.Windows.Forms.Control>によって提供されるものではないのビューのアダプターと呼ばれる、グラフィカル ユーザー インターフェイスを使用している場合、デザイナーは元に戻す管理を指定する必要があります。  
  
 Web ベースのグラフィカル デザイン インターフェイスを備えた製品を作成するこの例ではなく、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]ベースのグラフィカル インターフェイスです。  
  
 このような場合は、いずれかのしなければならない場合にこのビューのアダプタの登録[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]を使用して<xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute>、明示的な復元の管理が提供されます</xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute>。  
  
 デザイナーは、CodeDOM と永続性は使用しない場合にサポートを提供する必要があります、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]コード生成のモデルで提供される、<xref:System.CodeDom>よび名前空間</xref:System.CodeDom>。  
  
## <a name="undo-support-features-of-the-designer"></a>デザイナーのサポート機能を元に戻す  
 環境 SDK を提供するためのインターフェイスの既定の実装を使用していないデザイナーで使用できるサポートを元に戻すには<xref:System.Windows.Forms.Control>ベースのユーザー インターフェイスまたは標準の CodeDOM と永続化のモデルのクラス</xref:System.Windows.Forms.Control>。  
  
 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>クラスから派生する、 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] <xref:System.ComponentModel.Design.UndoEngine>クラスの実装を使用して、<xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>元に戻す操作を管理するクラス</xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager></xref:System.ComponentModel.Design.UndoEngine></xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>。  
  
 Visual Studio には、デザイナーの元に戻すには、次の機能が用意されています。  
  
-   複数のデザイナー間でリンク元に戻す機能します。  
  
-   デザイナー内で子単位がその親<xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>と<xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit><xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>。</xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit></xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit></xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>を実装することで対話します。  
  
 環境の SDK では、CodeDOM と永続性を提供することによってサポートを提供します。  
  
-   <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>実装として、<xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService></xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService></xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>  
  
 A<xref:System.ComponentModel.Design.IComponentChangeService>によって提供される、 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]' デザイン ホスト</xref:System.ComponentModel.Design.IComponentChangeService>。  
  
## <a name="using-the-environment-sdk-features-to-supply-undo-support"></a>環境の SDK の機能を使用して、取り消しのサポートを提供するには  
 取り消しのサポートを取得するには、デザイナーを実装するオブジェクトが必要です。  
  
-   インスタンスを作成しのインスタンスを初期化、<xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>に有効なクラス<xref:System.IServiceProvider>実装</xref:System.IServiceProvider></xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>。  
  
-   これは、<xref:System.IServiceProvider>クラスは、次のサービスを提供する必要があります:</xref:System.IServiceProvider>  
  
    -   <xref:System.ComponentModel.Design.IDesignerHost>.</xref:System.ComponentModel.Design.IDesignerHost>  
  
    -   <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService></xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
         使用するデザイナー [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] CodeDOM シリアル化を使用することできます<xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>で提供される、 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>.</xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>の実装として</xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>  
  
         この場合は、<xref:System.IServiceProvider>クラスの提供を<xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>コンス トラクターは、<xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>クラス</xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>の実装としては、このオブジェクトを返す必要があります</xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine></xref:System.IServiceProvider>  
  
    -   <xref:System.ComponentModel.Design.IComponentChangeService></xref:System.ComponentModel.Design.IComponentChangeService>  
  
         既定値を使用するデザイナー<xref:System.ComponentModel.Design.DesignSurface>によって提供される、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]デザイン ホストを<xref:System.ComponentModel.Design.IComponentChangeService>クラス</xref:System.ComponentModel.Design.IComponentChangeService>の既定の実装を持つという保証</xref:System.ComponentModel.Design.DesignSurface>  
  
 デザイナーを実装する、<xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>に基づいて取り消しメカニズムは、場合に自動的に変更を追跡します</xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>。  
  
-   プロパティの変更はを通じて行われますが、<xref:System.ComponentModel.TypeDescriptor>オブジェクト</xref:System.ComponentModel.TypeDescriptor>。  
  
-   <xref:System.ComponentModel.Design.IComponentChangeService>イベントは取り消し可能な変更がコミットされるときに手動で生成されます。</xref:System.ComponentModel.Design.IComponentChangeService>  
  
-   <xref:System.ComponentModel.Design.DesignerTransaction>。</xref:System.ComponentModel.Design.DesignerTransaction>のコンテキスト内で作成された、デザイナーでの変更  
  
-   デザイナーの選択元に戻す単位のいずれかを使用して<xref:System.ComponentModel.Design.UndoEngine.UndoUnit>、Visual Studio 固有の実装<xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit><xref:System.ComponentModel.Design.UndoEngine.UndoUnit>の両方<xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>と<xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit></xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit></xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>、実装も提供</xref:System.ComponentModel.Design.UndoEngine.UndoUnit>から派生した、</xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>または</xref:System.ComponentModel.Design.UndoEngine.UndoUnit>の実装によって提供される標準的な取り消し単位を明示的に作成するには  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ComponentModel.Design.UndoEngine></xref:System.ComponentModel.Design.UndoEngine>   
 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine></xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>   
 [デザイン時サポートを拡張します。](http://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)
