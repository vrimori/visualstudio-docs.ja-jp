---
title: ToggleHUD |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b224fdbd4dfadc6af29a0491bba5a18089c260b4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47536329"
---
# <a name="togglehud"></a>ToggleHUD
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ToggleHUD](https://docs.microsoft.com/visualstudio/debugger/graphics/togglehud)します。  
  
グラフィックス診断を切り替えます*HUD* (ヘッドアップ ディスプレイ) オーバーレイのオン/オフします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
void ToggleHUD();  
```  
  
## <a name="remarks"></a>Remarks  
 グラフィックス診断の HUD は、グラフィック診断で実行されているアプリケーションの左上隅に表示されます。 実行時情報、アプリケーションとグラフィックス情報のキャプチャ、および呼び出しによって追加されたメッセージが表示されます、 [AddMessage](../debugger/addmessage.md)メンバー関数。  
  
 HUD を切り替えるには、アクティブにグラフィックス情報をキャプチャする必要はありません — のインスタンスからの切り替えは、`VsgDbg`クラスが、 [Init](../debugger/init.md)メンバー関数は最初に呼び出す必要はありません。



