---
title: AddMessage |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a81dda4564d87fe33d9d8e9c497e4aa040b8830e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47534399"
---
# <a name="addmessage"></a>AddMessage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[AddMessage](https://docs.microsoft.com/visualstudio/debugger/graphics/addmessage)します。  
  
グラフィックス診断にカスタム メッセージを追加*HUD* (ヘッドアップ ディスプレイ)。  
  
## <a name="syntax"></a>構文  
  
```cpp  
void AddMessage(  
  wchar_t const * szMessage  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `szMessage`  
 HUD に追加するメッセージ。  
  
## <a name="remarks"></a>Remarks  
 グラフィックス診断の HUD は、グラフィック診断で実行されているアプリケーションの左上隅に表示されます。 これには、アプリケーションとグラフィックス情報キャプチャのランタイム情報、およびこの関数の呼び出しによって追加されたメッセージが表示されます。  
  
 HUD には、メッセージを追加するには、アクティブにグラフィックス情報をキャプチャする必要はありません — メッセージを追加してのインスタンスでは、`VsgDbg`クラスが、 [Init](../debugger/init.md)メンバー関数は、最初に呼び出すには。 メッセージは HUD に表示されるだけで、グラフィックのログ ファイルには記録されません。



