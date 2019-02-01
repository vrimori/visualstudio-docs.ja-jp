---
title: ToggleHUD |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e49066d4625990119159ea72f59a3a3fe59d581c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54953303"
---
# <a name="togglehud"></a>ToggleHUD
グラフィックス診断の *HUD* (ヘッドアップ ディスプレイ) オーバーレイのオンとオフを切り替えます。  
  
## <a name="syntax"></a>構文  
  
```C++  
void ToggleHUD();  
```  
  
## <a name="remarks"></a>コメント  
 グラフィックス診断の HUD は、グラフィック診断で実行されているアプリケーションの左上隅に表示されます。 実行時情報、アプリケーションとグラフィックス情報のキャプチャ、および呼び出しによって追加されたメッセージが表示されます、 [AddMessage](addmessage.md)メンバー関数。  
  
 HUD を切り替えるには、アクティブにグラフィックス情報をキャプチャする必要はありません。これは、`VsgDbg` クラスのインスタンスを通じて切り替えられますが、[Init](init.md) メンバー関数は最初に呼び出される必要はありません。