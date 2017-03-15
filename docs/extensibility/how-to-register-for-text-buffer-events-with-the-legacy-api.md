---
title: "方法: レガシ API でのテキスト バッファーのイベントに登録 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - register for text buffer events
ms.assetid: 5fc00ced-882c-4b48-b46c-1fa5a2469f94
caps.latest.revision: 13
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: b7da1dc26631294b6e41aa6335f2dca064c2831d
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-register-for-text-buffer-events-with-the-legacy-api"></a>方法: テキスト バッファーのイベント、レガシ API の登録
テキスト バッファーを従来の API を使用してアクセスする場合は、次の手順で示すように、テキスト バッファー イベントを登録してください。  
  
### <a name="to-advise-text-buffer-events"></a>テキスト バッファーのイベントを通知するには  
  
1.  上のインターフェイスのいずれかへのポインターから<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>、呼び出す`QueryInterface` <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>.</xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>へのポインターの</xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>  
  
2.  呼び出す、<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer.FindConnectionPoint%2A>メソッド、および登録するイベントのインターフェイス ID を渡します</xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer.FindConnectionPoint%2A>。  
  
     登録する場合など<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>、インターフェイス ID の IID_IVsTextLinesEvents に渡します</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>。  
  
     テキスト バッファーへのポインターを返す、<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>適切な接続ポイント オブジェクトのインターフェイス</xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>。  
  
3.  このポインターを使用して、呼び出す、<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>を登録する、たとえば、イベント インターフェイスの実装にポインターを渡し、メソッド、`IVsTextLinesEvents`インターフェイス</xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>。  
  
     環境を呼び出してイベントをリッスンを停止し、使用できる cookie を返す、<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Unadvise%2A>メソッド</xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Unadvise%2A>。  
  
## <a name="see-also"></a>関連項目  
 [レガシ API でのテキスト バッファー イベント](../extensibility/text-buffer-events-in-the-legacy-api.md)
