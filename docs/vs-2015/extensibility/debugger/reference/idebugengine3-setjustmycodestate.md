---
title: IDebugEngine3::SetJustMyCodeState |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugEngine3::SetJustMyCodeState
helpviewer_keywords:
- IDebugEngine3::SetJustMyCodeState
ms.assetid: 8ec17fbf-df93-424a-b2ed-fd1e5ee51256
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: dc701306166cacc1eb25881fee090c91af069589
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49818030"
---
# <a name="idebugengine3setjustmycodestate"></a>IDebugEngine3::SetJustMyCodeState
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このメソッドは、JustMyCode 状態情報のデバッグ エンジンを指示します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetJustMyCodeState(  
   BOOL           fUpdate,  
   DWORD          dwModules,  
   JMC_CODE_SPEC* rgJMCSpec  
);  
```  
  
```csharp  
int SetJustMyCodeState(  
   int             fUpdate,   
   uint            dwModules,   
   JMC_CODE_SPEC[] rgJMCSpec  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `fUpdate`  
 [in]0 以外の場合 (`TRUE`) 現在の情報を更新するには、0 (`FALSE`) (何も以前の設定は無視されます) すべての情報をリセットします。  
  
 `dwModules`  
 [in]情報構造体の数 `rgJMCSpec.`  
  
 `rgJMCSpec`  
 [in]配列[JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)を使用する構造体。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 JustMyCode をユーザーに属しているコードのみをデバッグして、システム コードなどのすべての中間コードを無視するという概念は、-場合でも、そのシステム コードのソース コードが使用されます。  
  
## <a name="see-also"></a>関連項目  
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)   
 [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)

