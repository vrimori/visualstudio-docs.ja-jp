---
title: AddMessage |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 28f9150c55c7475a9412ee440cd8ae5215ca25cb
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51788954"
---
# <a name="addmessage"></a>AddMessage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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



