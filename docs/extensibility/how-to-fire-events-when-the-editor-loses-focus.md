---
title: "方法: エディターがフォーカスを失ったときにイベントを発生させる | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "従来のエディター [Visual Studio SDK] がフォーカスを失うのイベントを発生させる"
ms.assetid: 64d40695-6917-468a-8037-a253453ac159
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# 方法: エディターがフォーカスを失ったときにイベントを発生させる
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

エディターでウィンドウ フレームのフォーカスをいつ失ったかを確認する必要があります。  たとえばエディターでは明確ではない場合コード ウィンドウからコードを抽出する必要がある場合があります。  次の手順では次の手順についてエディターでフォーカスの通知を受信する手順について説明します。  
  
### イベントをエディターにフォーカスが発生します。  
  
1.  <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> から <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> のオブジェクトを取得し選択イベントを監視します。  
  
2.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.AdviseSelectionEvents%2A> を呼び出しそのメソッドを <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents> オブジェクトの提供します。  
  
3.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A> の呼び出しで`elementid==SEID_WindowFrame` を検索します。  
  
4.  次の 2 点に `varValueNew` のパラメーターをテストする :  
  
    1.  検索するウィンドウ フレーム。  
  
    2.  プログラムがあるウィンドウ フレームの選択が失われるポイント。