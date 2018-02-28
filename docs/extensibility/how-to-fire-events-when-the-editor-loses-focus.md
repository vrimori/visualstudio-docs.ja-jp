---
title: "方法: エディターがフォーカスを失ったときにイベントを発生させる |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - fire events on losing focus
ms.assetid: 64d40695-6917-468a-8037-a253453ac159
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: bb20adf3950e87c37e2ca64bcd78913839f89d01
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-fire-events-when-the-editor-loses-focus"></a>方法: エディターがフォーカスを失ったときにイベントを発生させる
エディターは、ウィンドウ フレームにフォーカスを失ったときに知っておく必要があります。 たとえば、エディターが不要になったことにフォーカスが移動した後に、コード ウィンドウからコードを抽出する必要があります。 次の手順では、フォーカスを失うエディターの通知を受信するために従う手順を説明します。  
  
### <a name="to-fire-an-event-in-response-to-an-editor-losing-focus"></a>フォーカスを失うエディターへの応答でイベントを発生させる  
  
1.  取得することによって選択イベントを監視、<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>オブジェクトから<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>です。  
  
2.  呼び出す<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.AdviseSelectionEvents%2A>提供して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>オブジェクト。  
  
3.  呼び出しで<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A>、探します`elementid==SEID_WindowFrame`です。  
  
4.  テスト、`varValueNew`次の 2 つのパラメーター。  
  
    1.  探しているウィンドウ フレームです。  
  
    2.  プログラムがウィンドウ フレームに選択範囲を失うをポイントします。