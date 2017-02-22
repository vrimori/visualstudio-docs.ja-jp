---
title: "コンテキスト メニュー | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "エディター [Visual Studio SDK] レガシーのコンテキスト メニュー"
ms.assetid: 44fd9e6a-6d42-4aba-80ba-f37fa0070f1d
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# コンテキスト メニュー
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

コンテキスト メニューはマウスの右ボタンを離すとユーザーがクライアント領域およびクリアのアクティブな領域を右クリックすると表示されます。  
  
## エディターのコンテキスト メニュー  
 `ECMD_SHOWCONTEXTMENU` の傍受して言語サービスがエディターに表示されるコンテキスト メニューを制御できます。  <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> に <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A> の呼び出しを渡すときに独自のコンテキスト メニューを表示するにはこのコマンドを処理します。  このコマンドを処理しエディターに用意されている標準コンテキスト メニューを表示します。  またマーカーの基本のコンテキスト メニューの内容を制御できます。  詳細については、「[レガシ API でテキストのマーカーの使用](../extensibility/using-text-markers-with-the-legacy-api.md)」および「[従来の言語サービスのコマンドを受信](../extensibility/internals/intercepting-legacy-language-service-commands.md)」を参照してください。  
  
## 参照  
 [言語サービスを開発します。](../extensibility/internals/developing-a-legacy-language-service.md)   
 [拡張メニューとコマンド](../extensibility/extending-menus-and-commands.md)