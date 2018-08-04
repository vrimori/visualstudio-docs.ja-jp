---
title: レガシ API を使用してコードの Windows をカスタマイズする |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - code windows
ms.assetid: 5328ab2f-55cb-4680-9744-ec79f55acd1b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 454d58a48abafe9b23f8a812e5d40b9fc6477b50
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2018
ms.locfileid: "39499355"
---
# <a name="customize-code-windows-by-using-the-legacy-api"></a>従来の API を使用してコード ウィンドウをカスタマイズします。
コード ウィンドウは、1 つまたは複数のテキスト ビューをサポートしているドキュメント ウィンドウ オブジェクトです。 コード ウィンドウの正確な機能は、関連する言語サービスに依存します。 マルチ ドキュメント インターフェイス (MDI) モードでは、コード ウィンドウは、MDI 子フレームです。  
  
 コード ウィンドウは言語サービスによって制御され、各言語サービスは、独自のコード ウィンドウ マネージャーを提供できます。 これにより、波線、色付けなどのコード ウィンドウに、独自の表示要素を追加する言語サービス。 Core ウィンドウを作成する方法の詳細については、次を参照してください。[従来の API を使用して、コア エディターをインスタンス化](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)します。  
  
 コード ウィンドウは、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>テキスト ビューとオブジェクトの表示要素を持つオブジェクト。 言語サービスをアタッチできるエディターのコアのインスタンス化中に、コード ウィンドウを作成するときに、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>コード ウィンドウに次の図に示すとは。  
  
 ![CodeWindow グラフィック](../extensibility/media/vscodewindow.gif "vscodewindow")  
コード ウィンドウ  
  
 言語サービスは、コード ウィンドウ マネージャーを実装し、ドロップダウン バーなどの表示要素の管理を担当します。 コード ウィンドウでは、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A>メソッドのコード ウィンドウの初期化中にします。 ドロップダウン バーまたはボタン バーに、言語サービスを追加できますこの呼び出しが行われたときに (<xref:Microsoft.VisualStudio.TextManager.Interop.IVsButtonBarClient>) のコード ウィンドウにします。  
  
## <a name="in-this-section"></a>このセクションの内容  
 `Customizing Code Windows by Using the Legacy API`  
 従来の API を使用してコード ウィンドウをカスタマイズする方法について説明します。  
  
 [方法: 別のエディターで、エディターのホスト](../extensibility/how-to-host-an-editor-in-another-editor.md)  
 エディター ウィンドウ内の 2 つ目のエディターをホストする方法について説明します。  
  
 [方法: エディターがフォーカスを失ったときにイベントを発生させる](../extensibility/how-to-fire-events-when-the-editor-loses-focus.md)  
 ドキュメント データ オブジェクトをドキュメント ビューを接続する方法について説明します。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [従来の API を使用して、コア エディターをインスタンス化します。](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)   
 [従来の API を使用してアクセス テキスト ビュー](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)