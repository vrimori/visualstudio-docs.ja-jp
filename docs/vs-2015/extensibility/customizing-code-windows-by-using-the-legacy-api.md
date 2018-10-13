---
title: レガシ API を使用してコードの Windows をカスタマイズする |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - code windows
ms.assetid: 5328ab2f-55cb-4680-9744-ec79f55acd1b
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c698f9661866ad6d2900bb7feb0f0f4a17d21589
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49299989"
---
# <a name="customizing-code-windows-by-using-the-legacy-api"></a>レガシ API を使用してコードの Windows をカスタマイズします。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

コード ウィンドウは、1 つまたは複数のテキスト ビューをサポートしているドキュメント ウィンドウ オブジェクトです。 コード ウィンドウの正確な機能は、関連する言語サービスに依存します。 マルチ ドキュメント インターフェイス (MDI) モードでは、コード ウィンドウは、MDI 子フレームです。  
  
 コード ウィンドウは言語サービスによって制御され、各言語サービスは、独自のコード ウィンドウ マネージャーを提供できます。 これにより、波線、色付けなどのコード ウィンドウに、独自の表示要素を追加する言語サービス。 Core ウィンドウを作成する方法の詳細については、次を参照してください。[レガシ API を、コア エディターを使用してインスタンス化する](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)します。  
  
 コード ウィンドウは、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>テキスト ビューとオブジェクトの表示要素を持つオブジェクト。 言語サービスをアタッチできるエディターのコアのインスタンス化中に、コード ウィンドウを作成するときに、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>コード ウィンドウに次の図に示すとは。  
  
 ![CodeWindow グラフィック](../extensibility/media/vscodewindow.gif "vscodewindow")  
コード ウィンドウ  
  
 言語サービスは、コード ウィンドウ マネージャーを実装し、ドロップダウン バーなどの表示要素の管理を担当します。 コード ウィンドウでは、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A>メソッドのコード ウィンドウの初期化中にします。 ドロップダウン バーまたはボタン バーに、言語サービスを追加できますこの呼び出しが行われたときに (<xref:Microsoft.VisualStudio.TextManager.Interop.IVsButtonBarClient>) のコード ウィンドウにします。  
  
## <a name="in-this-section"></a>このセクションの内容  
 `Customizing Code Windows by Using the Legacy API`  
 従来の API を使用してコード ウィンドウをカスタマイズする方法について説明します。  
  
 [方法: エディターを別のエディターでホストする](../extensibility/how-to-host-an-editor-in-another-editor.md)  
 エディター ウィンドウ内の 2 つ目のエディターをホストする方法について説明します。  
  
 [方法: エディターでフォーカスが失われたときにイベントを発生させる](../extensibility/how-to-fire-events-when-the-editor-loses-focus.md)  
 ドキュメント データ オブジェクトをドキュメント ビューを接続する方法について説明します。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [レガシ API を使用して、コア エディターをインスタンス化します。](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)   
 [レガシ API を使用するテキスト ビューへのアクセス](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)

