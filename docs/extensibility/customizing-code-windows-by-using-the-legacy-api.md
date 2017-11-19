---
title: "レガシ API を使用してコード ウィンドウをカスタマイズする |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - code windows
ms.assetid: 5328ab2f-55cb-4680-9744-ec79f55acd1b
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4a958e6f6aa815b7d5726c2c441876331fba56b8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="customizing-code-windows-by-using-the-legacy-api"></a>レガシ API を使用してコード ウィンドウをカスタマイズします。
コード ウィンドウは、1 つまたは複数のテキスト ビューをサポートするドキュメント ウィンドウ オブジェクトです。 コード ウィンドウの正確な機能は、関連付けられた言語サービスによって異なります。 マルチ ドキュメント インターフェイス (MDI) モードでは、コード ウィンドウは、MDI 子フレームです。  
  
 コード ウィンドウが言語サービスによって制御され、各言語サービスは、独自のコード ウィンドウ マネージャーを提供できます。 これにより、コード ウィンドウで、波線、色付けなどに、独自の表示要素を追加する言語サービス。 コア ウィンドウを作成する方法の詳細については、次を参照してください。[をインスタンス化、コア エディターを使用した、レガシ API](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)です。  
  
 コード ウィンドウは、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>テキスト ビューとオブジェクトに配置された任意の修飾を持つオブジェクト。 エディターのコアのインスタンス化中に、コード ウィンドウを作成するときに、言語サービスが接続して、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>コード ウィンドウに次の図に示すとは。  
  
 ![CodeWindow グラフィック](../extensibility/media/vscodewindow.gif "vscodewindow")  
コード ウィンドウ  
  
 言語サービスは、コード ウィンドウ マネージャーを実装し、ドロップダウン バーなどの表示要素の管理を行います。 コード ウィンドウの呼び出し、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A>コード ウィンドウの初期化中にメソッドです。 ドロップダウン バーまたは含むボタン バーが言語サービスを追加できますこの呼び出しが行われたときに (<xref:Microsoft.VisualStudio.TextManager.Interop.IVsButtonBarClient>) をコード ウィンドウに保存します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 `Customizing Code Windows by Using the Legacy API`  
 従来の API を使用してコード ウィンドウをカスタマイズする方法について説明します。  
  
 [方法: 別のエディターでエディターをホストします。](../extensibility/how-to-host-an-editor-in-another-editor.md)  
 エディター ウィンドウ内の 2 つ目のエディターをホストする方法について説明します。  
  
 [方法: エディターがフォーカスを失ったときにイベントを発生させる](../extensibility/how-to-fire-events-when-the-editor-loses-focus.md)  
 ドキュメント データ オブジェクトをドキュメント ビューをアタッチする方法について説明します。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [レガシ API を使用して、コア エディターをインスタンス化します。](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)   
 [レガシ API を使用してテキスト ビューにアクセスします。](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)