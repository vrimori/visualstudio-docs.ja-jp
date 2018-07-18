---
title: Ijsdebugprocess::createbreakpoint メソッド |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugProcess.CreateBreakPoint
apilocation:
- jscript9diag.dll
ms.assetid: a2cb4233-2846-4d11-aa13-21de43abda9f
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 10d734f32d092d341dbb1b02a5cc7a0c127223a4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24728122"
---
# <a name="ijsdebugprocesscreatebreakpoint-method"></a>IJsDebugProcess::CreateBreakPoint メソッド
指定されたドキュメントの位置にブレークポイントを設定します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CreateBreakPoint(  
   UINT64 documentId,  
   DWORD characterOffset,  
   DWORD characterCount,  
   BOOL isEnabled,  
   IJsDebugBreakPoint **ppDebugBreakPoint  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `documentId`  
 [入力] IDebugDocumentText へのポインター。  
  
 `characterOffset`  
 [入力] ファイルの先頭からの文字オフセット。  
  
 `characterCount`  
 [入力] ブレークポイントを挿入するドキュメント テキストの長さ。  
  
 `isEnabled`  
 [入力] ブレークポイントが有効かどうかを指定します。  
  
 `ppDebugBreakPoint`  
 [出力] 作成されたブレークポイントを表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** jscript9diag.h です  
  
## <a name="see-also"></a>関連項目  
 [IJsDebugProcess インターフェイス](../../winscript/reference/ijsdebugprocess-interface.md)