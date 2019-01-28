---
title: レガシ API でのテキスト バッファー イベント |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text buffer events
ms.assetid: 9be49e9f-1864-41c2-8a3c-f66895881341
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cfa7c6852db66635b0a2b9d955a090b98dd1b61e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55041569"
---
# <a name="text-buffer-events-in-the-legacy-api"></a>従来の API でのテキスト バッファー イベント
テキスト バッファー オブジェクトは、さまざまな状況に対応するためのいくつかのイベントを出力します。  
  
 従来の API を使用しているときに、テキスト バッファーへの変更の通知を受信するには、次のインターフェイスを実装する必要があります。 テキスト バッファーを使用するインターフェイスを公開、`IConnectionPointContainer`バッファーから行の通知を受け取るテキスト バッファーのインターフェイスを変更します。 詳細については、「[方法 :従来の API を使用したテキスト バッファー イベント登録](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)します。 場合に`IVsTextStreamEvents`または`IVsTextLinesEvents`インターフェイス、変更が返されるいずれか 1 つまたは 2 次元座標で、それぞれします。  
  
## <a name="text-buffer-interfaces"></a>テキスト バッファー インターフェイス  
 テキスト バッファー オブジェクトによって実装されるインターフェイスを次に示します。  
  
|Interface|説明|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|複合アクション (元に戻す/やり直しの 1 つの単位にグループ化アクション) を作成できます。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|テキスト バッファーによって管理されるドキュメントのデータの永続化を有効にします。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|基本的なサービスを提供します。多くのクライアントによって使用されます。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|読み取りし、書き込みの 2 次元座標を使用して機能します。 `IVsTextBuffer`から継承します。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|高速で、バッファー内のテキストをストリーム指向、シーケンシャル アクセスを提供します。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|読み取りし、書き込みの 1 次元の座標を使用して機能します。 `IVsTextBuffer`から継承します。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|プロパティのジェネリック コレクションへのアクセスを提供します。 最も重要なプロパティは、名前、またはバッファーのモニカーです。 GUID の作成、キーとして使用して、このインターフェイスでバッファーのランダム データを格納できます。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|イベントのコネクション ポイントをサポートしています。|  
  
## <a name="text-buffer-event-interfaces"></a>テキスト バッファー イベント インターフェイス  
 テキスト バッファーのイベント通知用のインターフェイスを次に示します。  
  
|Interface|説明|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferEvents>|新しい言語サービスがテキスト バッファーに関連付けられている場合、クライアントに通知します。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferDataEvents>|テキスト バッファーを初期化し、テキスト バッファー内のデータに変更されたときに、クライアントに通知します。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamEvents>|1 次元の座標で基になるテキスト バッファーへの変更をクライアントに通知します。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>|2 次元座標で基になるテキスト バッファーへの変更をクライアントに通知します。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserDataEvents>|ユーザー データへの変更をクライアントに通知します。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>|イベントをトリガーする最後のコミットのジェスチャのクライアントに通知し、変更されたテキストの範囲を提供します。 `IVsPreliminaryTextChangeCommitEvents`インターフェイスは、取り消しまたはやり直しコマンドの応答では発生しません。 イベントは、元に戻すマネージャーのバッファーにのみ発生します。 `IVsPreliminaryTextChangeCommitEvents` 変更をコミットする前に、その他のイベントが、テキストを変更しないことを確認するためにかなりの一覧などの他のイベントの前に発生します。 VSPackage は、いずれかを監視する必要があります、`IVsPreliminaryTextChangeCommitEvents`インターフェイスまたは`IVsFinalTextChangeCommitEvents`両方ではなくインターフェイスです。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>|イベントをトリガーする最後のコミットのジェスチャのクライアントに通知し、変更されたテキストの範囲を提供します。 `IVsFinalTextChangeCommitEvents`インターフェイスは、取り消しまたはやり直しコマンドの応答では発生しません。 イベントは、元に戻すマネージャーのバッファーにのみ発生します。 `IVsFinalTextChangeCommitEvents` 言語サービスまたは編集を完全に制御する他のオブジェクトによってのみの使用は想定されてです。 VSPackage は、いずれかを監視する必要があります、`IVsPreliminaryTextChangeCommitEvents`インターフェイスまたは`IVsFinalTextChangeCommitEvents`両方ではなくインターフェイスです。|  
  
## <a name="see-also"></a>関連項目

- [従来の API を使用してテキスト バッファーへのアクセスします。](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)
- [方法: 従来の API を使用したイベントのテキスト バッファーの登録します。](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)