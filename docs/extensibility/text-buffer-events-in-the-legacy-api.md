---
title: "レガシ API でのテキスト バッファー イベント |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text buffer events
ms.assetid: 9be49e9f-1864-41c2-8a3c-f66895881341
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 39ac6a711278950d09ed16b157fc89980144e3d0
ms.lasthandoff: 02/22/2017

---
# <a name="text-buffer-events-in-the-legacy-api"></a>レガシ API でのテキスト バッファー イベント
テキスト バッファー オブジェクトは、さまざまな状況に対応するためのいくつかの異なるイベントを送出します。  
  
 従来の API を使用しているときに、テキスト バッファーへの変更の通知を受信するために、次のインターフェイスを実装する必要があります。 テキスト バッファーを使用するインターフェイスを公開、`IConnectionPointContainer`バッファーから行の通知を受け取るテキスト バッファーのインターフェイスを変更します。 詳細については、次を参照してください。[方法: レガシ API でのテキスト バッファーのイベント登録](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)します。 場合に`IVsTextStreamEvents`または`IVsTextLinesEvents`インターフェイス、変更内容が返されるいずれか&1; つまたは&2; 次元座標で、それぞれします。  
  
## <a name="text-buffer-interfaces"></a>テキスト バッファー インターフェイス  
 テキスト バッファー オブジェクトによって実装されるインターフェイスを次に示します。  
  
|インターフェイス|説明|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction></xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|複合操作 (つまり、元に戻す/やり直しの&1; つの単位にグループ化されているアクション) を作成できます。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData></xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|テキスト バッファーによって管理されるドキュメント データの永続化を有効にします。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|基本的なサービスを提供します。多くのクライアントによって使用されます。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|読み取りし、書き込みの&2; 次元座標を使用して機能します。 `IVsTextBuffer` から継承します。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|高速でストリーム指向シーケンシャルへのアクセス、バッファー内のテキストを提供します。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|読み取りし、書き込みの&1; 次元の座標を使用して機能します。 `IVsTextBuffer` から継承します。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData></xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|プロパティのジェネリック コレクションへのアクセスを提供します。 最も重要なプロパティは、名前、またはバッファーのモニカーです。 このインターフェイスでバッファーの独自のランダムなデータを格納するには、GUID を作成して、キーとして使用します。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer></xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|イベントのコネクション ポイントをサポートします。|  
  
## <a name="text-buffer-event-interfaces"></a>テキスト バッファー イベント インターフェイス  
 テキスト バッファーのイベント通知用のインターフェイスを次に示します。  
  
|インターフェイス|説明|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferEvents></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferEvents>|新しい言語サービスがテキスト バッファーと関連付けられている場合は、クライアントを通知します。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferDataEvents></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferDataEvents>|テキスト バッファーを初期化し、テキスト バッファー内のデータに変更が加えられたときに、クライアントを通知します。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamEvents></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamEvents>|1 次元の座標で基になるテキスト バッファーへの変更をクライアントに通知します。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>|2 次元座標で基になるテキスト バッファーへの変更をクライアントに通知します。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserDataEvents></xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserDataEvents>|ユーザー データへの変更をクライアントに通知します。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents></xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>|イベントをトリガーする最後のコミット ジェスチャのクライアントに通知し、変更されたテキストの範囲を提供します。 `IVsPreliminaryTextChangeCommitEvents`インターフェイスは、取り消しまたはやり直しコマンドへの応答では発生しません。 イベントは、元に戻すマネージャーのバッファーに対してのみ発生します。 `IVsPreliminaryTextChangeCommitEvents`変更をコミットする前に、その他のイベントが、テキストを変更しないことを確認するために、再などその他のイベントの前に発生します。 VSPackage がいずれかを監視する必要があります、`IVsPreliminaryTextChangeCommitEvents`インターフェイスまたは`IVsFinalTextChangeCommitEvents`が、どちらかです。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents></xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>|イベントをトリガーする最後のコミット ジェスチャのクライアントに通知し、変更されたテキストの範囲を提供します。 `IVsFinalTextChangeCommitEvents`インターフェイスは、取り消しまたはやり直しコマンドへの応答では発生しません。 イベントは、元に戻すマネージャーのバッファーに対してのみ発生します。 `IVsFinalTextChangeCommitEvents`使用するため、言語サービスまたは編集を完全に制御があるその他のオブジェクトだけです。 VSPackage がいずれかを監視する必要があります、`IVsPreliminaryTextChangeCommitEvents`インターフェイスまたは`IVsFinalTextChangeCommitEvents`が、どちらかです。|  
  
## <a name="see-also"></a>関連項目  
 [レガシ API を使用してテキスト バッファーにアクセスします。](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)   
 [方法: テキスト バッファーのイベント、レガシ API の登録](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)
