---
title: "IActiveScript::Close |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScript.Close
apilocation: scrobj.dll
helpviewer_keywords: IActiveScript_Close
ms.assetid: cc7dd63b-1d7e-410a-857b-09ea3aade275
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7c90b5d089ea6665060944e0a6f720a43aa1295a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptclose"></a>IActiveScript::Close
現在読み込まれているスクリプトの破棄の状態が失われるおよびその他のオブジェクトは、したがって closed の状態を入力する必要があるインターフェイス ポインターを解放するには、スクリプト エンジンが発生します。 イベント シンク、すぐに実行されたスクリプトのテキスト、およびが既に実行中のマクロの呼び出しが完了した後、状態の変更 (を使用して[IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)スクリプトの実行中のスレッドをキャンセルする)。 このメソッドは、循環参照の問題を防ぐために、インターフェイスが解放される前に、作成元のホストによって呼び出さ必要があります。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT Close(void);  
```  
  
## <a name="return-value"></a>戻り値  
 次のいずれかの値を返します。  
  
|値|説明|  
|-----------|-------------|  
|`S_OK`|成功。|  
|`E_UNEXPECTED`|呼び出しが予期されていませんでした (たとえば、スクリプト エンジンが既に閉じられた状態で)。|  
|`OLESCRIPT_S_PENDING`|メソッドが正常にキューに登録が状態がまだ変更されていません。 状態の変化、サイトがの場合にコールバックする、 [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)メソッドです。|  
|`S_FALSE`|メソッドが成功しましたが、スクリプトは既に閉じられています。|  
  
## <a name="see-also"></a>関連項目  
 [IActiveScript](../../winscript/reference/iactivescript.md)