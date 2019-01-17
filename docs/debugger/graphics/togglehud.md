---
title: ToggleHUD |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a4ee371f90636d98d5dd771cc508e58cd1d1a394
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53907976"
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