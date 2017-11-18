---
title: "ToggleHUD |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5bf1e27b9385257203653f3bff5241f6c3875373
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="togglehud"></a>ToggleHUD
グラフィックス診断を切り替えます*HUD* (ヘッドアップ ディスプレイ) オーバーレイのオンとオフします。  
  
## <a name="syntax"></a>構文  
  
```C++  
void ToggleHUD();  
```  
  
## <a name="remarks"></a>コメント  
 グラフィックス診断の HUD は、グラフィック診断で実行されているアプリケーションの左上隅に表示されます。 アプリについて、グラフィックス情報のキャプチャ、および呼び出しによって追加されたメッセージに関するランタイム情報が表示されます、 [AddMessage](addmessage.md)メンバー関数。  
  
 HUD を切り替えるにグラフィックス情報がキャプチャされてアクティブにする必要はありません-のインスタンスからの切り替えは、`VsgDbg`クラス、ですが、 [Init](init.md)メンバー関数は最初に呼び出す必要はありません。