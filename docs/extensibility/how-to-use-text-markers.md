---
title: '方法: テキスト マーカーを使用して |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - using text markers
ms.assetid: 76eed51c-eecb-4579-823e-13df2f0526b9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e484ba24eb1ebb8e92f07fb28b2e807ab5460cbc
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54967470"
---
# <a name="how-to-use-text-markers"></a>方法: テキスト マーカーを使用します。
テキスト マーカーは、編集に適用できる、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>オブジェクト。  
  
## <a name="procedures"></a>手順  
  
### <a name="to-apply-text-markers"></a>テキスト マーカーに適用するには  
  
1.  インスタンスを取得、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager>クラス。  
  
    > [!NOTE]
    >  コア エディターでは、それを編集すると、任意のドキュメントに、標準のテキスト マーカーを自動的に適用して、標準のテキスト マーカーを明示的に適用する必要はありません。  
  
2.  呼び出すことによって、関心のあるマーカーのマーカーの種類 ID を取得、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A>メソッドを`GUID`テキスト マーカーを使用したいのです。  
  
    > [!NOTE]
    >  使用しないでください、 `GUID` VSPackage またはテキスト マーカーを提供するサービス。  
  
3.  呼び出すことによって取得したマーカーの種類 ID を使用して、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A>メソッドを呼び出すをパラメーターとして、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A>メソッドまたは<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A>テキスト マーカーをテキストの特定のリージョンに適用する方法。  
  
### <a name="to-add-features-to-text-markers"></a>テキスト マーカーに機能を追加するには  
  
1. テキスト マーカー、ツール ヒント、特殊なコンテキスト メニュー ハンドラーなどの特殊な状況に追加の機能を追加することが望ましい場合があります。 次の手順に従います。  
  
2. 実装するオブジェクトを作成、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>インターフェイス。  
  
3. 追加の機能を使用する場合は、実装、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>、および<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced>インターフェイスを実装するオブジェクトと同じで、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>インターフェイス。  
  
4. 渡す、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>インターフェイスの呼び出しに、作成した、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A>メソッドまたは<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A>メソッドがテキストの特定のリージョンにテキスト マーカーを適用するために使用します。  
  
5. テキスト マーカーのリージョンにコンテキスト メニューのサポートを追加する場合は、メニューを作成する必要があります。  
  
    コンテキスト メニューを参照を作成する方法の詳細についての[コンテキスト メニュー](../extensibility/context-menus.md)します。  
  
6. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]環境などの指定のインターフェイスのメソッドの呼び出し、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetTipText%2A>メソッド、または<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A>メソッドに応じて。  
  
## <a name="see-also"></a>関連項目  
 [テキスト マーカーを使用して、従来の API を使用しました。](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [方法: 標準のテキスト マーカーを追加します。](../extensibility/how-to-add-standard-text-markers.md)   
 [方法: カスタム テキスト マーカーを作成します。](../extensibility/how-to-create-custom-text-markers.md)   
 [方法: エラーのマーカーを実装します。](../extensibility/how-to-implement-error-markers.md)