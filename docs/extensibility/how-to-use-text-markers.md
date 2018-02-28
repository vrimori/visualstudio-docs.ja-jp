---
title: "方法: テキスト マーカーを使用して |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - using text markers
ms.assetid: 76eed51c-eecb-4579-823e-13df2f0526b9
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: f5c5c2686bee9850da72c00e044952b15bed9c58
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-text-markers"></a>方法: テキスト マーカーを使用
テキスト マーカーは編集に適用できる、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>オブジェクト。  
  
## <a name="procedures"></a>手順  
  
#### <a name="to-apply-text-markers"></a>テキスト マーカーを適用するには  
  
1.  インスタンスを取得、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager>クラスです。  
  
    > [!NOTE]
    >  コア エディターでは、それを編集すると、任意のドキュメントに、標準のテキストのマーカーを自動的に適用し、標準のテキストのマーカーを明示的に適用するために必要なできないようにします。  
  
2.  呼び出して、関心のあるマーカーのマーカーの種類 ID を取得、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A>メソッドを`GUID`テキスト マーカーを使用したいのです。  
  
    > [!NOTE]
    >  使用しないで、 `GUID` VSPackage のまたはテキスト マーカーを提供するサービスです。  
  
3.  使用するマーカーの種類 ID は、呼び出すことによって取得、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A>メソッドを呼び出して、パラメーターとして、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A>メソッドまたは<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A>テキストの特定の領域とテキスト マーカーを適用する方法です。  
  
#### <a name="to-add-features-to-text-markers"></a>テキスト マーカーに機能を追加  
  
1.  テキスト マーカー、ツール ヒント、特殊なコンテキスト メニュー ハンドラーなどの特殊な状況に追加の機能を追加することが望ましい場合があります。 これを行うには。  
  
2.  実装するオブジェクトを作成、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>インターフェイスです。  
  
3.  追加の機能が必要な場合は、実装、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>、および<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced>のインターフェイスを実装するのと同じオブジェクトを<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>インターフェイスです。  
  
4.  渡す、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>インターフェイスの呼び出しに、作成した、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A>メソッドまたは<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A>メソッドを使用してテキストの特定の領域とテキスト マーカーを適用します。  
  
5.  テキスト マーカー リージョンにコンテキスト メニューのサポートを追加するときに、メニューを作成するために必要です。  
  
     詳細については、コンテキスト メニューは、「を作成する方法の[コンテキスト メニュー](../extensibility/context-menus.md)です。  
  
6.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]環境など、指定されたインターフェイスのメソッドの呼び出し、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetTipText%2A>メソッド、または<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A>必要に応じてメソッドです。  
  
## <a name="see-also"></a>参照  
 [レガシ API でテキスト マーカーの使用](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [方法: 標準のテキストのマーカーの追加](../extensibility/how-to-add-standard-text-markers.md)   
 [方法: カスタム テキスト マーカーを作成します。](../extensibility/how-to-create-custom-text-markers.md)   
 [方法: エラー マーカーを実装します。](../extensibility/how-to-implement-error-markers.md)