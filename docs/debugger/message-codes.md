---
title: コードのメッセージ |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- message codes
ms.assetid: 9f91f4e2-c1f1-4349-9f11-2fbbf59654be
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 96f980570bcbee7a26bf742556379899c0a88436
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="message-codes"></a>メッセージ コード
各メッセージに表示される行[メッセージ ビュー](../debugger/messages-view.md) 'P' を含むの 'の' または 'R' コード。 これらのコードでは、次の意味があります。  
  
|コード|説明|  
|----------|-------------|  
|P|メッセージがキューにポストされた、 **PostMessage**関数。 情報は、メッセージの最終的な廃棄に関連はありません。|  
|S|メッセージが送信された、 **SendMessage**関数。 これは、送信者は受信者が処理され、メッセージが返されますまでは制御を取り戻すしないことを意味します。 受信側では、送信者に送り返す戻り値を返すことができます、そのため、します。|  
|s|メッセージが送信されましたが、セキュリティでは、戻り値にアクセスができなくなります。|  
|R|それぞれの ' 行には対応する 'R' (return) 行がメッセージの戻り値を一覧表示されます。 場合によってメッセージ呼び出しが入れ子にその 1 つのメッセージ ハンドラーは、別のメッセージを送信することを意味します。|