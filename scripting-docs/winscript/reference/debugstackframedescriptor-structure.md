---
title: "DebugStackFrameDescriptor 構造体 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- DebugStackFrameDescriptor
apilocation:
- scrobj.dll
helpviewer_keywords:
- DebugStackFrameDescriptor structure
ms.assetid: a86bcb99-41e4-4a26-a1dd-e1458fb73139
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 346f039ca96f2160d7ac28686e542b3d88a91dfb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="debugstackframedescriptor-structure"></a>DebugStackFrameDescriptor 構造体
スタック フレームを列挙し、同じスレッドの複数の列挙型からの出力をマージします。  
  
## <a name="syntax"></a>構文  
  
```  
typedef struct tagDebugStackFrameDescriptor {  
   IDebugStackFrame *pdsf;  
   DWORD_PTR        dwMin;  
   DWORD_PTR        dwLim;  
   BOOL             fFinal;  
   IUnknown         *punkFinal;  
} DebugStackFrameDescriptor;  
```  
  
## <a name="members"></a>メンバー  
 `pdsf`  
 スタック フレーム オブジェクト。  
  
 `dwMin`  
 このスタック フレームに関連付けられている物理アドレスの範囲のコンピューターに依存する表現。  
  
 `dwLim`  
 このスタック フレームに関連付けられている物理アドレスの上限までのコンピューターに依存する表現。  
  
 `fFinal`  
 フレームが処理されていることを示すフラグです。  
  
 `punkFinal`  
 このパラメーターがない場合`NULL`、マージの現在の列挙子を停止して、新しいスレッドを開始する必要があります。 オブジェクトは、新しい列挙を開始する方法を示します。  
  
## <a name="remarks"></a>コメント  
 プロセスのデバッグ マネージャーでは、この構造体を使用して複数のスクリプト エンジンからのスタック フレームを並べ替えます。 規則では、スタックはダウンを拡大されます。 その結果、アーキテクチャでは、スタックは成長のアドレスは組補完をする必要があります。  
  
## <a name="see-also"></a>関連項目  
 [アクティブ スクリプト デバッガーの定数、列挙型、および構造体](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)