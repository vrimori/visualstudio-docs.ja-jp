---
title: Idiaframedata::execute |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::execute method
ms.assetid: 7a6c7d03-1ff1-4059-bd54-5f407eeebc26
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 933b05bbd9e0ff93a9e132578a72fb44db8be945
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49859724"
---
# <a name="idiaframedataexecute"></a>IDiaFrameData::execute
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

スタック アンワインドを実行し、スタック ウォーク フレーム インターフェイスで結果を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT execute (   
   IDiaStackWalkFrame* frame  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `frame`  
 [in][IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)フレーム レジスタの状態を保持するオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。 次の表では、このメソッドの戻り値を示します。  
  
|[値]|説明|  
|-----------|-----------------|  
|E_DIA_INPROLOG|プロローグ コードの中にスタック フレームを実行することはできません。|  
|E_DIA_SYNTAX|フレームのプログラムで発生したエラーを解析します。|  
|E_DIA_FRAME_ACCESS|アクセスのレジスタまたはメモリをできません。|  
|E_DIA_VALUE|(たとえば、0 による除算)、値の計算のエラーです。|  
  
## <a name="remarks"></a>Remarks  
 このメソッドは、スタックをアンワインドするデバッグ中に呼び出されます。 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)オブジェクトがレジスタに更新プログラムを受信しで使用されるメソッドを提供するクライアント アプリケーションによって実装される、`execute`メソッド。  
  
## <a name="see-also"></a>関連項目  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)



