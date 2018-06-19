---
title: AddMessage |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: de3460a345dba21e3a8f481adb510b9e3bdd4990
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
ms.locfileid: "31473349"
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