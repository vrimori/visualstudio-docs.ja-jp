---
title: レガシ API を使用してテキスト ビューへのアクセス |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text view
ms.assetid: 8f751f72-c972-4be3-84ee-19c281e02e25
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bee3e781e9cb504148ae46f6a9e0b37b6ae778fb
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54979648"
---
# <a name="access-the-text-view-by-using-the-legacy-api"></a>従来の API を使用して、テキスト ビューにアクセスします。
テキスト ビューは、テキスト バッファーに格納されているテキストのプレゼンテーションです。 テキスト ビューは、次のセクションで示すように、従来の API を使用してアクセスできます。

## <a name="text-view-object"></a>テキスト ビュー オブジェクト
 各ビューは、独自のテキスト バッファーに関連付けられていると、ビューは、バッファー内のデータでウィンドウを。 次の図は、キーによって表されるテキスト ビュー オブジェクトのインターフェイスを示しています。<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>します。

 ![Visual Studio テキスト ビュー オブジェクト](../extensibility/media/vstextview.gif "vstextview")テキスト ビュー オブジェクト

 ビューは、バッファー内のテキストを表示する方法です。 ビューで確認できますが、バッファー内のテキストの正確な表現されないように、折り返し、および、アウトラインなどの機能が含まれます。

 ビューには、他のサービスや着信するコマンドをインターセプトし、ビューの動作にする前に処理を実行するプロセスが有効になります。 これを行う最も一般的なサービスは、言語サービスです。 言語サービスは、ENTER キーをカスタムのインデントの動作またはツール ヒントを提供するためのコマンドをインターセプトする必要がありますなどが。

## <a name="add-functionality-to-the-text-view"></a>テキスト ビューに機能を追加します。
 特定のキーストロークを処理することによって、テキストの表示動作をカスタマイズできます。 実装する、キーストロークをインターセプトする<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>オブジェクト、コマンド ターゲットを提供し、(<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>) モニターと切片コマンド。

 テキスト ビューでは、コマンドのフィルターをシーケンシャルなアーキテクチャを使用します。 新しいコマンド フィルター (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>オブジェクト) 呼び出しによって、シーケンスに追加された、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>メソッド。

 使用して、テキスト ビューのイベント通知が提供される、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents>インターフェイス。 テキスト ビューへの変更の通知を受け取るクライアント オブジェクトをこのインターフェイスを実装します。 使用してテキスト ビューには、このインターフェイスを公開、<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>ビューからの変更の通知を受信する、テキスト ビュー上のインターフェイス。

## <a name="see-also"></a>関連項目

- [従来の API を使用して、表示設定の変更](../extensibility/changing-view-settings-by-using-the-legacy-api.md)
- [テキスト マネージャーを使用して、グローバル設定を監視するには](../extensibility/using-the-text-manager-to-monitor-global-settings.md)