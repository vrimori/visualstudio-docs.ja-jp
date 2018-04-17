---
title: ToggleHUD |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8839e41048a68adf09380e6fa428087299a12801
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
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