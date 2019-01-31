---
title: UnInit |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 48c4e76105c024f9f414a884c2e3cabde716db86
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55019110"
---
# <a name="uninit"></a>UnInit
グラフィックス ログ ファイルを終了して閉じ、アプリケーションがアクティブにグラフィックス情報を記録したときに使用されたリソースを解放します。  
  
## <a name="syntax"></a>構文  
  
```C++  
void UnInit();  
```  
  
## <a name="remarks"></a>コメント  
 `UnInit` は、`VsgDbg` クラスのインスタンスが破棄されるときに自動的に呼び出されます。 `VsgDbg` のインスタンスがグラフィックス情報をアクティブに記録しなかった場合、この操作による影響はありません。  
  
 `UnInit` が `VsgDbg` クラスのインスタンスで呼び出された後、新しいグラフィックス ログ ファイルは `Init` を呼び出して作成でき、`UnInit` を呼び出して終了できます。 この操作を何度でも繰り返して、同じ `VsgDbg` インスタンスを使用して複数の独立したグラフィックス ログ ファイルを作成することができます。  
  
## <a name="see-also"></a>「  
 [Init](init.md)