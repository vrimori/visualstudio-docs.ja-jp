---
title: "AddMessage |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b0050f5022b31020879b45e45da48546e5a7caa
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="addmessage"></a>AddMessage
グラフィックス診断にカスタム メッセージを追加*HUD* (ヘッドアップ ディスプレイ)。  
  
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
  
 HUD にメッセージを追加するにグラフィックス情報がキャプチャされてアクティブにする必要はありません: つまり、メッセージを追加するのインスタンス、`VsgDbg`クラス、ですが、 [Init](init.md)メンバー関数は、最初に呼び出すには。 メッセージは HUD に表示されるだけで、グラフィックのログ ファイルには記録されません。