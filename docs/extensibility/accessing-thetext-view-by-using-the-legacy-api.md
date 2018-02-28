---
title: "レガシ API を使用してテキスト ビューにアクセスする |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text view
ms.assetid: 8f751f72-c972-4be3-84ee-19c281e02e25
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: bea908ee04913c5ec56678f1438229e045bf68c7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="accessing-thetext-view-by-using-the-legacy-api"></a>レガシ API を使用してテキスト ビューにアクセスします。
テキスト ビューは、テキスト バッファーに格納されているテキストのプレゼンテーションです。 テキスト ビューは、次のセクションで示すようにレガシ API を使用してアクセスできます。  
  
## <a name="text-view-object"></a>テキスト ビュー オブジェクト  
 各ビューは独自のテキスト バッファーに関連付けられ、ビューは、バッファー内のデータでのウィンドウ。 次の図は、キーによって表されるテキスト ビュー オブジェクト インターフェイスを示しています。<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>です。  
  
 ![Visual Studio テキスト ビュー オブジェクト](../extensibility/media/vstextview.gif "vstextview")  
テキスト ビュー オブジェクト  
  
 ビューは、バッファー内のテキストを表示する方法です。 ビューで表示される内容が、バッファー内のテキストの形式とまったく同じにならないように、折り返し、および、アウトライン表示などの機能が含まれます。  
  
 ビューには、他のサービスまたは着信コマンドを途中受信して、ビューを処理する前に操作するプロセスが有効になります。 これを行う最も一般的なサービスは、言語サービスです。 言語サービスは、ENTER キーをカスタムのインデントの動作またはツール ヒントを提供するためのコマンドをインターセプトする必要がありますなどが。  
  
## <a name="adding-functionality-to-the-text-view"></a>テキスト ビューへの機能の追加  
 特定のキー入力を処理することによって、テキストの表示動作をカスタマイズできます。 実装するキーストロークを傍受する<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>、オブジェクトのコマンド ターゲットを指定し、(<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>) モニターと切片コマンドにします。  
  
 テキスト ビューでは、シーケンシャルなアーキテクチャを使用して、コマンドのフィルターをします。 新しいコマンド フィルタ (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>オブジェクト) を呼び出して、シーケンスに追加されます、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>メソッドです。  
  
 使用して、テキスト ビューに関するイベント通知が提供される、`T:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents`インターフェイスです。 テキスト ビューへの変更通知を受信するクライアント オブジェクトには、このインターフェイスを実装します。 使用してテキスト ビューには、このインターフェイスを公開、<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>ビューからの変更通知を受信するテキスト ビュー上のインターフェイスです。  
  
## <a name="see-also"></a>参照  
 [レガシ API を使用してビューの設定を変更します。](../extensibility/changing-view-settings-by-using-the-legacy-api.md)   
 [テキスト マネージャーを使用して、グローバル設定を監視するには](../extensibility/using-the-text-manager-to-monitor-global-settings.md)