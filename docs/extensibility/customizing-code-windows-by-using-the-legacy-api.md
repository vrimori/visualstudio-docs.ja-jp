---
title: "レガシ API を使用してコード ウィンドウをカスタマイズします。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "エディター [Visual Studio SDK] の従来のコード ウィンドウ"
ms.assetid: 5328ab2f-55cb-4680-9744-ec79f55acd1b
caps.latest.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 19
---
# レガシ API を使用してコード ウィンドウをカスタマイズします。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

コード ウィンドウは、1 つ以上のテキスト ビューをサポートしているドキュメント ウィンドウのオブジェクトです。 コード ウィンドウの機能は、関連する言語サービスに依存します。 マルチ ドキュメント インターフェイス \(MDI\) モードでは、コード ウィンドウは、MDI 子フレームです。  
  
 コード ウィンドウが言語サービスによって制御され、各言語のサービスが、独自のコード ウィンドウ マネージャーを提供します。 これにより、波線、色付けなどのコード ウィンドウに、独自の表示要素を追加する言語サービスです。 中核となるウィンドウを作成する方法の詳細については、次を参照してください。 [レガシ API を使用してコア エディターをインスタンス化します。](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)します。  
  
 コード ウィンドウが、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> テキスト ビューとオブジェクトの表示要素を持つオブジェクト。 言語サービスがアタッチできるエディターの中核となる、インスタンス化中に、コード ウィンドウを作成するとき、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> コード ウィンドウに次の図に示すとは。  
  
 ![CodeWindow グラフィック](~/extensibility/media/vscodewindow.gif "vscodewindow")  
コード ウィンドウ  
  
 言語サービスは、コード ウィンドウ マネージャーを実装し、ドロップダウン バーなどの表示要素の管理を行います。 コード ウィンドウの呼び出し、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> メソッドのコード ウィンドウの初期化中にします。 この呼び出しが行われたときに言語サービスは、ドロップダウン バーまたはボタン バーを追加できます \(<xref:Microsoft.VisualStudio.TextManager.Interop.IVsButtonBarClient>\) コード ウィンドウにします。  
  
## このセクションの内容  
 `Customizing Code Windows by Using the Legacy API`  
 従来の API を使用してコード ウィンドウをカスタマイズする方法について説明します。  
  
 [方法: 別のエディターで、エディターのホスト](../extensibility/how-to-host-an-editor-in-another-editor.md)  
 エディター ウィンドウ内の 2 つ目のエディターをホストする方法について説明します。  
  
 [方法: エディターがフォーカスを失ったときにイベントを発生させる](../extensibility/how-to-fire-events-when-the-editor-loses-focus.md)  
 ドキュメント データ オブジェクトをドキュメント ビューを接続する方法について説明します。  
  
## 参照  
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [レガシ API を使用してコア エディターをインスタンス化します。](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)   
 [レガシ API を使用してテキスト ビューにアクセスします。](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)