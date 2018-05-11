---
title: IDebugModule2::GetInfo |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugModule2::GetInfo
helpviewer_keywords:
- GetInfo method
- IDebugModule2::GetInfo method
ms.assetid: de337e66-294f-4ac9-b21e-71fac7418e36
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8eb4f06899b7b3bc30453282463c9402e45c2aee
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idebugmodule2getinfo"></a>IDebugModule2::GetInfo
このモジュールに関する情報を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetInfo(   
   MODULE_INFO_FIELDS dwFields,  
   MODULE_INFO*       pInfo  
);  
```  
  
```cpp  
int GetInfo(   
   enum_MODULE_INFO_FIELDS dwFields,  
   MODULE_INFO[]           pInfo  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwFields`  
 [in]フラグの組み合わせ、 [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)のどのフィールドを指定する列挙体`pInfo`に記入することはできます。  
  
 `pInfo`  
 [入力、出力].A [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)モジュールの説明が入力構造です。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)構造で表示されているモジュールの名前に含まれる、**モジュール**ウィンドウです。  
  
## <a name="see-also"></a>関連項目  
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)