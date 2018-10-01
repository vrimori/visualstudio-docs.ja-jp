---
title: '方法: テキスト バッファー イベント、レガシ API の登録 |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - register for text buffer events
ms.assetid: 5fc00ced-882c-4b48-b46c-1fa5a2469f94
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b98c6a084e8d77b9c85d56da95ec9abdcd469192
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47538648"
---
# <a name="how-to-register-for-text-buffer-events-with-the-legacy-api"></a>方法: テキスト バッファー イベント、レガシ API の登録
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: テキスト バッファー イベント、レガシ API の登録](https://docs.microsoft.com/visualstudio/extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api)します。  
  
テキスト バッファーを従来の API を使用してアクセスする場合は、テキスト バッファー イベント、次の手順で示すように登録してください。  
  
### <a name="to-advise-text-buffer-events"></a>テキスト バッファーのイベントを通知するには  
  
1.  上のインターフェイスのいずれかへのポインターから<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>、呼び出す`QueryInterface`へのポインターの<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>します。  
  
2.  呼び出す、<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer.FindConnectionPoint%2A>メソッド、および登録するイベントのインターフェイス ID を渡します。  
  
     例では、登録する場合の<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>、インターフェイス ID の IID_IVsTextLinesEvents で渡します。  
  
     テキスト バッファーへのポインターを返します、<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>適切な接続ポイント オブジェクトのインターフェイス。  
  
3.  このポインターを使用して、呼び出し、<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>を登録する、たとえば、イベント インターフェイスの実装にポインターを渡し、メソッド、`IVsTextLinesEvents`インターフェイス。  
  
     環境が呼び出すことによってイベントのリッスンを中止し、使用できるクッキーを返します、<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Unadvise%2A>メソッド。  
  
## <a name="see-also"></a>関連項目  
 [レガシ API のテキスト バッファー イベント](../extensibility/text-buffer-events-in-the-legacy-api.md)

