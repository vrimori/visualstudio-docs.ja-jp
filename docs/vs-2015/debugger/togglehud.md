---
title: ToggleHUD |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
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
ms.openlocfilehash: 62d202bfca33619c14d00ec99dc44857cb01bb6a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49250448"
---
# <a name="togglehud"></a>ToggleHUD
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

グラフィックス診断を切り替えます*HUD* (ヘッドアップ ディスプレイ) オーバーレイのオン/オフします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
void ToggleHUD();  
```  
  
## <a name="remarks"></a>Remarks  
 グラフィックス診断の HUD は、グラフィック診断で実行されているアプリケーションの左上隅に表示されます。 実行時情報、アプリケーションとグラフィックス情報のキャプチャ、および呼び出しによって追加されたメッセージが表示されます、 [AddMessage](../debugger/addmessage.md)メンバー関数。  
  
 HUD を切り替えるには、アクティブにグラフィックス情報をキャプチャする必要はありません — のインスタンスからの切り替えは、`VsgDbg`クラスが、 [Init](../debugger/init.md)メンバー関数は最初に呼び出す必要はありません。



