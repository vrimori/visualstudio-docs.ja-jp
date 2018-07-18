---
title: ToggleHUD |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 86ce582ab49d4d079f01f7231f49aa761baa1069
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
ms.locfileid: "31472514"
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