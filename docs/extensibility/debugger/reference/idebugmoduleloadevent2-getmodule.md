---
title: IDebugModuleLoadEvent2::GetModule |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugModuleLoadEvent2::GetModule
helpviewer_keywords:
- IDebugModuleLoadEvent2::GetModule
ms.assetid: c86482bb-9ce5-4e63-bbe0-969b50169424
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f0a043b3842805357de685484fcc4daf935aefcc
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49906835"
---
# <a name="idebugmoduleloadevent2getmodule"></a>IDebugModuleLoadEvent2::GetModule
取得されているモジュール読み込みまたはアンロードします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetModule(   
   IDebugModule2** pModule,  
   BSTR*           pbstrDebugMessage,  
   BOOL*           pbLoad  
);  
```  
  
```csharp  
int GetModule(   
   out IDebugModule2 pModule,  
   ref string        pbstrDebugMessage,  
   ref int           pbLoad  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pModule`  
 [out]返します、 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)読み込みまたはアンロードされているモジュールを表すオブジェクト。  
  
 `pbstrDebugMessage`  
 [入力、出力]このイベントを説明する省略可能なメッセージが返されます。 このパラメーターが null 値の場合は、メッセージは要求されません。  
  
 `pbLoad`  
 [入力、出力]0 以外の場合 (`TRUE`) モジュールが読み込みと 0 の場合 (`FALSE`) 場合は、モジュールをアンロードしています。 このパラメーターが null 値の場合は、状態は要求されません。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)