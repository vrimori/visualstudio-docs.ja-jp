---
title: "デザイナーには、サポート提供する元に戻す |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 98243c15f5f69a9aecba589b966d56a68201ab2a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="supplying-undo-support-to-designers"></a>デザイナーに元に戻す機能を提供します。
通常、デザイナー、エディターに対しと同様には、コード要素を変更する場合、ユーザーは、最近の変更を取り消すことができるように、元に戻す操作をサポートする必要があります。  
  
 Visual Studio で実装されているほとんどのデザイナーでは、環境によって自動的に提供元に戻す機能があります。  
  
 元に戻す機能のサポートを提供する必要があるデザイナーの実装。  
  
-   抽象基本クラスを実装することで元に戻す管理を提供します。<xref:System.ComponentModel.Design.UndoEngine>  
  
-   指定の永続化および CodeDOM を実装することによってサポート、<xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>と<xref:System.ComponentModel.Design.IComponentChangeService>クラスです。  
  
 使用するデザイナーの作成の詳細については[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]を参照してください[デザイン時サポートを拡張する](http://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)です。  
  
 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]によって既定の元に戻すインフラストラクチャを提供します。  
  
-   を通じて管理の実装を提供する元に戻す、<xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>と<xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>クラスです。  
  
-   永続性と既定のを通じて CodeDOM サポートを提供する<xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>と<xref:System.ComponentModel.Design.IComponentChangeService>実装します。  
  
## <a name="obtaining-undo-support-automatically"></a>取り消しのサポートを自動的に取得します。  
 作成されたすべてのデザイナー[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]自動と完全に元に戻す機能を持つ場合、デザイナー。  
  
-   は、使用、<xref:System.Windows.Forms.Control>ベースのユーザー インターフェイスのクラスです。  
  
-   コードの生成と永続化の標準的な CodeDOM ベースのコードの生成と解析システムを採用しています。  
  
     Visual Studio CodeDOM サポートの使用の詳細については、次を参照してください[動的ソース コードの生成とコンパイル。](/dotnet/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation)  
  
## <a name="when-to-use-explicit-designer-undo-support"></a>明示的なデザイナー元に戻す機能を使用する場合  
 以外から提供されたいずれかのビューのアダプターと呼ばれる、グラフィカル ユーザー インターフェイスを使用している場合、デザイナーは元に戻す管理を指定する必要があります<xref:System.Windows.Forms.Control>です。  
  
 Web ベースのグラフィカル デザイン インターフェイスを持つ製品を作成するこの例ではなく、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]ベースのグラフィカル インターフェイスです。  
  
 このような場合にする必要がありますでこのビューのアダプターを登録する[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]を使用して<xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute>、元に戻すの明示的な管理を提供します。  
  
 デザイナーは、CodeDOM と永続化を使用しない場合のサポートを提供する必要があります、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]コード生成のモデルで提供される、<xref:System.CodeDom>領域の名前を付けます。  
  
## <a name="undo-support-features-of-the-designer"></a>デザイナーのサポート機能元に戻す  
 環境の SDK では、提供するためのインターフェイスの既定の実装を使用していないデザイナーで使用できるサポートを元に戻す<xref:System.Windows.Forms.Control>ベースのユーザー インターフェイスまたは標準の CodeDOM と永続化モデルのクラスです。  
  
 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>から派生したクラス、 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] <xref:System.ComponentModel.Design.UndoEngine>クラスの実装を使用して、<xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>を管理するクラスは、操作を元に戻します。  
  
 Visual Studio には、デザイナーの元に戻すには、次の機能が用意されています。  
  
-   複数のデザイナー間でリンク元に戻す機能します。  
  
-   デザイナー内で子ユニットは、実装することでその親と対話できます<xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>と<xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit>で<xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>です。  
  
 環境の SDK では、CodeDOM と永続化を指定することによってサポートします。  
  
-   <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>実装として、<xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
 A<xref:System.ComponentModel.Design.IComponentChangeService>によって提供される、 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]' デザイン ホストします。  
  
## <a name="using-the-environment-sdk-features-to-supply-undo-support"></a>取り消しのサポートを提供する SDK の環境の機能を使用します。  
 取り消しのサポートを取得するには、デザイナーを実装するオブジェクトが必要です。  
  
-   インスタンスを作成しのインスタンスを初期化、 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> 、有効なクラス<xref:System.IServiceProvider>実装します。  
  
-   これは、<xref:System.IServiceProvider>クラスは、次のサービスを提供する必要があります。  
  
    -   <xref:System.ComponentModel.Design.IDesignerHost>。  
  
    -   <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
         使用するデザイナー [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] CodeDOM シリアル化を使用することできます<xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>で提供される、[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]の実装として、<xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>です。  
  
         ここで、<xref:System.IServiceProvider>に提供されるクラス、<xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>コンス トラクターの実装としてこのオブジェクトを返す必要があります、<xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>クラスです。  
  
    -   <xref:System.ComponentModel.Design.IComponentChangeService>  
  
         既定値を使用するデザイナー<xref:System.ComponentModel.Design.DesignSurface>によって提供される、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]デザイン ホストの保証がの既定の実装があるため、<xref:System.ComponentModel.Design.IComponentChangeService>クラスです。  
  
 デザイナーを実装する、<xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>に基づいて取り消しメカニズムは、場合に自動的に変更を追跡します。  
  
-   プロパティの変更はを通じて行われます、<xref:System.ComponentModel.TypeDescriptor>オブジェクト。  
  
-   <xref:System.ComponentModel.Design.IComponentChangeService>イベントは取り消し可能な変更がコミットされたときに手動で生成されます。  
  
-   コンテキスト内で作成された、デザイナーでの変更、<xref:System.ComponentModel.Design.DesignerTransaction>です。  
  
-   いずれかを使用して元に戻す単位の実装によって提供される標準の undo ユニットを明示的に作成する、デザイナーで選択<xref:System.ComponentModel.Design.UndoEngine.UndoUnit>または Visual Studio に固有の実装<xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>から派生した<xref:System.ComponentModel.Design.UndoEngine.UndoUnit>も提供し、両方の実装<xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>と<xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit>です。  
  
## <a name="see-also"></a>参照  
 <xref:System.ComponentModel.Design.UndoEngine>   
 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>   
 [デザイン時サポートの拡張](http://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)