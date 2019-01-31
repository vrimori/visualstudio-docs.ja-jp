---
title: AddMessage |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5aa23265c2f0d8d006d53faf575e2ea608c071d8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55027530"
---
# <a name="addmessage"></a>AddMessage
グラフィックス診断の *HUD* (ヘッドアップ ディスプレイ) にカスタム メッセージを追加します。  
  
## <a name="syntax"></a>構文  
  
```C++  
void AddMessage(  
  wchar_t const * szMessage  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `szMessage`  
 HUD に追加するメッセージ。  
  
## <a name="remarks"></a>コメント  
 グラフィックス診断の HUD は、グラフィック診断で実行されているアプリケーションの左上隅に表示されます。 これには、アプリケーションとグラフィックス情報キャプチャのランタイム情報、およびこの関数の呼び出しによって追加されたメッセージが表示されます。  
  
 HUD にメッセージを追加するには、アクティブにグラフィックス情報をキャプチャする必要はありません。メッセージは、`VsgDbg` クラスのインスタンスを使用して追加できますが、[Init](init.md) メンバー関数は最初に呼び出されません。 メッセージは HUD に表示されるだけで、グラフィックのログ ファイルには記録されません。