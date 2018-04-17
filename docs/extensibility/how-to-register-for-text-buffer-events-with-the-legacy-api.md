---
title: '方法: テキスト バッファー イベント、レガシ API の登録 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - register for text buffer events
ms.assetid: 5fc00ced-882c-4b48-b46c-1fa5a2469f94
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b708507096e7035039e54af7505c8f5f939b5724
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-register-for-text-buffer-events-with-the-legacy-api"></a>方法: テキスト バッファー イベント、レガシ API の登録
テキスト バッファーをレガシ API を使用してアクセスする場合は、テキスト バッファー イベント、次の手順で示すように登録する必要があります。  
  
### <a name="to-advise-text-buffer-events"></a>テキスト バッファーのイベントを通知するには  
  
1.  上のインターフェイスのいずれかへのポインターから<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>、呼び出す`QueryInterface`へのポインターの<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>します。  
  
2.  呼び出す、<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer.FindConnectionPoint%2A>メソッド、および登録するイベントのインターフェイス ID を渡します。  
  
     たとえばを登録する場合<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>、インターフェイス ID の IID_IVsTextLinesEvents に渡します。  
  
     テキスト バッファーへのポインターを返します、<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>適切な接続ポイント オブジェクトのインターフェイスです。  
  
3.  このポインターを使用して、呼び出し、<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>を登録する、たとえば、イベント インターフェイスの実装にポインターを渡し、メソッド、`IVsTextLinesEvents`インターフェイスです。  
  
     環境を停止イベントの待機を呼び出すことによって行うこともできますし、cookie が返されます、<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Unadvise%2A>メソッドです。  
  
## <a name="see-also"></a>関連項目  
 [レガシ API でのテキスト バッファー イベント](../extensibility/text-buffer-events-in-the-legacy-api.md)