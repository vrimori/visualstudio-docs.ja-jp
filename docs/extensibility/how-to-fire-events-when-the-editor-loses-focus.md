---
title: '方法: エディターがフォーカスを失ったときにイベントを発生させる |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - fire events on losing focus
ms.assetid: 64d40695-6917-468a-8037-a253453ac159
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d579b30c5eac25c815739149d3b3baacc22dc439
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53990767"
---
# <a name="how-to-fire-events-when-the-editor-loses-focus"></a>方法: エディターがフォーカスを失ったときにイベントを発生させる
エディターがウィンドウ フレームにフォーカスを失ったときに知っておく必要があります。 たとえば、エディターが不要になったことに重点を置いてコード ウィンドウからコードを展開する必要があります。 次の手順では、エディターのフォーカスを失うことの通知を受信するために従う手順を示します。  
  
## <a name="to-fire-an-event-in-response-to-an-editor-losing-focus"></a>フォーカスを失うエディターへの応答でイベントを発生させる  
  
1.  取得することによって選択イベントを監視、<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>オブジェクトから<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>します。  
  
2.  呼び出す<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.AdviseSelectionEvents%2A>提供して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>オブジェクト。  
  
3.  呼び出しで<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A>、探して`elementid==SEID_WindowFrame`します。  
  
4.  テスト、`varValueNew`次の 2 つのパラメーター。  
  
    1.  探しているウィンドウ フレーム。  
  
    2.  プログラムがウィンドウ フレームに選択範囲を失ったポイント。