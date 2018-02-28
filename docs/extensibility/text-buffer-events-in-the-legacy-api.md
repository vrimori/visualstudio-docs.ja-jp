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
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 7e7847cdca2065cadd6adaf0d4b3e6ea10444725
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="text-buffer-events-in-the-legacy-api"></a>レガシ API でのテキスト バッファー イベント
テキスト バッファー オブジェクトは、さまざまな状況に対応できるようにするいくつかのイベントを出力します。  
  
 従来の API を使用しているときに、テキスト バッファーへの変更通知を受信するために、次のインターフェイスを実装する必要があります。 テキスト バッファーを使用するインターフェイスを公開、`IConnectionPointContainer`バッファーから行の通知を受け取るテキスト バッファーのインターフェイスを変更します。 詳細については、次を参照してください。[する方法: テキスト バッファー イベント、レガシ API の登録](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)です。 場合、`IVsTextStreamEvents`または`IVsTextLinesEvents`インターフェイス、変更が返されるいずれか 1 つまたは 2 次元座標で、それぞれします。  
  
## <a name="text-buffer-interfaces"></a>テキスト バッファー インターフェイス  
 テキスト バッファー オブジェクトによって実装されるインターフェイスを次に示します。  
  
|Interface|説明|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|複合アクション (つまり、元に戻す/やり直しの 1 つの単位にグループ化されているアクション) を作成できます。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|テキスト バッファーによって管理されているドキュメント データの永続化を有効にします。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|基本的なサービスを提供します。多くのクライアントによって使用されます。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|読み取りし、書き込みの 2 次元座標を使用して機能します。 `IVsTextBuffer` から継承します。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|高速、バッファー内のテキストへのストリーム指向で連続的なアクセスを提供します。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|読み取りし、書き込みの 1 次元座標を使用して機能します。 `IVsTextBuffer` から継承します。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|プロパティのジェネリック コレクションへのアクセスを提供します。 最も重要なプロパティは、名前、またはバッファーのモニカーです。 このインターフェイスでバッファーのランダムなデータを格納するには GUID を作成して、キーとして使用します。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|イベントのコネクション ポイントをサポートします。|  
  
## <a name="text-buffer-event-interfaces"></a>テキスト バッファー イベント インターフェイス  
 テキスト バッファーのイベント通知用のインターフェイスを次に示します。  
  
|Interface|説明|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferEvents>|新しい言語サービスはテキスト バッファーを関連付けた場合は、クライアントを通知します。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferDataEvents>|テキスト バッファーを初期化する場合、およびテキスト バッファー内のデータを変更するときは、クライアントを通知します。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamEvents>|1 次元の座標で基になるテキスト バッファーへの変更のクライアントに通知します。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>|2 次元座標で基になるテキスト バッファーへの変更のクライアントに通知します。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserDataEvents>|ユーザー データへの変更のクライアントに通知します。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>|イベントをトリガーする最後のコミット ジェスチャのクライアントに通知し、変更されたテキストの範囲を提供します。 `IVsPreliminaryTextChangeCommitEvents`インターフェイスは、元に戻すまたはやり直すコマンドへの応答は発生しません。 イベントは、undo マネージャーのバッファーにのみ発生します。 `IVsPreliminaryTextChangeCommitEvents`変更をコミットする前に他のイベントが、テキストを変更しないことを確認するために再フォーマットの一覧についてなどの他のイベントの前に発生します。 VSPackage は、いずれかを監視する必要があります、`IVsPreliminaryTextChangeCommitEvents`インターフェイスまたは`IVsFinalTextChangeCommitEvents`が、両方は使用できません。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>|イベントをトリガーする最後のコミット ジェスチャのクライアントに通知し、変更されたテキストの範囲を提供します。 `IVsFinalTextChangeCommitEvents`インターフェイスは、元に戻すまたはやり直すコマンドへの応答は発生しません。 イベントは、undo マネージャーのバッファーにのみ発生します。 `IVsFinalTextChangeCommitEvents`向け言語サービスまたは編集を完全に制御があるその他のオブジェクトによってのみです。 VSPackage は、いずれかを監視する必要があります、`IVsPreliminaryTextChangeCommitEvents`インターフェイスまたは`IVsFinalTextChangeCommitEvents`が、両方は使用できません。|  
  
## <a name="see-also"></a>参照  
 [レガシ API を使用してテキスト バッファーにアクセスします。](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)   
 [方法: テキスト バッファー イベント、レガシ API の登録](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)