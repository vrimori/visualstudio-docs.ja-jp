---
title: 簡略化された埋め込み |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - simple view embedding
ms.assetid: f1292478-a57d-48ec-8c9e-88a23f04ffe5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c7ef7e297b834d03d5b7b29013cbe9f18fecbc31
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54921961"
---
# <a name="simplified-embedding"></a>簡略化された埋め込み
(つまりの子を作成する) のドキュメント ビュー オブジェクトの親がある場合、エディターで有効には、簡略化された埋め込み[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]、および<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>インターフェイスは、そのウィンドウのコマンドを処理するために実装されます。 簡略化された埋め込みエディターには、アクティブなコントロールをホストできません。 簡略化された埋め込みエディターを作成するために使用するオブジェクトは、次の図に表示されます。  
  
 ![簡略化された埋め込みエディター グラフィック](../extensibility/media/vssimplifiedembeddingeditor.gif "vsSimplifiedEmbeddingEditor")  
簡略化された埋め込みエディター  
  
> [!NOTE]
>  のみ、この図では、オブジェクトの`CYourEditorFactory`標準的なファイル ベースのエディターを作成するオブジェクトが必要です。 カスタム エディターを作成する場合は、実装する必要はありません<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>エディター、独自のプライベートの永続化メカニズムがないためです。 非カスタム エディターに対し、ただしを行う必要があります。  
  
 含まれるすべてのインターフェイスを簡素化された埋め込みエディターを作成するために実装、`CYourEditorDocument`オブジェクト。 ただし、ドキュメント データの複数のビューをサポートするために分割データとビューのオブジェクトを個別にインターフェイス、次の表に記載されています。  
  
|Interface|インターフェイスの場所|使用|  
|---------------|---------------------------|---------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|表示|親ウィンドウへの接続を提供します。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|表示|コマンドを処理します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|表示|ステータス バーを更新できるようにします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|表示|により、**ツールボックス**項目。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|データ|ファイルが変更されたときに通知を送信します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|データ|ファイルの種類の名前を付けて保存機能を有効にします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>|データ|ドキュメントの永続性を有効にします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|データ|再読み込みをトリガーするなどのファイル変更イベントの抑制を使用できます。|