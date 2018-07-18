---
title: Idiaframedata::execute |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::execute method
ms.assetid: 7a6c7d03-1ff1-4059-bd54-5f407eeebc26
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0645d2364712769a6b4f18ef14fbbcb503a51888
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
ms.locfileid: "31459511"
---
# <a name="idiaframedataexecute"></a>IDiaFrameData::execute
スタック アンワインドを実行し、スタック ウォーク フレーム インターフェイスで結果を返します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT execute (   
   IDiaStackWalkFrame* frame  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `frame`  
 [in][IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)フレーム レジスタの状態を保持するオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。 次の表は、このメソッドの戻り値を示します。  
  
|[値]|説明|  
|-----------|-----------------|  
|E_DIA_INPROLOG|プロローグ コードの中にスタック フレームを実行できません。|  
|E_DIA_SYNTAX|フレームのプログラムで発生したエラーを解析します。|  
|E_DIA_FRAME_ACCESS|アクセスのレジスタまたはメモリにできません。|  
|E_DIA_VALUE|値 (たとえば、0 による除算) の計算のエラーです。|  
  
## <a name="remarks"></a>コメント  
 このメソッドは、スタックをアンワインドするデバッグ中に呼び出されます。 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)オブジェクトは、レジスタに更新プログラムを受信しで使用されるメソッドを提供するクライアント アプリケーションによって実装される、`execute`メソッドです。  
  
## <a name="see-also"></a>関連項目  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)