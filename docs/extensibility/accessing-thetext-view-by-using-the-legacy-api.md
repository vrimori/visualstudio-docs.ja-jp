---
title: "レガシ API を使用してテキスト ビューにアクセスします。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "エディター [Visual Studio SDK] レガシー - テキスト ビュー"
ms.assetid: 8f751f72-c972-4be3-84ee-19c281e02e25
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# レガシ API を使用してテキスト ビューにアクセスします。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

テキスト ビューではテキスト バッファーに格納されているテキスト表示されます。  次のセクションに示すように従来の API を使用してテキスト ビューにアクセスできます。  
  
## テキスト ビュー オブジェクト  
 各ビューは独自のテキスト バッファーに関連付けられビューはバッファーのデータ ウィンドウです。  次の図は <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> によって表されるテキスト ビュー オブジェクトの重要なインターフェイスを示しています。  
  
 ![Visual Studio テキスト ビュー オブジェクト](~/docs/extensibility/media/vstextview.gif "vstextview")  
テキスト ビュー オブジェクト  
  
 ビューはバッファー内のテキストの表示方法です。  これはビューに表示される内容はバッファー内のテキストの正確に反映されないようにワード ラップアウトライン機能などの機能が含まれます。  
  
 ビューはビューの機能は以前に入力したコマンドを傍受して機能するように他のサービスまたはプロセスができます。  これを行う共通サービスは言語サービスです。  動作またはツール ヒントをインデント言語サービスによりカスタムを提供するたとえば必要なEnter キーのコマンドを受け取ることがあります。  
  
## テキスト ビューにフィーチャーを追加する  
 特定のキーストロークを処理してテキスト ビューの動作をカスタマイズできます。  キーストロークを受け取るにはオブジェクトの <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> を実行しコマンドを監視して受け取るようにコマンドの対象 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>\(\) を提供します。  
  
 テキスト ビューはコマンドのフィルターに順次アーキテクチャを使用します。  新しいコマンドのフィルター \(<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> のオブジェクト\) はシーケンスに <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> のメソッドを呼び出して追加されます。  
  
 テキスト ビューのイベント通知は `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents` のインターフェイスを使用して指定されます。  テキスト ビューの変更の通知を受け取るにはクライアント オブジェクトのこのインターフェイスを実装します。  テキスト ビューの <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> インターフェイスのビューの変更通知を受け取るにはを使用してテキスト ビューにこのインターフェイスをさらしてします。  
  
## 参照  
 [レガシ API を使用してビューの設定を変更します。](../extensibility/changing-view-settings-by-using-the-legacy-api.md)   
 [グローバル設定を監視するためのテキスト マネージャーの使用](../extensibility/using-the-text-manager-to-monitor-global-settings.md)