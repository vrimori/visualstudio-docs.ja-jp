---
title: コードのメッセージ |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- message codes
ms.assetid: 9f91f4e2-c1f1-4349-9f11-2fbbf59654be
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0464042c17a3ed0836b99183dacbe4918823c752
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51724634"
---
# <a name="message-codes"></a>メッセージ コード
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

表示される各メッセージ行[メッセージ ビュー](../debugger/messages-view.md) 'P' を含むの 'の' または 'R' コード。 これらのコードでは、次の意味があります。  
  
|コード|説明|  
|----------|-------------|  
|P|メッセージがキューにポストされた、 **PostMessage**関数。 情報のメッセージの最終的な廃棄に関連はありません。|  
|S|メッセージが送信された、 **SendMessage**関数。 これは、送信者は、受信側の処理し、メッセージを返すまでは制御を回復しないことを意味します。 受信側は、センダーに送り返す戻り値を返すため、ことができます。|  
|s|メッセージが送信されましたが、セキュリティでは、戻り値にアクセスができなくなります。|  
|R|それぞれの ' の行が 'R' (戻り値) の対応する行をメッセージの戻り値の一覧を表示します。 場合によってメッセージ呼び出しは入れ子に、その 1 つのメッセージ ハンドラーは、別のメッセージを送信することを意味します。|



