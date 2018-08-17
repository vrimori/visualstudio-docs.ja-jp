---
title: '方法: テキスト バッファー イベント、レガシ API の登録 |Microsoft Docs'
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
ms.openlocfilehash: 9ffe8362f26a55fdb6a9fe236782965a2062ed69
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/08/2018
ms.locfileid: "39639934"
---
# <a name="how-to-register-for-text-buffer-events-with-the-legacy-api"></a>方法: テキスト バッファー イベント、レガシ API の登録
テキスト バッファーを従来の API を使用してアクセスする場合は、テキスト バッファー イベント、次の手順で示すように登録してください。  
  
## <a name="to-advise-text-buffer-events"></a>テキスト バッファーのイベントを通知するには  
  
1.  上のインターフェイスのいずれかへのポインターから<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>、呼び出す`QueryInterface`へのポインターの<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>します。  
  
2.  呼び出す、<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer.FindConnectionPoint%2A>メソッド、および登録するイベントのインターフェイス ID を渡します。  
  
     例では、登録する場合の<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>、インターフェイス ID の IID_IVsTextLinesEvents で渡します。  
  
     テキスト バッファーへのポインターを返します、<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>適切な接続ポイント オブジェクトのインターフェイス。  
  
3.  このポインターを使用して、呼び出し、<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>を登録する、たとえば、イベント インターフェイスの実装にポインターを渡し、メソッド、`IVsTextLinesEvents`インターフェイス。  
  
     環境が呼び出すことによってイベントのリッスンを中止し、使用できるクッキーを返します、<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Unadvise%2A>メソッド。  
  
## <a name="see-also"></a>関連項目  
 [従来の API でのテキスト バッファー イベント](../extensibility/text-buffer-events-in-the-legacy-api.md)